# qs-swiper.md
轮播图组件

## 效果
用来展示轮播图

## 引入
`
import buttonGroup from '../../components/qs-swiper/index
`

## 属性
```
props: {
    size: String, //轮播组件大小 (small || medium || large)
    isPadding: Boolean, //轮播图是否保留边距
    isCorner: Boolean, //轮播图是否显示圆角
    isIndicator: Boolean, //是否显示指示器
    interval: Number, //每页停留毫秒时长
    page: String, //目标页面地址
    data: Array,
    /*
    [{
        param: 1001, //传给目标页面的参数
        image: 'https://', //轮播图片地址
    },]
    */
},
```

