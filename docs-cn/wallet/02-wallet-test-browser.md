
链化未来测试网提供一个和chain2future主网类似的多链环境。主要为chain2future的开发者（商户）进行dapp开发的测试联调工作提供服务。

无论是商户还是普通开发者，都可以到链化未来测试网行创建测试账户、申请测试资源套餐进行开发基于chain2future的dapp开发。

测试网和主网的不同之处在于主网是无法进行账户的创建和充值，而测试网可以。

## 名词解释及介绍
- 链化未来测试网：基于chain2future部署的一套测试网络，给chain2future开发者提供开发测试及联调验证服务。

- 链化未来测试网浏览器：给用户查看链化未来测试网数据的网站，可以查看链化未来测试网的区块、交易信息，以及进行账户创建、资源套餐申请、合约部署及调用等。
  
- 链化未来测试网的服务地址：
  - 测试网主链地址：[https://test-main.chain2futureinfo](https://test-main.chain2futureinfo)
  - 测试网主链history服务地址：[https://history-test-chain2futureinfo](https://history-test-chain2futureinfo)
- 链化未来测试网浏览器地址： [https://testnet-explorer.chain2futureinfo](https://testnet-explorer.chain2futureinfo)



## 创建测试账户
> 要在链化未来测试网进行dapp开发，首先需要创建链化未来测试网账户。

步骤如下：

  1. 进入链化未来测试网浏览器的账户创建页面[https://testnet-explorer.chain2futureinfo/chain2futureio/account-new](https://testnet-explorer.chain2futureinfo/chain2futureio/account-new)。账户名称文本框输入你要创建的账户名称（名称规则为：请输入5-12位字符，小写字母和数字1-5的组合）, 验证通过后，点击“创建“按钮。
   
   <img src="https://user-images.githubusercontent.com/44561751/61099792-2851a600-a496-11e9-9a2b-44e90c800399.jpg"/>
   

  2. 保存账户私钥和助记词。`请务必保存私钥和助记词，如丢失则账户将不可用`
  <img src="https://user-images.githubusercontent.com/44561751/61099794-2a1b6980-a496-11e9-9f93-7acc4ff5853b.jpg"/>
  
  3. 输入助记词，检查是否牢记。通过后将进行人机验证。
  <img src="https://user-images.githubusercontent.com/44561751/61099795-2be52d00-a496-11e9-8cde-336481055fa3.jpg"/>	
  <img src="https://user-images.githubusercontent.com/44561751/61099798-2daef080-a496-11e9-8c79-dd92fbfe529c.jpg"/>
  
  4. 账户创建交易成功发送到链化未来测试网，等待交易确认。`等待时间大约为十几秒`。  
   <img src="https://user-images.githubusercontent.com/44561751/61099802-31db0e00-a496-11e9-9175-1dda11bbadcb.jpg"/>
   
  5. 账户创建成功。  
   <img src="https://user-images.githubusercontent.com/44561751/61099806-33a4d180-a496-11e9-863e-9023914a3723.jpg"/>


## 申请资源套餐

### 资源的作用

>**UGAS**：用于链化未来测试网服务计费结算的工具，可用于申请资源，目前可以直接通过充值获取，充值地址：http://explorer.chain2futureinfo/account-recharge  
**SYS**：用于企业网服务计费阶段的工具，可用于申请资源，目前可以直接通过充值获取，充值地址：http://explorer.chain2futureinfo/account-recharge  
**RAM**：存储资源，创建账户等交易时需使用该资源，可以使用UGAS/SYS购买RAM。  
**NET**：通信资源，部署和调用智能合约时需占用该资源，可以通过抵押UGAS/SYS获取NET，目前暂不支持赎回操作。  
**CPU**：计算资源，部署和调用智能合约时需占用该资源，可以通过抵押UGAS/SYS获取CPU，目前暂不支持赎回操作。  


> chain2future使用资源套餐的模式(详细介绍见：[资源套餐介绍](https://developer.chain2futureinfo/tutorial/resourceIntroduce)章节)。在链化未来测试网创建好账户后，需要给账户申请资源套餐，才能将dapp合约部署到链化未来测试网。

步骤如下

  1. 进入测试网，点击菜单栏的`账户`-`账户充值`，进入账户充值、资源申请页面。
	<img src="https://user-images.githubusercontent.com/44561751/61099816-38698580-a496-11e9-855f-0a7858f87720.jpg"/>
	
  2. 账户充值页面，有两个功能：一是账户充值（即给账户充测试网UGAS）,二是资源申请（即给账户申请测试资源套餐）。因为进行dapp开发只需要资源，故此处只需要进行资源申请操作即可。
<img src="https://user-images.githubusercontent.com/44561751/61099822-3acbdf80-a496-11e9-879e-8c47a6ddbf83.jpg"/>

  3. 进行账户授权操作，需要输入`接收账户`的私钥或者助记词。确认后页面的按钮将处于loading中（注：此时在等待`授权交易确认`,大概需要十几秒，请耐心等待）
<img src="https://user-images.githubusercontent.com/44561751/61099824-40c1c080-a496-11e9-933c-acc2aa83b054.jpg"/>
<img src="https://user-images.githubusercontent.com/44561751/61099825-41f2ed80-a496-11e9-9c40-c037e9f7873c.jpg"/>

  4. 账户授权成功后，将进行人机验证。
<img src="https://user-images.githubusercontent.com/44561751/61099827-43bcb100-a496-11e9-9ea0-a3c55a763db2.jpg"/>

  5. 资源申请交易成功发送到链化未来测试网，等待交易确认。（注：等待时间大约为十几秒）。
<img src="https://user-images.githubusercontent.com/44561751/61099833-49b29200-a496-11e9-9047-a9dacf2fa3ca.jpg"/>

  6. 充值成功。点击账户名称可以跳转到账户详情，查看账户资源情况
<img src="https://user-images.githubusercontent.com/44561751/61099840-4c14ec00-a496-11e9-828e-7aae085822cd.jpg"/>
<img src="https://user-images.githubusercontent.com/44561751/61099842-4ddeaf80-a496-11e9-9232-18aec9b02e27.jpg"/>

   



