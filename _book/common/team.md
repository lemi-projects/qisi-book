# 组织 team

## 组织类型 TeamType

- 系统预设的类型
  - `system (type=0)` 系统管理，具有最高权限，可创建*平台运营*组
  - `manage (type=1)` 平台运营，可创建定义其他的组织类型
  

> 整个系统只有一个系统管理组，有一个或多个平台运营组

## 组织角色 TeamRole

```
<team_role>
{
    0 = "待加入"  
    1 = "创建人"  creator / owner
    2 = "负责人"  leader
    3 = "成员"    member
}
```

不同的组织类型，成员角色可以进一步拓展，role 取值 >= 3

  > 创建新的组织类型，并定义角色名称

  > dataset/jss/team.jss
```
test <team> {
    text: "测试组"
    roles: {
        leader: "主程"
        member: "测试"
    }
} 
```


## 组织成员 TeamMember

> 系统自动创建的组织，`创建人`不一定是`成员`，用户创建的组织，该用户即为`负责人`

- 申请待加入
- 状态
- 等级

## 创建 create
## 成员管理 manage
