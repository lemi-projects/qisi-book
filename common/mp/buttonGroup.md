# buttonGroup.md
用来嵌入到页面中显示按钮集合，可用来商品分类，功能入口等。

## 效果
每行最多支持四个按钮显示，每个按钮平均分配空间，超过四个会新增一行，每行有空位的时候居左对齐。
每个按钮上下布局，上面一张图片，下面一行标题。

## 引入
`import buttonGroup from '/components/buttonGroup/index`

## 传值
```
props: {
    pParam: Object, //给目标页面传递的参数，直接转给目标页面
    pUri: String, //目标页面路径
    pList: Array, //按钮组数据
},
```

### pList数据格式
```
pList:[{
    id: 分类数据id,
    title: '标题',
    image: '分类图片网络地址',
    },
    ...
]
```

