## 简介
U3链上的方法将帮助你更好的和Ultrain链进行交互。


## 方法列表

超脑U3链上所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [abiBin2json](docs-cn/u3/01-u3-chain#abiBin2json)                          |将bin十六进制转换为ABI JSON                              |
| [abiJson2bin](docs-cn/u3/01-u3-chain#abi_json2bin)                         |将JSON序列化为二进制十六进制。二进制码通常存储在action.data中 |
| [createUser](docs-cn/u3/01-u3-chain#createUser)                            |创建一个账户                                             |
| [deploy](docs-cn/u3/01-u3-chain#deploy)                                    |将合约部署到Ultrain链上                                             |
| [getAbi](docs-cn/u3/01-u3-chain#getAbi)                                    |根据账户名查找ABI                                            |
| [getAccountInfo](docs-cn/u3/01-u3-chain#getAccountInfo)                    |获取区块链帐户                                            |
| [getBlockHeaderState](docs-cn/u3/01-u3-chain#getBlockHeaderState)          |获取验证事务头所需的最小状态                                            |
| [getBlockInfo](docs-cn/u3/01-u3-chain#getBlockInfo)                        |从区块链中获取一个区块的信息                                            |
| [getChainInfo](docs-cn/u3/01-u3-chain#getChainInfo)                        |获取链的信息                                            |
| [getContract](docs-cn/u3/01-u3-chain#getContract)                        |获取智能合约的代码                                            |
| [getCurrencyBalance](docs-cn/u3/01-u3-chain#getCurrencyBalance)           |获取货币余额                                           |
| [getCurrencyStats](docs-cn/u3/01-u3-chain#getCurrencyStats)           |获取货币信息                                          |
| [getProducerInfo](docs-cn/u3/01-u3-chain#getProducerInfo)           |获取制作者信息                                          |
| [getRawCodeAndAbi](docs-cn/u3/01-u3-chain#getRawCodeAndAbi)           |获取原始代码和ABI                                          |
| [getRequiredKeys](docs-cn/u3/01-u3-chain#getRequiredKeys)           |获取所需密钥                                          |
| [getScheduledTransactions](docs-cn/u3/01-u3-chain#getScheduledTransactions)           |获取计划的事务                                          |
| [getTableByScope](docs-cn/u3/01-u3-chain#getTableByScope)           |从帐户获取智能合约数据                                          |
| [getTableRecords](docs-cn/u3/01-u3-chain#getTableRecords)           |从帐户获取智能合约数据                                          |
| [pushBlock](docs-cn/u3/01-u3-chain#pushBlock)           |将区块追加到链数据库                                          |
| [pushTx](docs-cn/u3/01-u3-chain#pushTx)           |尝试将事务推入挂起队列                                          |
| [pushTxs](docs-cn/u3/01-u3-chain#pushTxs)           |尝试将事务推入挂起队列                                          |
| [queryResource](docs-cn/u3/01-u3-chain#queryResource)           |返回帐户的资源详细信息                                          |
| [registerEvent](docs-cn/u3/01-u3-chain#registerEvent)           |订阅UltraIn链事件                                          |
| [sign](docs-cn/u3/01-u3-chain#sign)           |签署未签署的交易                                         |
| [unregisterEvent](docs-cn/u3/01-u3-chain#unregisterEvent)           |取消订阅UltraIn链事件                                         |




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
import {abiBin2json} from "u3.js/src";
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
import {abiJson2bin} from "u3.js/src";
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
(static) createUser(creator, name, owner, active, updateablenullable)
```
创建一个账户

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|creator           |account_name  |创建者账户                       |是     |
|name              |account_name  |被创建的账户                     |是     |
|owner             |string        |创建者的公钥                     |是     |
|active            |string        |要绑定的active公钥               |是     |
|updateable        |uint32        |是否可以更新账户                  |否     |

#### 参考示例
```nodejs
import {createUser} from "u3.js/src";
const u3 = createU3(config);
await u3.createUser({
  "creator": "ben",
  "name": "abcdefg12345",
  "owner": "UTR1uHKWW5tvmw6eQpbv92cVmkpDFhQ9q7xsee5Da2X2pVeYUNy4D",
  "active": "UTR1uHKWW5tvmw6eQpbv92cVmkpDFhQ9q7xsee5Da2X2pVeYUNy4D",
  "updateable": 1
});
```

## deploy
```
(static) deploy(contract, account)
```
将合约部署到Ultrain链上

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|contract           |string       |合约文件路径                       |是     |
|account            |account_name  |合约所属账户                     |是     |


#### 参考示例
```nodejs
import {deploy} from "u3.js/src";
const u3 = createU3(config);
await u3.deploy({
  "contract": "/Users/benyasin/demo/contracts/token/token",
  "account": "ben"
});
```

## getAbi
```
(static) getAbi(account_name)
```
根据账户名查找ABI

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|account_name           |name       |检索ABI的帐户名                       |是     |



#### 参考示例
```nodejs
import {getAbi} from "u3.js/src";
const u3 = createU3(config);
await u3.getAbi({
  "account_name": "account"
});
```

## getAccountInfo
```
(static) getAccountInfo(account_name)
```
获取区块链帐户

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|account_name           |name       |提供的帐户名                       |是     |



#### 参考示例
```nodejs
import {getAccountInfo} from "u3.js/src";
const u3 = createU3(config);
await u3.getAccountInfo({
  "account_name": "account"
});
```

## getBlockHeaderState
```
(static) getBlockHeaderState(block_num_or_id)
```
获取验证事务头所需的最小状态

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|block_num_or_id           |string       |提供区块编号或ID         |是     |


#### 参考示例
```nodejs
import {getBlockHeaderState} from "u3.js/src";
const u3 = createU3(config);
await u3.getBlockHeaderState({
  "block_id": "0000000280155952392ddaa5c4fb6611e74e3c93f61852c50f67f47c9c8b90ba"
});
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
import {getBlockInfo} from "u3.js/src";
const u3 = createU3(config);
await u3.getBlockInfo({
  "block_id": "0000000280155952392ddaa5c4fb6611e74e3c93f61852c50f67f47c9c8b90ba"
});
```

## getChainInfo
```
(static) getChainInfo()
```
获取链的信息

## getContract
```
(static) getContract(account_name)
```
获取智能合约代码

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|account_name           |name       |提供的智能合约的账户名         |是     |


#### 参考示例
```nodejs
import {getContract} from "u3.js/src";
const u3 = createU3(config);
await u3.getContract({
  "account_name": "account"
});
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
import {getCurrencyBalance} from "u3.js/src";
const u3 = createU3(config);
await u3.getCurrencyBalance({
  "code": "account",
  "account": "account",
  "symbol": "UGAS"
});
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
import {getCurrencyStats} from "u3.js/src";
const u3 = createU3(config);
await u3.getCurrencyStats({
  "code": "account",
  "symbol": "UGAS"
});
```

## getProducerInfo
```
(static) getProducerInfo(owner)
```
获取制造者信息

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|owner           |account_name       |制造者账户         |是     |


#### 参考示例
```nodejs
import {getCurrencyStats} from "u3.js/src";
const u3 = createU3(config);
await u3.getCurrencyStats({
  "code": "account",
  "symbol": "UGAS"
});
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
import {getRawCodeAndAbi} from "u3.js/src";
const u3 = createU3(config);
await u3.getRawCodeAndAbi({
  "account_name": "account"
});
```

## getRequiredKeys
```
(static) getRequiredKeys(transaction, available_keys)
```
获取所需密钥

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|transaction           |transaction       |提供事务对象         |是     |
|available_keys           |Array       |提供可用的密钥         |是     |


#### 参考示例
```nodejs
import {getRequiredKeys} from "u3.js/src";
const u3 = createU3(config);
await u3.getRequiredKeys({
  "transaction": {
    "ref_block_num": "100",
    "ref_block_prefix": "137469861",
    "expiration": "2017-09-25T06:28:49",
    "scope": [
      "initb",
      "initc"
    ],
    "actions": [
      {
        "code": "currency",
        "type": "transfer",
        "recipients": [
          "initb",
          "initc"
        ],
        "authorization": [
          {
            "account": "initb",
            "permission": "active"
          }
        ],
        "data": "000000000041934b000000008041934be803000000000000"
      }
    ],
    "signatures": [],
    "authorizations": []
  },
  "available_keys": [
    "EOS4toFS3YXEQCkuuw1aqDLrtHim86Gz9u3hBdcBw5KNPZcursVHq",
    "EOS7d9A3uLe6As66jzN8j44TXJUqJSK3bFjjEEqR4oTvNAB3iM9SA",
    "EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV"
  ]
});
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
import {getScheduledTransactions} from "u3.js/src";
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
从帐户获取智能合约数据

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|code           |name       |提供智能合约名称         |是     |
|table           |name       |提供表名         |是     |
|lower_bound           |string       |下限         |是     |
|upper_bound           |string       |上限ID         |是     |
|limit           |uint32       |限制条件         |是     |


#### 参考示例
```nodejs
import {getTableByScope} from "u3.js/src";
const u3 = createU3(config);
await u3.getTableByScope({
  "code": "account1",
  "table": "table",
  "lower_bound": "0",
  "upper_bound": "-1",
  "limit": "10"
});
```

## getTableRecords
```
(static) getTableRecords(json, code, scope, table, table_key, lower_bound, upper_bound, limit, key_type, index_position)
```
从帐户获取智能合约数据

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|json           |bool       |提供真假         |是     |
|code           |name       |提供智能合约名称        |是     |
|scope           |string       |提供账户名         |是     |
|table           |name       |提供表名         |是     |
|table_key           |string       |表键         |是     |
|lower_bound	           |string       |下限         |是     |
|upper_bound           |string       |上限        |是     |
|limit           |uint32       |限制         |是     |
|key_type           |string       |键类型--index，仅主支架（I64）所有其他支持（i64、i128、i256、float64、float128）。特殊类型“name”表示帐户名。        |是     |
|index_position           |string       |索引         |是     |

#### 参考示例
```nodejs
import {getTableRecords} from "u3.js/src";
const u3 = createU3(config);
await u3.getTableRecords({
  "json": false,
  "code": "account1",
  "scope": "account2",
  "table": "table",
  "table_key": "",
  "lower_bound": "0",
  "upper_bound": "-1",
  "limit": "10",
  "key_type": "i64",
  "index_position": ""
});
```

## pushBlock
```
(static) pushBlock(block)
```
将区块追加到链数据库

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|block           |signed_block	       |签名区块         |是     |

## pushTx
```
(static) pushTx(signed_transaction)
```
尝试将事务推入挂起队列

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|signed_transaction           |signed_transaction       |提供交易授权         |是     |


## pushTxs
```
(static) pushTxs(signed_transaction)
```
尝试将事务推入挂起队列

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|signed_transaction           |signed_transaction       |提供交易授权         |是     |


## queryResource
```
(static) queryResource(name)
```
返回帐户的资源详细信息

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|name           |account_name       |要查询的帐户         |是     |

#### 参考示例
```nodejs
import {queryResource} from "u3.js/src";
const u3 = createU3(config);
await u3.queryResource({
  "name": "du3kwow2bkay"
});
```

## registerEvent
```
(static) registerEvent(account, post_url)
```
订阅UltraIn链事件

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|account           |name       |提供action名称         |是     |
|post_url           |string       |提供url         |是     |

#### 参考示例
```nodejs
import {registerEvent} from "u3.js/src";
const u3 = createU3(config);
await u3.registerEvent({
  "account": "name",
  "post_url": "http://10.10.10.114:3002"
});
```

## sign
```
(static) sign(unsigned_transaction, privateKeyOrMnemonic, chainId)
```
签署未签署的交易

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|unsigned_transaction           |object       |脱机U3实例调用操作时返回的未签名事务         |是     |
|privateKeyOrMnemonic	           |string       |私钥或助记键         |是     |
|chainId           |string       |提供链的id         |是     |

#### 参考示例
```nodejs
import {sign} from "u3.js/src";
const u3_offline = createU3({ sign: false, broadcast: false });
const unsigned_transaction = await u3_offline.anyAction('args', {keyProvider});
let signature = await u3_offline.sign(unsigned_transaction, '5KWW3MQbqibqmC...','baf8bb9d3636...');
```

## unregisterEvent
```
(static) unregisterEvent(account, post_url)
```
取消订阅UltraIn链事件

#### 参数说明
|参数               |类型          |说明                            |是否必填|
| :----------------| :------------| :-----------------------------|:-----|
|account           |name       |提供action名称         |是     |
|post_url           |string       |提供url         |是     |

#### 参考示例
```nodejs
import {unregisterEvent} from "u3.js/src";
const u3 = createU3(config);
await u3.unregisterEvent({
  "account": "name",
  "post_url": "http://10.10.10.114:3002"
});
```