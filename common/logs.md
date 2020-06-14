# 记录 logs

## 用户行为定义

```
ActionBase {
    action_id      UINT-ID defautl auto     行为id
    descript       VARCHAR(200)             描述
    score          MEDIUMINT(10) default 0  积分  行为对应的积分增加或扣减  

    primary key (action_id)
}
```

## 用户的行为记录

## 成员的行为记录
