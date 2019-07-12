## 类
超脑TS_lib的ACTION的类如下所示

| 类                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [Action](docs-cn/contract/02-ts-action#Action类)                          | 类操作用于访问操作的上下文信息。这个类是静态的。                             |
| [ActionImpl](docs-cn/contract/02-ts-action#ActionImpl)                          | 类actionimpl代表真正的action结构                             |
| [PermissionLevel](docs-cn/contract/02-ts-action#PermissionLevel)                          | 类transferParams用于将代币从一个帐户传输到另一个帐户                             |
| [NameEx](docs-cn/contract/02-ts-action#NameEx)                          |权限级别代表“-p”参数。例如，permissionLevel（n（“tom”）、n（“active”）等于“-p tom@active”                            |
| [TransferParams](docs-cn/contract/02-ts-action#TransferParams)                          | 类nameex用于存储21个字符的名称，方法nex将包含“.0123456789abcdefghijklmnopqrstuvwxyzabedefghijklmnopqrstuvwxyz”的字符串转换为nameex。例如，actionname是nameex的一个入口                             |

## Action类
类操作用于访问操作的上下文信息。这个类是静态的。

#### 使用示例
```nodejs
import { Action } from "ultrain-contract/src/action";
```

## ActionImpl
类actionimpl代表真正的action结构

#### 使用示例
```nodejs
import { ActionImpl } from "ultrain-contract/src/action";
```

## PermissionLevel
权限级别代表“-p”参数。例如，permissionLevel（n（“tom”）、n（“active”）等于“-p tom@active”


## NameEx
类nameex用于存储21个字符的名称，方法nex将包含“.0123456789abcdefghijklmnopqrstuvwxyzabedefghijklmnopqrstuvwxyz”的字符串转换为nameex。例如，actionname是nameex的一个入口。


## TransferParams
类transferParams用于将代币从一个帐户传输到另一个帐户

#### 使用示例
```nodejs
import { TransferParams } from "ultrain-contract/src/action";
```

## 方法列表
超脑TS_lib的ACTION所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [ACTION](docs-cn/contract/02-ts-action#ACTION)                           |将字符串转换为action                              |
| [SerializableToArray](docs-cn/contract/02-ts-action#SerializableToArray)                           |将可序列化数字转变为u8数组                             |
| [composeActionData](docs-cn/contract/02-ts-action#composeActionData)                           |类actionimpl代表真正的action结构                              |


## ACTION
```
(static) ACTION(str)
```
将字符串转换为action

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|str              |string  |操作名的可读字符串。只能包括：_0-9a-zA-Z                     |是     |


#### 参考示例
```nodejs
import { ACTION } from "ultrain-contract/src/action";
```

#### 返回结果类型
[`Action`](docs-cn/contract/01-ts-account#Action类)

## SerializableToArray
```
SerializableToArray<T>(dt: T)
```
将可序列化参数转变为u8数组

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|T              |  |可序列化参数                    |是     |


#### 返回结果类型
`u8[]`

## composeActionData
```
composeActionData<T>(pl: PermissionLevel[], receiver: account_name, action: NameEx, data: T)
```
类actionimpl代表真正的action结构 

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|pl                |PermissionLevel|[PermissionLevel](docs-cn/contract/02-ts-action#PermissionLevel)                     |是     |
|account_name      |string  |                     |是     |
|action            |NameEx  |[NameEx](docs-cn/contract/02-ts-action#NameEx)                     |是     |
|data              |T       |可序列化的参数                    |是     |

#### 返回结果类型
`DataStream`
