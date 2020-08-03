# swiper.md
轮播图组件

## 效果
用来展示轮播图。

## 引入
`import buttonGroup from '/components/qs-swiper/index`

## 属性
```
props: {
    props: 
    {
        page: String, //点击跳转页
        indicatorDots: Boolean, //是否显示指示器
        interval: Number, //轮换时间间隔
        autoPlay: Boolean, //是否自动播放
        pList: Array, 
            [
                param: Object, //点击传递参数
                image: 'https://ckfhq.oss-cn-beijing.aliyuncs.com/mp20/demo/images/sw1.jpg',
            ]
    },
},
```

