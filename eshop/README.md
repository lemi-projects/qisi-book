# 电商框架 eshop

## 商品信息 `GoodsBase`

 `goods_id` 商品ID

用于存放商品的基本信息

## 销售的商品 `SaleGoods`

`sale_id` 销售货号
`shop_id` `goods_id`

对应的商品信息，只能由商家修改

当有订单产生时，需对商品信息进行存档


## 售卖存档 `SaleArchive`

销售商品信息的存档, 当商品信息有对应的订单时存档（以防更改）

`archive_id` 存档号
`sale_id`   销售货号


