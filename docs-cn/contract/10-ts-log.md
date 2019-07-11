## 类
超脑TS_lib的LOG的类如下所示

| 类                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [Logger](docs-cn/ts-lib/10-ts-log#Logger)                          |类记录器提供了在调用函数“flush”后立即将日志打印到控制台的API                             |


## Logger
类记录器提供了在调用函数“flush”后立即将日志打印到控制台的API


## 方法列表
超脑TS_lib的LOG所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [Log](docs-cn/ts-lib/10-ts-log#Log)                           |记录器的全局变量。同时只有一个日志对象。这是@class logger的全局实例                              |


## Log
```
Log: Logger = new Logger()
```
记录器的全局变量。同时只有一个日志对象。这是@class logger的全局实例


#### 参考示例
```nodejs
import { Log } from "ultrain-ts-lib/src/log";
```