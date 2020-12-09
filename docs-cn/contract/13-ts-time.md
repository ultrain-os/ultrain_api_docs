## 类
链化未来TS_lib的DBMANAGER的类如下所示

| 类                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [BlockTimestamp](docs-cn/contract/13-ts-time#BlockTimestamp)                          |块时间戳类                           |
| [GmtTime](docs-cn/contract/13-ts-time#GmtTime)                          |gmt time代表格林威治时间                           |
| [LocalTime](docs-cn/contract/13-ts-time#LocalTime)                          |类localtime表示根据特定时区的日历时间                           |
| [Microseconds](docs-cn/contract/13-ts-time#Microseconds)                          |微秒                          |
| [TimePoint](docs-cn/contract/13-ts-time#TimePoint)                          |时间点                           |
| [TimePointSec](docs-cn/contract/13-ts-time#TimePointSec)                          |时间点秒                           |
| [TimeUtil](docs-cn/contract/13-ts-time#TimeUtil)                          |类TimeUtil提供了将UTC时间字符串转换为LocalTime和gmttime的工具                           |
| [TimeZone](docs-cn/contract/13-ts-time#TimeZone)                          |时区                           |


## BlockTimestamp
块时间戳类

## GmtTime
gmt time代表格林威治时间

#### 参考示例
```nodejs
import { GmtTime } from "ultrain-ts-lib/src/time;"
```

## LocalTime
类localtime表示根据特定时区的日历时间

#### 参考示例
```nodejs
import { LocalTime } from "ultrain-ts-lib/src/time;"
```

## Microseconds
微秒

## TimePoint
时间点

## TimePointSec
时间点秒

## TimeUtil
类TimeUtil提供了将UTC时间字符串转换为LocalTime和gmttime的工具

#### 参考示例
```nodejs
import { TimeUtil } from "ultrain-ts-lib/src/time;"
```

## TimeZone
时区

## 方法列表
链化未来TS_lib的DBMANAGER所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [days](docs-cn/contract/13-ts-time#days)                           |获取日期                              |
| [getDaysOfMonth](docs-cn/contract/13-ts-time#getDaysOfMonth)                           |获取每月的天数                              |
| [hours](docs-cn/contract/13-ts-time#hours)                           |获取小时                              |
| [milliseconds](docs-cn/contract/13-ts-time#milliseconds)                           |获取毫秒                              |
| [minutes](docs-cn/contract/13-ts-time#minutes)                           |获取分钟                              |
| [now](docs-cn/contract/13-ts-time#now)                           |此函数返回头块时间，以秒为单位。                              |
| [seconds](docs-cn/contract/13-ts-time#seconds)                           |获取秒                              |


## days
```
days(d: u64)
```
获取日期

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|d              | u64 |                     |是     |


#### 返回结果类型
[`Microseconds`](docs-cn/contract/13-ts-time#Microseconds)

## getDaysOfMonth
```
getDaysOfMonth(year: u32)
```
获取每月的天数 

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|year              | u32 | 年份                    |是     |

#### 返回结果类型
`u32[]`

## hours
```
hours(h: u64)
```
获取小时

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|h              | u64 |                     |是     |


#### 返回结果类型
[`Microseconds`](docs-cn/contract/13-ts-time#Microseconds)


## milliseconds
```
milliseconds(c: u64)
```
获取毫秒

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|c              | u64 |                     |是     |


#### 返回结果类型
[`Microseconds`](docs-cn/contract/13-ts-time#Microseconds)

## minutes
```
minutes(m: u64)
```
获取分钟

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|m              | u64 |                     |是     |


#### 返回结果类型
[`Microseconds`](docs-cn/contract/13-ts-time#Microseconds)

## now
```
now
```
此函数返回头块时间，以秒为单位。

#### 参考示例
```nodejs
import { now } from "ultrain-ts-lib/src/time";
```



#### 返回结果类型
`u32`

## seconds
```
seconds(sec: u64)
```
获取秒

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|sec              | u64 |                     |是     |


#### 返回结果类型
[`Microseconds`](docs-cn/contract/13-ts-time#Microseconds)
