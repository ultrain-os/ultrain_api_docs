## 类
超脑TS_lib的ACCOUNT的类如下所示

| 类                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [Account](docs-cn/ts-lib/01-ts-account#Account)                          | 类帐户代表帐户名，它包装操作余额的方法。                             |

## Account
类帐户代表帐户名，它包装操作余额的方法。

#### 使用示例
```nodejs
import { Account } from "ultrain-ts-lib/src/account";
```

## 方法列表
超脑TS_lib的ACCOUNT所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [ACCOUNT](docs-cn/ts-lib/01-ts-account#ACCOUNT)                          |将字符串转换为类帐户                              |
| [NAME](docs-cn/ts-lib/01-ts-account#NAME)                                |将字符串转换为帐户名，即U64                              |
| [RNAME](docs-cn/ts-lib/01-ts-account#RNAME)                              |将帐户名转换为字符串                              |

## ACCOUNT
```
(static) ACCOUNT(str)
```
将字符串转换为类帐户

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|str              |string  |要转化为账户的字符串                     |是     |


#### 参考示例
```nodejs
import { ACCOUNT } from "ultrain-ts-lib/src/account";
 let ceo = ACCOUNT("jack.ma");
 let employ = ACCOUNT("miny");
 ceo.transfer(employ.code, "1000.000 UGS", "your annual award.");
```


#### 返回结果类型
[`Account`](docs-cn/ts-lib/01-ts-account#Account)


## NAME
```
(static) NAME(str)
```
将字符串转换为帐户名，即U64

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|str              |string  |要转化为账户的字符串                     |是     |


#### 参考示例
```nodejs
import { NAME } from "ultrain-ts-lib/src/account";
```

#### 返回结果类型
`account_name`


## RNAME
```
(static) RNAME(code)
```
将账户名转换为字符串

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|code              |string  |要转换为字符串的帐户名的值                     |是     |


#### 参考示例
```nodejs
import { RNAME } from "ultrain-ts-lib/src/account";
```

#### 返回结果类型
`string`
