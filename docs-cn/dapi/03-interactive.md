## 简介

超脑对Dapp提供的可以调用UltrainOne内部功能交互方法，通过```postMessage```与UltrainOne进行交互
 
## 方法列表

提供的交互方法如下


| 方法                                                                                           | 描述                                             |
| :---------------------------------------------------------------------------------------------| :-----------------------------------------------|
| [outLink](docs-cn/dapi/03-interactive#outLink)            |通过UltrainOne唤起外部应用打开一个url链接，比如唤起手机内置浏览器或AppStore等                                      |
| [externalShare](docs-cn/dapi/03-interactive#externalShare)            |唤起UltrainOne内部分享功能或直接调用分享组件中的菜单，如分享至微信或截屏等                                      |
| [route](docs-cn/dapi/03-interactive#route)            |调用UltrainOne导航组件，可以使app内部回退返回上一个请求的页面，不会关闭当前dapp                                      |
| [downloadImg](docs-cn/dapi/03-interactive#downloadImg)            |调用UltrainOne内部图片下载功能                                      |


## outLink
```
  window.postMessage(JSON.stringify({
    outLink: outLink
  }));
```
在H5中，通过UltrainOne唤起外部应用打开一个url链接，比如唤起手机内置浏览器或AppStore等 

#### 参数说明  
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
| outLink         |String  |用户跳转的链接		                    |是     |

#### 参考示例

```
  // 注：使用前请确保有能打开链接的应用

  // 唤起浏览器打开外部链接
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
唤起UltrainOne内部分享功能或直接调用分享组件中的菜单，如分享到微信朋友圈或截屏

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
| externalShare         |String  |	值'open','wexin','timeline','facebook','twitter','snapshot','clipboard'	                    |是     |

#### 参考示例

```
  //弹出分享组件
  window.postMessage(JSON.stringify({
    externalShare: 'open'
  }));

  //直接分享给微信朋友
  window.postMessage(JSON.stringify({
    externalShare: 'wexin'
  }));

  //直接分享到微信朋友圏
  window.postMessage(JSON.stringify({
    externalShare: 'timeline'
  }));

  //直接分享到facebook
  window.postMessage(JSON.stringify({
    externalShare: 'facebook'
  }));

  //直接分享到twitter
  window.postMessage(JSON.stringify({
    externalShare: 'twitter'
  }));

  //直接截屏
  window.postMessage(JSON.stringify({
    externalShare: 'snapshot'
  }));

  //直接复制链接
  window.postMessage(JSON.stringify({
    externalShare: 'clipboard'
  }));
```

## route
```
  window.postMessage(JSON.stringify({
    route: route,
    name: name
  }));
```
调用UltrainOnen导航组件，可以使app内部回退返回上一个请求的页面，不会关闭当前dapp

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
| route         |String  |	1.跳转链接：希望跳转的对应链接 2.goBack：回退到上一个页面                    |是     |
| name         |String  |	APP头部导航显示的名称                    |否     |

#### 参考示例

```
  window.postMessage(JSON.stringify({
    route: 'https://www.baidu.com/',
    name: '百度'
  }));

  window.postMessage(JSON.stringify({
    route: 'goBack',
    name: ''
  }));
```

## downloadImg
```
  window.postMessage(JSON.stringify({
    downloadImg: imageUrl
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
    downloadImg: 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1579059962&di=4477b25a3d8b054c28c8191a753567ab&imgtype=jpg&er=1&src=http%3A%2F%2Ffile02.16sucai.com%2Fd%2Ffile%2F2014%2F0704%2Fe53c868ee9e8e7b28c424b56afe2066d.jpg'
  }));
```

