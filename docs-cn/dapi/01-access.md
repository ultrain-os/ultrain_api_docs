## 简介
DAPP与超脑之间的数据交互，需要首先通过访问授权。

所有DAPP在超脑DAPP开放平台中都会被分配一个唯一的ultrainId和一个secretId。这两个属性作为DAPP在超脑平台唯一标识。
DAPP开发者在开放平台添加一个DAPP时，系统会自动生成ultrainId和secretId，并返回给开发者。
ultrainId一经生成就不能改变，而secretId可以再次重置。

所谓访问授权，就是开发者将ultrainId与secretId传输给超脑开放平台而获得一个token的过程。token有效期为一天。

默认情况下，```授权访问``` 接口的正式环境地址为[https://dev.ultrain.io/api/dapp/getAccessToken](https://dev.ultrain.io/api/dapp/getAccessToken)，
测试环境地址为[https://testnet-dev.ultrain.io/api/dapp/getAccessToken](https://testnet-dev.ultrain.io/api/dapp/getAccessToken)。

## 方法列表

授权访问所支持的方法如下表所示。

| 方法                                                                                           | 描述                                             |
| :---------------------------------------------------------------------------------------------| :-----------------------------------------------|
| [getAccessToken](docs-cn/dapi/01-access#getAccessToken)            |授权第三方应用访问                                      |

## getAccessToken  
```
(static) getAccessToken(req, res, next)
```
授权第三方应用访问

#### 参数说明  
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
| ultrainId         |String  |	dapp所拥有的唯一开放平台id		                    |是     |
| secretId          |String  |	dapp所拥有的开放平台密钥		                    |是     |

#### 参考示例

```nodejs
{
  "method": "post",
  "url":"https://dev.ultrain.io/api/dapp/getAccessToken",
  headers: {'content-type': 'application/x-www-form-urlencoded'},
  body: JSON.stringify(
      {
        "ultrainId": "ultrain****************fvZVK",
        "secretId":"JdjaLrjR2****************ot47Ygq3kG"
      }
  )
}
```
 
#### 返回结果类型  
`Object`

#### 返回结果
![11531562920381_ pic_hd](https://user-images.githubusercontent.com/44561751/61114512-09b5d400-a4c3-11e9-8f91-6aab6a2b45cb.jpg)  

```
{
    "state": "success",
    "auth": true,
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.ey***********************Z6T3dKVm55ZnZaVksiLCJpYXQiOjE1NjI5MTc1NzUsImV4cCI6MTU2MzAwMzk3NX0.YmdR984lsUPuekaGtmk3aanfQlLNfHtlebXOfxdGjhY"
}
```
