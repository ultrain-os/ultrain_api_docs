
Cona是一款基于浏览器插件的超脑链轻钱包，涵盖转账、收款、账号同步及授权认证等功能，可以让你在浏览器环境中运行超脑链的dApp  

## 主要特性

>导入账户  
创建测试网账户  
账户详情  
查看交易历史  
查看代币列表  
发起转账交易  
账户同步到侧链  
账户设置-导出私钥助记词  
设置-切换网络、中英文及密码修改  

## 安装

Cona目前只支持chrome浏览器。可以到chrome应用商店搜索cona下载。  
另：如果不能访问chrome应用商店，也可以离线下载安装包，开发者模式导入到扩展中。  
离线安装包下载地址：https://ultrain-cona.oss-cn-hangzhou.aliyuncs.com/cona.crx

## 创建钱包

安装成功后，在chrome浏览器右上角点击Cona图标，打开Cona插件。主界面有主网测试网切换、中英文切换。按提示填写表单即可创建一个钱包。（钱包创建后，并没有账户，账户需要导入）  
https://user-images.githubusercontent.com/44561751/61096847-8fb62880-a48b-11e9-9b1f-c993b95a18ca.png

<img width="300px" src="https://user-images.githubusercontent.com/44561751/61096847-8fb62880-a48b-11e9-9b1f-c993b95a18ca.png"  />


## 部分功能和页面展示

#### 账户详情

账户详情页面，可以看到账户的UGAS余额、交易历史，以及代币查看、转账交易、账户同步的操作入口。

<img width="300px" src="https://user-images.githubusercontent.com/44561751/61096853-93e24600-a48b-11e9-9bb0-75475a7a9a64.png"  />

#### 查看代币列表

<img width="300px" src="https://user-images.githubusercontent.com/44561751/61096859-96dd3680-a48b-11e9-9277-5f9b7466ffeb.png"  />

<img width="300px" src="https://user-images.githubusercontent.com/44561751/61096861-993f9080-a48b-11e9-8413-4b33fb810624.png"  />


#### 账户设置-导出助记词私钥

账户设置，主要功能有导出私钥、导出助记词等

<img width="300px" src="https://user-images.githubusercontent.com/44561751/61096863-9ba1ea80-a48b-11e9-9dea-8bc549c91f08.png"  />

<img width="300px" src="https://user-images.githubusercontent.com/44561751/61096866-9e044480-a48b-11e9-9b0e-7c5f5986b87f.png"  />



#### 设置

设置页面可以进行网络切换、语言切换，以及钱包修改密码

<img width="300px" src="https://user-images.githubusercontent.com/44561751/61096868-a0669e80-a48b-11e9-875e-a816f03c03fc.png"  />

#### API

**检测cona是否安装**  

Cona会在浏览器注入window.Cona对象，检测window.Cona如果存在则表示用户有安装。

Cona在线安装地址为 https://chrome.google.com/webstore/detail/cona/joopmnkobcdaojgcmohnjhloldhfgfgk

Cona离线下载地址为 https://ultrain-cona.oss-cn-hangzhou.aliyuncs.com/cona.crx.zip

离线包安装方法：

>1.解压出cona.crx文件；
>
>2.打开Chrome，在URL中输入 chrome://extensions,同时打开右上角的开发者模式；
>
>3.将cona.crx拖拽到该网页中间进行添加；

<img width="80%" src="https://user-images.githubusercontent.com/1866848/61033042-34395b80-a3f5-11e9-8b64-df6f7d65d383.png">


检查是否成功安装的方法如下：

```
window.addEventListener('load', function () {
  if (typeof window.Cona !== 'undefined') {
    console.log('Cona is enabled')
  } else {
    console.log('Cona is not installed')
  }
})

```


Cona还提供了针对DAPP"连接"请求，"鉴权"请求，以及转账，调用智能合约的接口服务。详细的API请参照《[DAPP接入规范的](/docs-cn/dapp/wallet.md)》的钱包接入章节。
