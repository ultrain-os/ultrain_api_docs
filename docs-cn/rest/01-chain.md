## 简介 

实时REST接口的BaseUrl如下：

开发环境（单链）

> http://127.0.0.1:8888
  
测试网环境（多链）

**主链**
> http://ultrain.natapp1.cc 

**侧链11**
> http://pioneer.natapp1.cc 

**侧链12**
> http://power.natapp1.cc

主网环境（多链）

**主链**
> https://ultrainio.ultrain.info

**侧链poineer**
> https://pioneer.ultrain.info  

**侧链unitopia**
> https://unitopia.ultrain.info 

**侧链new-retail**
> https://newretail.ultrain.info 

## 方法列表

超脑线上 REST 接口所支持的方法如下表所示。

| 方法                                                                                           | 描述                                             |
| :---------------------------------------------------------------------------------------------| :-----------------------------------------------|
| [get_currency_balance](docs-cn/rest/01-chain#get_currency_balance)            |获取货币余额                                       |
| [get_currency_stats](docs-cn/rest/01-chain#get_currency_stats)                |获取代币的发行信息                                  |
| [get_trans_fee](docs-cn/rest/01-chain#get_trans_fee)                          |获取交易费用                                  |
| [get_scheduled_transactions](docs-cn/rest/01-chain#get_scheduled_transactions)|获取已调度的交易信息                                  |
| [get_chain_info](docs-cn/rest/01-chain#get_chain_info)                        |获取链的相关信息                                  |
| [get_block_info](docs-cn/rest/01-chain#get_block_info)                        |获取某个区块的相关信息                                  |
| [get_account_info](docs-cn/rest/01-chain#get_account_info)                    |获取账户的相关信息                                  |
| [get_contract](docs-cn/rest/01-chain#get_contract)                            |获取智能合约的代码                               |
| [get_abi](docs-cn/rest/01-chain#get_abi)                                      |获取ABI的相关信息                               |
| [get_raw_code_and_abi](docs-cn/rest/01-chain#get_raw_code_and_abi)            |获取代码和ABI的相关信息                               |
| [get_table_records](docs-cn/rest/01-chain#get_table_records)                  |从帐户获取智能合约数据                               |
| [push_tx](docs-cn/rest/01-chain#push_tx)                                      |广播签名后的交易信息                               |
| [get_table_by_scope](docs-cn/rest/01-chain#get_table_by_scope)                |从帐户获取智能合约数据                               |                         |
| [push_txs](docs-cn/rest/01-chain#push_txs)                                      |尝试将事务推送到挂起队列中                              |
| [register_event](docs-cn/rest/01-chain#register_event)                           |订阅Ultrain公链上的事件                              |
| [unregister_event](docs-cn/rest/01-chain#unregister_event)                       |取消订阅Ultrain公链上的事件                              |



## get_currency_balance
获取货币余额

#### 参数说明
|参数        |类型    |说明            |是否必填|
| :---------| :------| :-------------|:-----|
|code       |string  |部署合约的账户   |是     |
|account    |string  |要获取余额的账户  |是     |
|symbol     |string  |要查询的代币符号  |是     |

#### 参考示例
```
  var url = 'http://127.0.0.1:8888/v1/chain/get_currency_balance';
  var data = {
    'code': 'utrio.token',
    'account': 'ben',
    'symbol': 'UGAS',
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{"code":"utrio.token","account":"ben","symbol":"UGAS"}' http://127.0.0.1:8888/v1/chain/get_currency_balance

```

#### 返回结果类型
`Array`

#### 返回结果
```json
[
    "470.9500 UGAS"
]
```

## get_currency_stats
获取代币的发行信息

#### 参数说明
|参数        |类型    |说明            |是否必填|
| :---------| :------| :-------------|:-----|
|code       |string  |部署合约的账户   |是     |
|account    |string  |获取统计信息的账户|是     |

#### 参考示例

```
  var url = 'http://127.0.0.1:8888/v1/chain/get_currency_stats';
  var data = {
    "code": "utrio.token",
    "symbol":"UGAS"
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{"code":"utrio.token","symbol":"UGAS"}' http://127.0.0.1:8888/v1/chain/get_currency_stats

```

#### 返回结果类型
`Object`

#### 返回结果
```json
{
    "UGAS": {
        "supply": "900620417.9000 UGAS",
        "max_supply": "1000000000.0000 UGAS",
        "issuer": "ultrainio"
    }
}
```

## get_trans_fee
获取交易费用

#### 参考示例

```
  var url = 'http://127.0.0.1:8888/v1/chain/get_trans_fee';
  var data = {
     "block_height": "1",
  };
  await Axios.get(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl http://127.0.0.1:8888/v1/chain/get_trans_fee

```

#### 返回结果
```json
{
    "fee": "0.2000 UGAS"
}
```


## get_chain_info
获取链的相关信息

#### 参考示例

```
  var url = 'http://127.0.0.1:8888/v1/chain/get_chain_info';
  await Axios.get(url).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl http://127.0.0.1:8888/v1/chain/get_chain_info

```

#### 返回结果
```json
{
    "server_version": "0035a4ca+2.0.0",
    "chain_id": "1f1155433d9097e0f67de63a48369916da91f19cb1feff6ba8eca2e5d978a2b2",
    "head_block_num": 448699,
    "last_irreversible_block_num": 448698,
    "last_irreversible_block_id": "0006d8ba3599cdcfcb973050af15321ccfdddc071430813d930eac2049689be7",
    "head_block_id": "0006d8bb5866a9a1b9e4b476ceb37bbcf65e1558e55a75b3c274b1884dc14f40",
    "head_block_time": "2019-06-26T02:10:10.000",
    "head_block_proposer": "master.114",
    "virtual_block_cpu_limit": 3000000,
    "virtual_block_net_limit": 2097152,
    "block_cpu_limit": 2985634,
    "block_net_limit": 2096872,
    "block_interval_ms": 10000
}
```

## get_block_info
获取某个区块的相关信息

#### 参数说明
|参数            |类型    |说明                            |是否必填|
| :-------------| :------| :-----------------------------|:------|
|block_num_or_id|string  |区块的块高或者区块的ID            |是     |

#### 参考示例

```
  var url = 'http://127.0.0.1:8888/v1/chain/get_block_info';
  var data = {
    "block_num_or_id": 100,
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{"block_num_or_id": 100}' http://127.0.0.1:8888/v1/chain/get_block_info

```

#### 返回结果
```json
{
    "timestamp": "2019-05-05T04:02:30.000",
    "proposer": "master.113",
    "version": 0,
    "previous": "00000063c96c62b5e20ec7c408c56d9fabba420a6cfb6cedbb766457d8792895",
    "transaction_mroot": "0000000000000000000000000000000000000000000000000000000000000000",
    "action_mroot": "5ce8b349d0aa67361523f82ea2b704b5323073eb73e7dc8c558a736d90c755c1",
    "committee_mroot": "fa4976d810c625b34a7662019705e3cd8fd5a2e87837d1183d8d42f59cc32564",
    "header_extensions": [],
    "signature": "cf26a7d382f94d977ffce09c8b0efb1364043dee822c18e6a88cd03f5cd391d8fb1568010b9d33c98170e6c7b46ebdcf1ba4d52116766517144be91120fa6507",
    "transactions": [],
    "block_extensions": [],
    "id": "00000064a0a1a0336aff35739faba8043ed7be4aa982a2c061768614e85a2173",
    "block_num": 100,
    "ref_block_prefix": 1932918634,
    "timevalue": 42264150
}
```

## get_account_info
获取账户的相关信息

#### 参数说明
|参数            |类型    |说明                            |是否必填|
| :-------------| :------| :-----------------------------|:-----|
|account_name   |string  |查询账户的账户名                  |是    |

#### 参考示例

```
  var url = 'http://127.0.0.1:8888/v1/chain/get_account_info';
  var data = {
    "account_name": "ben",
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{"account_name": "ben"}' http://127.0.0.1:8888/v1/chain/get_account_info

```

#### 返回结果
```json
{
    "account_name": "ultrainio",
    "head_block_num": 448906,
    "head_block_time": "2019-06-26T02:44:40.000",
    "privileged": true,
    "updateable": true,
    "last_code_update": "2019-06-12T09:50:30.000",
    "created": "2019-05-05T03:46:00.000",
    "core_liquid_balance": "898121135.9000 UGAS",
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
    "ram_usage": 17025765,
    "permissions": [
        {
            "perm_name": "active",
            "parent": "owner",
            "required_auth": {
                "threshold": 1,
                "keys": [
                    {
                        "key": "UTR7qXCoEiK2Mm9E2kP3i412fvyEwp6WmQYogowjCcM5Er4Nw4ziY",
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
                        "key": "UTR7qXCoEiK2Mm9E2kP3i412fvyEwp6WmQYogowjCcM5Er4Nw4ziY",
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

## get_contract
获取智能合约的代码

#### 参数说明
|参数            |类型    |说明                            |是否必填|
| :-------------| :------| :-----------------------------|:------|
|account_name   |string  |查询智能合约的账户名              |是     |

#### 参考示例


```
  var url = 'http://127.0.0.1:8888/v1/chain/get_contract';
  var data = {
    "account_name": "ben",
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{"account_name": "ben"}' http://127.0.0.1:8888/v1/chain/get_contract

```

#### 返回结果
```
{
    "account_name": "ultrainio",
    "code_hash": "3dc9db161d1b37d768d0122950105daa3035cc74111872f36863f4d3c90a2d0d",
    "wast":"..."，
	"wasm": "...",
    "abi": {
        "version": "ultrainio::abi/1.0/1501af",
        "types": [
            {
                "new_type_name": "account_name",
                "type": "name"
            },
            {
                "new_type_name": "permission_name",
                "type": "name"
            },
            {
                "new_type_name": "action_name",
                "type": "name_ex"
            },
            {
                "new_type_name": "transaction_id_type",
                "type": "checksum256"
            },
            {
                "new_type_name": "weight_type",
                "type": "uint16"
            },
            {
                "new_type_name": "block_id_type",
                "type": "checksum256"
            }
        ],
        "structs":[
			{
                "name": "ultrainio_system_params",
                "base": "",
                "fields": [
                    {
                        "name": "chain_type",
                        "type": "uint64"
                    },
                    {
                        "name": "max_ram_size",
                        "type": "uint64"
                    },
                    {
                        "name": "min_activated_stake",
                        "type": "int64"
                    },
                    {
                        "name": "min_committee_member_number",
                        "type": "uint32"
                    },
                    {
                        "name": "block_reward_vec",
                        "type": "block_reward[]"
                    },
                    {
                        "name": "max_resources_number",
                        "type": "uint64"
                    },
                    {
                        "name": "newaccount_fee",
                        "type": "uint32"
                    },
                    {
                        "name": "chain_name",
                        "type": "name"
                    },
                    {
                        "name": "worldstate_interval",
                        "type": "uint64"
                    },
                    {
                        "name": "resource_fee",
                        "type": "uint32"
                    },
                    {
                        "name": "table_extension",
                        "type": "exten_type[]"
                    }
                
            },
			...
				]
			"ricardian_clauses": [],
            "error_messages": [],
            "abi_extensions": []
		]
	}
}	
```

## get_abi
获取ABI的相关信息

#### 参数说明
|参数            |类型    |说明                            |是否必填|
| :-------------| :------| :-----------------------------|:------|
|account_name   |string  |查询ABI的账户名                  |是     |

#### 参考示例

```
  var url = 'http://127.0.0.1:8888/v1/chain/get_abi';
  var data = {
    "account_name": "ben",
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{"account_name": "ben"}' http://127.0.0.1:8888/v1/chain/get_abi

```

#### 返回结果
```json
{
    "account_name": "utrio.bank",
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
    }
}
```

## get_raw_code_and_abi
获取代码和ABI的相关信息

#### 参数说明
|参数            |类型    |说明                            |是否必填|
| :-------------| :------| :-----------------------------|:------|
|account_name   |string  |查询代码和ABI的账户名             |是     |

#### 参考示例

```
  var url = 'http://127.0.0.1:8888/v1/chain/get_raw_code_and_abi';
  var data = {
    "account_name": "ben",
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{"account_name": "ben"}' http://127.0.0.1:8888/v1/chain/get_raw_code_and_abi

```

#### 返回结果
```json
{
    "account_name": "ben",
    "wasm": "...",
    "abi": "..."
}
```

## get_table_records
从帐户获取智能合约数据

#### 参数说明
|参数            |类型    |说明                            |是否必填|
| :-------------| :------| :-----------------------------|:-----|
|json           |bool    |结果是否以json格式输出            |否     |
|code           |string  |智能合约的名称                   |是     |
|scope          |string  |账户名                          |是     |
|table          |string  |表名                            |是     |
|table_key      |string  |表的键名                        |否     |
|lower_bound    |string  |下限                            |否     |
|upper_bound    |string  |上限                            |否     |
|limit          |uint32  |限制条件                        |否     |
|key_type       |string  |键的类型（primary仅支持（i64），其他支持（i64，i128，i256，float64，float128），特殊类型“string”表示帐户名）|否     |
|index_position |string  |索引                           |否     |

#### 参考示例

```
  var url = 'http://127.0.0.1:8888/v1/chain/get_table_records';
  var data = {
    "code": "utrio.token",
    "scope": "ultrainio",
    "table": "accounts",
    "json": true
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{ "code": "utrio.token","scope": "ultrainio","table": "accounts","json": true}' http://127.0.0.1:8888/v1/chain/get_table_records

```

#### 返回结果
```json
{
    "rows": [
        {
            "balance": "898121135.9000 UGAS",
            "last_block_height": 397158
        }
    ],
    "more": false
}
```

## get_table_by_scope
根据账户获取智能合约数据

#### 参数说明
|参数            |类型    |说明                            |是否必填|
| :-------------| :------| :-----------------------------|:-----|
|code           |string  |智能合约的名称                   |是     |
|table          |string  |表名                            |是     |
|lower_bound    |string  |下限                            |否     |
|upper_bound    |string  |上限                            |否     |
|limit          |uint32  |限制条件（默认为10）              |否     |

#### 参考示例


```
  var url = 'http://127.0.0.1:8888/v1/chain/get_table_by_scope';
  var data = {
    "code": "utrio.token",
    "table": "accounts"
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{ "code": "utrio.token","table": "accounts"}' http://127.0.0.1:8888/v1/chain/get_table_by_scope

```

#### 返回结果
```json
{
    "rows": [
        {
            "code": "utrio.token",
            "scope": "594493310320508928",
            "table": "accounts",
            "payer": "utrio.token",
            "count": 1
        },
        {
            "code": "utrio.token",
            "scope": "594493327500378112",
            "table": "accounts",
            "payer": "utrio.token",
            "count": 1
        },
        {
            "code": "utrio.token",
            "scope": "594493344680247296",
            "table": "accounts",
            "payer": "utrio.token",
            "count": 1
        },
        {
            "code": "utrio.token",
            "scope": "594493361860116480",
            "table": "accounts",
            "payer": "utrio.token",
            "count": 1
        },
        {
            "code": "utrio.token",
            "scope": "594493379039985664",
            "table": "accounts",
            "payer": "utrio.token",
            "count": 1
        },
        {
            "code": "utrio.token",
            "scope": "612507708829990912",
            "table": "accounts",
            "payer": "utrio.token",
            "count": 1
        },
        {
            "code": "utrio.token",
            "scope": "612507726009860096",
            "table": "accounts",
            "payer": "utrio.token",
            "count": 1
        },
        {
            "code": "utrio.token",
            "scope": "612507743189729280",
            "table": "accounts",
            "payer": "utrio.token",
            "count": 1
        },
        {
            "code": "utrio.token",
            "scope": "612507760369598464",
            "table": "accounts",
            "payer": "utrio.token",
            "count": 1
        },
        {
            "code": "utrio.token",
            "scope": "612507777549467648",
            "table": "accounts",
            "payer": "utrio.token",
            "count": 1
        }
    ],
    "more": "3812286752692404736"
}
```


## push_tx

广播签名后的交易信息

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|signed_transaction|string  |签名后的交易信息                  |是     |

#### 参考示例

```
  var url = 'http://127.0.0.1:8888/v1/chain/push_tx';
  var data = {
    "signed_transaction": { compression: 'none',
                            transaction: 
                             { expiration: '2019-07-14T01:59:38',
                               ref_block_num: 4492,
                               ref_block_prefix: 3817828507,
                               net_usage_words: 0,
                               max_cpu_usage_ms: 0,
                               delay_sec: 0,
                               context_free_actions: [],
                               actions: [ [Object] ],
                               transaction_extensions: [] },
                            signatures: 
                             [ 'SIG_K1_JxnJ83HHCfC1JbYq6gUnCFrgjTqLsUN85njNfjhoQ3c8gBBep79Z99ZdPZjbZtfBtHaV8HTKyHk8wtsD9RHbpGJ5Mz3SvW' ] },
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{ compression: 'none',
                    transaction: 
                     { expiration: '2019-07-14T01:59:38',
                       ref_block_num: 4492,
                       ref_block_prefix: 3817828507,
                       net_usage_words: 0,
                       max_cpu_usage_ms: 0,
                       delay_sec: 0,
                       context_free_actions: [],
                       actions: [ [Object] ],
                       transaction_extensions: [] },
                    signatures: 
                     [ 'SIG_K1_JxnJ83HHCfC1JbYq6gUnCFrgjTqLsUN85njNfjhoQ3c8gBBep79Z99ZdPZjbZtfBtHaV8HTKyHk8wtsD9RHbpGJ5Mz3SvW' ] }' http://127.0.0.1:8888/v1/chain/push_tx

```

## push_txs
尝试将事务推送到挂起队列中

#### 参数说明
|参数                 |类型    |说明                            |是否必填|
| :------------------| :------| :-----------------------------|:-----|
|signed_transaction[]|Array  |签名后的交易信息                  |是     |

#### 参考示例

```
  var url = 'http://127.0.0.1:8888/v1/chain/push_tx';
  var data = {
    "signed_transaction": [{ compression: 'none',
                            transaction: 
                             { expiration: '2019-07-14T01:59:38',
                               ref_block_num: 4492,
                               ref_block_prefix: 3817828507,
                               net_usage_words: 0,
                               max_cpu_usage_ms: 0,
                               delay_sec: 0,
                               context_free_actions: [],
                               actions: [ [Object] ],
                               transaction_extensions: [] },
                            signatures: 
                             [ 'SIG_K1_JxnJ83HHCfC1JbYq6gUnCFrgjTqLsUN85njNfjhoQ3c8gBBep79Z99ZdPZjbZtfBtHaV8HTKyHk8wtsD9RHbpGJ5Mz3SvW' ] }],
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '[{ compression: 'none',
                    transaction: 
                     { expiration: '2019-07-14T01:59:38',
                       ref_block_num: 4492,
                       ref_block_prefix: 3817828507,
                       net_usage_words: 0,
                       max_cpu_usage_ms: 0,
                       delay_sec: 0,
                       context_free_actions: [],
                       actions: [ [Object] ],
                       transaction_extensions: [] },
                    signatures: 
                     [ 'SIG_K1_JxnJ83HHCfC1JbYq6gUnCFrgjTqLsUN85njNfjhoQ3c8gBBep79Z99ZdPZjbZtfBtHaV8HTKyHk8wtsD9RHbpGJ5Mz3SvW' ] }]' http://127.0.0.1:8888/v1/chain/push_tx

```

## register_event
订阅Ultrain公链上的事件

#### 参数说明
|参数                 |类型    |说明                            |是否必填|
| :------------------| :------| :-----------------------------|:-----|
|account             |string  |提供行为名称                     |是     |
|post_url            |string  |路由                           |是     |

#### 参考示例


```
  var url = 'http://127.0.0.1:8888/v1/chain/register_event';
  var data = {
    "account": "ben",
    "post_url": 'http://[your url]'
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{ "account": "ben", "post_url": "http://[your url]"}' http://127.0.0.1:8888/v1/chain/register_event

```

#### 返回结果
```json
{
    "result": "Success"
}
```

## unregister_event

取消订阅Ultrain公链上的事件

#### 参数说明
|参数                 |类型    |说明                            |是否必填|
| :------------------| :------| :-----------------------------|:-----|
|account             |string  |提供行为名称                     |是     |
|post_url            |string  |路由                           |是     |

#### 参考示例

```
  var url = 'http://127.0.0.1:8888/v1/chain/unregister_event';
  var data = {
    "account": "ben",
    "post_url": 'http://[your url]'
  };
  await Axios.post(url, data).then(response => response.data)
    .then(response => {
      console.log('Success:', response);
    }).catch(error => {
      console.error('Error:', error);
  });
```

或者

```
 curl -X POST -d '{ "account": "ben", "post_url": "http://[your url]"}' http://127.0.0.1:8888/v1/chain/unregister_event

```

#### 返回结果类型
`Object`

#### 返回结果
```json
{
    "result": "Success"
}
```
