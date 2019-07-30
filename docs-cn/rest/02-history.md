## 简介

历史REST接口的BaseUrl如下：

开发环境（单链）

> http://127.0.0.1:3000
  
### 测试网环境（多链）

**主链**
> http://ultrain-history.natapp1.cc

**侧链11**
> http://pioneer-history.natapp1.cc

**侧链12**
> http://power-history.natapp1.cc

### 主网环境（多链）

**主链**
> https://history.ultrain.services

**侧链poineer**
> https://history-pioneer.ultrain.services

**侧链unitopia**
> https://history-unitopia.ultrain.services

**侧链new-retail**
> https://history-new-retail.ultrain.services

## 方法列表

超脑历史 REST 接口所支持的方法如下表所示。

| 方法                                                                                        | 描述                                             |
| :------------------------------------------------------------------------------------------| :------------------------------------------------|
| [getAccountByName](docs-cn/rest/02-history#getAccountByName)                |根据账户名称获取账户信息                              |
| [getActionsByAccount](docs-cn/rest/02-history#getActionsByAccount)          |根据账户名称查找其所有的交易行为                       |
| [getActionsByTxid](docs-cn/rest/02-history#getActionsByTxid)                |根据交易id查找相应的交易行为                          |
| [getAllAccounts](docs-cn/rest/02-history#getAllAccounts)                    |获取全部的账户信息                                   |
| [getAllBlocks](docs-cn/rest/02-history#getAllBlocks)                        |获取全部的区块信息                                   |
| [getAllTokens](docs-cn/rest/02-history#getAllTokens)                        |获取所以的代币信息                                   |
| [getAllTxs](docs-cn/rest/02-history#getAllTxs)                              |获取全部的交易信息                                   |
| [getContractByName](docs-cn/rest/02-history#getContractByName)              |根据合约名称查找完整合约信息                           |
| [getContracts](docs-cn/rest/02-history#getContracts)                        |获取全部的合约信息                                   |
| [getCreateAccountByName](docs-cn/rest/02-history#getCreateAccountByName)    |根据合约名称查找账户创建者                            |
| [getHoldersBySymbol](docs-cn/rest/02-history#getHoldersBySymbol)            |根据代币名称和创建者获取其代币持有者                    |
| [getTokenBalanceByAccount](docs-cn/rest/02-history#getTokenBalanceByAccount)|根据账户名获取代币余额                                |
| [getTokenBySymbol](docs-cn/rest/02-history#getTokenBySymbol)                |根据代币名称和创建者获取其代币的基本信息                 |
| [getTxByTxId](docs-cn/rest/02-history#getTxByTxId)                          |根据交易id查找相应的交易信息                           |
| [getTxsByBlockNum](docs-cn/rest/02-history#getTxsByBlockNum)                |根据区块块高查询交易信息                               |
| [getTxTraceByTxid](docs-cn/rest/02-history#getTxTraceByTxid)                |根据交易id查找交易信息                                |


## getAccountByName

根据账户名称查找完整的账户信息

#### 参数说明
|参数        |类型    |说明              |是否必填|
| :---------| :------| :---------------|:-----|
|name       |string  |获取其信息的账户名称|是     |

#### 参考示例


```
  var url = 'http://127.0.0.1:3000/accounts/ben';
  await Axios.post(url).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST http://127.0.0.1:3000/accounts/ben

```


#### 返回结果类型
`Object`

#### 返回结果
```
{ _id: '5d2952d977ebf1f9237ac0d6',
  name: 'ben',
  createdAt: '2019-07-13T03:41:13.142Z',
  abi: 
   { version: 'ultraio:1.0:UIP06',
     types: [ [Object], [Object], [Object] ],
     structs: 
      [ [Object],
        [Object],
        [Object],
        [Object],
        [Object],
        [Object],
        [Object],
        [Object] ],
     actions: [ [Object], [Object], [Object], [Object], [Object], [Object] ],
     tables: [ [Object], [Object] ],
     ricardian_clauses: [],
     error_messages: [],
     abi_extensions: [] },
  updatedAt: '2019-07-13T03:42:40.725Z',
  id: '5d2952d977ebf1f9237ac0d6',
  activePk: 'UTR6ujHgxt2hUz7BfvJz6epfvWzhXEp1ChVKEFZxf1Ld5ea83WE6V',
  ownerPk: 'UTR6ujHgxt2hUz7BfvJz6epfvWzhXEp1ChVKEFZxf1Ld5ea83WE6V' }
```


## getActionsByAccount
根据账户名称查找其所以的交易行为

#### 参数说明
|参数         |类型    |说明                    |是否必填|
| :----------| :------| :---------------------|:------|
|account_name|string  |获取其交易行为信息的账户名称|是     |
|page        |number  |当前显示交易行为的页数     |否     |
|pageSize    |number  |每页显示的交易行为数量     |否     |
|queryParams |object  |查询参数                 |否     |
|sortParams  |object  |排列参数                 |否     |

#### 参考示例

```
  var url = 'http://127.0.0.1:3000/actions/by/account';
  var data = {
    'page': 1,
    'pageSize': 10,
    'sortParams': { _id: -1 },
    "queryParams":{ "account_name": "ben" }
  }
  await Axios.post(url,data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
curl -H "Content-Type:application/json" -X POST -d '{"page":1,"pageSize":10,"sortParams":{"_id":-1},"queryParams":{"account_name":"ben"}}' http://127.0.0.1:3000/actions/by/account

```

#### 返回结果类型
`Object`

#### 返回结果
```
{ pageNumber: 1,
  total: 7,
  pageCount: 1,
  results: 
   [ { _id: '5d29ea68f988c000544c0331',
       action_num: 0,
       trx_id: 'd3f084f023af7b187dbd0acdc4bc083e00c3162b9fb5c1f6f3d987d7038d6eaa',
       cfa: false,
       account: 'ultrainio',
       name: 'resourcelease',
       authorization: [Array],
       data: [Object],
       id: '5d29ea68f988c000544c0331',
       updatedAt: '2019-07-13T14:28:00.500Z',
       createdAt: '2019-07-13T14:27:52.747Z' },
     { _id: '5d29e1f4f988c000544c032c',
       action_num: 1,
       trx_id: '230bbb14446ca02b80d32695d185e5a0a5cb13a84dd498cc8a3c8a588778d679',
       cfa: false,
       account: 'ben',
       name: 'issue',
       authorization: [Array],
       data: [Object],
       id: '5d29e1f4f988c000544c032c',
       updatedAt: '2019-07-13T13:51:56.281Z',
       createdAt: '2019-07-13T13:51:48.721Z' },
     { _id: '5d29e1f4f988c000544c032b',
       action_num: 0,
       trx_id: '230bbb14446ca02b80d32695d185e5a0a5cb13a84dd498cc8a3c8a588778d679',
       cfa: false,
       account: 'ben',
       name: 'create',
       authorization: [Array],
       data: [Object],
       id: '5d29e1f4f988c000544c032b',
       updatedAt: '2019-07-13T13:51:56.281Z',
       createdAt: '2019-07-13T13:51:48.721Z' },
     { _id: '5d29d230f988c000544c031d',
       action_num: 0,
       trx_id: 'f8b426780499d8b0561331d61acba73d73b549164cc2bd9dd429242845775164',
       cfa: false,
       account: 'ultrainio',
       name: 'newaccount',
       authorization: [Array],
       data: [Object],
       id: '5d29d230f988c000544c031d',
       updatedAt: '2019-07-13T12:44:40.660Z',
       createdAt: '2019-07-13T12:44:32.103Z' },
     { _id: '5d295330f988c000544c031b',
       action_num: 1,
       trx_id: 'ba952e3c3f035b875a660bc7d9e573ac3e4c828765a534d0522b544b4128e683',
       cfa: false,
       account: 'ultrainio',
       name: 'setabi',
       authorization: [Array],
       data: [Object],
       id: '5d295330f988c000544c031b',
       updatedAt: '2019-07-13T03:42:48.215Z',
       createdAt: '2019-07-13T03:42:40.716Z' },
     { _id: '5d295330f988c000544c031a',
       action_num: 0,
       trx_id: 'ba952e3c3f035b875a660bc7d9e573ac3e4c828765a534d0522b544b4128e683',
       cfa: false,
       account: 'ultrainio',
       name: 'setcode',
       authorization: [Array],
       data: [Object],
       id: '5d295330f988c000544c031a',
       updatedAt: '2019-07-13T03:42:48.215Z',
       createdAt: '2019-07-13T03:42:40.716Z' },
     { _id: '5d295308f988c000544c02eb',
       action_num: 0,
       trx_id: 'bc4f2d5d464ca5b4ee4706b8550c8983c07589db9e226caf01f1c378525c4f97',
       cfa: false,
       account: 'utrio.token',
       name: 'transfer',
       authorization: [Array],
       data: [Object],
       id: '5d295308f988c000544c02eb',
       updatedAt: '2019-07-13T03:42:08.693Z',
       createdAt: '2019-07-13T03:42:00.156Z' } ] }
```

## getActionsByTxid

根据交易id查找交易行为

#### 参数说明
|参数        |类型    |说明                   |是否必填|
| :---------| :------| :--------------------|:-----|
|trx_id     |string  |获取其交易行为信息的交易id|是    |

#### 参考示例

```
  var url = 'http://127.0.0.1:3000/actions/tx/d3f084f023af7b187dbd0acdc4bc083e00c3162b9fb5c1f6f3d987d7038d6eaa';
  await Axios.post(url).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST http://127.0.0.1:3000/actions/tx/d3f084f023af7b187dbd0acdc4bc083e00c3162b9fb5c1f6f3d987d7038d6eaa

```

#### 返回结果类型
`Array`

#### 返回结果
```
[ { _id: '5d29ea68f988c000544c0331',
    action_num: 0,
    trx_id: 'd3f084f023af7b187dbd0acdc4bc083e00c3162b9fb5c1f6f3d987d7038d6eaa',
    cfa: false,
    account: 'ultrainio',
    name: 'resourcelease',
    authorization: [ [Object] ],
    data: 
     { from: 'ben',
       receiver: 'bob',
       combosize: 1,
       days: 2,
       location: 'ultrainio' },
    id: '5d29ea68f988c000544c0331' } ]
```

## getAllAccounts
获取所有的合约信息

#### 参数说明
|参数        |类型    |说明           |是否必填|
| :---------| :------| :-------------|:-----|
|page       |number  |当前显示账户的页数|否   |
|pageSize   |number  |每页显示的账户数量|否   |
|queryParams|object  |查询参数        |否   |
|sortParams |object  |排列参数        |否   |

#### 参考示例

```
  var url = 'http://127.0.0.1:3000/accounts';
  var data = {
    'page': 1,
    'pageSize': 10,
    'sortParams': { _id: -1 },
    "queryParams":{ }
  }
  await Axios.post(url,data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
curl -H "Content-Type:application/json" -X POST -d '{"page":1,"pageSize":10,"sortParams":{"_id":-1},"queryParams":{}}' http://127.0.0.1:3000/accounts

```

#### 返回结果类型
`Object`

#### 返回结果

```
{
    "pageNumber": 1,
    "total": 331,
    "pageCount": 34,
    "results": [
        {
            "_id": "5d0f359094b14cda69bcd99e",
            "name": "haiyang123",
            "createdAt": "2019-06-23T08:17:20.332Z",
            "id": "5d0f359094b14cda69bcd99e",
            "activePk": "UTR7MdWUHC4cYDisav9XoMmHCgAWsPX3iojxtcCtfu4748D6mzxdB",
            "ownerPk": "UTR7MdWUHC4cYDisav9XoMmHCgAWsPX3iojxtcCtfu4748D6mzxdB"
        },
        {
            "_id": "5d0ee66294b14cda69bbf555",
            "name": "eeee1",
            "createdAt": "2019-06-23T02:39:30.478Z",
            "id": "5d0ee66294b14cda69bbf555",
            "activePk": "UTR7by54TQp7APnvSbB95hgNjag4ES6UmevMhtSk6jp8wMhsivc5M",
            "ownerPk": "UTR7by54TQp7APnvSbB95hgNjag4ES6UmevMhtSk6jp8wMhsivc5M"
        },
		...
	]
}
```

## getAllBlocks

获取所有的区块信息

#### 参数说明
|参数        |类型    |说明           |是否必填|
| :---------| :------| :-------------|:-----|
|page       |number  |当前显示区块的页数|否    |
|pageSize   |number  |每页显示的区块数量|否    |
|queryParams|object  |查询参数        |否    |
|sortParams |object  |排列参数        |否    |

#### 参考示例

```
  var url = 'http://127.0.0.1:3000/blocks';
  var data = {
    'page': 1,
    'pageSize': 10,
    'sortParams': { _id: -1 },
    "queryParams":{ "block.producer":"ultrainio" }
  }
  await Axios.post(url,data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
curl -H "Content-Type:application/json" -X POST -d '{"page":1,"pageSize":10,"sortParams":{"_id":-1},"queryParams":{"block.producer":"ultrainio"}}' http://127.0.0.1:3000/blocks

```

#### 返回参数类型
`Object`

#### 返回结果
```
{
    "pageNumber": 1,
    "total": 431436,
    "pageCount": 43144,
    "results": [
		{
            "_id": "5d1031b694b14cda69bfae9e",
            "block_id": "0006954cbcc0863127ed33b3bbfcb414476dd73ce2802d345ff0e52470a2548d",
            "block": {
                "timestamp": "2019-06-24T02:13:00.000",
                "proposer": "master.113",
                "version": 0,
                "previous": "0006954b818e6ebf6fcd06815b32da36e8dbae5549e975c0153f43bb9c7c703c",
                "transaction_mroot": "2fdb2e54668558092f1a1a40c4215bbecf4805827808ea35b686fe3fba863969",
                "action_mroot": "0fa9439a8161a628bc0b4436be9a4faaa8d99a232f24d06efa93664f218dcd87",
                "committee_mroot": "fa4976d810c625b34a7662019705e3cd8fd5a2e87837d1183d8d42f59cc32564",
                "header_extensions": [],
                "signature": "502f3638348e4a95563d6c643f25e20de286d638b65628182ef3006ecacdcd6581693d8f5e6f875bd29ec082675ec66008d55471937013269fb77e6146f3700d",
                "trx_ids": [
                    "14983086b2e1994569239be6106d295ae43427a60952df42a7939d97bd3d525c",
                    "291c1d54c5438198cc5caf428dc73115115593e5e5d81fbca9eb3e8e31124da9",
                    "2a5972054e567d7281d329bef32287c50c4927460d5922697c9b28866d79be22",
                    "b19c9e0c3c2cd7bc9e51a5eabfb128cd147bff0b3725b5d8c342a03b502fce6b"
                ],
                "block_extensions": []
            },
            "block_num": 431436,
            "createdAt": "2019-06-24T02:13:10.324Z",
            "id": "5d1031b694b14cda69bfae9e"
        },
		...
	]
}
```

## getAllTokens
获取所以的代币信息

#### 参数说明
|参数        |类型    |说明                   |是否必填|
| :---------| :------| :--------------------|:------|
|page       |number  |当前显示代币的页数       |否      |
|pageSize   |number  |每页显示的代币数量       |否      |
|queryParams|object  |查询参数               |否      |
|sortParams |object  |排列参数               |否      |

#### 参考案例

```
  var url = 'http://127.0.0.1:3000/tokens';
  var data = {
    'page': 1,
    'pageSize': 10,
    'sortParams': { _id: -1 },
    "queryParams":{  }
  }
  await Axios.post(url,data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
curl -H "Content-Type:application/json" -X POST -d '{"page":1,"pageSize":10,"sortParams":{"_id":-1},"queryParams":{}}' http://127.0.0.1:3000/tokens

```

#### 返回结果类型
`Object`

#### 返回结果

```
{ pageNumber: 1,
  total: 1,
  pageCount: 1,
  results: 
   [ { _id: '5d29e21e77ebf1f9237afd57',
       account: 'ben',
       symbol: 'GLJV',
       __v: 0,
       createdAt: '2019-07-13T13:52:30.131Z',
       decimals: 4,
       issue_time: '2019-07-13T13:51:48.721Z',
       issuer: 'ben',
       max_supply: '10000000.0000',
       supply: '10000000.0000',
       updatedAt: '2019-07-14T02:31:30.021Z',
       id: '5d29e21e77ebf1f9237afd57',
       holders: 1 } ] }
```

## getAllTxs
获取全部的交易信息

#### 参数说明
|参数        |类型    |说明           |是否必填|
| :---------| :------| :-------------|:----|
|page       |number  |当前显示交易的页数|否   |
|pageSize   |number  |每页显示的交易数量|否   |
|queryParams|object  |查询参数        |否   |
|sortParams |object  |排列参数        |否   |

#### 参考示例

```
  var url = 'http://127.0.0.1:3000/txs';
  var data = {
    'page': 1,
    'pageSize': 10,
    'sortParams': { _id: -1 },
    "queryParams":{  }
  }
  await Axios.post(url,data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
curl -H "Content-Type:application/json" -X POST -d '{"page":1,"pageSize":10,"sortParams":{"_id":-1},"queryParams":{}}' http://127.0.0.1:3000/txs

```

#### 返回结果类型
`Object`

#### 返回结果
```
{
    "pageNumber": 1,
    "total": 1136962,
    "pageCount": 113697,
    "results": [
        {
            "_id": "5d1035da436aea32405a726e",
            "trx_id": "e0f1dadf878b7542b573daa185fe2267dd9a8784ae3439e042687b673845558b",
            "irreversible": false,
            "action_count": 1,
            "transaction_header": {
                "expiration": "2019-06-24T02:31:20",
                "ref_block_num": 38323,
                "ref_block_prefix": 4168243994,
                "max_net_usage_words": 0,
                "max_cpu_usage_ms": 0,
                "delay_sec": 0
            },
            "signing_keys": {
                "0": "UTR5kNr7rCgkkkyqXXZh51ZAHm8QbvhhX1KHH6wT4zzVMi7w8miZz"
            },
            "signatures": {
                "0": "SIG_K1_K12FSPBBtjC26tZajmHqRkJh1P4KwLBo2XJYLioxZGYwXQhWsNqGG7Q8QYA3isTzH8WceFDLdYsBEfj3nSBtsrkoEqEb8G"
            },
            "createdAt": "2019-06-24T02:30:50.063Z",
            "id": "5d1035da436aea32405a726e",
            "actions": [
                {
                    "_id": "5d1035da436aea32405a726d",
                    "action_num": 0,
                    "trx_id": "e0f1dadf878b7542b573daa185fe2267dd9a8784ae3439e042687b673845558b",
                    "cfa": false,
                    "account": "utrio.rand",
                    "name": "vote",
                    "authorization": [
                        {
                            "actor": "master.113",
                            "permission": "active"
                        }
                    ],
                    "data": {
                        "pk_proof": "0323E4B32475601C2DF377F4B2BF30424D2231318FDFBFFE413798BB8A945937C34D7384D798E8C1758C7E2AB7479EC6A9D6C868CD5B71796D3BB1E303191C95A9F30AB927D945BB614C2285E4CFC03A92",
                        "blockNum": 431540
                    },
                    "id": "5d1035da436aea32405a726d"
                }
            ]
        },
		...
	]
}
```

## getContractByName
根据合约名称查找完整的合约信息

#### 参数说明
|参数        |类型    |说明               |是否必填|
| :---------| :------| :----------------|:-----|
|name       |string  |获取合约信息的合约名称|是    |


#### 参考示例

```
  var url = 'http://127.0.0.1:3000/contracts/ben';
  await Axios.post(url).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST http://127.0.0.1:3000/contracts/ben

```

#### 返回参数类型
`Object`

#### 返回结果
```json
{
    "_id": "5ce75b6c94b14cda6904203a",
    "name": "utrio.bank",
    "createdAt": "2019-05-24T02:48:12.338Z",
    "abi": {
        "version": "ultrainio::abi/1.0",
        "types": [
            {
                "new_type_name": "account_name",
                "type": "name"
            }
        ],
        "structs": [
            {
                "name": "bulletin_info",
                "base": "",
                "fields": [
                    {
                        "name": "receiver",
                        "type": "account_name"
                    },
                    {
                        "name": "quantity",
                        "type": "asset"
                    }
                ]
            },
            {
                "name": "bulletin_bank",
                "base": "",
                "fields": [
                    {
                        "name": "block_height",
                        "type": "uint64"
                    },
                    {
                        "name": "bulletin_infos",
                        "type": "bulletin_info[]"
                    }
                ]
            },
            {
                "name": "chain_balance",
                "base": "",
                "fields": [
                    {
                        "name": "chain_name",
                        "type": "name"
                    },
                    {
                        "name": "balance",
                        "type": "asset"
                    }
                ]
            }
        ],
        "actions": [],
        "tables": [
            {
                "name": "bulletinbank",
                "index_type": "i64",
                "key_names": [
                    "block_height"
                ],
                "key_types": [
                    "uint64"
                ],
                "type": "bulletin_bank"
            },
            {
                "name": "chainbalance",
                "index_type": "i64",
                "key_names": [
                    "chain_name"
                ],
                "key_types": [
                    "uint64"
                ],
                "type": "chain_balance"
            }
        ],
        "ricardian_clauses": [],
        "error_messages": [],
        "abi_extensions": []
    },
    "updatedAt": "2019-05-24T02:48:12.358Z",
    "id": "5ce75b6c94b14cda6904203a"
}
```

## getContracts
获取所以的合约信息

#### 参数说明
|参数        |类型    |说明           |是否必填|
| :---------| :------| :-------------|:-----|
|page       |number  |当前显示合约的页数|否    |
|pageSize   |number  |每页显示的合约数量|否    |
|queryParams|object  |查询参数        |否    |
|sortParams |object  |排列参数        |否    |

#### 参考示例

```
  var url = 'http://127.0.0.1:3000/contracts';
  var data = {
    'page': 1,
    'pageSize': 10,
    'sortParams': { _id: -1 },
    "queryParams":{  }
  }
  await Axios.post(url,data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -H "Content-Type:application/json" -X POST -d '{"page":1,"pageSize":10,"sortParams":{"_id":-1},"queryParams":{}}' http://127.0.0.1:3000/contracts

```

#### 返回结果类型
`Object`

#### 响应结果
```
{
    "pageNumber": 1,
    "total": 5,
    "pageCount": 1,
    "results": [
		{
            "_id": "5ce75b6c94b14cda6904203a",
            "name": "utrio.bank",
            "createdAt": "2019-05-24T02:48:12.338Z",
            "abi": {
                "version": "ultrainio::abi/1.0",
                "types": [
                    {
                        "new_type_name": "account_name",
                        "type": "name"
                    }
                ],
                "structs": [
                    {
                        "name": "bulletin_info",
                        "base": "",
                        "fields": [
                            {
                                "name": "receiver",
                                "type": "account_name"
                            },
                            {
                                "name": "quantity",
                                "type": "asset"
                            }
                        ]
                    },
                    {
                        "name": "bulletin_bank",
                        "base": "",
                        "fields": [
                            {
                                "name": "block_height",
                                "type": "uint64"
                            },
                            {
                                "name": "bulletin_infos",
                                "type": "bulletin_info[]"
                            }
                        ]
                    },
                    {
                        "name": "chain_balance",
                        "base": "",
                        "fields": [
                            {
                                "name": "chain_name",
                                "type": "name"
                            },
                            {
                                "name": "balance",
                                "type": "asset"
                            }
                        ]
                    }
                ],
                "actions": [],
                "tables": [
                    {
                        "name": "bulletinbank",
                        "index_type": "i64",
                        "key_names": [
                            "block_height"
                        ],
                        "key_types": [
                            "uint64"
                        ],
                        "type": "bulletin_bank"
                    },
                    {
                        "name": "chainbalance",
                        "index_type": "i64",
                        "key_names": [
                            "chain_name"
                        ],
                        "key_types": [
                            "uint64"
                        ],
                        "type": "chain_balance"
                    }
                ],
                "ricardian_clauses": [],
                "error_messages": [],
                "abi_extensions": []
            },
            "updatedAt": "2019-05-24T02:48:12.358Z",
            "id": "5ce75b6c94b14cda6904203a"
        }
	...
	]
}
```

## getCreateAccountByName
根据合约名称查找账户创建者

#### 参数说明
|参数        |类型    |说明             |是否必填|
| :---------| :------| :--------------|:-----|
|name       |string  |获取创建合约者的合约名称|是|

#### 参考示例


```
  var url = 'http://127.0.0.1:3000/getcreateaccount';
  var data = {
    'name': "ben",
  }
  await Axios.post(url,data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X -d '{ "name": "ben" }' POST http://127.0.0.1:3000/getcreateaccount

```

#### 返回结果类型
Object

#### 返回结果
```json
{
    "account": "utrioaccount",
    "updatedAt": "2019-06-23T08:17:40.458Z"
}
```

## getHoldersBySymbol
根据代币名称和创建者获取其代币持有者

#### 参数说明
|参数        |类型    |说明                   |是否必填|
| :---------| :------| :--------------------|:------|
|page       |number  |当前显示代币持有者的页数  |否     |
|pageSize   |number  |每页显示的代币持有者数量  |否     |
|queryParams|object  |查询参数               |否     |
|sortParams |object  |排列参数               |否     |

#### 参考示例

```
  var url = 'http://127.0.0.1:3000/holders/by/symbol';
  var data = {
    'page': 1,
    'pageSize': 10,
    'sortParams': { _id: -1 },
    "queryParams":{ "token_symbol":"GLJV" }
  }
  await Axios.post(url,data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
curl -H "Content-Type:application/json" -X POST -d '{"page":1,"pageSize":10,"sortParams":{"_id":-1},"queryParams":{"token_symbol":"GLJV"}}' http://127.0.0.1:3000/holders/by/symbol

```

#### 返回结果类型
`Object`

#### 返回结果
```
{ pageNumber: 1,
  total: 1,
  pageCount: 1,
  results: 
   [ { current_balance: 10000000,
       _id: '5d29e21e77ebf1f9237afd53',
       holder_account: 'ben',
       token_account: 'ben',
       token_symbol: 'GLJV',
       __v: 0,
       createdAt: '2019-07-13T13:52:30.043Z',
       updatedAt: '2019-07-14T02:39:30.012Z',
       id: '5d29e21e77ebf1f9237afd53' } ] }
```

## getTokenBalanceByAccount
根据账户名获取其代币余额

#### 参数说明
|参数         |类型     |说明                      |是否必填|
| :----------| :------| :------------------------|:-----|
|account_name|string  |获取其代币余额的账户名        |是    |

#### 参考示例
```
  var url = 'http://127.0.0.1:3000/balance/ben';
  var data = {
    'page': 1,
    'pageSize': 10,
    'sortParams': { _id: -1 },
    "queryParams":{ "token_symbol":"GLJV" }
  }
  await Axios.post(url,data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
curl -H "Content-Type:application/json" -X POST -d '{"page":1,"pageSize":10,"sortParams":{"_id":-1},"queryParams":{"token_symbol":"GLJV"}}' http://127.0.0.1:3000/balance/ben

```

#### 返回结果类型
`Array`

#### 返回结果
```
[ { current_balance: 10000000,
    _id: '5d29e21e77ebf1f9237afd53',
    holder_account: 'ben',
    token_account: 'ben',
    token_symbol: 'GLJV',
    __v: 0,
    createdAt: '2019-07-13T13:52:30.043Z',
    updatedAt: '2019-07-14T02:43:30.013Z',
    id: '5d29e21e77ebf1f9237afd53' } ]
```

## getTokenBySymbol
根据代币名称和创建者获取其代币信息

#### 参数说明
|参数        |类型    |说明                   |是否必填|
| :---------| :------| :--------------------|:-----|
|symbol     |string  |代币符号               |是    |
|creator    |string  |代币的创建者            |是    |

#### 参考示例

```
  var url = 'http://127.0.0.1:3000/token/GLJV/ben';
  await Axios.post(url).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST http://127.0.0.1:3000/token/GLJV/ben

```

#### 返回结果类型
`Object`

#### 返回结果
```
{ _id: '5d29e21e77ebf1f9237afd57',
  account: 'ben',
  symbol: 'GLJV',
  __v: 0,
  createdAt: '2019-07-13T13:52:30.131Z',
  decimals: 4,
  issue_time: '2019-07-13T13:51:48.721Z',
  issuer: 'ben',
  max_supply: '10000000.0000',
  supply: '10000000.0000',
  updatedAt: '2019-07-14T02:47:30.020Z',
  id: '5d29e21e77ebf1f9237afd57' }
```


## getTxByTxId
根据交易id查找交易信息

#### 参数说明
|参数        |类型    |说明            |是否必填|
| :---------| :------| :-------------|:------|
|trx_id     |string  |获取其信息的交易id|是     |

#### 参考示例

```
  var url = 'http://127.0.0.1:3000/txs/d3f084f023af7b187dbd0acdc4bc083e00c3162b9fb5c1f6f3d987d7038d6eaa';
  await Axios.post(url).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST http://127.0.0.1:3000/txs/d3f084f023af7b187dbd0acdc4bc083e00c3162b9fb5c1f6f3d987d7038d6eaa

```

#### 返回类型结果
`Object`

#### 返回结果
```json
{
    "_id": "5d1035da436aea32405a726e",
    "trx_id": "d3f084f023af7b187dbd0acdc4bc083e00c3162b9fb5c1f6f3d987d7038d6eaa",
    "irreversible": true,
    "action_count": 1,
    "transaction_header": {
        "expiration": "2019-06-24T02:31:20",
        "ref_block_num": 38323,
        "ref_block_prefix": 4168243994,
        "max_net_usage_words": 0,
        "max_cpu_usage_ms": 0,
        "delay_sec": 0
    },
    "signing_keys": {
        "0": "UTR5kNr7rCgkkkyqXXZh51ZAHm8QbvhhX1KHH6wT4zzVMi7w8miZz"
    },
    "signatures": {
        "0": "SIG_K1_K12FSPBBtjC26tZajmHqRkJh1P4KwLBo2XJYLioxZGYwXQhWsNqGG7Q8QYA3isTzH8WceFDLdYsBEfj3nSBtsrkoEqEb8G"
    },
    "createdAt": "2019-06-24T02:30:50.063Z",
    "block_id": "000695b608f56fa654b92514c3a3e9de92032f510ec07e191e101f8bd5ba305a",
    "block_num": 431542,
    "updatedAt": "2019-06-24T02:31:10.091Z",
    "id": "5d1035da436aea32405a726e"
}
```

## getTxsByBlockNum
根据区块块高查询交易信息

#### 参数说明
|参数        |类型    |说明                    |是否必填|
| :---------| :------| :---------------------|:------|
|block_num  |number  |获取其交易行为信息的区块块号|是     |
|page       |number  |当前显示交易行为的页数     |否     |
|pageSize   |number  |每页显示的交易行为数量     |否     |
|queryParams|object  |查询参数                 |否     |
|sortParams |object  |排列参数                 |否     |

#### 参考示例

```
  var url = 'http://127.0.0.1:3000/txs/by/blocknum';
  var data = {
    'page': 1,
    'pageSize': 10,
    'sortParams': { _id: -1 },
    "queryParams":{ "block_num": 100 }
  }
  await Axios.post(url,data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
curl -H "Content-Type:application/json" -X POST -d '{"page":1,"pageSize":10,"sortParams":{"_id":-1},"queryParams":{"block_num": 100}}' http://127.0.0.1:3000/txs/by/blocknum

```

#### 返回结果类型
`Array`

#### 返回结果
```
{
    "pageNumber": 1,
    "total": 4,
    "pageCount": 1,
    "results": [
        {
            "_id": "5d108bf2436aea32405ac29c",
            "trx_id": "a7dbb2692b10805ad4de096cdf79b88c0a9c158ccf5f0fee631f32381433475f",
            "irreversible": true,
            "action_count": 1,
            "transaction_header": {
                "expiration": "2019-06-24T08:38:40",
                "ref_block_num": 40527,
                "ref_block_prefix": 1157117559,
                "max_net_usage_words": 0,
                "max_cpu_usage_ms": 0,
                "delay_sec": 0
            },
            "signing_keys": {
                "0": "UTR5kNr7rCgkkkyqXXZh51ZAHm8QbvhhX1KHH6wT4zzVMi7w8miZz"
            },
            "signatures": {
                "0": "SIG_K1_JyCsqQYUx8F3j4YjtrvYZv9ZgEoZQ981gihxc9eHTfujzbBNUapyKZfo54m9uau24ZhQ4kpF1p2HYfHX5toZqu71sNBZ3z"
            },
            "createdAt": "2019-06-24T08:38:10.394Z",
            "block_id": "00069e524ab06ffcec2d93e19f4a457f2d432c26ded9adee54cd64fe7eb83c72",
            "block_num": 100,
            "updatedAt": "2019-06-24T08:38:30.437Z",
            "id": "5d108bf2436aea32405ac29c"
        },
        {
            "_id": "5d108bf2436aea32405ac298",
            "trx_id": "a8126bcfbaec3496af50df97965723d233b287376686621a74c38717b7d3d209",
            "irreversible": true,
            "action_count": 1,
            "transaction_header": {
                "expiration": "2019-06-24T08:38:30",
                "ref_block_num": 40526,
                "ref_block_prefix": 4090110442,
                "max_net_usage_words": 0,
                "max_cpu_usage_ms": 0,
                "delay_sec": 0
            },
            "signing_keys": {
                "0": "UTR8YCCmCEAM4GGqhSwQTB4SwP3J4sJTs721cAjZ6AXHr55qbig29"
            },
            "signatures": {
                "0": "SIG_K1_JwnzH7wPhtJMWjCfHqDJJz8cKYRBDDAk7ZDv1PzNszmZX2pc6CJmxcm6cJjjqRFtLAt1LL8GCb2RAEKpCUfPAFvHwGdmra"
            },
            "createdAt": "2019-06-24T08:38:10.386Z",
            "block_id": "00069e524ab06ffcec2d93e19f4a457f2d432c26ded9adee54cd64fe7eb83c72",
            "block_num": 100,
            "updatedAt": "2019-06-24T08:38:30.437Z",
            "id": "5d108bf2436aea32405ac298"
        },
        ...
    ]
}
```


## getTxTraceByTxid
根据交易id查找交易信息

#### 参数说明
|参数        |类型    |说明                   |是否必填|
| :---------| :------| :--------------------|:------|
|tx_id      |number  |查询交易信息的交易id     |是     |

#### 参考示例

```
  var url = 'http://127.0.0.1:3000/txtraces/0b2da96a5b9527c03957acce623e2019d5b4ecf6bc1c178c203013246c623d4f';
  await Axios.post(url).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST http://127.0.0.1:3000/txtraces/0b2da96a5b9527c03957acce623e2019d5b4ecf6bc1c178c203013246c623d4f

```

#### 返回结果类型
`Object`

#### 返回结果
```json
{
    "_id": "5d109700436aea32405accdc",
    "id": "0b2da96a5b9527c03957acce623e2019d5b4ecf6bc1c178c203013246c623d4f",
    "receipt": {
        "status": "executed",
        "cpu_usage_us": 3979,
        "net_usage_words": 83
    },
    "elapsed": 4560,
    "net_usage": 664,
    "scheduled": false,
    "action_traces": [
        {
            "receipt": {
                "receiver": "ultrainio",
                "act_digest": "f3f1d99ccbd679543615a29f308d5264cad3bda798e9e6064dd13b127fa1c5a5",
                "global_sequence": 2604049,
                "recv_sequence": 1193084,
                "auth_sequence": [
                    [
                        "12.111",
                        232
                    ]
                ],
                "code_sequence": 7,
                "abi_sequence": 7
            },
            "act": {
                "account": "ultrainio",
                "name": "acceptheader",
                "authorization": [
                    {
                        "actor": "12.111",
                        "permission": "active"
                    }
                ],
                "data": {
                    "chain_name": "12",
                    "headers": [
                        {
                            "timestamp": "2019-06-24T09:24:35.000",
                            "proposer": "11.115",
                            "version": 0,
                            "previous": "000667daf669251acdb6dc7af8d6ee60cb43533991144e47f52bc8230c797593",
                            "transaction_mroot": "0000000000000000000000000000000000000000000000000000000000000000",
                            "action_mroot": "13097f54f45bd25eeda3502646ef7a7db171ee762f5b0615196234927f2fccd3",
                            "committee_mroot": "6d4dccaee5273e6a3851d1adb635e0ca24716044bb1599fa8be6644f25daa951",
                            "header_extensions": [],
                            "signature": "1709d600e79174ee16998d207e02f0c0be683f212d574973c7eb346da6f0796791c1102d98467100c5492dbe7f03a52d2f4ee5b196dc3c5a67d24cc315c6a70c"
                        },
                        {
                            "timestamp": "2019-06-24T09:24:45.000",
                            "proposer": "13.111",
                            "version": 0,
                            "previous": "000667db1a171441b13b8bfa08313738d092f45ce8a891cf5996a6ffed163c02",
                            "transaction_mroot": "09faad7e526c414ce83c89d7b2cec984c1d8edf9b327a43affb5fa2ae8fd42ec",
                            "action_mroot": "e89283d8fa3a4e938a00d56e3ea745d92d1c26c5d5f85f8378ac6d85878fafee",
                            "committee_mroot": "6d4dccaee5273e6a3851d1adb635e0ca24716044bb1599fa8be6644f25daa951",
                            "header_extensions": [],
                            "signature": "4d8ddd05cab4105d50704771ac9df53b4b364bca50f18502324b54d0395db470c7b436903cae2ae971fb44183d99abd415eff496598f7c2a328d7ab021f36506"
                        }
                    ]
                },
                "hex_data": "000000000000800802d31cc702000000009410400800000000000667daf669251acdb6dc7af8d6ee60cb43533991144e47f52bc8230c797593000000000000000000000000000000000000000000000000000000000000000013097f54f45bd25eeda3502646ef7a7db171ee762f5b0615196234927f2fccd36d4dccaee5273e6a3851d1adb635e0ca24716044bb1599fa8be6644f25daa9510080013137303964363030653739313734656531363939386432303765303266306330626536383366323132643537343937336337656233343664613666303739363739316331313032643938343637313030633534393264626537663033613532643266346565356231393664633363356136376432346363333135633661373063dd1cc702000000008410c00800000000000667db1a171441b13b8bfa08313738d092f45ce8a891cf5996a6ffed163c0209faad7e526c414ce83c89d7b2cec984c1d8edf9b327a43affb5fa2ae8fd42ece89283d8fa3a4e938a00d56e3ea745d92d1c26c5d5f85f8378ac6d85878fafee6d4dccaee5273e6a3851d1adb635e0ca24716044bb1599fa8be6644f25daa9510080013464386464643035636162343130356435303730343737316163396466353362346233363462636135306631383530323332346235346430333935646234373063376234333639303363616532616539373166623434313833643939616264343135656666343936353938663763326133323864376162303231663336353036"
            },
            "elapsed": 4281,
            "cpu_usage": 0,
            "console": "",
            "total_cpu_usage": 0,
            "trx_id": "0b2da96a5b9527c03957acce623e2019d5b4ecf6bc1c178c203013246c623d4f",
            "return_value": "",
            "inline_traces": []
        }
    ],
    "except": null,
    "ability": "Normal",
    "createdAt": "2019-06-24T09:25:20.312Z"
}
```
