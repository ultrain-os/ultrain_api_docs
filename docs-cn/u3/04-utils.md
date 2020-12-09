## 简介
U3工具的相关方法将帮助你更好了解链化未来技术的相关信息


## 方法列表

链化未来U3工具类相关的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [DecimalImply](docs-cn/u3/04-utils#DecimalImply) |确保正确的尾随零，然后删除小数点                             |
| [DecimalPad](docs-cn/u3/04-utils#DecimalPad) |确保小数位数固定                          |
| [DecimalString](docs-cn/u3/04-utils#DecimalString) |规范化和验证十进制字符串（可能是较大的值）                          |
| [DecimalUnimply](docs-cn/u3/04-utils#DecimalUnimply) |将小数点放回其位置，并返回规范化的数字字符串（去掉任何不必要的零或不必要的小数)                          |
| [decodeName](docs-cn/u3/04-utils#decodeName) |将u64类型的账户名解码为string类型                          |
| [decodeNameEx](docs-cn/u3/04-utils#decodeNameEx) |decodeName的扩展类型                          |
| [decodeSymbolName](docs-cn/u3/04-utils#decodeSymbolName) |将整数样式值解码为资产的符号名称                          |
| [encodeName](docs-cn/u3/04-utils#encodeName) |将string类型的账户名解码为u64类型                       |
| [encodeNameEx](docs-cn/u3/04-utils#encodeNameEx) |encodeName的扩展                       |
| [isName](docs-cn/u3/04-utils#isName) | 检查名称是否合法                         |
| [parseExtendedAsset](docs-cn/u3/04-utils#parseExtendedAsset) | 分析扩展资产                        |


## DecimalImply
```
(static) DecimalImply(value, precision) 
```
确保小数位数固定

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|value              |number、string、object.toString  |要精确的数                     |是     |
|precision              |number  |小数点后的位数                     |是     |

#### 参考示例
```nodejs
import {format} from "u3.js";
assert.equals(format.DecimalImply(10.2, 3),'10200')
```

#### 返回结果类型
`String`

## DecimalPad
```
(static) DecimalPad(num, precisionopt)
```
确保正确的尾随零，然后删除小数点

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|num              |number、string、object.toString  |要精确的数                     |是     |
|precision              |number  |小数位数。空跳过填充后缀，但仍应用数字格式规范化                     |是     |

#### 参考示例
```nodejs
import {format} from "u3.js";
assert.equals(format.DecimalPad(10.2, 3),'10.200')
assert.equals(format.UDecimalPad(10.1, 1),'10.1')
```

#### 返回结果类型
`String`

## DecimalString
```
(static) DecimalString()
```
规范化和验证十进制字符串（可能是较大的值）


#### 参考示例
```nodejs
import {format} from "u3.js";
assert.equals(format.DecimalString("13.010"),13.01)
```

#### 返回结果类型
`String`

## DecimalUnimply
```
(static) DecimalUnimply(num, precisionopt)
```
将小数点放回其位置，并返回规范化的数字字符串（去掉任何不必要的零或不必要的小数)

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|value              |number、string、object.toString  |要精确的数                     |是     |
|precision              |number  |小数位数。                     |是     |

#### 参考示例
```nodejs
import {format} from "u3.js";
assert.equals(format.DecimalUnimply(10000, 4),'1.0000')
```

#### 返回结果类型
`number`

## decodeName
```
(static) decodeName(value, littleEndian)
```
将u64类型的账户名解码为string类型

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|value              |string|要转化的账户名                     |是     |
|littleEndian        |bool  |判断低字节的处理顺序为左还是右                     |是     |

#### 参考示例
```nodejs
import {format} from "u3.js";
assert.equal(format.decodeName(format.encodeName('chain2future')), 'chain2future')
      
```

#### 返回结果类型
`string`

## decodeNameEx
```
(static) decodeNameEx(valueH, valueL, littleEndian)
```
u64类型的账户名解码的扩展方法

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|valueL              |string|要转化的账户名的长度                     |是     |
|valueH              |string|                     |是     |
|littleEndian        |bool  |判断低字节的处理顺序为左还是右                     |是     |

#### 参考示例
```nodejs
import {format} from "u3.js";
 assert.equal(format.decodeNameHex(format.encodeNameHex("chain2future")), 'chain2future')
```

#### 返回结果类型
`string`

## decodeSymbolName
```
(static) decodeSymbolName(symbolName, littleEndianopt)
```
将整数样式值解码为资产的符号名称

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|symbolName              |*|uint 64值要解析为资产的符号名                     |是     |
|littleEndian              |boolean|判断低字节的处理顺序为左还是右                     |是     |


#### 返回结果类型
`string`—资产的符号名称

## encodeName
```
(static) encodeName(name, littleEndian) 
```
将string类型的账户名解码为u64类型

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|name              |string|名称（最长可为12个字符）                  |是     |
|littleEndian        |bool  |判断低字节的处理顺序为左还是右                     |是     |

#### 参考示例
```nodejs
import {format} from "u3.js";
format.encodeName('chain2future')
```

#### 返回结果类型
`string`

## encodeNameEx
```
(static) encodeNameEx(name, littleEndian) 
```
将string类型的账户名解码为u64类型

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|name              |string|名称（最长可为21个字符）                  |是     |
|littleEndian        |bool  |判断低字节的处理顺序为左还是右                     |是     |

#### 参考示例
```nodejs
import {format} from "u3.js";
format.encodeNameEx('chain2future')
```

#### 返回结果类型
`string`

## isName
```
(static) isName(str, err) 
```
检查名称是否合法

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|str              |string|名称                  |是     |
|err        |boolean  |是否显示错误消息                     |是     |

#### 参考示例
```nodejs
import {format} from "u3.js";
format.isName('chain2future')
```

#### 返回结果类型
`boolean`


## parseExtendedAsset
```
(static) parseExtendedAsset(str) 
```
分析扩展资产

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|str              |string  |要分析的字符串                  |是     |


#### 参考示例
```nodejs
import {format} from "u3.js";

const parseExtendedAssets = [
  ['SYM', null, null, 'SYM', null],
  ['SYM@contract', null, null, 'SYM', 'contract'],
  ['4,SYM', null, 4, 'SYM', null],
  ['4,SYM@contract', null, 4, 'SYM', 'contract'],
  ['1 SYM', '1', null, 'SYM', null],
  ['1.0 SYM', '1.0', null, 'SYM', null],
  ['1.0 4,SYM@contract', '1.0', 4, 'SYM', 'contract'],
  ['1.0 4,SYM@tract.token', '1.0', 4, 'SYM', 'tract.token'],
  ['1.0 4,SYM@tr.act.token', '1.0', 4, 'SYM', 'tr.act.token'],
  ['1.0 4,SYM', '1.0', 4, 'SYM', null],
]
for(const [str, amount, precision, symbol, contract] of parseExtendedAssets) {
  assert.deepEqual(format.parseExtendedAsset(str),{amount, precision, symbol, contract}
  )
}
    
```

#### 返回结果类型
`Object`


