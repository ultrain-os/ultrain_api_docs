## 简介
U3的历史方法将帮助你更好了解超脑的相关技术信息


## 方法列表

超脑U3相关的历史方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [getActionsByAccount](docs-cn/u3/03-u3-history#getActionsByAccount) |按帐户名获取操作                             |
| [getActionsByTxid](docs-cn/u3/03-u3-history#getActionsByTxid) |按交易ID获取操作                            |
| [getAllAccounts](docs-cn/u3/03-u3-history#getAllAccounts) |获取所有的账户信息                            |
| [getAllBlocks](docs-cn/u3/03-u3-history#getAllBlocks) |获取所有的区块信息                            |
| [getAllBlocksHeader](docs-cn/u3/03-u3-history#getAllBlocksHeader) |按符号和创建者获取持有者                            |
| [getAllTokens](docs-cn/u3/03-u3-history#getAllTokens) |获取所有的代币信息                            |
| [getAllTxs](docs-cn/u3/03-u3-history#getAllTxs) |获取所有的交易信息                            |
| [getBalanceByAccount](docs-cn/u3/03-u3-history#getBalanceByAccount) |按帐户获取余额                            |
| [getBaseInfo](docs-cn/u3/03-u3-history#getBaseInfo) |获取代币基本信息                            |
| [getBlocksByContract](docs-cn/u3/03-u3-history#getBlocksByContract) |按块编号、帐户名称、合约名称、合约方法获取块                           |
| [getContractByName](docs-cn/u3/03-u3-history#getContractByName) |按名称获取合约                           |
| [getContracts](docs-cn/u3/03-u3-history#getContracts) |获取所有的合约信息                           |
| [getCreateAccountByName](docs-cn/u3/03-u3-history#getCreateAccountByName) |按名称获取创建帐户                           |
| [getExistAccount](docs-cn/u3/03-u3-history#getExistAccount) |按帐户名称获取帐户信息                           |
| [getHoldersBySymbol](docs-cn/u3/03-u3-history#getHoldersBySymbol) |按符号和创建者获取持有者                           |
| [getProposerList](docs-cn/u3/03-u3-history#getProposerList) |获取提议者列表                           |
| [getTokenBySymbol](docs-cn/u3/03-u3-history#getTokenBySymbol) |通过代币和创建者获取令牌                          |
| [getTxByTxId](docs-cn/u3/03-u3-history#getTxByTxId) |按交易ID获取交易信息                         |
| [getTxsByBlockNum](docs-cn/u3/03-u3-history#getTxsByBlockNum) |按块高查询交易信息                         |
| [getTxTraceByTxid](docs-cn/u3/03-u3-history#getTxTraceByTxid) |按交易ID获取交易跟踪                         |
| [search](docs-cn/u3/03-u3-history#search) |查询块/交易/帐户                         |



## getActionsByAccount 
```
(static) getActionsByAccount(page, pageSize, queryParams, sortParams)
```
按帐户名获取操作

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|page              |Number  |页数                    |是     |
|pageSize              |Number  |每页显示的操作数                    |是     |
|queryParams              |Object  |账户查询参数                     |是     |
|sortParams              |Object  |排序参数                     |是     |

#### 参考示例
```nodejs
import {getActionsByAccount} from "u3.js/src";
const u3 = createU3(config)
u3.getActionsByAccount({
     'page': 1,
     'pageSize': 10,
     'queryParams': {account:'ultrainio'},
     'sortParams': { _id: -1 }
})

json structure:
{ 
    "_id" : ObjectId("5b7d11b859bd97fab30ba7f3"), 
    "action_num" : NumberInt(0), 
    "trx_id" : "40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9", 
    "cfa" : false, 
    "account" : "ultrainio", 
    "name" : "onblock", 
    "authorization" : [
        {
            "actor" : "ultrainio", 
            "permission" : "active"
        }
    ], 
    "hex_data" : "80e34745000000000000000001000000000000..."
}
```

## getActionsByTxid 
```
(static) getActionsByTxid(id)
```
按帐户名获取操作

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|id              |String  |交易id                    |是     |


#### 参考示例
```nodejs
import {getActionsByTxid} from "u3.js/src";
const u3 = createU3(config)
u3.getActionsByTxid({
  'trx_id': "40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9"
})

json structure:
{ 
    "_id" : ObjectId("5b7d11b859bd97fab30ba7f3"), 
    "action_num" : NumberInt(0), 
    "trx_id" : "40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9", 
    "cfa" : false, 
    "account" : "ultrainio", 
    "name" : "onblock", 
    "authorization" : [
        {
            "actor" : "ultrainio", 
            "permission" : "active"
        }
    ], 
    "hex_data" : "80e3474500000000000000000100000000000..."
}
```

## getAllAccounts 
```
(async, static) getAllAccounts(page, pageSize, queryParams, sortParams)
```
按帐户名获取操作

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|page              |Number  |页数                    |是     |
|pageSize              |Number  |每页显示的账户数                    |是     |
|queryParams              |Object  |账户查询参数                     |是     |
|sortParams              |Object  |排序参数                     |是     |


#### 参考示例
```nodejs
import {getAllAccounts} from "u3.js/src";
const u3 = createU3(config)
u3.getAllAccounts({
    'page': 1,
    'pageSize': 10,
    'queryParams': {},
    'sortParams': { _id: -1 }
})

json structure:
{ 
    "_id" : ObjectId("5b7d11cc59bd97fab30ba86b"), 
    "name" : "utrio.code", 
    "owner" : "UTR6uHKWW5tvmw6eQpbv92cVmkpDFhQ9q7xsee5Da2X2pVeYUNy4D",
    "active" : "UTR8uHKWW5tvmw6eQpbv92cVmkpDFhQ9q7xsee5Da2X2pVeYUNy4D",
    "createdAt" : ISODate("2018-08-22T07:33:32.092+0000")
}
```

## getAllBlocks 
```
(static) getAllBlocks(page, pageSize, queryParams, sortParams)
```
按帐户名获取操作

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|page              |Number  |页数                    |是     |
|pageSize              |Number  |每页显示的区块数                    |是     |
|queryParams              |Object  |区块查询参数                     |是     |
|sortParams              |Object  |排序参数                     |是     |


#### 参考示例
```nodejs
import {getAllBlocks} from "u3.js/src";
const u3 = createU3(config)
u3.getAllBlocks({
    'page': 1,
    'pageSize': 10,
    'queryParams': {"block.producer":"ultrainio"},
    'sortParams': { _id: -1 }
})

json structure:
{ 
    "_id" : ObjectId("5b7d11b90fae3a7948ccc241"), 
    "block_id" : "00000002d99f33473ee5553e0993f6b821f68ce12787c7d5e8ba90393eb1f6e6", 
    "block" : {
        "timestamp" : "2018-08-22T07:33:13.000", 
        "producer" : "ultrainio", 
        "confirmed" : NumberInt(0), 
        "previous" : "00000001bcf2f448225d099685f14da76803028926af04d2607eafcf609c265c", 
        "transaction_mroot" : "0000000000000000000000000000000000000000000000000000000000000000", 
        "action_mroot" : "62c9c892ea1f9f7000a22c05d4aa6f2664637838536da3a7d3c16db447addaa8", 
        "schedule_version" : NumberInt(0), 
        "new_producers" : null, 
        "header_extensions" : [

        ], 
        "producer_signature" : "SIG_K1_K2fughyG1DWU21kahiCa7MCrc14Kg37dnW4Ck9PSH9b1c1LjbSmp...", 
        "transactions" : [

        ], 
        "block_extensions" : [

        ]
    }, 
    "block_num" : NumberInt(2), 
    "createdAt" : ISODate("2018-08-22T07:33:13.005+0000"), 
    "irreversible" : false
}
```

## getAllBlocksHeader 
```
(static) getAllBlocksHeader(page, pageSize, queryParams, sortParams)
```
按符号和创建者获取持有者

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|page              |Number  |页数                    |是     |
|pageSize              |Number  |每页显示的持有者数目                    |是     |
|queryParams              |Object  |持有者查询参数                     |是     |
|sortParams              |Object  |排序参数                     |是     |


#### 参考示例
```nodejs
import {createU3} from "u3.js/src";
const u3 = createU3(config)
u3.getHoldersBySymbol({
    'page': 1,
    'pageSize': 10,
    'queryParams': {"token_account":"ben","token_symbol":"BJMZ"},
    'sortParams': { current_balance: -1 }
})

json structure:
{
      "_id": "5be8fb7144ed468a4c348078",
      "block_id": "00002a69fd784315971f971571684d01dffd612efb791dabf12dff8b56dc2eb1",
      "block": {
          "timestamp": "2018-11-12T04:31:20.000",
          "proposer": "genesis",
          "proposerProof": "28bd727f9b9771cda08241fefab6426500e4d99a3083defef26d6860d02230abb2788a8a94aa009c05cee3fa05e82d57953008880de9fb74e31b31970a0c1c03",
          "version": 0,
          "previous": "00002a684784f9c27c0c22b749ec396aee458db7d4bb4aae9b2547ca1bfa6d22",
          "transaction_mroot": "0000000000000000000000000000000000000000000000000000000000000000",
          "action_mroot": "bfc55c5a4cbf78b7bd5cfb3ab67dde8f3c048d1a95ad85e1e869fb8a5f6d5ad5",
          "committee_mroot": "0000000000000000000000000000000000000000000000000000000000000000",
          "header_extensions": [],
          "signature": "",
          "block_extensions": []
      },
      "block_num": 10857,
      "createdAt": "2018-11-12T04:02:58.011Z",
      "irreversible": false,
      "id": "5be8fb7144ed468a4c348078"
    }
```

## getAllTokens 
```
(static) getAllTokens(page, pageSize, queryParams, sortParams)
```
获取所有的代币

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|page              |Number  |页数                    |是     |
|pageSize              |Number  |每页显示的代币数目                    |是     |
|queryParams              |Object  |代币查询参数                     |是     |
|sortParams              |Object  |排序参数                     |是     |


#### 参考示例
```nodejs
import {createU3} from "u3.js/src";
const u3 = createU3(config)
u3.getAllTokens({
    'page': 1,
    'pageSize': 10,
    'queryParams': {},
    'sortParams': { _id: -1 }
})

json structure:
{
      "_id": "5be2ccfe44ed468a4c33150c",
      "account": "ben",
      "symbol": "BJMZ",
      "__v": 0,
      "createdAt": "2018-11-07T11:31:10.065Z",
      "decimals": 4,
      "issue_time": "2018-11-07T11:30:57.654Z",
      "issuer": "ben",
      "max_supply": "10000000.0000",
      "supply": "10000000.0000",
      "updatedAt": "2018-11-08T01:51:10.074Z",
      "id": "5be2ccfe44ed468a4c33150c",
      "holders": 2
   }
```

## getAllTxs 
```
(static) getAllTxs(page, pageSize, queryParams, sortParams)
```
获取所有的交易信息

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|page              |Number  |页数                    |是     |
|pageSize              |Number  |每页显示的交易数目                    |是     |
|queryParams              |Object  |交易查询参数                     |是     |
|sortParams              |Object  |排序参数                     |是     |


#### 参考示例
```nodejs
import {getAllTxs} from "u3.js/src";
const u3 = createU3(config)
let query = { $and: [{ "actions.0.account": "ben" }, { $or: [{ "actions.0.data.id": 1257 }, { "actions.0.data.id": "1257" }] }] };
u3.getAllTxs({
    'page': 1,
    'pageSize': 10,
    'queryParams': query,
    'sortParams': { _id: -1 }
})

json structure:
{ 
    "_id" : ObjectId("5b7d11b859bd97fab30ba7f4"), 
    "trx_id" : "40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9", 
    "irreversible" : false, 
    "transaction_header" : {
        "expiration" : "2018-08-22T07:33:13", 
        "ref_block_num" : NumberInt(1), 
        "ref_block_prefix" : NumberLong(2517196066), 
        "max_net_usage_words" : NumberInt(0), 
        "max_cpu_usage_ms" : NumberInt(0), 
        "delay_sec" : NumberInt(0)
    }, 
    "actions" : [
        {
            "action_num" : NumberInt(0), 
            "trx_id" : "40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9", 
            "cfa" : false, 
            "account" : "ultrainio", 
            "name" : "onblock", 
            "authorization" : [
                {
                    "actor" : "ultrainio", 
                    "permission" : "active"
                }
            ], 
            "hex_data" : "80e34745000000000000000001000000000000000000000000000...",
            "data":{"id":1257}
        }
    ], 
    "transaction_extensions" : {

    }, 
    "signatures" : {

    }, 
    "context_free_data" : {

    }, 
    "createdAt" : ISODate("2018-08-22T07:33:12.469+0000")
}
```

## getBalanceByAccount 
```
(static) getBalanceByAccount(account)
```
按帐户获取余额

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|account              |String  |提供的账户                    |是     |



#### 参考示例
```nodejs
import {createU3} from "u3.js/src";
const u3 = createU3(config)
u3.getBalanceByAccount()

json structure:
[
 {
        "_id": "5be2ccfe44ed468a4c331510",
        "holder_account": "ben",
        "token_account": "ben",
        "token_symbol": "BJMZ",
        "__v": 0,
        "createdAt": "2018-11-07T11:31:10.070Z",
        "current_balance": "9999998.0000",
        "updatedAt": "2018-11-08T01:51:10.080Z",
        "id": "5be2ccfe44ed468a4c331510"
      }
]
```

## getBaseInfo 
```
(static) getBaseInfo(symbol)
```
获取代币基本信息

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|symbol              |String  |提供的代币符号                    |是     |



#### 参考示例
```nodejs
import {createU3} from "u3.js/src";
const u3 = createU3(config)
u3.getBaseInfo()

json structure:
{
    "head_block_num": 1559,
    "tx_num": 37,
    "tps": 0,
    "token_num": 0,
    "account_num": 17,
    "contract_num": 3
    }
```

## getBlocksByContract 
```
(static) getBlocksByContract(block_num, account, contract, contract_method)
```
按块编号、帐户名称、合约名称、合约方法获取块

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|block_num              |Number  |区块高度                    |是     |
|account              |String  |账户名称                    |是     |
|contract              |String  |合约名称                    |是     |
|contract_method              |String  |合约方法                    |是     |

#### 参考示例
```nodejs
import {getBlocksByContract} from "u3.js/src";
const u3 = createU3(config)
u3.getBlocksByContract({
    'block_num': 1,
    'account': "ultrainio",
    'contract': "utrio.token",
    'contract_method': "transfer"
})

json structure:
{ 
    "_id" : ObjectId("5b7d11b90fae3a7948ccc241"), 
    "block_id" : "00000002d99f33473ee5553e0993f6b821f68ce12787c7d5e8ba90393eb1f6e6", 
    "block" : {
        "timestamp" : "2018-08-22T07:33:13.000", 
        "producer" : "ultrainio", 
        "confirmed" : NumberInt(0), 
        "previous" : "00000001bcf2f448225d099685f14da76803028926af04d2607eafcf609c265c", 
        "transaction_mroot" : "0000000000000000000000000000000000000000000000000000000000000000", 
        "action_mroot" : "62c9c892ea1f9f7000a22c05d4aa6f2664637838536da3a7d3c16db447addaa8", 
        "schedule_version" : NumberInt(0), 
        "new_producers" : null, 
        "header_extensions" : [

        ], 
        "producer_signature" : "SIG_K1_K2fughyG1DWU21kahiCa7MCrc14Kg37dnW4Ck9PSH9b1c1LjbSmp...", 
        "transactions" : [

        ], 
        "block_extensions" : [

        ]
    }, 
    "block_num" : NumberInt(2), 
    "createdAt" : ISODate("2018-08-22T07:33:13.005+0000"), 
    "irreversible" : false
}
```

## getContractByName 
```
(static) getContractByName(name)
```
按名称获取合约

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|name              |String  |合约的名称                    |是     |


#### 参考示例
```nodejs
import {getContractByName} from "u3.js/src";
const u3 = createU3(config)
u3.getContractByName({
    'name': 'utrio.code'
})

json structure:
 {
    "_id" : ObjectId("5bd2e8347705c6005a6f4d12"),
    "name" : "utrio.code",
    "createdAt" : ISODate("2018-10-26T10:11:00.683+0000"),
    "abi" : {
        "version" : "ultrainio::abi/1.0",
        "types" : [...],
        "structs" : [...],
        "actions" : [...],
        "tables" : [...],
        "ricardian_clauses" : [],
        "error_messages" : [],
        "abi_extensions" : []
    },
    "updatedAt" : ISODate("2018-10-26T10:11:49.162+0000")
}
```

## getContracts 
```
(static) getContracts(page, pageSize, queryParams, sortParams)
```
获取所有合约信息

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|page              |Number  |页数                    |是     |
|pageSize              |Number  |每页显示的合约数目                    |是     |
|queryParams              |Object  |合约查询参数                     |是     |
|sortParams              |Object  |排序参数                     |是     |


#### 参考示例
```nodejs
import {getContracts} from "u3.js/src";
const u3 = createU3(config)
u3.getContracts({
    'page': 1,
    'pageSize': 10,
    'queryParams': {},
    'sortParams': { _id: -1 }
})

json structure:
 {
    "_id" : ObjectId("5bd2e8347705c6005a6f4d12"),
    "name" : "ultrainio",
    "createdAt" : ISODate("2018-10-26T10:11:00.683+0000"),
    "abi" : {
        "version" : "ultrainio::abi/1.0",
        "types" : [...],
        "structs" : [...],
        "actions" : [...],
        "tables" : [...],
        "ricardian_clauses" : [],
        "error_messages" : [],
        "abi_extensions" : []
    },
    "updatedAt" : ISODate("2018-10-26T10:11:49.162+0000")
}
```

## getCreateAccountByName 
```
(static) getCreateAccountByName(name)
```
按名称获取创建帐户

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|name              |String  |账户名称                    |是     |



#### 参考示例
```nodejs
import {getCreateAccountByName} from "u3.js/src";
const u3 = createU3(config)
u3.getCreateAccountByName({
     'name': 'utrio.code'
})

json structure:
{ 
    "_id" : ObjectId("5b7d11cc59bd97fab30ba86b"), 
    "name" : "utrio.code", 
    "createdAt" : ISODate("2018-08-22T07:33:32.092+0000")
}
```

## getExistAccount 
```
(static) getExistAccount(name) 
```
按帐户名称获取该帐户信息

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|name              |String  |账户名称                    |是     |


#### 参考示例
```nodejs
import {getExistAccount} from "u3.js/src";
const u3 = createU3(config)
u3.getExistAccount({
     'name': 'utrio.code'
})

json structure:
{ 
    "_id" : ObjectId("5b7d11cc59bd97fab30ba86b"), 
    "name" : "utrio.code", 
    "createdAt" : ISODate("2018-08-22T07:33:32.092+0000")
}
```

#### 返回结果类型
`Account` 或 `Null`

## getHoldersBySymbol 
```
(static) getHoldersBySymbol(page, pageSize, queryParams, sortParams)
```
按符号和创建者获取持有者

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|page              |Number  |页数                    |是     |
|pageSize              |Number  |每页显示的持有者数目                    |是     |
|queryParams              |Object  |持有者查询参数                     |是     |
|sortParams              |Object  |排序参数                     |是     |


#### 参考示例
```nodejs
import {createU3} from "u3.js/src";
const u3 = createU3(config)
u3.getHoldersBySymbol({
    'page': 1,
    'pageSize': 10,
    'queryParams': {"token_account":"ben","token_symbol":"BJMZ"},
    'sortParams': { current_balance: -1 }
})

json structure:
{
      "_id": "5be2ccfe44ed468a4c331510",
      "holder_account": "ben",
      "token_account": "ben",
      "token_symbol": "BJMZ",
      "__v": 0,
      "createdAt": "2018-11-07T11:31:10.070Z",
      "current_balance": "9999998.0000",
      "updatedAt": "2018-11-08T01:51:10.080Z",
      "id": "5be2ccfe44ed468a4c331510"
    }
```

## getProposerList 
```
(static) getProposerList(page, pageSize)
```
获取提议者列表

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|page              |Number  |页数                    |是     |
|pageSize              |Number  |每页显示的提议者数目                    |是     |


#### 参考示例
```nodejs
import {createU3} from "u3.js/src";
const u3 = createU3(config)
u3.getProposerList({
    'page': 1,
    'pageSize': 10
})

json structure:
{
      "_id": "genesis",
      "count": 972
    }
```

## getTokenBySymbol 
```
(static) getTokenBySymbol(symbol, creator)
```
通过代币和创建者获取令牌

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|symbol              |String  |代币符号                    |是     |
|creator              |String  |代币创建者                    |是     |


#### 参考示例
```nodejs
import {createU3} from "u3.js/src";
const u3 = createU3(config)
u3.getTokenBySymbol("ZTPJ","ben")

json structure:
{
    "_id": "5be2ccc244ed468a4c331487",
    "account": "ben",
    "symbol": "ZTPJ",
    "__v": 0,
    "createdAt": "2018-11-07T11:30:10.057Z",
    "decimals": 4,
    "issue_time": "2018-11-07T11:29:57.777Z",
    "issuer": "ben",
    "max_supply": "10000000.0000",
    "supply": "10000000.0000",
    "updatedAt": "2018-11-08T01:51:10.049Z",
    "id": "5be2ccc244ed468a4c331487"
    }
```

## getTxByTxId 
```
(static) getTxByTxId(id)
```
按照交易id获取交易信息

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|id              |String  |交易id                    |是     |



#### 参考示例
```nodejs
import {getTxByTxId} from "u3.js/src";
const u3 = createU3(config)
u3.getTxByTxId({
    'id': '40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9',
})

json structure:
{ 
    "_id" : ObjectId("5b7d11b859bd97fab30ba7f4"), 
    "trx_id" : "40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9", 
    "irreversible" : false, 
    "transaction_header" : {
        "expiration" : "2018-08-22T07:33:13", 
        "ref_block_num" : NumberInt(1), 
        "ref_block_prefix" : NumberLong(2517196066), 
        "max_net_usage_words" : NumberInt(0), 
        "max_cpu_usage_ms" : NumberInt(0), 
        "delay_sec" : NumberInt(0)
    }, 
    "actions" : [
        {
            "action_num" : NumberInt(0), 
            "trx_id" : "40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9", 
            "cfa" : false, 
            "account" : "ultrainio", 
            "name" : "onblock", 
            "authorization" : [
                {
                    "actor" : "ultrainio", 
                    "permission" : "active"
                }
            ], 
            "hex_data" : "80e34745000000000000000001000000000000000000000000000..."
        }
    ], 
    "transaction_extensions" : {

    }, 
    "signatures" : {

    }, 
    "context_free_data" : {

    }, 
    "createdAt" : ISODate("2018-08-22T07:33:12.469+0000")
}
```

## getTxsByBlockNum 
```
(static) getTxsByBlockNum(page, pageSize, queryParams, sortParams)
```
按照块高获取交易信息

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|page              |Number  |页数                    |是     |
|pageSize              |Number  |每页显示的交易数目                    |是     |
|queryParams              |Object  |交易查询参数                     |是     |
|sortParams              |Object  |排序参数                     |是     |



#### 参考示例
```nodejs
import {getTxsByBlockNum} from "u3.js/src";
const u3 = createU3(config)
u3.getTxsByBlockNum({
    'page': 1,
    'pageSize': 10,
    'queryParams': {
      'block_num': 1
    },
    'sortParams': { _id: -1 }
})

json structure:
{ 
    "_id" : ObjectId("5b7d11b859bd97fab30ba7f4"), 
    "trx_id" : "40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9", 
    "irreversible" : false, 
    "transaction_header" : {
        "expiration" : "2018-08-22T07:33:13", 
        "ref_block_num" : NumberInt(1), 
        "ref_block_prefix" : NumberLong(2517196066), 
        "max_net_usage_words" : NumberInt(0), 
        "max_cpu_usage_ms" : NumberInt(0), 
        "delay_sec" : NumberInt(0)
    }, 
    "actions" : [
        {
            "action_num" : NumberInt(0), 
            "trx_id" : "40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9", 
            "cfa" : false, 
            "account" : "ultrainio", 
            "name" : "onblock", 
            "authorization" : [
                {
                    "actor" : "ultrainio", 
                    "permission" : "active"
                }
            ], 
            "hex_data" : "80e347450000000000000000010000000000000000000000..."
        }
    ], 
    "transaction_extensions" : {

    }, 
    "signatures" : {

    }, 
    "context_free_data" : {

    }, 
    "createdAt" : ISODate("2018-08-22T07:33:12.469+0000")
}
```

## getTxTraceByTxid 
```
(static) getTxTraceByTxid(id)
```
按交易ID获取交易跟踪

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|id              |String  |交易id                    |是     |




#### 参考示例
```nodejs
import {getTxTraceByTxid} from "u3.js/src";
const u3 = createU3(config)
u3.getTxTraceByTxid({
    'id': '40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9'
})

json structure:

 "_id" : ObjectId("5b7d11b859bd97fab30ba7f4"),
 "trx_id" : "40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9",
 "irreversible" : false,
 "transaction_header" : {
        "expiration" : "2018-08-22T07:33:13", 
        "ref_block_num" : NumberInt(1), 
        "ref_block_prefix" : NumberLong(2517196066), 
        "max_net_usage_words" : NumberInt(0), 
        "max_cpu_usage_ms" : NumberInt(0), 
        "delay_sec" : NumberInt(0)
    },
 "actions" : [
 {
            "action_num" : NumberInt(0), 
            "trx_id" : "40ed51618da80804373fd84015548c8343da8c7ade8af00548ada4952d3e38b9", 
            "cfa" : false, 
            "account" : "ultrainio", 
            "name" : "onblock", 
            "authorization" : [
                {
                    "actor" : "ultrainio", 
                    "permission" : "active"
                }
            ], 
            "hex_data" : "80e347450000000000000000010000000000000000000000..."
        }
 ],
 "transaction_extensions" : {

    },
 "signatures" : {

    },
 "context_free_data" : {

    },
 "createdAt" : ISODate("2018-08-22T07:33:12.469+0000")
 }
```

## search 
```
(async, static) search(param)
```
查询块/交易/帐户

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|param              |String  |账户/区块高度/交易hash/合同账户                    |是     |



#### 参考示例
```nodejs
import {search} from "u3.js/src";
const u3 = createU3(config)
u3.search(5b7d11b859bd97fab30ba7f5)
```