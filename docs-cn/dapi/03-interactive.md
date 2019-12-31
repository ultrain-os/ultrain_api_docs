## 简介

超脑对Dapp提供的可以调用UltrainOne内部功能交互方法，通过```postMessage```与UltrainOne进行交互
 
## 方法列表

提供的交互方法如下


| 方法                                                                                           | 描述                                             |
| :---------------------------------------------------------------------------------------------| :-----------------------------------------------|
| [outLink](docs-cn/dapi/02-async#outLink)            |在UltrainOne内唤起外部应用连接                                      |
| [externalShare](docs-cn/dapi/02-async#externalShare)            |唤起UltrainOne内部分享功能                                      |
| [route](docs-cn/dapi/02-async#route)            |调用UltrainOne内部跳转，可以使app内部回退返回上一个请求的页面，不会关闭当前dapp                                      |
| [route](docs-cn/dapi/02-async#downloadImg)            |调用UltrainOne内部图片下载功能                                      |


## outLink
```
  window.postMessage(JSON.stringify({
    outLink: outLink
  }));
```
在UltrainOne内唤起外部应用连接  

#### 参数说明  
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
| outLink         |String  |用户跳转的链接		                    |是     |

#### 参考示例

```
  // 注：使用前请确保有能打开链接的应用

  // 浏览器打开外部链接
  window.postMessage(JSON.stringify({
    outLink: 'https://developer.ultrain.info/ShareSoftware'
  }));

  // 跳转到 App Store
  window.postMessage(JSON.stringify({
    outLink: 'itms-apps://itunes.apple.com/app/id1407704761'
  }));
```

## externalShare
```
  window.postMessage(JSON.stringify({
    externalShare: externalShare
  }));
```
唤起UltrainOne内部分享功能

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
| externalShare         |String  |	share		                    |是     |

#### 参考示例

```
  window.postMessage(JSON.stringify({
    externalShare: 'share'
  }));
```

## route
```
  window.postMessage(JSON.stringify({
    route: route,
    name: name
  }));
```
调用UltrainOne内部跳转，可以使app内部回退返回上一个请求的页面，不会关闭当前dapp

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
| route         |String  |	1.跳转链接：希望跳转的对应链接<br>2.goBack：回退到上一个页面                    |是     |
| name         |String  |	APP头部导航显示的名称                    |否     |

#### 参考示例

```
  window.postMessage(JSON.stringify({
    route: 'https://www.baidu.com/',
    name: '百度'
  }));
```

## downloadImg
```
  window.postMessage(JSON.stringify({
    downloadImg: downloadImg
  }));
```
调用UltrainOne内部图片下载功能，将图片下载到本地

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
| downloadImg         |String  |	网络图片链接                    |是     |

#### 参考示例

```
  window.postMessage(JSON.stringify({
    downloadImg: 'https://developer.ultrain.info/downloadImg.png'
  }));
```

