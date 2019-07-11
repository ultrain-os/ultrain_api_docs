## 简介
U3的加密方法将帮助你更好了解超脑加密的相关信息


## 方法列表
超脑U3加密相关的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [generateKeyPairByMnemonic](docs-cn/u3/02-u3-ecc#generateKeyPairByMnemonic) |生成密钥对符号                              |
| [generateKeyPairBySeed](docs-cn/u3/02-u3-ecc#generateKeyPairBySeed) |按种子生成密钥对                              |
| [generateKeyPairWithMnemonic](docs-cn/u3/02-u3-ecc#generateKeyPairWithMnemonic) |用助记键生成密钥对                              |
| [privateToPublic](docs-cn/u3/02-u3-ecc#privateToPublic) |将私钥转换为公钥                              |


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
import {generateKeyPairByMnemonic} from "u3.js/src";
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
import {generateKeyPairBySeed} from "u3.js/src";
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
import {privateToPublic} from "u3.js/src";
const u3 = createU3(config)
u3.privateToPublic({
    "wif": "5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3"
})
```

#### 返回结果类型
`String`