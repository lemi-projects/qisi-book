#商城api
##商品列表
```javascript
request({
url: 'get/query_shop_saling_goods_1603088780',
data:{
    pagefrom:1 //页码
    pagesize:10 //分页大小
    shop_id:1 //商店id
},
}).then((res) => {
    console.log(res)
})
```
##商品详情
```javascript
request({
url: '/get/goods_detail_1603122030', 
data:{
    sale_id:1, //商品id
},
}).then((res) => {
    console.log(res)
})
```
##积分详情列表
```javascript
request({
url: '/get/gain_list_1603448250', 
}).then((res) => {
    console.log(res)
})
```
##用户总积分
```javascript
request({
url: '/get/user_gain_1603448251', 
}).then((res) => {
    console.log(res)
})
```