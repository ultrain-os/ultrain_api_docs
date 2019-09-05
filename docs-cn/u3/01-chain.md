## 简介

U3接口的配置信息如下

#### 开发环境（单链）

> httpEndpoint: "http://127.0.0.1:8888",  
httpEndpointHistory: "http://127.0.0.1:3000",  
chainId: "80a5d6aa3e0c2e2052c3df1cc6b591b90b8307fb102bd174805e06c8b8b16ec1",
  
#### 测试网环境（多链）

**主链**
> httpEndpoint:"http://ultrain.natapp1.cc",  
 httpEndpointHistory:"http://ultrain-history.natapp1.cc",  
 chainId:"1f1155433d9097e0f67de63a48369916da91f19cb1feff6ba8eca2e5d978a2b2",

**侧链11**
> httpEndpoint:"http://pioneer.natapp1.cc",  
 httpEndpointHistory:"http://pioneer-history.natapp1.cc",  
 chainId:"20c35b993c10b5ea1007014857bb2b8832fb8ae22e9dcfdc61dacf336af4450f",

**侧链12**
> httpEndpoint:"http://power.natapp1.cc",  
 httpEndpointHistory:"http://power-history.natapp1.cc",  
 chainId:"0120d06d4a73b60357a5ed24a9145c967308738d70397c25eeedcbb736166ccf",

#### 主网环境（多链）

**主链**
> httpEndpoint:"https://ultrain.services",  
 httpEndpointHistory:"https://history.ultrain.services",  
 chainId:"99b1cef2acdf6c4bcbce64c6490a999b819c236b19e3cd7cd2c3accc71da30ef",

**侧链poineer**
> httpEndpoint:"https://pioneer.ultrain.services",  
 httpEndpointHistory:"https://history-pioneer.ultrain.services",  
 chainId:"13c654dcffbed7b6d615aa92b75ebf1a3049ff74ffe73fdeafb9113be6b6fe22",

**侧链unitopia**
> httpEndpoint:"https://unitopia.ultrain.services",  
 httpEndpointHistory:"https://history-unitopia.ultrain.services",  
 chainId:"7c3040786b0d1de5af5bdba73800acb1767fbdea402da0613ba8601f3a1a2acb",

**侧链new-retail**
> httpEndpoint:"https://new-retail.ultrain.services",  
 httpEndpointHistory:"https://history-new-retail.ultrain.services",  
 chainId:"23b412f2ab81a33c1a3aabfa550984475accdd1d2906c26d77cabb17f53d24ac",

## 方法列表

超脑U3链上所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [abiBin2json](docs-cn/u3/01-chain#abiBin2json)                          |将bin十六进制转换为ABI JSON                              |
| [abiJson2bin](docs-cn/u3/01-chain#abi_json2bin)                         |将JSON序列化为二进制十六进制。二进制码通常存储在action.data中 |
| [createUser](docs-cn/u3/01-chain#createUser)                            |创建一个账户                                             |
| [empoweruser](docs-cn/u3/01-chain#empoweruser)                           |将账户从主链同步到某一条侧链上                                             |
| [updateauth](docs-cn/u3/01-chain#updateauth)                           |修改账户的私钥                                             |
| [deploy](docs-cn/u3/01-chain#deploy)                                    |将合约部署到链上                                             |
| [getAbi](docs-cn/u3/01-chain#getAbi)                                    |根据账户名查找ABI                                            |
| [getAccountInfo](docs-cn/u3/01-chain#getAccountInfo)                    |获取帐户基本信息                                            |
| [getBlockInfo](docs-cn/u3/01-chain#getBlockInfo)                        |从区块链中获取一个区块的信息                                            |
| [getChainInfo](docs-cn/u3/01-chain#getChainInfo)                        |获取链的信息                                            |
| [getContract](docs-cn/u3/01-chain#getContract)                        |获取智能合约的代码                                            |
| [getCurrencyBalance](docs-cn/u3/01-chain#getCurrencyBalance)           |获取货币余额                                           |
| [getCurrencyStats](docs-cn/u3/01-chain#getCurrencyStats)           |获取货币信息                                          |
| [getTransFee](docs-cn/u3/01-chain#getTransFee)                    |获取交易信息                                          |
| [getRawCodeAndAbi](docs-cn/u3/01-chain#getRawCodeAndAbi)           |获取原始代码和ABI                                          |                                          |
| [getTableByScope](docs-cn/u3/01-chain#getTableByScope)           |从命名空间获取智能合约数据                                          |
| [getTableRecords](docs-cn/u3/01-chain#getTableRecords)           |从智能合约的表中读数据                                          |
| [resourcelease](docs-cn/u3/01-chain#resourcelease)           |资源购买                                          |
| [pushTx](docs-cn/u3/01-chain#pushTx)           |尝试将事务推入挂起队列                                          |
| [pushTxs](docs-cn/u3/01-chain#pushTxs)           |尝试将多个事务推入挂起队列                                          |
| [registerEvent](docs-cn/u3/01-chain#registerEvent)           |订阅UltraIn链事件                                          |
| [unregisterEvent](docs-cn/u3/01-chain#unregisterEvent)           |取消订阅UltraIn链事件                                         |
| [sign](docs-cn/u3/01-chain#sign) |针对待上链的未签名交易进行离线签名  



## abiBin2json
```
(static) abiBin2json (code, action, binargs)
```
将bin十六进制转换为ABI JSON

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|code              |name  |智能合约名称                     |是     |
|action            |name  |行为名称                        |是     |
|binargs           |bytes   |二进制参数参数                   |是     |

#### 参考示例
```nodejs
import {abiBin2json} from "u3.js";
const u3 = createU3(config);
await u3.abiBin2json({
  "code": "account1",
  "action": "account2",
  "binargs": "000000008093dd74000000000094dd74e803000000000000"
});
```

## abiJson2bin
```
(static) abiJson2bin(code, action, args)
```
手动将JSON序列化为二进制十六进制。二进制码通常存储在action.data中。

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|code              |name  |账户名                          |是     |
|action            |name  |行为参数                         |是     |
|args              |bytes   |json参数                        |是     |

#### 参考示例
```nodejs
import {abiJson2bin} from "u3.js";
const u3 = createU3(config);
await u3.abiJson2bin({
  "code": "account1",
  "action": "account2",
  "args": {
    "from": "initb",
    "to": "initc",
    "quantity": 1000
  }
});
```

## createUser
```
(static) createUser(creator, name, owner, active, updateable)
```
创建一个账户

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|creator           |account_name  |创建者账户                       |是     |
|name              |account_name  |被创建账户                     |是     |
|owner             |string        |被创建账户的owner公钥                     |是     |
|active            |string        |被创建账户的active公钥               |是     |
|updateable        |uint32        |是否可以更新账户                  |否     |

#### 参考示例
```nodejs
import {createUser} from "u3.js";
const u3 = createU3(config);
await u3.createUser({
  "creator": "ben",
  "name": "abcdefg12345",
  "owner": "UTR1uHKWW5tvmw6eQpbv92cVmkpDFhQ9q7xsee5Da2X2pVeYUNy4D",
  "active": "UTR1uHKWW5tvmw6eQpbv92cVmkpDFhQ9q7xsee5Da2X2pVeYUNy4D",
  "updateable": 1
});
```
#### 返回格式
```
{
    "transaction_id": "f8b426780499d8b0561331d61acba73d73b549164cc2bd9dd429242845775164",
    "processed": {
        "id": "f8b426780499d8b0561331d61acba73d73b549164cc2bd9dd429242845775164",
        "receipt": {
            "status": "executed",
            "cpu_usage_us": 30793,
            "net_usage_words": 26
        },
        "elapsed": 30793,
        "net_usage": 208,
        "scheduled": false,
        "action_traces": [
            {
                "receipt": {
                    "receiver": "ultrainio",
                    "act_digest": "997311d5873f3bc77a91c9b926539098f4e54fc15bc640d93704946366769626",
                    "global_sequence": 249,
                    "recv_sequence": 231,
                    "auth_sequence": [
                        [
                            "ben",
                            3
                        ]
                    ],
                    "code_sequence": 1,
                    "abi_sequence": 1
                },
                "act": {
                    "account": "ultrainio",
                    "name": "newaccount",
                    "authorization": [
                        {
                            "actor": "ben",
                            "permission": "active"
                        }
                    ],
                    "data": {
                        "creator": "ben",
                        "name": "44jn5qcnaa2v",
                        "owner": {
                            "threshold": 1,
                            "keys": [
                                {
                                    "key": "UTR6rBwNTWJSNMYu4ZLgEigyV5gM8hHiNinqejXT1dNGZa5xsbpCB",
                                    "weight": 1
                                }
                            ],
                            "accounts": [],
                            "waits": []
                        },
                        "active": {
                            "threshold": 1,
                            "keys": [
                                {
                                    "key": "UTR6rBwNTWJSNMYu4ZLgEigyV5gM8hHiNinqejXT1dNGZa5xsbpCB",
                                    "weight": 1
                                }
                            ],
                            "accounts": [],
                            "waits": []
                        },
                        "updateable": 1
                    },
                    "hex_data": "000000000000a63ab0853113d9321f2101000000010003022b4dce3b2921209ec9bb9060161ba7a4c772605ab32e63f0d5227d43d2263f0100000001000000010003022b4dce3b2921209ec9bb9060161ba7a4c772605ab32e63f0d5227d43d2263f0100000001"
                },
                "elapsed": 20175,
                "cpu_usage": 0,
                "console": "",
                "total_cpu_usage": 0,
                "trx_id": "f8b426780499d8b0561331d61acba73d73b549164cc2bd9dd429242845775164",
                "return_value": "",
                "inline_traces": [
                    {
                        "receipt": {
                            "receiver": "utrio.token",
                            "act_digest": "8cf59888b786b86ed60a0880d4ddd3092b9d1e65cdcf6e7147173ec5d2063e9d",
                            "global_sequence": 250,
                            "recv_sequence": 11,
                            "auth_sequence": [
                                [
                                    "ben",
                                    4
                                ]
                            ],
                            "code_sequence": 1,
                            "abi_sequence": 1
                        },
                        "act": {
                            "account": "utrio.token",
                            "name": "safe_transfer",
                            "authorization": [
                                {
                                    "actor": "ben",
                                    "permission": "active"
                                }
                            ],
                            "data": {
                                "from": "ben",
                                "to": "utrio.fee",
                                "quantity": "0.2000 UGAS",
                                "memo": "create account"
                            },
                            "hex_data": "000000000000a63a0000506a01ea6ed6d00700000000000004554741530000000e637265617465206163636f756e74"
                        },
                        "elapsed": 10069,
                        "cpu_usage": 0,
                        "console": "",
                        "total_cpu_usage": 0,
                        "trx_id": "f8b426780499d8b0561331d61acba73d73b549164cc2bd9dd429242845775164",
                        "return_value": "",
                        "inline_traces": []
                    }
                ]
            }
        ],
        "except": null,
        "ability": "Normal"
    }
}

```

## empoweruser
```
(static) empoweruser(user, chain_name, owner_pk, active_pk, updateable)
```
创建一个账户

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|user           |string  |要同步的账号                       |是     |
|chain_name              |string  |要同步到的链名                     |是     |
|owner_pk             |string        |要同步的账号的owner公钥                     |是     |
|active_pk            |string        |要同步的账号的active公钥               |是     |
|updateable        |uint32        |是否可以更新账户                  |否     |

#### 参考示例
```nodejs
import {createUser} from "u3.js";
const u3 = createU3(config);
const c = await u3.contract('ultrainio');//系统合约
await c.empoweruser({
  user: 'cona1',
  chain_name: '11', //pioneer sidechain name
  owner_pk: 'UTR5jKHKQZHCvrmfpZ8cjdf6QJFWKQrxUtBvj5QBPKdWUBob8BkqS',
  active_pk: 'UTR5jKHKQZHCvrmfpZ8cjdf6QJFWKQrxUtBvj5QBPKdWUBob8BkqS',
  updateable: 1,
});
```
#### 返回格式

```
{
    "transaction_id": "39fc99137b00ecd7a84fe4318a2871d73e54416f2271afbbd09f4d434dcbcc05",
    "processed": {
        "id": "39fc99137b00ecd7a84fe4318a2871d73e54416f2271afbbd09f4d434dcbcc05",
        "receipt": {
            "status": "executed",
            "cpu_usage_us": 4241,
            "net_usage_words": 29
        },
        "elapsed": 4241,
        "net_usage": 232,
        "scheduled": false,
        "action_traces": [
            {
                "receipt": {
                    "receiver": "ultrainio",
                    "act_digest": "3471723b44cc90f5a060afd399720e977b74809e8eab8134d9fdaf5e01aedba9",
                    "global_sequence": 3321018,
                    "recv_sequence": 1777087,
                    "auth_sequence": [
                        [
                            "temp1",
                            1
                        ]
                    ],
                    "code_sequence": 8,
                    "abi_sequence": 8
                },
                "act": {
                    "account": "ultrainio",
                    "name": "empoweruser",
                    "authorization": [
                        {
                            "actor": "temp1",
                            "permission": "active"
                        }
                    ],
                    "data": {
                        "user": "temp1",
                        "chain_name": "11",
                        "owner_pk": "UTR6rBwNTWJSNMYu4ZLgEigyV5gM8hHiNinqejXT1dNGZa5xsbpCB",
                        "active_pk": "UTR6rBwNTWJSNMYu4ZLgEigyV5gM8hHiNinqejXT1dNGZa5xsbpCB",
                        "updateable": 1
                    },
                    "hex_data": "000000008050a5ca000000000000400835555452367242774e54574a534e4d5975345a4c67456967795635674d386848694e696e71656a585431644e475a613578736270434235555452367242774e54574a534e4d5975345a4c67456967795635674d386848694e696e71656a585431644e475a613578736270434201"
                },
                "elapsed": 3718,
                "cpu_usage": 0,
                "console": "",
                "total_cpu_usage": 0,
                "trx_id": "39fc99137b00ecd7a84fe4318a2871d73e54416f2271afbbd09f4d434dcbcc05",
                "return_value": "",
                "inline_traces": []
            }
        ],
        "except": null,
        "ability": "Normal"
    }
}

```



## updateauth
```
(static) updateauth(account,auth,parent,permission)
```
创建一个账户

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|account           |string  |要修改的账号                       |是     |
|auth              |string  |账号权限                     |是     |
|parent             |string        |父权限                     |是     |
|permission            |string        |权限级别               |是     |

#### 参考示例
```nodejs
import {createUser} from "u3.js";
const u3 = createU3(config);
const c = await u3.contract('ultrainio');//系统合约

let account_ = 'ben'

//update active permission of ben
//sign with ben's active or owner key
let activeObj = {
    account: account_,
    auth: {
      'threshold': 1,
      'keys': [{ 'key': 'UTR....', 'weight': 1 }],
      'accounts': [],
      'waits': [],
    },
    parent: 'owner',
    permission: 'active',
};
await c.updateauth(activeObj, { authorization: [account_ + `@active`] });


//update owner permission of ben
//sign with ben's owner key
let ownerObj = {
    account: account_,
    auth: {
      'threshold': 1,
      'keys': [{ 'key': 'UTR...', 'weight': 1 }],
      'accounts': [],
      'waits': [],
    },
    parent: '',
    permission: 'owner',
};
await c.updateauth(ownerObj, { authorization: [account_ + `@owner`] });

```
#### 返回格式

```
{
    "transaction_id": "12383689c08e26ea9675ad9c99064a84117362a383c2d4135013dc0f7336d0af",
    "processed": {
        "id": "12383689c08e26ea9675ad9c99064a84117362a383c2d4135013dc0f7336d0af",
        "receipt": {
            "status": "executed",
            "cpu_usage_us": 5768,
            "net_usage_words": 21
        },
        "elapsed": 5768,
        "net_usage": 168,
        "scheduled": false,
        "action_traces": [
            {
                "receipt": {
                    "receiver": "ultrainio",
                    "act_digest": "c5bf370a7d2ed1c7092c0efefd8ce195653fd3f60ebe7739366011e3a6b2a2a8",
                    "global_sequence": 5051986,
                    "recv_sequence": 3413915,
                    "auth_sequence": [
                        [
                            "cona4",
                            10
                        ]
                    ],
                    "code_sequence": 19,
                    "abi_sequence": 19
                },
                "act": {
                    "account": "ultrainio",
                    "name": "updateauth",
                    "authorization": [
                        {
                            "actor": "cona4",
                            "permission": "active"
                        }
                    ],
                    "data": {
                        "account": "cona4",
                        "permission": "active",
                        "parent": "owner",
                        "auth": {
                            "threshold": 1,
                            "keys": [
                                {
                                    "key": "UTR7PgMuL8NBQwMn2brEVmCbWutnHHMVzstLxTtNnWhNqX8mGafFe",
                                    "weight": 1
                                }
                            ],
                            "accounts": [],
                            "waits": []
                        }
                    },
                    "hex_data": "000000000062264500000000a8ed32320000000080ab26a70100000001000349abd1c424762b087937c739e5628e1017f0e743c806db3da95f01332f1666a701000000"
                },
                "elapsed": 1847,
                "cpu_usage": 0,
                "console": "",
                "total_cpu_usage": 0,
                "trx_id": "12383689c08e26ea9675ad9c99064a84117362a383c2d4135013dc0f7336d0af",
                "return_value": "",
                "inline_traces": [
                    {
                        "receipt": {
                            "receiver": "utrio.token",
                            "act_digest": "71e63487fbde72beaa420f7afaf4738151587e36e2d3ed91083930cd88b2e53a",
                            "global_sequence": 5051987,
                            "recv_sequence": 291004,
                            "auth_sequence": [
                                [
                                    "cona4",
                                    11
                                ]
                            ],
                            "code_sequence": 4,
                            "abi_sequence": 4
                        },
                        "act": {
                            "account": "utrio.token",
                            "name": "transfer",
                            "authorization": [
                                {
                                    "actor": "cona4",
                                    "permission": "active"
                                }
                            ],
                            "data": {
                                "from": "cona4",
                                "to": "utrio.fee",
                                "quantity": "1.0000 UGAS",
                                "memo": "update auth"
                            },
                            "hex_data": "00000000006226450000506a01ea6ed6102700000000000004554741530000000b7570646174652061757468"
                        },
                        "elapsed": 1367,
                        "cpu_usage": 0,
                        "console": "",
                        "total_cpu_usage": 0,
                        "trx_id": "12383689c08e26ea9675ad9c99064a84117362a383c2d4135013dc0f7336d0af",
                        "return_value": "",
                        "inline_traces": [
                            {
                                "receipt": {
                                    "receiver": "cona4",
                                    "act_digest": "71e63487fbde72beaa420f7afaf4738151587e36e2d3ed91083930cd88b2e53a",
                                    "global_sequence": 5051988,
                                    "recv_sequence": 4,
                                    "auth_sequence": [
                                        [
                                            "cona4",
                                            12
                                        ]
                                    ],
                                    "code_sequence": 4,
                                    "abi_sequence": 4
                                },
                                "act": {
                                    "account": "utrio.token",
                                    "name": "transfer",
                                    "authorization": [
                                        {
                                            "actor": "cona4",
                                            "permission": "active"
                                        }
                                    ],
                                    "data": {
                                        "from": "cona4",
                                        "to": "utrio.fee",
                                        "quantity": "1.0000 UGAS",
                                        "memo": "update auth"
                                    },
                                    "hex_data": "00000000006226450000506a01ea6ed6102700000000000004554741530000000b7570646174652061757468"
                                },
                                "elapsed": 1071,
                                "cpu_usage": 0,
                                "console": "",
                                "total_cpu_usage": 0,
                                "trx_id": "12383689c08e26ea9675ad9c99064a84117362a383c2d4135013dc0f7336d0af",
                                "return_value": "",
                                "inline_traces": []
                            },
                            {
                                "receipt": {
                                    "receiver": "utrio.fee",
                                    "act_digest": "71e63487fbde72beaa420f7afaf4738151587e36e2d3ed91083930cd88b2e53a",
                                    "global_sequence": 5051989,
                                    "recv_sequence": 6,
                                    "auth_sequence": [
                                        [
                                            "cona4",
                                            13
                                        ]
                                    ],
                                    "code_sequence": 4,
                                    "abi_sequence": 4
                                },
                                "act": {
                                    "account": "utrio.token",
                                    "name": "transfer",
                                    "authorization": [
                                        {
                                            "actor": "cona4",
                                            "permission": "active"
                                        }
                                    ],
                                    "data": {
                                        "from": "cona4",
                                        "to": "utrio.fee",
                                        "quantity": "1.0000 UGAS",
                                        "memo": "update auth"
                                    },
                                    "hex_data": "00000000006226450000506a01ea6ed6102700000000000004554741530000000b7570646174652061757468"
                                },
                                "elapsed": 1075,
                                "cpu_usage": 0,
                                "console": "",
                                "total_cpu_usage": 0,
                                "trx_id": "12383689c08e26ea9675ad9c99064a84117362a383c2d4135013dc0f7336d0af",
                                "return_value": "",
                                "inline_traces": []
                            }
                        ]
                    }
                ]
            }
        ],
        "except": null,
        "ability": "Normal"
    }
}

```


## deploy
```
(static) deploy(contract, account)
```
将合约部署到链上

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|contract           |string       |合约文件路径                       |是     |
|account            |account_name  |合约所属账户                     |是     |


#### 参考示例
```nodejs
import {deploy} from "u3.js";
const u3 = createU3(config);
await u3.deploy({
  "contract": "/Users/benyasin/demo/contracts/token/token",
  "account": "ben"
});

或者

await u3.deploy({
  "contract": "/Users/benyasin/demo/contracts/token/token",
  "account": "ben",
  {keyProvider: '5HqLjaqC7...'}
});

```
#### 返回格式

```
{
    "transaction_id": "d626ab9f45dfb4e78a6ebe73bceb35d3c19b7c0da96500ccb4baa4818fb8a9c9",
    "processed": {
        "id": "d626ab9f45dfb4e78a6ebe73bceb35d3c19b7c0da96500ccb4baa4818fb8a9c9",
        "receipt": {
            "status": "executed",
            "cpu_usage_us": 13054,
            "net_usage_words": 2974
        },
        "elapsed": 13054,
        "net_usage": 23792,
        "scheduled": false,
        "action_traces": [
            {
                "receipt": {
                    "receiver": "ultrainio",
                    "act_digest": "933460bec99bdd3d164737b2fde334aff32674933f5b56d5f8d2865dbf24356d",
                    "global_sequence": 456,
                    "recv_sequence": 437,
                    "auth_sequence": [
                        [
                            "bob",
                            1
                        ]
                    ],
                    "code_sequence": 1,
                    "abi_sequence": 1
                },
                "act": {
                    "account": "ultrainio",
                    "name": "setcode",
                    "authorization": [
                        {
                            "actor": "bob",
                            "permission": "active"
                        }
                    ],
                    "data": {
                        "account": "bob",
                        "vmtype": 0,
                        "vmversion": 0,
                        "code": "00617..."
                    },
                    "hex_data": "0000000000...."
                },
                "elapsed": 1212,
                "cpu_usage": 0,
                "console": "",
                "total_cpu_usage": 0,
                "trx_id": "d626ab9f45dfb4e78a6ebe73bceb35d3c19b7c0da96500ccb4baa4818fb8a9c9",
                "return_value": "",
                "inline_traces": []
            },
            {
                "receipt": {
                    "receiver": "ultrainio",
                    "act_digest": "cd31826fba290d52c45b7f098b271065a04c5db379374276d86705e8df967bb0",
                    "global_sequence": 457,
                    "recv_sequence": 438,
                    "auth_sequence": [
                        [
                            "bob",
                            2
                        ]
                    ],
                    "code_sequence": 1,
                    "abi_sequence": 1
                },
                "act": {
                    "account": "ultrainio",
                    "name": "setabi",
                    "authorization": [
                        {
                            "actor": "bob",
                            "permission": "active"
                        }
                    ],
                    "data": {
                        "account": "bob",
                        "abi": "11756c...."
                    },
                    "hex_data": "0000000000...."
                },
                "elapsed": 9296,
                "cpu_usage": 0,
                "console": "",
                "total_cpu_usage": 0,
                "trx_id": "d626ab9f45dfb4e78a6ebe73bceb35d3c19b7c0da96500ccb4baa4818fb8a9c9",
                "return_value": "",
                "inline_traces": []
            }
        ],
        "except": null,
        "ability": "Normal"
    }
}
```

## getAbi
```
(static) getAbi(account_name)
```
根据账户名取出合约的ABI

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|account_name           |name       |根据账户名取出合约的ABI                       |是     |

#### 参考示例
```nodejs
import {getAbi} from "u3.js";
const u3 = createU3(config);
await u3.getAbi({
  "account_name": "account"
});
```
#### 返回格式 
```
{
    "account_name": "ben",
    "abi": {
        "version": "ultraio:1.0:UIP06",
        "types": [
            {
                "new_type_name": "account_name",
                "type": "name"
            },
            {
                "new_type_name": "Asset",
                "type": "asset"
            },
            {
                "new_type_name": "u64",
                "type": "uint64"
            }
        ],
        "structs": [
            {
                "name": "create",
                "base": "",
                "fields": [
                    {
                        "name": "issuer",
                        "type": "account_name"
                    },
                    {
                        "name": "maximum_supply",
                        "type": "Asset"
                    }
                ]
            },
            {
                "name": "issue",
                "base": "",
                "fields": [
                    {
                        "name": "to",
                        "type": "account_name"
                    },
                    {
                        "name": "quantity",
                        "type": "Asset"
                    },
                    {
                        "name": "memo",
                        "type": "string"
                    }
                ]
            },
            {
                "name": "transfer",
                "base": "",
                "fields": [
                    {
                        "name": "from",
                        "type": "account_name"
                    },
                    {
                        "name": "to",
                        "type": "account_name"
                    },
                    {
                        "name": "quantity",
                        "type": "Asset"
                    },
                    {
                        "name": "memo",
                        "type": "string"
                    }
                ]
            },
            {
                "name": "totalSupply",
                "base": "",
                "fields": [
                    {
                        "name": "sym_name",
                        "type": "string"
                    }
                ]
            },
            {
                "name": "getSupply",
                "base": "",
                "fields": [
                    {
                        "name": "sym_name",
                        "type": "string"
                    }
                ]
            },
            {
                "name": "balanceOf",
                "base": "",
                "fields": [
                    {
                        "name": "owner",
                        "type": "account_name"
                    },
                    {
                        "name": "sym_name",
                        "type": "string"
                    }
                ]
            },
            {
                "name": "CurrencyStats",
                "base": "",
                "fields": [
                    {
                        "name": "supply",
                        "type": "Asset"
                    },
                    {
                        "name": "max_supply",
                        "type": "Asset"
                    },
                    {
                        "name": "issuer",
                        "type": "account_name"
                    },
                    {
                        "name": "timestamp",
                        "type": "u64"
                    }
                ]
            },
            {
                "name": "CurrencyAccount",
                "base": "",
                "fields": [
                    {
                        "name": "balance",
                        "type": "Asset"
                    }
                ]
            }
        ],
        "actions": [
            {
                "name": "create",
                "type": "create",
                "ricardian_contract": "",
                "ability": "normal"
            },
            {
                "name": "issue",
                "type": "issue",
                "ricardian_contract": "",
                "ability": "normal"
            },
            {
                "name": "transfer",
                "type": "transfer",
                "ricardian_contract": "",
                "ability": "normal"
            },
            {
                "name": "totalSupply",
                "type": "totalSupply",
                "ricardian_contract": "",
                "ability": "pureview"
            },
            {
                "name": "getSupply",
                "type": "getSupply",
                "ricardian_contract": "",
                "ability": "pureview"
            },
            {
                "name": "balanceOf",
                "type": "balanceOf",
                "ricardian_contract": "",
                "ability": "pureview"
            }
        ],
        "tables": [
            {
                "name": "stat",
                "index_type": "i64",
                "key_names": [],
                "key_types": [],
                "type": "CurrencyStats"
            },
            {
                "name": "accounts",
                "index_type": "i64",
                "key_names": [],
                "key_types": [],
                "type": "CurrencyAccount"
            }
        ],
        "ricardian_clauses": [],
        "error_messages": [],
        "abi_extensions": []
    }
}
```

## getAccountInfo
```
(static) getAccountInfo(account_name)
```
获取区块链帐户

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|account_name           |name       |查询账号基本信息                       |是     |

#### 参考示例
```nodejs
import {getAccountInfo} from "u3.js";
const u3 = createU3(config);
await u3.getAccountInfo({
  "account_name": "account"
});
```
#### 返回格式

```
{
    "account_name": "ben",
    "head_block_num": 568,
    "head_block_time": "2019-07-13T13:08:58.000",
    "privileged": false,
    "updateable": true,
    "last_code_update": "2019-07-13T03:42:36.000",
    "created": "2019-07-13T03:41:08.000",
    "core_liquid_balance": "999.8000 UGAS",
    "ram_quota": -1,
    "net_weight": -1,
    "cpu_weight": -1,
    "net_limit": {
        "used": -1,
        "available": -1,
        "max": -1
    },
    "cpu_limit": {
        "used": -1,
        "available": -1,
        "max": -1
    },
    "ram_usage": 229748,
    "permissions": [
        {
            "perm_name": "active",
            "parent": "owner",
            "required_auth": {
                "threshold": 1,
                "keys": [
                    {
                        "key": "UTR6ujHgxt2hUz7BfvJz6epfvWzhXEp1ChVKEFZxf1Ld5ea83WE6V",
                        "weight": 1
                    }
                ],
                "accounts": [],
                "waits": []
            }
        },
        {
            "perm_name": "owner",
            "parent": "",
            "required_auth": {
                "threshold": 1,
                "keys": [
                    {
                        "key": "UTR6ujHgxt2hUz7BfvJz6epfvWzhXEp1ChVKEFZxf1Ld5ea83WE6V",
                        "weight": 1
                    }
                ],
                "accounts": [],
                "waits": []
            }
        }
    ],
    "self_delegated_consensus": null,
    "refund_cons": null,
    "producer_info": null,
    "chain_resource": []
}
```


## getTransFee
```
(static) getTransFee(block_height)
```
获取某个块的交易费

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|block_height           |string       |提供区块高度         |是     |


#### 参考示例
```nodejs
import {getTransFee} from "u3.js";
const u3 = createU3(config);
await u3.getTransFee("1");
```

#### 返回格式

```
{
    "fee": "0.2000 UGAS",
}
```

## getBlockInfo
```
(static) getBlockInfo(block_num_or_id)
```
从区块链中获取一个区块

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|block_num_or_id           |string       |提供区块编号或ID         |是     |


#### 参考示例
```nodejs
import {getBlockInfo} from "u3.js";
const u3 = createU3(config);
await u3.getBlockInfo({
  "block_id": "0000000280155952392ddaa5c4fb6611e74e3c93f61852c50f67f47c9c8b90ba"
});
```

#### 返回格式

```
{
    "timestamp": "2019-07-13T03:40:48.000",
    "proposer": "genesis",
    "version": 0,
    "previous": "0000000198a5fe5833a07b758f1e168b5b57f96524e129ca74c775c934d39d03",
    "transaction_mroot": "0000000000000000000000000000000000000000000000000000000000000000",
    "action_mroot": "813cb712f0daf00fb2062e5120dd256e2ba70a3905d9f3a0dfb2ebce47fdd218",
    "committee_mroot": "0000000000000000000000000000000000000000000000000000000000000000",
    "header_extensions": [],
    "signature": "",
    "transactions": [],
    "block_extensions": [],
    "id": "00000002f68058634c34126e0a4fb1ab3d6837404707181f25979d693794a5d7",
    "block_num": 2,
    "ref_block_prefix": 1846686796,
    "timevalue": 48224448
}
```

## getChainInfo

```
(static) getChainInfo()
```
获取链的信息

#### 参考示例
```nodejs
import {getBlockInfo} from "u3.js";
const u3 = createU3();
await u3.getChainInfo();

```
#### 返回格式

```
{
    "server_version": "da32d5b7+2.1.0",
    "chain_id": "20c35b993c10b5ea1007014857bb2b8832fb8ae22e9dcfdc61dacf336af4450f",
    "head_block_num": 593970,
    "last_irreversible_block_num": 593969,
    "last_irreversible_block_id": "00091031b12faa0db84c42c6e57874cdbf4bdda60ace23c83ce80ddba2b2350a",
    "head_block_id": "000910329b698c43143fca43fa815881c0d315b5a9df4cbf40c2f42dc88b61f8",
    "head_block_time": "2019-07-13T03:36:55.000",
    "head_block_proposer": "13.115",
    "virtual_block_cpu_limit": 3000000,
    "virtual_block_net_limit": 2097152,
    "block_cpu_limit": 3000000,
    "block_net_limit": 2097152,
    "block_interval_ms": 10000
}

```

## getContract
```
(static) getContract(account_name)
```
获取智能合约代码(wasm,wast,abi)

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|account_name           |name       |提供的智能合约的账户名         |是     |

#### 参考示例
```nodejs
import {getContract} from "u3.js";
const u3 = createU3(config);
await u3.getContract({
  "account_name": "account"
});
```
#### 返回格式

```
{
    "account_name": "ben",
    "code_hash": "ff560677c1a8ef92a54321ff9d26e1fb20e5c340a20a8bc12cde552c2997ea9b",
    "wast": "(module\n  (type $0 (func ))\n  (type $1 (func (param i32) (result i32)))\n  ...",
    "wasm": "",
    "abi": {
        "version": "ultraio:1.0:UIP06",
        "types": [
            {
                "new_type_name": "account_name",
                "type": "name"
            },
            {
                "new_type_name": "Asset",
                "type": "asset"
            },
            {
                "new_type_name": "u64",
                "type": "uint64"
            }
        ],
        "structs": [
            {
                "name": "create",
                "base": "",
                "fields": [
                    {
                        "name": "issuer",
                        "type": "account_name"
                    },
                    {
                        "name": "maximum_supply",
                        "type": "Asset"
                    }
                ]
            },
            ...
        ],
        "actions": [
            {
                "name": "create",
                "type": "create",
                "ricardian_contract": "",
                "ability": "normal"
            },
            ...
        ],
        "tables": [
            {
                "name": "stat",
                "index_type": "i64",
                "key_names": [],
                "key_types": [],
                "type": "CurrencyStats"
            },
            {
                "name": "accounts",
                "index_type": "i64",
                "key_names": [],
                "key_types": [],
                "type": "CurrencyAccount"
            }
        ],
        "ricardian_clauses": [],
        "error_messages": [],
        "abi_extensions": []
    }
}

```

## getCurrencyBalance
```
(static) getCurrencyBalance(code, account, symbol)
```
获取货币余额

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|code           |name       |部署合同的帐户         |是     |
|account           |name       |要获取余额的帐户         |是     |
|symbol           |optional.<string>  |要查询代币的符号         |是     |


#### 参考示例
```nodejs
import {getCurrencyBalance} from "u3.js";
const u3 = createU3(config);
await u3.getCurrencyBalance({
  "code": "utrio.token",
  "account": "ben",
  "symbol": "UGAS"
});
```
#### 返回格式

```
["999.8000 UGAS"]
```

## getCurrencyStats
```
(static) getCurrencyStats(code, symbol)
```
获取货币信息

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|code           |name       |部署合同的帐户         |是     |
|symbol           |optional.<string>  |要查询代币的符号         |是     |


#### 参考示例
```nodejs
import {getCurrencyStats} from "u3.js";
const u3 = createU3(config);
await u3.getCurrencyStats({
  "code": "account",
  "symbol": "UGAS"
});
```
#### 返回格式

```
{
    "UGAS": {
        "supply": "1000000000.0000 UGAS",
        "max_supply": "8000000000.0000 UGAS",
        "issuer": "ultrainio"
    }
}
```

## getRawCodeAndAbi
```
(static) getRawCodeAndAbi(account_name)
```
获取原始代码和ABI

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|owner           |account_name       |要获取代码和ABI的帐户名         |是     |


#### 参考示例
```nodejs
import {getRawCodeAndAbi} from "u3.js";
const u3 = createU3(config);
await u3.getRawCodeAndAbi({
  "account_name": "account"
});
```

#### 返回格式
```
{
    "account_name": "ben",
    "wasm": "AGFzbQEAAAABvwEfYAAAYA...",
    "abi": "EXVsdHJhaW86MS4wOlVJ..."
}
```

## getScheduledTransactions
```
(static) getScheduledTransactions(json, lower_bound, limit)
```
获取原始代码和ABI

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|json           |bool       |提供真假         |是     |
|lower_bound           |string       |时间戳或事务ID         |是     |
|limit           |uint32       |限制条件         |是     |


#### 参考示例
```nodejs
import {getScheduledTransactions} from "u3.js";
const u3 = createU3(config);
await u3.getScheduledTransactions({
  "json": false,
  "lower_bound": "2a57d0f636625abc9f63656e3b8ada8b8b7a4fdf7a7663e4db27bc88be730b51",
  "limit": "50"
});
```

## getTableByScope
```
(static) getTableByScope(code, table, lower_bound, upper_bound, limit)
```
查询一个token的holders

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|code           |name       |提供token的creator名         |是     |
|table           |name       |提供token表名         |是     |
|lower_bound           |string       |下限         |是     |
|upper_bound           |string       |上限ID         |是     |
|limit           |uint32       |限制条件         |是     |


#### 参考示例
```nodejs
import {getTableByScope} from "u3.js";
const u3 = createU3(config);
await u3.getTableByScope({
  "code": "ben",
  "table": "accounts",
  "lower_bound": "0",
  "upper_bound": "-1",
  "limit": "10"
});
```
#### 返回格式
```
{
    "rows": [
        {
            "code": "ben",
            "scope": "4226065300333789184",
            "table": "accounts",
            "payer": "ben",
            "count": 1
        },
        ...
    ],
    "more": 0
}
```
## getTableRecords
```
(static) getTableRecords(json, code, scope, table, table_key, lower_bound, upper_bound, limit, key_type, index_position)
```
从帐户获取智能合约数据

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|json           |bool       |是否json         |是     |
|code           |name       |合约Owner账号        |是     |
|scope           |string       |查询的账号         |是     |
|table           |name       |提供表名         |是     |
|table_key           |string       |表键         |是     |
|lower_bound	           |string       |下限         |是     |
|upper_bound           |string       |上限        |是     |
|limit           |uint32       |限制         |是     |
|key_type           |string       |键类型--index，仅主支架（I64）所有其他支持（i64、i128、i256、float64、float128）。特殊类型“name”表示帐户名。        |是     |
|index_position           |string       |索引         |是     |

#### 参考示例
```nodejs
import {getTableRecords} from "u3.js";
const u3 = createU3(config);
await u3.getTableRecords({
  "json": true,
  "code": "utrio.token",
  "scope": "ben",
  "table": "accounts"
});
```
#### 返回格式
```
{
    "rows": [
        {
            "balance": "999.8000 UGAS",
            "last_block_height": 198
        }
    ],
    "more": false
}
```



## resourcelease

```
(static) resourcelease(from, receiver, combosize, days, location)
```
获取原始代码和ABI

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|from           |account_name       |埋单账号         |是     |
|receiver           |account_name       |接收账号         |是     |
|combosize           |uint64       |单位数         |是     |
|days           |uint64       |有效天数         |是     |
|location           |name       |买到哪条链         |是     |


#### 参考示例
```nodejs
import {getScheduledTransactions} from "u3.js";
const u3 = createU3(config);
const c = await u3.contract("ultrainio");

//lease 1 slot for 365 days.
//the last parameter should be the name of the side chain.
//should connect to mainchain
await c.resourcelease('ben', 'bob', 1, 365, "pioneer");
```

## pushTx
```
(static) pushTx(signed_transaction)
```
尝试将事务推入挂起队列

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|signed_transaction           |signed_transaction       |提供签名的交易         |是     |


## pushTxs
```
(static) pushTxs(signed_transaction)
```
尝试将事务推入挂起队列

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|signed_transaction           |signed_transaction[]       |提供签名的交易数组         |是     |

## registerEvent
```
(static) registerEvent(account, post_url)
```
订阅Ultrain链事件

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|account           |name       |提供action名称         |是     |
|post_url           |string       |提供url         |是     |

#### 参考示例
```nodejs
import {registerEvent} from "u3.js";
const u3 = createU3(config);
await u3.registerEvent({
  "account": "name",
  "post_url": "http://10.10.10.114:3002"
});
```

## unregisterEvent
```
(static) unregisterEvent(account, post_url)
```
取消订阅Ultrain链事件

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|account           |name       |提供action名称         |是     |
|post_url           |string       |提供url         |是     |

#### 参考示例
```nodejs
import {unregisterEvent} from "u3.js";
const u3 = createU3(config);
await u3.unregisterEvent({
  "account": "name",
  "post_url": "http://10.10.10.114:3002"
});
```


## sign
```
(static) sign(unsigned_transaction, privateKeyOrMnemonic, chainId)
```
签署未签名的交易

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|unsigned_transaction           |object       |脱机U3实例调用操作时返回的未签名事务         |是     |
|privateKeyOrMnemonic	           |string       |私钥或助记键         |是     |
|chainId           |string       |提供链的id         |是     |

#### 参考示例
```nodejs
import {sign} from "u3.js";
const u3_offline = createU3({ sign: false, broadcast: false });
const unsigned_transaction = await u3_offline.anyAction('args', {keyProvider});
let signature = await u3_offline.sign(unsigned_transaction, '5KWW3MQbqibqmC...','baf8bb9d3636...');
```
