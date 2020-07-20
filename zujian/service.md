# 模块组件 service 
   * Grid 宫格
   > 宫格可以在水平方向上把页面分隔成等宽度的区块，用于展示内容或进行页面导航
    
```
基本用法
通过icon属性设置格子内的图标，text属性设置文字内容

<van-grid>
  <van-grid-item icon="photo-o" text="文字" />
  <van-grid-item icon="photo-o" text="文字" />
  <van-grid-item icon="photo-o" text="文字" />
  <van-grid-item icon="photo-o" text="文字" />
</van-grid>
```
    
```
自定义列数
默认一行展示四个格子，可以通过column-num自定义列数

<van-grid column-num="3">
  <van-grid-item icon="photo-o" text="文字" wx:for="{{ 6 }}" />
</van-grid>
```
   * IndexBar 索引栏
   * Sidebar 侧边导航
   * NavBar 导航栏
   * Tabbar 标签栏     
   * Login 登录模块
   * Search 搜索模块
   * RichText 图文模块
   * Voice 语音模块
   * Video 视频模块
   * Share 分享模块
   * Area 省市区选择
   * Card 商品卡片
   * SubmitBar 提交订单栏
   * GoodsAction 商品导航
   * AD 广告播放
   

   
   
    
