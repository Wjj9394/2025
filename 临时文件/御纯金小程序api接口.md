# 测试环境：https://d52b257212.goho.co/czzb/



## /小程序订单推送ERP 

#### 接口URL

> /pickGoods/send

#### 请求方式

> POST

#### Content-Type

> json

#### 请求Body参数

```javascript
{
    "pickGoods": {
        "custName": "安港珠宝",
        "fineness":"足金999",
        "outDate1" : "2023-11-20",
        "outDate2" : "2023-11-26",
        "oprtNo" : "硬金打砂-黄家金",
        "keyin" : "字印",
        "remark" : "备注",
        "oriOrderNo": "NO0015",
        "username":"明天L"
    },
    "pickGoodsDtls": [
        {
            "styleNo": "YPJ1601",
            "qty": 100
        },
        {
            "styleNo": "YPJ1600",
            "qty": 100
        },
        {
            "styleNo": "YPJ1602",
            "qty": 100
        },
        {
            "styleNo": "YPJ1603",
            "qty": 100
        },
        {
            "styleNo": "YPJ1604",
            "qty": 20
        }
    ]
}
```

| 参数名 | 示例值 | 参数类型 | 是否必填 | 参数描述 |
| --- | --- | ---- | ---- | ---- |
| pickGoods | - | Object | 是 | json对象 |
| pickGoods.custName | 安港珠宝 | String | 是 | 客户名称 |
| pickGoods.fineness | - | String | 否 | 金成色 |
| pickGoods.outDate1 | - | String | 否 | 出货日期1 |
| pickGoods.outDate2 | - | String | 否 | 出货日期2 |
| pickGoods.oprtNo | 业务员 | String | 否 | 业务员名称 |
| pickGoods.keyin | 字印 | String | 否 | 字印 |
| pickGoods.remark | 备注 | String | 否 | 备注 |
| pickGoods.oriOrderNo | NO0011 | String | 是 | 订单号 |
| pickGoods.username | 明天L | String | 是 | 注册账号 |
| pickGoodsDtls | - | Array | 是 | json对象数组 |
| pickGoodsDtls.styleNo | YPJ1601 | String | 是 | 款式编号 |
| pickGoodsDtls.qty | 100 | Integer | 是 | 下单数量，必须大于0 |

#### 

#### 成功响应示例

```javascript
{"msg":"操作成功","code":200}
```

| 参数名 | 示例值 | 参数类型 | 参数描述 |
| --- | --- | ---- | ---- |
| msg | 操作成功 | String | 消息： 必有 |
| code | 200 | Integer | 响应码： 200 ：成功，其它：失败 |

#### 错误响应示例

```javascript
{"msg":"订单号已存在，不能再次推送","code":500}
```

| 参数名 | 示例值 | 参数类型 | 参数描述 |
| --- | --- | ---- | ---- |
| msg | 订单号已存在，不能再次推送 | String | 消息： 必有 |
| code | 500 | Integer | 响应码： 200 ：成功，其它：失败， 必有 |



## /小程序查询ERP款式库存

#### 接口URL

> /pickGoods/style/stock

#### 请求方式

> POST

#### Content-Type

> json

#### 请求Body参数

```javascript
{
    "styleNos": [
        "MF004"
    ]
}
```

| 参数名   | 示例值 | 参数类型      | 是否必填 | 参数描述     |
| -------- | ------ | ------------- | -------- | ------------ |
| styleNos | -      | Array<String> | 否       | 款式编号数组 |


#### 成功响应示例

```javascript
{
    "msg": "操作成功",
    "code": 200,
    "data": [
        {
            "style_no": "MF004",
            "stock_qty": 30
        }
    ]
}
```

| 参数名         | 示例值   | 参数类型 | 参数描述                                   |
| -------------- | -------- | -------- | ------------------------------------------ |
| msg            | 操作成功 | String   | 消息： 必有                                |
| code           | 200      | Integer  | 响应码： 200 ：成功，其它：失败            |
| data           | -        | Array    | 响应返回的对象,,当查不到数据时，返回空数组 |
| data.style_no  |          | String   | 款式编号                                   |
| data.stock_qty | 0        | Integer  | 库存件数                                   |
| data.stock_wgt | 106      | Double   | 库存金重                        |
| data.pic_url   |          | String   | 图片链接                        |


#### 错误响应示例

```javascript
{
    "msg": "操作成功",
    "code": 200,
    "data": []
}
```

| 参数名 | 示例值   | 参数类型 | 参数描述                                  |
| ------ | -------- | -------- | ----------------------------------------- |
| msg    | 操作成功 | String   | 消息： 必有                               |
| code   | 200      | Integer  | 响应码： 200 ：成功，其它：失败           |
| data   | -        | Array    | 响应返回的对象,当查不到数据时，返回空数组 |



 
## /小程序取消订单，推送给ERP同步订单状态

#### 接口URL

> /pickGoods/cancel

#### 请求方式

> POST

#### Content-Type

> json

#### 请求Body参数

```javascript
{
  "oriOrderNo": "",
  "remark": ""
}
```

| 参数名     | 示例值 | 参数类型 | 参数描述      |
| ---------- | ------ | -------- | ------------- |
| oriOrderNo |        | String   | 订单号： 必传 |
| remark     |        | String   | 备注：非必传  |

#### 成功响应示例

```javascript
{
    "msg": "操作成功",
    "code": 200
}
```

| 参数名 | 示例值   | 参数类型 | 参数描述                        |
| ------ | -------- | -------- | ------------------------------- |
| msg    | 操作成功 | String   | 消息： 必有                     |
| code   | 200      | Integer  | 响应码： 200 ：成功，其它：失败 |

#### 错误响应示例

```javascript
{
  "msg": "推送失败，订单号不存在。",
  "code": 500
}
```

| 参数名 | 示例值   | 参数类型 | 参数描述                        |
| ------ | -------- | -------- | ------------------------------- |
| msg    | 操作成功 | String   | 消息： 必有                     |
| code   | 500      | Integer  | 响应码： 200 ：成功，其它：失败 |




小程序提供接口：

1.标记订单状态接口 post请求
/app/markOrderStatus
入参：
oriOrderNo：订单号
orderSatus：状态值 （1：已处理 2：已发货）

2.ERP款式库存数发生变动推送接口 post请求
/goldshop/app/pushStocks
{
    "pickGoodsDtls": [
     {
         "styleNo": "123",
         "stockQty": 1
     }
    ]
}
styleNo：款号
stockQty：更新库存数








