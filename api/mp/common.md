#通用模块api
##获取点赞数量
```javascript
url: '/get/post_action_1602245717',
data: {
    post_id: 1, //post_id
},
```
##设置点赞 & 收藏 & 转发
```javascript
request({
    url: '/proc/SetPostAction1603594782', 
    data: {
        post_id: 1, //关联文章，公告的id
        // flag使用位操作，执行的操作对应下面值，多个用|取值
        // 1 = "点赞" 2 = "收藏" 4 = "转发"
        flag: 1,
        action: 1 //0 = "正常" 1 = "取消"
    },
}).then((res) => {
    console.log(res)
})
```

