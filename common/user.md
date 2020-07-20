# 用户 user

### 注册 regist

### 登录 login

### 退出 logout

### 个人资料 profile

* 头像 avatar
* 名称 
  * 姓名 rel_name   真实姓名
  * 昵称 nick       中文名
  * 别称 alias      英文名
* 手机 m_phone
* 邮箱 email
* 地址 address
* 认证 Certification

### 预定义角色 ###

  * `admin` 系统管理员
    * 系统管理权限
  * `super` 平台管理员
    * 平台管理权限
      * 初始化业务平台
      * 增加/修改管理员 `manager`
      * 查询/修改用户信息  
      * 重置用户密码
      * 查询/修改组织信息
      * 查询/修改发布信息
      * 查询/修改展示信息
  * `manager` 业务管理员
    * 业务管理权限
      * 增加/修改业务主管 `leader`
