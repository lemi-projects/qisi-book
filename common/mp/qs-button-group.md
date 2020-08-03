# buttonGroup.md
用来嵌入到页面中显示按钮集合，可用来商品分类，功能入口等。

## 效果
每行最多支持四个按钮显示，每个按钮平均分配空间

超过四个会新增一行，每行有空位的时候居左对齐

每个按钮上下布局，上面一张图片，下面一行标题

## 引入
`import buttonGroup from '/components/qs-button-group/index`

## 属性
```
props: {
    pRadiusType: 'round | square' //显示正方形或者正圆形图标
    pUri: '目标页面'
    pList: 
        [{
            param: '转发到目标页面的参数',
            title: '图标文字',
            image: '图标url',
            },
            ...
       ]
},
```

