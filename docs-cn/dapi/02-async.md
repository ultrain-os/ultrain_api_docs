## 简介

超脑对外提供的数据接口，需要DAPP通过访问授权接口获取token，并将token信息放在headers的x-access-token属性中带过来。

默认情况下，```对外接口``` 
正式环境接口域名前缀为[https://dev.ultrain.info/api/](https://dev.ultrain.info/api/)。
测试环境接口域名前缀为[https://testnet-dev.ultrain.info/api/](https://testnet-dev.ultrain.info/api/)。
 
## 方法列表

对外接口所支持的方法如下表所示。


| 方法                                                                                           | 描述                                             |
| :---------------------------------------------------------------------------------------------| :-----------------------------------------------|
| [asyncOutsideUser](docs-cn/dapi/02-async#asyncOutsideUser)            |同步外部回流进来的用户【第三方dapp授权访问】                                      |
| [getUserBasicInfo](docs-cn/dapi/02-async#getUserBasicInfo)            |返回用户基础信息【第三方dapp授权访问】                                      |
| [getChainList](docs-cn/dapi/02-async#getChainList)            |返回链列表【第三方dapp授权访问】                                      |


## asyncOutsideUser
```
(static) asyncOutsideUser(req, res, next)
```
同步外部回流进来的用户【第三方dapp授权访问】

#### 参数说明  
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
| phoneNum         |Number  |用户的手机号码		                    |是     |
| logo          |String  |	用户的图像		                    |是     |
| name         |String  |	用户名		                    |是     |
| email          |String  |	用户邮箱		                    |是     |


#### 参考示例

```nodejs
{
  "method": "post",
  "url":"https://dev.ultrain.info/api/user/asyncOutsideUser",
  headers: {'content-type': 'application/x-www-form-urlencoded',
    'x-access-token':'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.ey***********************Z6T3dKVm55ZnZaVksiLCJpYXQiOjE1NjI5MTc1NzUsImV4cCI6MTU2MzAwMzk3NX0.YmdR984lsUPuekaGtmk3aanfQlLNfHtlebXOfxdGjhY'},
  body: JSON.stringify(
      {
        "phoneNum": "0086177*****560",
        "logo":"https://developer.ultrain.info/upload/213432fasd.png",
        "name": "ben",
        "email":"98******62@qq.com"
      }
  )
}
```
 
#### 返回结果类型  
`Object`

#### 返回结果
![11551562920447_ pic_hd](https://user-images.githubusercontent.com/44561751/61114516-0b7f9780-a4c3-11e9-9461-82984ad139f9.jpg)
```
{
    "state": "success",
    "doc": {
        "logo": "https://developer.ultrain.info/upload/213432fasd.png",
        "inWhiteList": false,
        "phoneNum": "1771*******7169467",
        "name": "anfen",
        "email": "98*****62@qq.com",
        "_id": "NSQq0NO2-",
        "sourceId": "_E-dhoyQl",
        "wallets": [],
        "createdAt": "2019-07-12T07:29:49.287Z",
        "__v": 0,
        "date": "2019-07-12 15:29:49",
        "id": "NSQq0NO2-"
    }
}
```


## getUserBasicInfo
```
(static) getUserBasicInfo(req, res, next)
```
返回用户基础信息【第三方dapp授权访问】

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
| phoneNum         |String  |	用户手机号		                    |是     |

#### 参考示例

```nodejs
{
  "method": "get",
  "url":"https://dev.ultrain.info/api/user/getUserBasicInfo?phoneNum=00569****1570,
  headers: {'content-type': 'application/x-www-form-urlencoded',
    'x-access-token':'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.ey***********************Z6T3dKVm55ZnZaVksiLCJpYXQiOjE1NjI5MTc1NzUsImV4cCI6MTU2MzAwMzk3NX0.YmdR984lsUPuekaGtmk3aanfQlLNfHtlebXOfxdGjhY'},
}
```
 
#### 返回结果类型  
`Object`

#### 返回结果
![11561562920477_ pic](https://user-images.githubusercontent.com/44561751/61114520-0de1f180-a4c3-11e9-92d8-b1c715755d00.jpg)
```
{
    "state": "success",
    "data": {
        "logo": "/upload/avatars/avatar-1556159977279.jpg",
        "_id": "-79Qm9k_s",
        "phoneNum": "00569****1570",
        "name": "Juan L****n",
        "email": "c****ot19@hotmail.com",
        "date": "2019-07-12 15:44:24",
        "id": "-79**9k_s"
    }
}
```



## getChainList
```
(static) getChainList(req, res, next)
```
返回用户基础信息【第三方dapp授权访问】

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
| network         |String  |	测试网或主网（MainNet|TestNet），默认主网		                    |否     |

#### 参考示例

```nodejs
{
  "method": "get",
  "url":"https://dev.ultrain.info/api/chain/getList?network=TestNet,
  headers: {'content-type': 'application/x-www-form-urlencoded',
    'x-access-token':'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.ey***********************Z6T3dKVm55ZnZaVksiLCJpYXQiOjE1NjI5MTc1NzUsImV4cCI6MTU2MzAwMzk3NX0.YmdR984lsUPuekaGtmk3aanfQlLNfHtlebXOfxdGjhY'},
}
```
 
#### 返回结果类型  
`Object`

#### 返回结果
![1573119589761 (1)](https://user-images.githubusercontent.com/1866848/68377710-dc81e580-0185-11ea-8d40-0f83c180c30d.jpg)
```
{
    "state": "success",
    "data": [
        {
            "locale": {
                "zh-CN": "测试网动力链",
                "en": "Testnet Power"
            },
            "httpEndpoint": "https://test-power.ultrain.info",
            "httpEndpointHistory": "https://history-test-power.ultrain.info",
            "network": "TestNet",
            "isSideChain": true,
            "_id": "2hNhi3NqT",
            "name": "12",
            "chainId": "0120d06d4a73b60357a5ed24a9145c967308738d70397c25eeedcbb736166ccf"
        },
        {
            "locale": {
                "zh-CN": "测试网先锋链",
                "en": "Testnet Pioneer"
            },
            "httpEndpoint": "https://test-pioneer.ultrain.info",
            "httpEndpointHistory": "http://history-test-pioneer.ultrain.info",
            "network": "TestNet",
            "isSideChain": true,
            "_id": "M2WL3lbih",
            "name": "11",
            "chainId": "20c35b993c10b5ea1007014857bb2b8832fb8ae22e9dcfdc61dacf336af4450f"
        },
        {
            "locale": {
                "zh-CN": "测试网主链",
                "en": "Testnet MainChain"
            },
            "httpEndpoint": "https://test-main.ultrain.info",
            "httpEndpointHistory": "https://history-test-ultrainio.ultrain.info",
            "network": "TestNet",
            "isSideChain": false,
            "_id": "psnW5_1sQ",
            "name": "ultrainio",
            "chainId": "1f1155433d9097e0f67de63a48369916da91f19cb1feff6ba8eca2e5d978a2b2"
        }
    ]
}
```
