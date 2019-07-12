## 简介
默认情况下，```授权访问``` 接口域名为[https://dev.ultrain.io/api/dapp](https://dev.ultrain.io/api/dapp)。

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
| ultrainId         |String  |	用户所携带的账户		                    |是     |
| secretId          |String  |	Ultrain给予该应用的密钥		                    |是     |

#### 参考示例

```nodejs
{
  "method": "post",
  "url":"https://dev.ultrain.io/api/dapp/getAccessToken",
  headers: {
          'content-type': 'application/json'
        },
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