# 通用框架 common

## 数据集 dataset

* 数据表 .dbs
    - 定义表
      - 表名： 按驼峰命名法取名， 如： UserBase , TeamBase
      - 字段： 小写字母下划线命名法， 如： net_name , post_time
      - 说明： 行末用汉字开始，或 -- 注释符开始， 用于说明字段含义
    - 字段类型
      - 兼容 MySQL 的类型定义之外，增设预定义类型
      - ID 类型: USER-ID, TEAM-ID, TYPE-ID, UINT-ID
      - 时间: TSTAMP, DATE-TM
    - 预设值
      - 将初始记录预先插入表中
    - 标志 `flag`
      - 预定义标志的含义，将被写入表 `LabelMap` 中
    - 类型 `type`
      - 预设分类，名称含义也将被写入 `LabelMap` 中
    - 时间戳 `timestamp`
      - 规定时间记录均为 UNIX-TIMESTAMP 格式，即 INT(10)
  
* 存储过程 .dbx
    - 命名规则： 驼峰命名时，改存储过程将被自动生成为 procedue 接口，可通过 /***SAPI***/proc/***KEY*** 远程调用
    - 如果按小写字母下划线命名法，则**不会**公开成为远程接口
    - 字段的取名，尽量与数据表 .dbs 中的定义保持一致
    - 返回值： 调用 return XXX 
    - 错误退出： 调用 error 'message string'

* 数据定义 .jss
    * 一种类似 JSON 格式的数据描述语法
    * 增加了类型分类
    * 可引用已定义的数据
    * 可方便定义多行字符串
```
    ident <type> {
        propA : {Object}
        propB : [Array]
        propC : "string a"
                "string b"
        propD : ident2
        propE : [ident3, ident4]
    }
```

## 表单集 formset

为了方便地提供数据记录的添加Insert/更新Update的方法，预定义了 `<control>` `<tview>` `<widget>` 三种数据格式

#### 表单控件 `<control>`
举例
```
net_name <control>{
    textedit:{
        fid: net_name
        label: "帐号"
        placeholder: "平台中的帐号标识"
        tips: "4-16 个英文字母"
        validate: "/^[A-Za-z0-9]{4,16}$/"
        rules: [
            { required: true, message: "请输入帐号", trigger: ["blur", "change"] },
            { min: 4, max: 16, message: "长度在 4 到 16 个字符", trigger: ["blur", "change"] }
        ]        
    }
}
```
说明

    net_name 为数据对象ID名
    textedit 为所用VUE组件
    {
        VUE 组件的属性数据
    }
    默认情况下 VUE 组件属性 fid 与数据对象名称相同，也可以直接指定 fid 的值，如：

```
that_user_id <control> {
    textedit:{
        fid: "user_id"
        --------------
        label: "UID"
        placeholder: "用户的ID号"
        validate: "/^\d+$/"
        rules: [
            { required: true, message: "请输入用户ID", trigger: ["blur", "change"] },
        ]        
    }    
}
```    

[预定义的 VUE 表单组件](./form-control.md)
* textedit
* textarea
* select-ls
* radio-ls
* readonly
* hidden-ls
* html-editor
* password
* pick-date
* pick-thumb

#### 列表视图 `<tview>`
举例
```
users <tview> {
    sql:
        "SELECT user_id, net_name, rel_name, nick, alias, sex, birthday, email, brief"
        "FROM UserBase"
        "WHERE user_id>2 ORDER BY user_id DESC"

    args: ["pagesize", "pagefrom"]

    columns: {
        user_id: "UID"
        net_name: "帐号"
        rel_name: rel_name
        nick: nick
        alias: alias
        sex: sex
        birthday: birthday
        email: email
        brief: user_brief
    }

    updates: [
        {
            table: UserBase
            fields: [rel_name, nick, alias, sex, birthday, email, brief]
            refer: {
                user_id: ":user_id"
            }
        }
    ]

    fsearch: [net_name, rel_name, nick]
}
```
说明

    sql 数据库查询语句
    args 查询参数， pagesize 每页记录数，pagefrom 显示页 (base 1)
    columns 列表显示字段，当指定字段为 `<control>` 格式时，数据更新表单中会按该组件方式提供编辑
    updates 数据更新描述，可以有多个数据更新

        table 需要更新的表名
        fields 需要更新的字段， 对应于网络请求request中需填写的参数，
             与 columns 中的 `<control>` 字段一一对应
        refer 引用字段，即在 Update 语句中 WHERE 子句的条件限定，上例中为 user_id,
             :user_id 表示为网络请求 request 中的变量值

    fsearch 用于缺省情况下模糊查询 （fuzzy search：filed like %keywords%） 的字段

列表视图，可以配合VUE组件 TableView/TableEdit 用于数据查看和编辑，同时在服务器端有对应的调用接口（存在 /api/tview.php中）

#### 表单部件 `<widget>`
举例
```
new_account <widget> {
    tmpl: sForm
    form: [rel_name, nick, net_name, password, user_id]
    
    inserts:[
        {
            table: UserBase
            fields: [rel_name, nick, net_name, password]
            extras: [reg_time]
            handle: [user_id]
            unless: { user_id: 0 }
        }
    ]
}
```
说明

    new_account 部件名称
    tmpl    所用的模板文件名
    form    表单中包含的 `<control>` VUE表单组件
    inserts 数据插入描述，可以有多个数据插入

        table 需要插入的表名
        fields 需要插入的字段， 对应于网络请求request中需填写的参数，
        extras 额外的插入字段，如用于插入服务器当前时间的字段
        handle 结合 unless 使用
            当 unless 中的字段值为true，如上例中 user_id=0 时，则插入数据 insert
                插入数据的 last_insert_id 将赋值给 handle 中的 user_id
            否则，以 handle 中的字段为查询条件，进行数据更新 update

表单部件会自动生成同名的 vue 组件，同时也会在服务器端有对应的调用接口（存在 /api/tform.php中）

#### 数据校验 validate

js 模块文件
``` javascript
module.exports = {
    'net_name':{type:'string', validate:'/^[A-Za-z0-9]{3,15}$/'},
    'password':{type:'string', validate:'/^\\w{3,32}$/'},
    'nick':{type:'string', validate:'/^[A-Za-z\\x{4e00}-\\x{9fa5}]{2,16}$/u'},
}
```
用于嵌入到服务器端网络请求 request 时进行参数数据校验

## 模块集 modules
举例
```
manager_list <module> {
    tmpl: vueModuleEx
    components:[
        {
            vue: TableEdit
            data: {
                viewData: managers
                args: {
                    pagesize: 5
                    pagefrom: 0
                }
            }
        }
    ]
}

manager_add <module> {
    tmpl: vueModule
    components:[
        {
            widget: new_manager
            data: {
                formData: {}
                submit: {
                    label: "提交"
                    keyId: "new_manager"
                    refresh: [ManagerList, ManagerAdd]
                }                
            }        
        }
    ]
}
```
说明

    user_list 模块名
    tmpl    所用的模板文件
    componets   子组件
        vue / widget  所用的 VUE 组件名，vue 组件名需在 comps.jss 文件中有定义
        data 组件所用的数据，对应于 vue 定义的 props

            submit 表单提交按钮
                keyId 服务器端接口key
                refresh 指在表单提交后，数据返回成功后，需自动刷新同一页面中的模块名

模块会自动生成对应的 VUE 组件，并将名称自动改为驼峰命名方式

## 页面集 pages
举例
```
g_super <group> {
    path: '/super'
    redirect: '/'
    alwaysShow: true
    name: 'super'
    title: "平台管理"
    icon: "el-icon-s-help"
}

set_manager <page> {
    group: g_super
    title: "设管理员"
    permission: [ admin, super ]
    tmpl: pageVue
    modules: [
        {   
            title: "管理员列表"
            id: manager_list
            col: 14
        }
        {
            title: "新增管理员"
            id: manager_add
            col: 10
        }
    ]
}
```
说明

页面 page 会涉及三个方面：
1. 页面导航 routers
   * <group> 是菜单导航的分组
2. 模块及布局 modules
   * set_manager 页面名称
   * group   所属导航分组
   * title   页面标题
   * permission 页面可访问角色
   * tmpl    所用的模板文件名
   * modules 包含的模块，可以为多个模块
       - title   模块名称
       - id      模块id， 需在 modules 中有定义
       - col     布局占用列宽，fix 布局，一行分为24格

3. 权限设置 permission


### 权限设置 permission
举例
```
xiaoqu <permission> {
    team: xiaoqu
    text: "小区"
    role: leader
}
```
说明

    xiaoqu 角色名称
    team    对应的组织类型名称，在 TeamType 表中有记录
    text    文字标签
    role    角色名称， 在 TeamRole 表中有记录



