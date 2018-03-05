# 通用支付模块调用

## McPopPay 支付模块
> 通过调用 `McPopPay` 初始化支付模块

支付模块包括 `微信支付` `支付宝支付` `账户支付`(余额支付) `其他支付`(自定义扩展)

#### 微信支付
自动判断 h5 环境还是 app 环境 分别调用 移动端微信支付 以及 app微信支付

#### 支付宝支付
跳转支付宝网页支付页面, 待优化(在微信浏览器中体验较差)

#### 账户支付（余额支付）
在带有余额的系统中使用用户账户余额支付

#### 其他支付
因为支付是个弹出的 ActionSheet 所以要集成按钮到 ActionSheet中
> 该项为一个数组，可传入多个其他支付

---

### 1. 初始化

每种支付支付模块都分为支付开关，以及该支付配置项

#### 微信支付（网页端）

`WeChatPay` 微信支付模块开关
参数 | 说明 | 类型 | 可选值 | 默认值
-|-|-|-|-|-
WeChatPay | 是否有微信支付 | Bool | - | true

`WeChatPayConfig` 微信支付配置项

配置项参数
参数 | 说明 | 类型 | 可选值 | 默认值
-|-|-|-|-|-
api | 是否Api请求 | Bool | - | true
url | 请求地址 | String | - | null
data | 请求参数 | Object | - | 空对象
text | 按钮文本 | String | - | 微信支付
clickCallback | 按钮点击回调 | Function | - | null
paySuccess | 支付成功回调 | Function | - | null
success | 请求成功回调 | Function | - | 空函数
fail | 请求失败回调 | Function | - | 空函数
beforeSend | 请求发送前回调 | Function | - | 空函数

**`示例`** 仅初始化微信支付

因为 `WeChatPay` 参数默认 true, 直接传入配置项即可

```js
// 初始化支付
var simplePay = new McPopPay({
  WeChatPayConfig: {
    api: false,
    url: '/PayCommon/WechatPay',
    data: {
      OrderCode: code // 订单号
    },
    paySuccess: function () {
        showTip('支付成功')
    }
  },
  WeChatAppPay: false,
  AliPay: false,
  AccountPay: false
})
```

---

#### 微信支付（app端）

`WeChatAppPay` 微信支付模块开关

参数 | 说明 | 类型 | 可选值 | 默认值
-|-|-|-|-|-
WeChatAppPay | 是否有微信支付 | Bool | - | true

`WeChatAppPayConfig` 微信支付配置项

配置项参数

参数 | 说明 | 类型 | 可选值 | 默认值
-|-|-|-|-|-
api | 是否Api请求 | Bool | - | true
url | 请求地址 | String | - | null
data | 请求参数 | Object | - | 空对象
text | 按钮文本 | String | - | 微信支付
clickCallback | 按钮点击回调 | Function | - | null
paySuccess | 支付成功回调 | Function | - | null
success | 请求成功回调 | Function | - | 空函数
fail | 请求失败回调 | Function | - | 空函数
beforeSend | 请求发送前回调 | Function | - | 空函数

**`示例`** 仅初始化微信支付

因为 `WeChatAppPay` 参数默认 true, 直接传入配置项即可

```js
// 初始化支付
var simplePay = new McPopPay({
  WeChatPay: false,
  WeChatAppPayConfig: {
    api: false,
    url: '/PayCommon/WechatAppPay',
    data: {
      OrderCode: code // 订单号
    },
    paySuccess: function () {
        showTip('支付成功')
    }
  },
  AliPay: false,
  AccountPay: false
})
```

---

#### 支付宝支付

`AliPay` 支付宝支付模块开关

参数 | 说明 | 类型 | 可选值 | 默认值
-|-|-|-|-|-
AliPay | 是否有支付宝支付 | Bool | - | true

`AliPayConfig` 支付宝支付配置项

配置项参数

参数 | 说明 | 类型 | 可选值 | 默认值
-|-|-|-|-|-
url | 请求地址 | String | - | null
data | 请求参数 | Object | - | 空对象
text | 按钮文本 | String | - | 支付宝支付
clickCallback | 按钮点击回调 | Function | - | null

**`示例`** 仅初始化支付宝支付

因为 `AliPay` 参数默认 true, 直接传入配置项即可

```js
// 初始化支付
var simplePay = new McPopPay({
  WeChatPay: false,
  WeChatAppPay: false,
  AliPayConfig: {
    url: '/PayCommon/AlipayPay',
    data: {
      OrderCode: code // 订单号
    }
  },
  AccountPay: false
})
```

#### 账户支付（余额支付）

`AccountPay` 账户支付模块开关

参数 | 说明 | 类型 | 可选值 | 默认值
-|-|-|-|-|-
AccountPay | 是否有账户支付 | Bool | - | true

`AccountPayConfig` 账户支付配置项

配置项参数

参数 | 说明 | 类型 | 可选值 | 默认值
-|-|-|-|-|-
api | 是否Api请求 | Bool | - | true
url | 请求地址 | String | - | null
data | 请求参数 | Object | - | 空对象
text | 按钮文本 | String | - | 余额支付
nowBalance | 当前余额 | Number | - | 0
clickCallback | 按钮点击回调 | Function | - | null
paySuccess | 支付成功回调 | Function | - | null
success | 请求成功回调 | Function | - | 空函数
fail | 请求失败回调 | Function | - | 空函数
beforeSend | 请求发送前回调 | Function | - | 空函数

**`示例`** 仅初始化账户支付

因为 `AccountPay` 参数默认 true, 直接传入配置项即可

```js
// 初始化支付
var simplePay = new McPopPay({
  WeChatPay: false,
  WeChatAppPay: false,
  AliPay: false,
  AccountPay: {
    api: false,
    url: '/PayCommon/AccountPayPay',
    data: {
      OrderCode: code // 订单号
    },
    paySuccess: function () {
        showTip('支付成功')
    }
  }
})
```

---

#### 其他支付

`OtherPay` 其他支付模块开关

参数 | 说明 | 类型 | 可选值 | 默认值
-|-|-|-|-|-
OtherPay | 是否有其他支付 | Bool | - | false

`OtherPayConfig` 账户支付配置项

配置项为数组

每一项可选参数

参数 | 说明 | 类型 | 可选值 | 默认值
-|-|-|-|-|-
text | 按钮文本 | String | - | 其他支付
nowBalance | 当前余额, 可选, 传了就显示余额 | Number | - | 0
clickCallback | 按钮点击回调 | Function | - | null
hasPayPwd | 支付成功回调 | Bool | - | false
pay | 支付调用函数 | Function | - | null

