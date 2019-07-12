## 方法列表
超脑TS_lib的UTILS所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [intToString](docs-cn/contract/15-ts-utils#intToString)                           |将int转为string                              |
| [printstr](docs-cn/contract/15-ts-utils#printstr)                           |在WASM VM退出后，将字符串打印到控制台                              |
| [string2cstr](docs-cn/contract/15-ts-utils#string2cstr)                           |将字符串转换为usize。这里，uCube在C/C++中喜欢“conchchar”                              |
| [toUTF8Array](docs-cn/contract/15-ts-utils#toUTF8Array)                           |将utf-16转换为utf-8字符串数组                              |


## intToString
```
intToString(_int: u64, leftPadWith0?: u32)
```
将int转为string

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|_int              | u64 |    要转换的数                 |是     |
|leftPadWith0              | u32 | 默认为0                    |否     |

#### 参考示例
```nodejs
import { intToString } from "ultrain-contract/src/utils";
```

#### 返回结果类型
`string`

## printstr
```
printstr(str: string)
```
在WASM VM退出后，将字符串打印到控制台

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|str              | string |    打印的字符串                 |是     |

#### 参考示例
```nodejs
import { printstr } from "ultrain-contract/src/utils";
```

#### 返回结果类型
`void`

## string2cstr
```
string2cstr(str: string)
```
将字符串转换为usize。这里，uCube在C/C++中喜欢“conchchar”

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|str              | string |一个UTF-16的typescript字符串                 |是     |

#### 参考示例
```nodejs
import { string2cstr } from "ultrain-contract/src/utils";
```

#### 返回结果类型
`u32`

## toUTF8Array
```
toUTF8Array(str: string)
```
将utf-16转换为utf-8字符串数组

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|str              | string |一个typescript字符串                 |是     |

#### 参考示例
```nodejs
import { toUTF8Array } from "ultrain-contract/src/utils";
```

#### 返回结果类型
`u8[]`