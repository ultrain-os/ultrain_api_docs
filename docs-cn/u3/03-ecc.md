## 简介
U3的加密方法将帮助你更好了解超脑加密的相关信息


## 方法列表
超脑U3加密相关的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [generateKeyPairByMnemonic](docs-cn/u3/03-ecc#generateKeyPairByMnemonic) |生成密钥对符号                              |
| [generateKeyPairBySeed](docs-cn/u3/03-ecc#generateKeyPairBySeed) |按种子生成密钥对                              |
| [generateKeyPairWithMnemonic](docs-cn/u3/03-ecc#generateKeyPairWithMnemonic) |用助记键生成密钥对                              |
| [privateToPublic](docs-cn/u3/03-ecc#privateToPublic) |将私钥转换为公钥                              |                            |
| [isValidPublic](docs-cn/u3/03-ecc#isValidPublic) |判断是否有效公钥                              |
| [isValidPrivate](docs-cn/u3/03-ecc#isValidPrivate) |判断是否有效私钥                              |
| [sign](docs-cn/u3/03-ecc#sign) |对数据签名                              |
| [signHash](docs-cn/u3/03-ecc#signHash) |对sha256数据签名                              |
| [verify](docs-cn/u3/03-ecc#verify) |对签名进行验签                              |
| [verifyHash](docs-cn/u3/03-ecc#verifyHash) |对hash的签名进行验签                              |
| [recover](docs-cn/u3/03-ecc#recover) |从签名中解出公钥                              |
| [recoverHash](docs-cn/u3/03-ecc#recoverHash) |从hash的签名中解出公钥                              |


## generateKeyPairByMnemonic 
```
(static) generateKeyPairByMnemonic (mnemonic)
```
生成密钥对符号

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|mnemonic              |string  |助记词                     |是     |

#### 参考示例
```nodejs
import {generateKeyPairByMnemonic} from "u3.js";
const u3 = createU3(config)
u3.generateKeyPairByMnemonic({
    "mnemonic": "ben john tony jack bob tom jerry alice"
})
```

## generateKeyPairBySeed 
```
(static) generateKeyPairBySeed(seed)
```
按种子生成密钥对

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|seed              |string  |种子可以再生相同的密钥对 |是     |

#### 参考示例
```nodejs
import {generateKeyPairBySeed} from "u3.js";
const u3 = createU3(config)
u3.generateKeyPairBySeed({
    "seed": "ultrain12345"
})
```

#### 返回结果类型
`Object`

## generateKeyPairWithMnemonic 
```
(static) generateKeyPairWithMnemonic()
```
按助记词生成密钥对

#### 返回结果类型
`Object`


## privateToPublic 
```
(static) privateToPublic(wif)
```
将私钥转换为公钥

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|wif              |string  |私钥 |是     |

#### 参考示例
```nodejs
import {privateToPublic} from "u3.js";
const u3 = createU3(config)
u3.privateToPublic({
    "wif": "5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3"
})
```

#### 返回结果类型
`String`


## isValidPublic
```
(static) isValidPublic(public_key)
```
签署未签署的交易

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|public_key           |string       |公钥字符串         |是     |

#### 参考示例
```nodejs
import {U3Utils} from "u3.js";
U3Utils.ecc.isValidPublic('UTR859gxfnXyUriMgUeThh1fWv3oqcpLFyHa3TfFYC4PK2HqhToVM')
```


## isValidPrivate
```
(static) isValidPrivate(private_key)
```
签署未签署的交易

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|private_key           |string       |私钥字符串         |是     |

#### 参考示例
```nodejs
import {U3Utils} from "u3.js";
U3Utils.ecc.isValidPublic('5KYZdUEo39z3FPrtuX2QbbwGnNP5zTd7yyr2SC1j299sBCnWjss')
```

## sign
```
(static) sign(data, private_key)
```
签署未签署的交易

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|data           |string       |加密的数据         |是     |
|private_key           |string       |私钥字符串         |是     |

#### 参考示例
```nodejs
import {U3Utils} from "u3.js";
const pvt = U3Utils.ecc.seedPrivate('')
const data = 'hi'
const sign = U3Utils.ecc.sign(data, pvt)
```

## signHash
```
(static) signHash(dataSha256, private_key)
```
签署未签署的交易

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|dataSha256           |string       |加密的sha256数据         |是     |
|private_key           |string       |私钥字符串         |是     |

#### 参考示例
```nodejs
import {U3Utils} from "u3.js";
const pvt = U3Utils.ecc.seedPrivate('')
const data = 'hi'
const dataSha256 = U3Utils.ecc.sha256(data)
const sign = U3Utils.ecc.signHash(dataSha256, pvt)
```

## verify
```
(static) verify(sig, data, public_key)
```
签署未签署的交易

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|sig           |string       |签名信息         |是     |
|data           |string       |被签名的数据         |是     |
|public_key           |string       |公钥         |是     |

#### 参考示例
```nodejs
import {U3Utils} from "u3.js";
const pvt = U3Utils.ecc.seedPrivate('')
const pubkey = U3Utils.ecc.privateToPublic(pvt)
const data = 'hi';
const sig = U3Utils.ecc.sign(data, pvt);
assert(U3Utils.ecc.verify(sig, data, pubkey), 'verify data')
```

## verifyHash
```
(static) verifyHash(sig, data, public_key)
```
签署未签署的交易

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|sig           |string       |签名信息         |是     |
|dataSha256           |string       |被签名的sha256数据         |是     |
|public_key           |string       |公钥         |是     |

#### 参考示例
```nodejs
import {U3Utils} from "u3.js";
const pvt = U3Utils.ecc.seedPrivate('')
const pubkey = U3Utils.ecc.privateToPublic(pvt)
const data = 'hi';
const dataSha256 = U3Utils.ecc.sha256(data)
const sig = U3Utils.ecc.signHash(dataSha256, pvt)
assert(U3Utils.ecc.verifyHash(sig, dataSha256, pubkey), 'verify hash')
```

## recover
```
(static) recover(sig, data)
```
根据签名与原数据，解签名出公钥

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|sig           |string       |签名信息         |是     |
|data           |string       |被签名的数据         |是     |

#### 参考示例
```nodejs
import {U3Utils} from "u3.js";
const pvt = U3Utils.ecc.seedPrivate('')
const pubkey = U3Utils.ecc.privateToPublic(pvt)
const data = 'hi';
const sig = U3Utils.ecc.sign(data, pvt)
const publicKey = U3Utils.ecc.recover(sig, data);

assert.equal(pubkey, publicKey)
```


## recoverHash
```
(static) recoverHash(sig, dataSha256)
```
根据签名与原数据，解签名出公钥

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|sig           |string       |签名信息         |是     |
|dataSha256           |string       |被签名的sha256数据         |是     |

#### 参考示例
```nodejs
import {U3Utils} from "u3.js";
const pvt = U3Utils.ecc.seedPrivate('')
const pubkey = U3Utils.ecc.privateToPublic(pvt)
const data = 'hi';
const dataSha256 = U3Utils.ecc.sha256(data)
const sig = U3Utils.ecc.signHash(dataSha256, pvt)
const publicKey = U3Utils.ecc.recoverHash(sig, dataSha256);

assert.equal(pubkey, publicKey)
```
