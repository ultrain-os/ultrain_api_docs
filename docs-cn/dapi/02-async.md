## 简介
默认情况下，```RPC``` 接口域名为[http://ultrain-history.natapp1.cc](http://ultrain-history.natapp1.cc)。

## 方法列表

超脑历史 RPC 接口所支持的方法如下表所示。

| 方法                                                                                        | 描述                                             |
| :------------------------------------------------------------------------------------------| :------------------------------------------------|
| [getAccountByName](docs-cn/rpc/01-history-rpc-api#getAccountByName)                |根据账户名称获取账户信息                              |
| [getActionsByAccount](docs-cn/rpc/01-history-rpc-api#getActionsByAccount)          |根据账户名称查找其所有的交易行为                       |
| [getActionsByTxid](docs-cn/rpc/01-history-rpc-api#getActionsByTxid)                |根据交易id查找相应的交易行为                          |
| [getAllAccounts](docs-cn/rpc/01-history-rpc-api#getAllAccounts)                    |获取全部的账户信息                                   |
| [getAllBlocks](docs-cn/rpc/01-history-rpc-api#getAllBlocks)                        |获取全部的区块信息                                   |
| [getAllTokens](docs-cn/rpc/01-history-rpc-api#getAllTokens)                        |获取所以的代币信息                                   |
| [getAllTxs](docs-cn/rpc/01-history-rpc-api#getAllTxs)                              |获取全部的交易信息                                   |
| [getBaseInfo](docs-cn/rpc/01-history-rpc-api#getBaseInfo)                          |获取基本信息                                        |
| [getContractByName](docs-cn/rpc/01-history-rpc-api#getContractByName)              |根据合约名称查找完整合约信息                           |
| [getContracts](docs-cn/rpc/01-history-rpc-api#getContracts)                        |获取全部的合约信息                                   |
| [getCreateAccountByName](docs-cn/rpc/01-history-rpc-api#getCreateAccountByName)    |根据合约名称查找账户创建者                            |
| [getHoldersBySymbol](docs-cn/rpc/01-history-rpc-api#getHoldersBySymbol)            |根据代币名称和创建者获取其代币持有者                    |
| [getTokenBalanceByAccount](docs-cn/rpc/01-history-rpc-api#getTokenBalanceByAccount)|根据账户名获取代币余额                                |
| [getTokenBySymbol](docs-cn/rpc/01-history-rpc-api#getTokenBySymbol)                |根据代币名称和创建者获取其代币的基本信息                 |
| [getTxByTxId](docs-cn/rpc/01-history-rpc-api#getTxByTxId)                          |根据交易id查找相应的交易信息                           |
| [getTxsByBlockNum](docs-cn/rpc/01-history-rpc-api#getTxsByBlockNum)                |根据区块块高查询交易信息                               |
| [getTxTraceByTxid](docs-cn/rpc/01-history-rpc-api#getTxTraceByTxid)                |根据交易id查找交易信息                                |
| [search](docs-cn/rpc/01-history-rpc-api#search)                                    |根据账户名、块高、交易hash和合约名查询交易、区块、合约和账户|


## getAccountByName

根据账户名称查找完整的账户信息

#### 参数说明
|参数        |类型    |说明              |是否必填|
| :---------| :------| :---------------|:-----|
|name       |string  |获取其信息的账户名称|是     |

#### 参考示例
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/accounts/[name]",
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData)
}
例：name：utrio.fee
```

#### 返回结果类型
`Object`

#### 返回结果
```json
{
    "_id": "5ce75b6c94b14cda69042028",
    "name": "utrio.fee",
    "createdAt": "2019-05-24T02:48:12.335Z",
    "id": "5ce75b6c94b14cda69042028"
}
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
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/actions/by/account",
  "params": ['page': 1,
             'pageSize': 10,
             'sortParams': { _id: -1 },
			 "queryParams":{ "account_name": "coboultrain2" }
  ],
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData),
}
```

#### 返回结果类型
`Object`

#### 返回结果
```json
{
    "pageNumber": 1,
    "total": 29,
    "pageCount": 3,
    "results": [
		{
            "_id": "5d0ca078436aea32405722ac",
            "action_num": 0,
            "trx_id": "ba8537f30de0c48de406903f0a196cea1c3423d8c82349a10253ba1e54242526",
            "cfa": false,
            "account": "utrio.token",
            "name": "transfer",
            "authorization": [
                {
                    "actor": "coboultrain1",
                    "permission": "active"
                }
            ],
            "data": {
                "from": "coboultrain1",
                "to": "coboultrain2",
                "quantity": "1.0000 UGAS",
                "memo": ""
            },
            "id": "5d0ca078436aea32405722ac",
            "updatedAt": "2019-06-21T09:17:00.252Z",
            "createdAt": "2019-06-21T09:16:40.169Z"
        },
		结果过多，只显示部分结果
	]
}
```

## getActionsByTxid
根据交易id查找交易行为

#### 参数说明
|参数        |类型    |说明                   |是否必填|
| :---------| :------| :--------------------|:-----|
|trx_id     |string  |获取其交易行为信息的交易id|是    |

#### 参考示例
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/actions/tx/[trx_id]",
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData)
}
例：trx_id：e0f1dadf878b7542b573daa185fe2267dd9a8784ae3439e042687b673845558b
```

#### 返回结果类型
`Array`

#### 返回结果
```json
[
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
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/accounts"，
  "params":['page': 1,
            'pageSize': 10,
            'queryParams': {},
            'sortParams': { _id: -1 }
  ],
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData)
}
```

#### 返回结果类型
`Object`

#### 返回结果
```json
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
		由于结果过多，只显示部分结果
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
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/blocks"，
  "params":['page': 1,
            'pageSize': 10,
            'queryParams': {"block.producer":"ultrainio"},
            'sortParams': { _id: -1 }
  ],
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData)
}
```

#### 返回参数类型
`Object`

#### 返回结果
```json
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
		由于内容过多，只显示部分结果
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
```json
  "method": "post",
  "url":"http://pioneer-history.natapp1.cc/tokens",
  "params": [
    'page': 1,
    'pageSize': 10,
    'queryParams': {},
    'sortParams': { _id: -1 }
  ],
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData),
}
```

#### 返回结果类型
`Object`

#### 返回结果
```json
{
    "pageNumber": 1,
    "total": 7,
    "pageCount": 1,
    "results": [
        {
            "disabled": true,
            "_id": "5cfdffefef6c7944b4711029",
            "account": "test22222221",
            "symbol": "LYMS",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.201Z",
            "decimals": 4,
            "issue_time": "2019-05-22T12:14:35.498Z",
            "issuer": "test22222221",
            "max_supply": "10000000.0000",
            "supply": "10000000.0000",
            "updatedAt": "2019-06-25T02:01:01.013Z",
            "id": "5cfdffefef6c7944b4711029",
            "holders": 1
        },
        {
            "disabled": false,
            "_id": "5cf648dd940842a7af98fade",
            "account": "antennacoins",
            "symbol": "ANT",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.218Z",
            "decimals": 2,
            "issue_time": "2019-05-08T07:27:40.599Z",
            "issuer": "antennacoins",
            "max_supply": "1000000000.00",
            "supply": "1000000000.00",
            "updatedAt": "2019-06-25T02:01:01.137Z",
            "id": "5cf648dd940842a7af98fade",
            "holders": 11
        },
        {
            "disabled": false,
            "_id": "5cf648dd940842a7af98fad2",
            "account": "test22222224",
            "symbol": "LYMS",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.201Z",
            "decimals": 4,
            "issue_time": "2019-05-22T12:14:35.498Z",
            "issuer": "test22222224",
            "max_supply": "10000000.0000",
            "supply": "10000000.0000",
            "updatedAt": "2019-06-25T02:01:01.125Z",
            "id": "5cf648dd940842a7af98fad2",
            "holders": 1
        },
        {
            "disabled": false,
            "_id": "5cf648dd940842a7af98faca",
            "account": "test22222224",
            "symbol": "DRTQ",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.192Z",
            "decimals": 4,
            "issue_time": "2019-05-22T12:14:35.512Z",
            "issuer": "test22222224",
            "max_supply": "10000000.0000",
            "supply": "10000000.0000",
            "updatedAt": "2019-06-25T02:01:01.119Z",
            "id": "5cf648dd940842a7af98faca",
            "holders": 5
        },
        {
            "disabled": false,
            "_id": "5cf648dd940842a7af98fac4",
            "account": "cona1",
            "symbol": "XOFZ",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.185Z",
            "decimals": 0,
            "issue_time": "2019-06-02T08:38:05.682Z",
            "issuer": "cona1",
            "max_supply": "8000000000",
            "supply": "8000000000",
            "updatedAt": "2019-06-25T02:01:01.114Z",
            "id": "5cf648dd940842a7af98fac4",
            "holders": 2
        },
        {
            "disabled": true,
            "_id": "5cf648dd940842a7af98faba",
            "account": "xxxxxxxxxxx1",
            "symbol": "XXX",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.172Z",
            "decimals": 4,
            "issue_time": "2019-05-25T11:49:25.586Z",
            "issuer": "xxxxxxxxxxx1",
            "max_supply": "10000000.0000",
            "supply": "10000000.0000",
            "updatedAt": "2019-06-25T02:01:01.005Z",
            "id": "5cf648dd940842a7af98faba",
            "holders": 4
        },
        {
            "disabled": false,
            "_id": "5cf648dd940842a7af98fab7",
            "account": "cona1",
            "symbol": "XVFJ",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.167Z",
            "decimals": 3,
            "issue_time": "2019-06-02T08:36:25.537Z",
            "issuer": "cona1",
            "max_supply": "8000000000.000",
            "supply": "8000000000.000",
            "updatedAt": "2019-06-25T02:01:01.061Z",
            "id": "5cf648dd940842a7af98fab7",
            "holders": 2
        }
    ]
}
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
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/contracts/txs",
  "params":['page': 1,
            'pageSize': 10,
            'queryParams':query,
            'sortParams':{ _id: -1 }
  ],
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData),
}
```

#### 返回结果类型
`Object`

#### 返回结果
```json
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
		由于信息过多，只显示部分结果
	]
}
```

## getBaseInfo
获取主网基本信息

#### 参考案例
```json
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/base",
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData),
}
```

#### 返回结果类型
`Object`

#### 返回结果
```json
{
    "head_block_num": 439936,
    "tx_num": 1156437,
    "tps": 0.4,
    "token_num": 0,
    "account_num": 332,
    "contract_num": 5
}
```

## getContractByName
根据合约名称查找完整的合约信息

#### 参数说明
|参数        |类型    |说明               |是否必填|
| :---------| :------| :----------------|:-----|
|name       |string  |获取合约信息的合约名称|是    |


#### 参考示例
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/contracts/[name]",
  "headers": {
          'content-type': 'application/json'
        },
  "body": JSON.stringify(requestData)
}
例：name：utrio.bank
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
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/contracts",
  "headers": {
          'content-type': 'application/json'
        },
  "params":['page': 1,
            'pageSize': 10,
            'queryParams': {},
            'sortParams': { _id: -1 }
  ]
}
```

#### 返回结果类型
`Object`

#### 响应结果
```json
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
	由于合约信息过多只显示部分结果.
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
```json
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/getcreateaccount",
  "body": JSON.stringify({ name: 'ot112' })
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData),
}
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
```json
  "method": "post",
  "url":"http://pioneer-history.natapp1.cc/holders/by/symbol",
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData)
}
```

#### 返回结果类型
`Object`

#### 返回结果
```json
{
    "pageNumber": 1,
    "total": 26,
    "pageCount": 3,
    "results": [
        {
            "current_balance": 7999999090,
            "disabled": false,
            "_id": "5cf648dd940842a7af98fa85",
            "holder_account": "cona1",
            "token_account": "cona1",
            "token_symbol": "XVFJ",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.103Z",
            "token_details": "5cf648dd940842a7af98fab7",
            "updatedAt": "2019-06-25T02:19:01.031Z",
            "id": "5cf648dd940842a7af98fa85"
        },
        {
            "current_balance": 7999992156,
            "disabled": false,
            "_id": "5cf648dd940842a7af98fa8b",
            "holder_account": "cona1",
            "token_account": "cona1",
            "token_symbol": "XOFZ",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.113Z",
            "token_details": "5cf648dd940842a7af98fac4",
            "updatedAt": "2019-06-25T02:19:01.037Z",
            "id": "5cf648dd940842a7af98fa8b"
        },
        {
            "current_balance": 999948831.6,
            "disabled": false,
            "_id": "5cf648dd940842a7af98fa92",
            "holder_account": "antennacoins",
            "token_account": "antennacoins",
            "token_symbol": "ANT",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.120Z",
            "token_details": "5cf648dd940842a7af98fade",
            "updatedAt": "2019-06-25T02:19:01.040Z",
            "id": "5cf648dd940842a7af98fa92"
        },
        {
            "current_balance": 10000000,
            "disabled": false,
            "_id": "5cf648dd940842a7af98fa9a",
            "holder_account": "test22222224",
            "token_account": "test22222224",
            "token_symbol": "LYMS",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.129Z",
            "token_details": "5cf648dd940842a7af98fad2",
            "updatedAt": "2019-06-25T02:19:01.042Z",
            "id": "5cf648dd940842a7af98fa9a"
        },
        {
            "current_balance": 9999960,
            "disabled": true,
            "_id": "5cf648dd940842a7af98fa8f",
            "holder_account": "xxxxxxxxxxx1",
            "token_account": "xxxxxxxxxxx1",
            "token_symbol": "XXX",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.116Z",
            "token_details": "5cf648dd940842a7af98faba",
            "updatedAt": "2019-06-25T02:19:01.006Z",
            "id": "5cf648dd940842a7af98fa8f"
        },
        {
            "current_balance": 9936778,
            "disabled": false,
            "_id": "5cf648dd940842a7af98fa93",
            "holder_account": "test22222224",
            "token_account": "test22222224",
            "token_symbol": "DRTQ",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.120Z",
            "token_details": "5cf648dd940842a7af98faca",
            "updatedAt": "2019-06-25T02:19:01.039Z",
            "id": "5cf648dd940842a7af98fa93"
        },
        {
            "current_balance": 58222,
            "disabled": false,
            "_id": "5cf648dd940842a7af98fa84",
            "holder_account": "test22222221",
            "token_account": "test22222224",
            "token_symbol": "DRTQ",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.095Z",
            "token_details": "5cf648dd940842a7af98faca",
            "updatedAt": "2019-06-25T02:19:01.030Z",
            "id": "5cf648dd940842a7af98fa84"
        },
        {
            "current_balance": 10000,
            "disabled": false,
            "_id": "5cf648dd940842a7af98faab",
            "holder_account": "versly331513",
            "token_account": "antennacoins",
            "token_symbol": "ANT",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.146Z",
            "token_details": "5cf648dd940842a7af98fade",
            "updatedAt": "2019-06-25T02:19:01.053Z",
            "id": "5cf648dd940842a7af98faab"
        },
        {
            "current_balance": 10000,
            "disabled": false,
            "_id": "5cf648dd940842a7af98fab4",
            "holder_account": "versly331523",
            "token_account": "antennacoins",
            "token_symbol": "ANT",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.161Z",
            "token_details": "5cf648dd940842a7af98fade",
            "updatedAt": "2019-06-25T02:19:01.060Z",
            "id": "5cf648dd940842a7af98fab4"
        },
        {
            "current_balance": 9800,
            "disabled": false,
            "_id": "5cf648dd940842a7af98fabf",
            "holder_account": "wutianqing15",
            "token_account": "antennacoins",
            "token_symbol": "ANT",
            "__v": 0,
            "createdAt": "2019-06-04T10:33:01.177Z",
            "token_details": "5cf648dd940842a7af98fade",
            "updatedAt": "2019-06-25T02:19:01.066Z",
            "id": "5cf648dd940842a7af98fabf"
        }
    ]
}
```

## getTokenBalanceByAccount
根据账户名获取其代币余额

#### 参数说明
|参数         |类型     |说明                      |是否必填|
| :----------| :------| :------------------------|:-----|
|account_name|string  |获取其代币余额的账户名        |是    |

#### 参考示例
```json
  "method": "post",
  "url":"http://pioneer-history.natapp1.cc/balance/[account_name]",
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData),
}
例：account_name:antennacoins
```

#### 返回结果类型
`Array`

#### 返回结果
```json
[
    {
        "current_balance": 999948831.6,
        "disabled": false,
        "_id": "5cf648dd940842a7af98fa92",
        "holder_account": "antennacoins",
        "token_account": "antennacoins",
        "token_symbol": "ANT",
        "__v": 0,
        "createdAt": "2019-06-04T10:33:01.120Z",
        "token_details": {
            "account": "antennacoins",
            "symbol": "ANT",
            "decimals": 2,
            "issue_time": "2019-05-08T07:27:40.599Z",
            "issuer": "antennacoins",
            "max_supply": "1000000000.00",
            "supply": "1000000000.00",
            "id": null
        },
        "updatedAt": "2019-06-25T02:05:01.041Z",
        "id": "5cf648dd940842a7af98fa92"
    }
]
```

## getTokenBySymbol
根据代币名称和创建者获取其代币信息

#### 参数说明
|参数        |类型    |说明                   |是否必填|
| :---------| :------| :--------------------|:-----|
|symbol     |string  |代币符号               |是    |
|creator    |string  |代币的创建者            |是    |

#### 参考示例
```json
  "method": "post",
  "url":"http://pioneer-history.natapp1.cc/token/[symbol]/[creator]",
  body: JSON.stringify(requestData),
}
例：
symbol：ANT
creator：antennacoins
```

#### 返回结果类型
`Object`

#### 返回结果
```json
{
    "disabled": false,
    "_id": "5cf648dd940842a7af98fade",
    "account": "antennacoins",
    "symbol": "ANT",
    "__v": 0,
    "createdAt": "2019-06-04T10:33:01.218Z",
    "decimals": 2,
    "issue_time": "2019-05-08T07:27:40.599Z",
    "issuer": "antennacoins",
    "max_supply": "1000000000.00",
    "supply": "1000000000.00",
    "updatedAt": "2019-06-25T02:23:01.096Z",
    "id": "5cf648dd940842a7af98fade"
}
```


## getTxByTxId
根据交易id查找交易信息

#### 参数说明
|参数        |类型    |说明            |是否必填|
| :---------| :------| :-------------|:------|
|trx_id     |string  |获取其信息的交易id|是     |

#### 参考示例
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/txs/[trx_id]",
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData)
}
例:trx_id:e0f1dadf878b7542b573daa185fe2267dd9a8784ae3439e042687b673845558b
```

#### 返回类型结果
`Object`

#### 返回结果
```json
{
    "_id": "5d1035da436aea32405a726e",
    "trx_id": "e0f1dadf878b7542b573daa185fe2267dd9a8784ae3439e042687b673845558b",
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
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/txs/by/blocknum",
  "params": [
    'page': 1,
    'pageSize': 10,
    'sortParams': { _id: -1 }
  ],
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(
						'queryParams': {
										'block_num': 433746
						}
  ),
}
```

#### 返回结果类型
`Array`

#### 返回结果
```json
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
            "block_num": 433746,
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
            "block_num": 433746,
            "updatedAt": "2019-06-24T08:38:30.437Z",
            "id": "5d108bf2436aea32405ac298"
        },
        {
            "_id": "5d108bf2436aea32405ac294",
            "trx_id": "1b68fd1e7dd987dd179f74fdcd139c523d430e3e0f5a019d320ca0648148cda3",
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
                "0": "UTR7bggm3iyTDmZMHfsnZ96N8wQnGmam6x97uuTYtxgSLWR3zyCix"
            },
            "signatures": {
                "0": "SIG_K1_JvF8cRZKkywSmof8mtfJxTLGxp1Gk3mKv6nP13ZimTAkaySZWcT5Ncb8bbhudweaPrSfXGa6JKAMX1qE5ysqVGAmiGxWae"
            },
            "createdAt": "2019-06-24T08:38:10.379Z",
            "block_id": "00069e524ab06ffcec2d93e19f4a457f2d432c26ded9adee54cd64fe7eb83c72",
            "block_num": 433746,
            "updatedAt": "2019-06-24T08:38:30.437Z",
            "id": "5d108bf2436aea32405ac294"
        },
        {
            "_id": "5d108bf2436aea32405ac28e",
            "trx_id": "43cd04f0afae8ce60ea42c699a812e5654d9c2c8b371127e3e84c512ae2b81ba",
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
                "0": "SIG_K1_K4EZhWyKpzbpfSsSqWyjXKRojLURajv6AQKpPt7TzLk4hZ747y7tTHzRnFs6N3DbAGeLBk9dsU5yrBW91HC6WFRhkxgYmv"
            },
            "createdAt": "2019-06-24T08:38:10.371Z",
            "block_id": "00069e524ab06ffcec2d93e19f4a457f2d432c26ded9adee54cd64fe7eb83c72",
            "block_num": 433746,
            "updatedAt": "2019-06-24T08:38:30.437Z",
            "id": "5d108bf2436aea32405ac28e"
        }
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
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/txtraces/[tx_id]",
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData),
}
例:tx_id:0b2da96a5b9527c03957acce623e2019d5b4ecf6bc1c178c203013246c623d4f
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

## search
根据账户名、块高、交易hash和合约名查询交易、区块、合约和账户 

#### 参数说明
|参数        |类型    |说明                      |是否必填|
| :---------| :------| :-----------------------|:------|
|param      |String  |账户名、块高、交易hash和合约名|是     |

#### 参考示例
```json
{
  "method": "post",
  "url":"http://ultrain-history.natapp1.cc/search/[param]",
  headers: {
          'content-type': 'application/json'
        },
  body: JSON.stringify(requestData),
}
例：param：0b2da96a5b9527c03957acce623e2019d5b4ecf6bc1c178c203013246c623d4f
```

#### 返回结果类型
`Object`

#### 返回结果
```json
{
    "data": {
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
    },
    "type": "trx"
}
```
