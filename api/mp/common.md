#通用模块api
##文章详情

##用户点击点赞 & 收藏 & 转发
```javascript
request({
    url: '/proc/SetPostAction1603594782', 
    data: {
        post_id: 1, //关联文章，公告的id
        /*
            flag使用位操作，执行的三种操作相加作为值
            初始化时用&判断是否对应选择
            1 = "点赞" 2 = "收藏" 4 = "转发"
        */
        flag: 1,
        action: 1 //0 = "正常" 1 = "取消"
    },
}).then((res) => {
    console.log(res)
})
```

