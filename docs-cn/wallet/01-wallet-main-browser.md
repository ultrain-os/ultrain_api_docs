## Ultrain主网浏览器的定义

Ultrain主网提供一个多链的环境，主要为Ultrain的用户提供查询、充值、部署等功能。通过Ultrain主网浏览器，用户可以查询Ultrain区块链中的区块、交易、账户、合约等信息，并支持切换测试网和企业网等进行信息查询。除了信息查询外，利用Ultrain浏览器还可以进行以下功能的操作：     
>部署合约  
>调用合约  

## 合约的部署  

将编译好的合约代码部署到Ultrain区块链之后，合约代码可存储在链上，用户可获得合约账户名称，可用于后续调用合约使用。合约部署过程需要消耗RAM、CPU或NET资源。

### 部署合约步骤  

进入Ultrain浏览器：http://explorer.ultrain.info ，右上角选择部署合约所在的网络（测试网或企业网），点击菜单【工具-部署合约】，进入部署合约流程。

![image](https://user-images.githubusercontent.com/44561751/61106285-3cee6800-a4af-11e9-8170-190f4e28fb8d.png)

#### 1、关联账户  
需输入本合约关联的账户名称，目前一个账户只可部署一个合约，部署成功后，关联账户名称也是合约的名称。

![image](https://user-images.githubusercontent.com/44561751/61106340-71622400-a4af-11e9-8bad-f16bcd2ed2d7.png)

#### 2、上传合约文件  
需上传合约的三个文件，格式分别为abi、wast和wasm。上传时，根据文件类型，相同类型的新文件会覆盖旧文件。

![image](https://user-images.githubusercontent.com/44561751/61106938-2fd27880-a4b1-11e9-82d3-313e9b9bbf4e.png)

#### 3、签名交易

使用关联账户的私钥或助记词，对部署进行签名。

![image](https://user-images.githubusercontent.com/44561751/61106944-32cd6900-a4b1-11e9-9ecc-101275aee052.png)

#### 4、查询合约

交易成功后，查询关联账户名称，可查看合约的信息。也可通过交易哈希，了解本次部署合约交易的内容。

![image](https://user-images.githubusercontent.com/44561751/61106511-f9e0c480-a4af-11e9-97dd-eaf075830be2.png)

## 调用合约

合约部署之后，就可以通过调用合约，执行合约的内容。部署后产生的合约，既可以被合约关联的账户调用，也可以被其他任何账户调用。

### 调用合约步骤

进入Ultrain浏览器：http://explorer.ultrain.info ，右上角选择部署合约所在的网络（测试网或企业网），点击菜单【工具-调用合约】，进入调用合约流程。

![image](https://user-images.githubusercontent.com/44561751/61106285-3cee6800-a4af-11e9-8170-190f4e28fb8d.png)

#### 1、输入或选择合约

![image](https://user-images.githubusercontent.com/44561751/61106683-74a9df80-a4b0-11e9-9c70-6b270b2513a7.png)

#### 2、选择调用方法

合约内可能有多种方法，每次调用合约时只能选择其中一种方法，并填写该方法中参数信息。

![image](https://user-images.githubusercontent.com/44561751/61106838-eb46dd00-a4b0-11e9-9f00-7308e0ee1b3b.png)

#### 3、调用账户填写及签名

填写调用合约的账户，及用该账户的私钥或助记词签名。

![image](https://user-images.githubusercontent.com/44561751/61106886-09144200-a4b1-11e9-90be-a53bf4e87f23.png)

#### 4、查询调用结果

交易成功后，通过交易哈希，了解本次调用合约交易的内容。

![image](https://user-images.githubusercontent.com/44561751/61106896-0e718c80-a4b1-11e9-9a2b-5f94b6f7a950.png)


## 部分功能展示

#### 1、首页功能展示

首页的功能主要是展示主侧链的数量、节点数量、账户数量、交易数量以及相关的分布数据图示和最新区块和交易的展示。

![image](https://user-images.githubusercontent.com/44561751/61107013-64decb00-a4b1-11e9-87d8-9922d371efbf.png)
![image](https://user-images.githubusercontent.com/44561751/61107044-71fbba00-a4b1-11e9-901e-6bdac3dba350.png)
![image](https://user-images.githubusercontent.com/44561751/61107056-7b852200-a4b1-11e9-866b-0216c2207293.png)

#### 区块和交易功能展示  
![image](https://user-images.githubusercontent.com/44561751/61107099-95266980-a4b1-11e9-84b8-6fed1834346a.png)
![image](https://user-images.githubusercontent.com/44561751/61107117-a1122b80-a4b1-11e9-92a2-1669d7df67a4.png)


#### 账户功能展示

![image](https://user-images.githubusercontent.com/44561751/61107135-b5562880-a4b1-11e9-90ff-25bd1c66d0bb.png)
