# 组织关系 orgnize

### 按行政级别划分上下级

* 市级      `shiji`
* 区级      `quji`
* 镇街      `zhenjie`
* 社区      `shequ`
* 居委会    `juweihui`
* 小区      `xiaoqu`
* 楼宇      `louyu`
    
#### 初始化 

由 `super` 创建，预先初始化 镇街/社区/居委会/小区 的上下级关系，后续不可轻易修改

> shequ_init



### 管理员 `manager `

由 `super` 创建帐号，为每个镇街配备一个管理员 `manager`。

初始时，该镇街所含的社区及小区的所有者`owner` ，为该镇街管理员，管理员可进一步指定相应社区/小区的主管 `leader`