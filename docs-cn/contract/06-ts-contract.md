## 类
超脑TS_lib的CONTRACT的类如下所示

| 类                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [Contract](docs-cn/contract/06-ts-contract#Contract)                          |它是任何可执行合同的基类，每个具体合同都应该扩展类合同                             |

## Contract
它是任何可执行合同的基类，每个具体合同都应该扩展类合同

#### 使用示例
```nodejs
import { Contract } from "ultrain-ts-lib/src/contract";
```

## 方法列表
超脑TS_lib的CONTRACT所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [DataStreamFromCurrentAction](docs-cn/contract/06-ts-contract#DataStreamFromCurrentAction)                           |获取当前操作的数据流                              |


## DataStreamFromCurrentAction
```
DataStreamFromCurrentAction()
```
获取当前操作的数据流


#### 参考示例
```nodejs
import { DataStreamFromCurrentAction } from "ultrain-ts-lib/src/contract";
```

#### 返回结果类型
`DataStream`

