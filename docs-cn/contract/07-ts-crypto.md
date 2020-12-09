## 类
链化未来TS_lib的CRYPTO的类如下所示

| 类                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [Crypto](docs-cn/contract/07-ts-crypto#Crypto)                          |类加密用于用所需算法散列字符串。它的派生类是sha1、sha256、sha512和ripemd160。                             |
| [MerkleProof](docs-cn/contract/07-ts-crypto#MerkleProof)                          |梅克尔证明                             |
| [Ripemd160](docs-cn/contract/07-ts-crypto#Ripemd160)                          |使用ripemd160计算字符串的哈希                             |
| [SHA1](docs-cn/contract/07-ts-crypto#SHA1)                          |使用SHA1计算字符串的哈希                             |
| [SHA256](docs-cn/contract/07-ts-crypto#SHA256)                          |使用SHA256计算字符串的哈希                             |
| [SHA512](docs-cn/contract/07-ts-crypto#SHA512)                          |使用SHA512计算字符串的哈希                             |

## Crypto
类加密用于用所需算法散列字符串。它的派生类是sha1、sha256、sha512和ripemd160。

## MerkleProof
梅克尔证明

## Ripemd160
使用ripemd160计算字符串的哈希

#### 使用示例
```nodejs
import { Ripemd160 } from "ultrain-ts-lib/src/crypto";
```

## SHA1
使用SHA1计算字符串的哈希

#### 使用示例
```nodejs
import { SHA1 } from "ultrain-ts-lib/src/crypto";
```

## SHA256
使用SHA256计算字符串的哈希

#### 使用示例
```nodejs
import { SHA256 } from "ultrain-ts-lib/src/crypto";
```

## SHA512
使用SHA512计算字符串的哈希

#### 使用示例
```nodejs
import { SHA512 } from "ultrain-ts-lib/src/crypto";
```

## 方法列表
链化未来TS_lib的CRYPTO所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [assert_ripemd160](docs-cn/contract/07-ts-crypto#assert_ripemd160)                           |断言源数据是否由ripemd160组成                              |
| [assert_sha1](docs-cn/contract/07-ts-crypto#assert_sha1)                           |断言源数据是否由sha1组成                              |
| [assert_sha256](docs-cn/contract/07-ts-crypto#assert_sha256)                           |断言源数据是否由sha256组成                              |
| [assert_sha512](docs-cn/contract/07-ts-crypto#assert_sha512)                           |断言源数据是否由sha512组成                              |
| [charcode_to_digital](docs-cn/contract/07-ts-crypto#charcode_to_digital)                           |将字符代码转为数字                             |
| [from_hex](docs-cn/contract/07-ts-crypto#from_hex)                           |                                 |
| [get_random_number](docs-cn/contract/07-ts-crypto#get_random_number)       |从系统服务获取随机数。这个数字将在协商一致期间保持不变，因此，如果在一个操作中多次调用这个函数，随机数就不会改变。                             |
| [to_hex](docs-cn/contract/07-ts-crypto#to_hex)                          | 十六进制字符串的加密结果转换为字符串                            |
| [verify_with_pk](docs-cn/contract/07-ts-crypto#verify_with_pk)                           |验证pk和证明                             |


## assert_ripemd160
```
(static) assert_ripemd160(data, ripe)
```
断言源数据是否由ripemd160组成

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|data              |  | 要断言的源数据                    |是     |
|ripe              |  | 加密算法                    |是     |

#### 参考示例
```nodejs
import { assert_ripemd160 } from "ultrain-ts-lib/src/crypto";
```

## assert_sha1
```
(static) assert_sha1(data, sha1)
```
断言源数据是否由sha1组成

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|data              |  | 要断言的源数据                    |是     |
|sha1              |  | 加密算法                    |是     |

#### 参考示例
```nodejs
import { assert_sha1 } from "ultrain-ts-lib/src/crypto";
```

## assert_sha256
```
(static) assert_sha256(data, sha256)
```
断言源数据是否由sha256组成

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|data              |  | 要断言的源数据                    |是     |
|sha256              |  | 加密算法                    |是     |

#### 参考示例
```nodejs
import { assert_sha256 } from "ultrain-ts-lib/src/crypto";
```

## assert_sha512
```
(static) assert_sha512(data, sha512)
```
断言源数据是否由sha512组成

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|data              |  | 要断言的源数据                    |是     |
|sha512              |  | 加密算法                    |是     |

#### 参考示例
```nodejs
import { assert_sha512 } from "ultrain-ts-lib/src/crypto";
```

## charcode_to_digital
```
charcode_to_digital(char: i32)
```
将字符代码转为数字

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|char              | i32 |                     |是     |

#### 返回结果类型
`u8`


## from_hex
```
from_hex(hexStr: string, buffer: usize, bufferSize: u32)
```


#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|hexStr              | string |                     |是     |
|buffer              | usize |                     |是     |
|bufferSize              | u32 |                     |是     |

#### 返回结果类型
`void`


## get_random_number
```
get_random_number(code: account_name, table: u64, scope: u64, primary: u64)
```
从系统服务获取随机数。这个数字将在协商一致期间保持不变，因此，如果在一个操作中多次调用这个函数，随机数就不会改变

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|code              | account_name | 系统服务帐户                    |是     |
|table              | u64 | 随机数的表名                    |是     |
|scope              | u64 |随机数的范围                     |是     |
|primary              | u64 | 随机数的主数                    |是     |

#### 返回结果类型
`u64`

## to_hex
```
to_hex(buffer: usize, buffersize: u32)
```
十六进制字符串的加密结果转换为字符串

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|buffer              | usize | 缓冲区                    |是     |
|buffersize              | u32 |缓冲区大小                     |是     |

#### 返回结果类型
`string`



## verify_with_pk
```
(static) verify_with_pk(pk_str, pk_proof, message)
```
验证pk和证明

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|pk_str              | account_name | pk字符串                    |是     |
|pk_proof              | u64 | 证明字符串                    |是     |
|message              | u64 | 讯息                    |是     |

#### 参考示例
```nodejs
import { verify_with_pk } from "ultrain-ts-lib/src/crypto";
```



