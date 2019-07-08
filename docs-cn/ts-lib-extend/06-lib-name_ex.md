## 类
超脑TS_lib的NAME_EX的类如下所示

| 类                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [NameEx](docs-cn/ts-lib-extend/06-lib-name_ex#NameEx)                          |nameex类用于存储21个字符的名称，方法nex将包含“.0123456789abcdefghijklmnopqrstuvwxyzabedefghijklmnopqrstuvwxyz”的字符串转换为nameex。例如，actionname是nameex的一个入口                             |

## NameEx
nameex类用于存储21个字符的名称，方法nex将包含“.0123456789abcdefghijklmnopqrstuvwxyzabedefghijklmnopqrstuvwxyz”的字符串转换为nameex。例如，actionname是nameex的一个入口

## 方法列表
超脑TS_lib的NAME_EX所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [NEX](docs-cn/ts-lib-extend/06-lib-balance#NEX)                           |将字符串转换为nameex。参数str有一些限制：1、str的长度必须小于21。2、仅包含“.0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZABCEFGHIJKLMNOPQRSTUVWXYZ”。3、不能以“”结尾。                             |
| [RNEX](docs-cn/ts-lib-extend/06-lib-balance#RNEX)                           |将nameex.valueh、nameex.valuel转换为字符串                             |
| [char_to_symbol_ex](docs-cn/ts-lib-extend/06-lib-balance#char_to_symbol_ex)                           |将字符转为符号Ex                             |


## NEX
```
NEX(str: string)
```
将字符串转换为nameex。参数str有一些限制：1、str的长度必须小于21。2、仅包含“.0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZABCEFGHIJKLMNOPQRSTUVWXYZ”。3、不能以“”结尾。

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|str              |string  |要转换为nameex的字符串                     |是     |


#### 返回结果类型
[`NameEx`](docs-cn/ts-lib-extend/06-lib-name_ex#NameEx) 

## RNEX
```
RNEX(h: u64, l: u64)
```
将nameex.valueh、nameex.valuel转换为字符串

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|h              |u64  |nameex的高64位                     |是     |
|l              |u64  |nameex的低64位                     |是     |


#### 返回结果类型
`string`

## char_to_symbol_ex
```
char_to_symbol_ex(c: u8)
```
将字符转为符号Ex

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|c              |u8  |                     |是     |

#### 返回结果类型
`u64`