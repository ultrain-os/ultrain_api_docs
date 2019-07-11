<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>docs_homepage</title>
    <link href="https://cdn.bootcss.com/twitter-bootstrap/4.2.1/css/bootstrap.min.css" rel="stylesheet">
</head>
<style scoped>
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
        font-size: 22px;
        font-family: SourceSansPro-Regular;
        font-weight: 400;
        color: rgba(110, 111, 112, 1);
        position: relative;
        padding-left: 10px;
    }

    li a::before {
        content: '';
        width: 4px;
        height: 4px;
        border-radius: 50%;
        background: #000000;
        position: absolute;
        /* display: block; */
        left: 0;
        top: 15px;
    }

    .content-title {
        font-size: 22px;
        font-family: SourceSansPro-Bold;
        font-weight: bold;
        color: rgba(0, 0, 0, 1);
        padding-bottom: 10px;
        border-bottom: 1px solid #979797;
        text-align: left;
        margin-bottom: 10px;
    }

    .content-container {
        margin: 40px 120px;
        padding: 40px 30px;
        background: rgba(245, 247, 247, 1);
    }

    .content-container .content-row:first-child {
        margin-bottom: 40px;
    }

    @media screen and (max-width: 576px) {
        .content-container {
            margin: 40px 20px;
        }
    }

</style>
<body>
<h1 align="center">超脑开发者中心</h1>

<div>欢迎来到超脑开发者中心。借助此开发者文档，你可以快速了解超脑的技术和工具。</div>
<div>
</br></br>
<h4>超脑开发指南</h4>
    <div class="content-container" style="background-color: #f4f4f4;padding: 1.2rem 1.2rem 2.4rem;margin: 2.4rem 0;">
        <div class="row content-row">
            <div class="col-sm-4 col-xs-12">
                <p class="content-title" style="border-bottom: 1px solid #979797;">开发者手册</p>
                <div>
                    <div>
                        <a href="#/docs-cn/developer/foundation.md">基础介绍</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/developer/architecture.md">架构设计</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/developer/environment.md">环境配置</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/developer/tool.md">开发工具</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/developer/contract.md">智能合约</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/developer/middleware.md">中间件</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/developer/demo.md">DAPP示例</a>
                    </div>
                </div>
            </div>
            <div class="col-sm-4 col-xs-12">
                <p class="content-title" style="border-bottom: 1px solid #979797;">DAPP接入规范</p>
                <div>
                    <div>
                        <a href="#/docs-cn/dapp/flow.md">流程规范</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/dapp/wallet.md">钱包接入</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/dapp/operation.md">运营规范</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/dapp/service.md">服务条款</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</br>
    <h4>超脑技术文档</h4>
    <div class="content-container" style="background-color: #f4f4f4;padding: 1.2rem 1.2rem 2.4rem;margin: 2.4rem 0;">
        <div class="row content-row">
            <div class="col-sm-12 col-xs-12">
                <p class="content-title" style="text-align:center;border-bottom: 1px solid #979797;">Contract API</p>
                <div class="row content-row">
                    <div class="col-sm-3 col-xs-12">
                        <div>
                            <a href="#/docs-cn/contract/01-ts-account.md">ACCOUNT</a>
                        </div>
                        <div>
                            <a href="#/docs-cn/contract/02-ts-action.md">ACTION</a>
                        </div>
                        <div>
                            <a href="#/docs-cn/contract/03-ts-asset.md">ASSET</a>
                        </div>
                        <div>
                            <a href="#/docs-cn/contract/04-ts-bigNumber.md">BIGNUMBER</a>
                        </div>
                    </div>
                    <div class="col-sm-3 col-xs-12">
                        <div>
                            <a href="#/docs-cn/contract/05-ts-block.md">BLOCK</a>
                        </div>
                        <div>
                            <a href="#/docs-cn/contract/06-ts-contract.md">CONTRACT</a>
                        </div>
                        <div>
                            <a href="#/docs-cn/contract/07-ts-crypto.md">CRYPTO</a>
                        </div>
                        <div>
                            <a href="#/docs-cn/contract/08-ts-dbmanager.md">DBMANAGER</a>
                        </div>
                    </div>
                    <div class="col-sm-3 col-xs-12">
                        <div>
                            <a href="#/docs-cn/contract/09-ts-events.md">EVENTS</a>
                        </div>
                        <div>
                            <a href="#/docs-cn/contract/10-ts-log.md">LOG</a>
                        </div>
                        <div>
                            <a href="#/docs-cn/contract/11-ts-PermissionLevel.md">PERMISSIONLEVEL</a>
                        </div>
                        <div>
                            <a href="#/docs-cn/contract/12-ts-return.md">RETURN</a>
                        </div>
                    </div>
                    <div class="col-sm-3 col-xs-12">
                        <div>
                            <a href="#/docs-cn/contract/13-ts-time.md">TIME</a>
                        </div>
                        <div>
                            <a href="#/docs-cn/contract/14-ts-transaction.md">TRANSACTION</a>
                        </div>
                        <div>
                            <a href="#/docs-cn/contract/15-ts-utils.md">UTILS</a>
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-sm-4 col-xs-12">
                <p class="content-title" style="border-bottom: 1px solid #979797;">Contract API</p>
                <div>
                    <div>
                        <a href="#/docs-cn/contract/01-lib-arraymap">ARRAYMAP</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/contract/02-lib-balance">BALANCE</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/contract/03-lib-headblock">HEADBLOCK</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/contract/04-lib-map">MAP</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/contract/05-lib-name">NAME</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/contract/06-lib-name_ex">NAME_EX</a>
                    </div>
                </div>
            </div>
            <div class="col-sm-4 col-xs-12">
                <p class="content-title" style="border-bottom: 1px solid #979797;">U3 API</p>
                <div>
                    <div>
                        <a href="#/docs-cn/u3/01-u3-chain.md">实时U3方法</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/u3/02-u3-history.md">历史U3方法</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/u3/03-u3-ecc.md">U3加密算法</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/u3/04-u3-utils.md">U3其它工具</a>
                    </div>
                </div>
            </div>
            <div class="col-sm-4 col-xs-12">
                <p class="content-title" style="border-bottom: 1px solid #979797;">REST API</p>
                <div>
                    <div>
                        <a href="#/docs-cn/rest/01-chain">实时REST接口</a>
                    </div>
                    <div>
                        <a href="#/docs-cn/rest/02-history">历史REST接口</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

</body>
</html>
