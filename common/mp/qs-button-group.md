# qs-button-group.md
嵌入到页面中显示按钮集合，可用用在商品分类，功能入口等

## 效果
每行最多显示四个按钮，每个平均分配空间

超过四个会新增一行，每行有空位的时候居左对齐

每个按钮上下布局，包括上面一张图片，下面一行说明

## 引入
`
import qsButtonGroup from '../../components/qs-button-group/index'
`

## 属性
```
export default {
    props: {
        isRound: Boolean, //是否圆形图标 不传为方形
        isShadow: Boolean, //是否有阴影效果
        url: String, //点击后跳转的目标页面
        data: Array,
        /*
        data: [{
            param: 1001, //传给目标页面的参数
            label: '环球美食', //按钮文字
            image: 'https://', //按钮图标url
        },]
        */
    },
```

