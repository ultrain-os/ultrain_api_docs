## 类
超脑TS_lib的DBMANAGER的类如下所示

| 类                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [Cursor](docs-cn/ts-lib/08-ts-dbmanager#Cursor)                          |光标类，代表dbmanger行                             |
| [DBManager](docs-cn/ts-lib/08-ts-dbmanager#DBManager)                          |dbmanager类应用于合同的Manager持久数据                             |


## Cursor
类光标，代表dbmanger行

## DBManager
dbmanager类应用于合同的Manager持久数据


## 方法列表
超脑TS_lib的DBMANAGER所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [retrieve_db_iterators](docs-cn/ts-lib/08-ts-dbmanager#retrieve_db_iterators)                           |检索数据库的迭代器                              |


## assert_ripemd160
```
retrieve_db_iterators(code: u64, table: u64, scope: u64)
```
检索数据库的迭代器

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|code              | u64 |                     |是     |
|table              | u64 |                     |是     |
|scope              | u64 |                     |是     |

#### 返回结果类型
`i32[]`