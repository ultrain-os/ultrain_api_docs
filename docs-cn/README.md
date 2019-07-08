<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>docs_homepage</title>
<link href="https://cdn.bootcss.com/twitter-bootstrap/4.2.1/css/bootstrap.min.css" rel="stylesheet">

  </head>
  <style scoped >
  h1, h2 {
    font-weight: normal;
  }
  ul {
    /* list-style-type: none; */
    padding: 0;
    text-align: left;
  }
  li {
    display: block;
    margin: 0;

  }
  ul a {
      font-size:22px;
  font-family:SourceSansPro-Regular;
  font-weight:400;
  color:rgba(110,111,112,1);
  position: relative;
  padding-left: 10px;
  }

  li a::before {
    content: '';
    width:4px;
    height:4px;
    border-radius: 50%;
    background:#000000;
    position: absolute;
      /* display: block; */
      left: 0;
      top: 15px;
  }

  .content-title {
    font-size:22px;
    font-family:SourceSansPro-Bold;
    font-weight:bold;
    color:rgba(0,0,0,1);
    padding-bottom: 10px;
    border-bottom: 1px solid #979797;
    text-align:left;
    margin-bottom:10px;
  }

  .content-container {
    margin:40px 120px;
    padding:40px 30px;
    background:rgba(245,247,247,1);
  }

  .content-container .content-row:first-child {
    margin-bottom: 40px;
  }

  @media screen and (max-width:576px) {
     .content-container {
        margin:40px 20px;
    }
  }

  </style>
  <body>
  <h1 align="center">超脑开发者中心</h1>
  <div>欢迎来到超脑开发者中心。借助此开发者文档，你可以快速了解超脑的技术和工具。</div>
    <div ></br></br>
      <h4>超脑的技术和工具</h4>
      <div class="content-container" style="background-color: #f4f4f4;padding: 1.2rem 1.2rem 2.4rem;margin: 2.4rem 0;" >
          <div class="row content-row">
						<div class="col-sm-12 col-xs-12">
								<p class="content-title" style="text-align:center;border-bottom: 1px solid #979797;">TS_lib—与智能合约交互的通用库</p>
									<div class="row content-row">
											<div class="col-sm-3 col-xs-12">
													<div>
															<a href="#/docs-cn/ts-lib/01-ts-account.md">ACCOUNT</a>
													</div>
													<div>
															<a href="#/docs-cn/ts-lib/02-ts-action.md">ACTION</a>
													</div>
													<div>
															<a href="#/docs-cn/ts-lib/03-ts-asset.md">ASSET</a>
													</div>
													<div>
															<a href="#/docs-cn/ts-lib/04-ts-bigNumber.md">BIGNUMBER</a>
													</div>
											</div>
											<div class="col-sm-3 col-xs-12">
													<div>
															<a href="#/docs-cn/ts-lib/05-ts-block.md">BLOCK</a>
													</div>
													<div>
															<a href="#/docs-cn/ts-lib/06-ts-contract.md">CONTRACT</a>
													</div>
													<div>
															<a href="#/docs-cn/ts-lib/07-ts-crypto.md">CRYPTO</a>
													</div>
													<div>
															<a href="#/docs-cn/ts-lib/08-ts-dbmanager.md">DBMANAGER</a>
													</div>
											</div>
											<div class="col-sm-3 col-xs-12">
													<div>
															<a href="#/docs-cn/ts-lib/09-ts-events.md">EVENTS</a>
													</div>
													<div>
															<a href="#/docs-cn/ts-lib/10-ts-log.md">LOG</a>
													</div>
													<div>
															<a href="#/docs-cn/ts-lib/11-ts-PermissionLevel.md">PERMISSIONLEVEL</a>
													</div>
													<div>
															<a href="#/docs-cn/ts-lib/12-ts-return.md">RETURN</a>
													</div>
											</div>
											<div class="col-sm-3 col-xs-12">
													<div>
															<a href="#/docs-cn/ts-lib/13-ts-time.md">TIME</a>
													</div>
													<div>
															<a href="#/docs-cn/ts-lib/14-ts-transaction.md">TRANSACTION</a>
													</div>
													<div>
															<a href="#/docs-cn/ts-lib/15-ts-utils.md">UTILS</a>
													</div>
											</div>
									</div>	
						</div>
	 <div class="col-sm-4 col-xs-12">
	        <p class="content-title" style="border-bottom: 1px solid #979797;">TSLIB的扩展方法</p>
	         <div>
			<div>
				<a href="#/docs-cn/ts-lib-extend/01-lib-arraymap">ARRAYMAP</a>
			</div>
			<div>
				<a href="#/docs-cn/ts-lib-extend/02-lib-balance">BALANCE</a>
			</div>
			<div>
				<a href="#/docs-cn/ts-lib-extend/03-lib-headblock">HEADBLOCK</a>
			</div>
			<div>
				<a href="#/docs-cn/ts-lib-extend/04-lib-map">MAP</a>
			</div>
			<div>
				<a href="#/docs-cn/ts-lib-extend/05-lib-name">NAME</a>
			</div>
			<div>
				<a href="#/docs-cn/ts-lib-extend/06-lib-name_ex">NAME_EX</a>
			</div>
		</div>
	</div>
        <div class="col-sm-4 col-xs-12">
                <p class="content-title" style="border-bottom: 1px solid #979797;">Ultrain RPC API</p>
                 <div>
			<div>
				<a href="#/docs-cn/ultrain-rpc/01-history-rpc-api">历史RPC接口</a>
			</div>
			<div>
				<a href="#/docs-cn/ultrain-rpc/02-online-rpc-api">线上RPC接口</a>
			</div>
		</div>
	</div>
	<div class="col-sm-4 col-xs-12">
		<p class="content-title" style="border-bottom: 1px solid #979797;">U3—与链交互的通用库</p>
		<div>
			<div>
				<a href="#/docs-cn/u3/01-u3-chain.md">U3链上方法</a>
			</div>
			<div>
				<a href="#/docs-cn/u3/02-u3-ecc.md">U3加密相关方法</a>
			</div>
			<div>
				<a href="#/docs-cn/u3/03-u3-history.md">U3历史方法</a>
			</div>
			<div>
				<a href="#/docs-cn/u3/04-u3-utils.md">U3工具类方法</a>
			</div>
		</div>
	</div>
	</div>
	</div>
</div>
  </body>
</html>
