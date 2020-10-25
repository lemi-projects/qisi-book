#小程序接口
##request
小程序的请求统一封装在request.js文件，不同的请求只需要替换掉url和data部分，详见具体章节
```javascript
import request from '@utils/request'

request({
    url: '/url',
    data: {
        id: 1, //需要的参数用key:value包装在data对象里
    },
    method: 'POST' //默认可不填
}).then((res) => {
    console.log(res) //解析response
})
```