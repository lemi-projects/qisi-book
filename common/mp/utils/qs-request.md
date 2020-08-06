# qs-request.js
uni小程序网络访问工具 封装了uni.request功能

返回promise对象

## 使用
```
import request from '@/utils/qs-request.js'

request(param)
```

## 参数说明
```
 param:{
  url: String //必填 接口地址
  method: String //选填 http方法 默认GET 要求全大写
  data: Object //选填 传给接口的数据
 }
```

