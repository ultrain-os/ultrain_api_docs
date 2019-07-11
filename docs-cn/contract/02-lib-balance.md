## 类
超脑TS_lib的BALANCE的类如下所示

| 类                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [CurrencyAccount](docs-cn/ts-lib/02-lib-balance#CurrencyAccount)                          |货币账户类                             |
| [CurrencyStats](docs-cn/ts-lib/02-lib-balance#CurrencyStats)                          |令牌系统的类货币统计                             |


## ArrayMap
货币账户类

## CurrencyStats
令牌系统的类货币统计

## 方法列表
超脑TS_lib的BALANCE所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [queryBalance](docs-cn/ts-lib/02-lib-balance#queryBalance)                           |从ultin token系统查询账户余额                             |


## queryBalance
```
queryBalance(owner: account_name)
```
从ultin token系统查询账户余额

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|owner              |account_name  |要查询的帐户名                     |是     |


#### 参考示例
```nodejs
import { ACTION } from "ultrain-ts-lib/src/action";
```

#### 返回结果类型
[Asset](docs-cn/ts-lib/03-ts-asset#Asset)
