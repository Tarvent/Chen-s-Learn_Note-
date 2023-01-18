# 开发人员必须知道的 Web3 基本工具和技术

# Web3 第一课

在深入研究 Web 3 应用程序中使用的技术之前，让我们首先了解[Web 3](https://www.infoq.cn/video/9XgAQ2GxwUVgMKZBpi0j)是什么，以及它为什么重要。

 Web 3 的五个关键特性是去中心化、区块链、安全性、可扩展性和隐私。在 Web 3 的去中心化世界中，区块链技术和其他协议从根本上改变了数据的存储、分发和访问方式，同时提供了一个本地事务层。当下流行的[Web3应用案例](https://www.infoq.cn/article/a7ls8rH7EoAweEdLcNfO)是去中心化金融（DeFi 和加密货币）、在称为“DAO”的去中心化治理模式中投票、以及作为所有权证明的不可伪造代币（NFT）。

 

Web 3 背后的许多动机，都是基于用户、公司和政府之间的信任受到侵蚀。看上去好像有点愤世嫉俗，但确是如此。

 

在去中心化金融里，用户将资金存储在自己的私人钱包中，交易时无需与中心化机构互动或依赖国家的法定货币。

 

建立在区块链上的投票应用程序，所有投票数据都是透明的，且任何人验证起来都很简便，因此不必再担心选举中发生徇私舞弊。这就是让 Web 3 “无需信人”的原因：该技术是透明的，并且通过密码学得到保护，因此不再是只能盲目信任某些机构。

 

NFT 可用于证明任何数字资产（如音乐或艺术）的所有权，让你可以更直接地支持创作者。

 

所有这些例子，其核心都牵涉到不再需要依赖中央机构或中介机构。

 

需要注意的是，Web 3 并不是要取代 Web 2，就像 Web 2 没有取代 Web 1 一样。对于 Web 1 中出现的静态网站，在 Web 上仍然占有重要地位。即使 Web 3 越来越受欢迎和使用，Web 2 应用程序也将有一席之地。

 

# 去中心化的应用程序（Dapps）

我们现在大致了解了[什么是 Web 3](https://www.infoq.cn/article/jsf43rxkftgecP5aQCNG)，以及为什么去中心化的概念很重要。那么 Web3 应用程序实际上是什么样子的呢？

 

嗯……它们看起来很像 Web 2 应用程序！[去中心化的应用程序](https://www.infoq.cn/article/6tiOQEV3UHCLAMGDXPXH)，也称为“dapps”（或“dApps”），由一个前端 UI 组成，其与部署在区块链上的“智能合约”（一个小代码程序）交互。在交易或将数据写入区块链时，前端还可以与用户的钱包交互。与 Web 2 应用程序的主要区别在于，智能合约和区块链取代了由单个人或公司拥有和维护的经典的服务器和数据库。



![img](https://static001.geekbang.org/infoq/bd/bdf139b8d62ec581970b55da99a0240d.png)



去中心化应用架构

 

# 定义 Web 3 技术栈的技术

 

那么，如何真正构建一个去中心化的应用程序（dapp）？好消息是，可以从已有的编程技能和经验开始！我们已经知道 dapp 有一个前端，这意味着需要了解 HTML、CSS 和 [JavaScript](https://www.infoq.cn/article/CSRgKxyZK0XNK9ZARYEp)。可能还会使用 Angular、React 或 Vue 等框架或库，除非你喜欢用原生 JavaScript。这对于已经精通这些技术的前端开发人员来说是个好消息。

 

现在，让我们看看需要专门为 Web3 学习哪些语言、工具和框架：

 

[Solidity](https://soliditylang.org/) 是一种编程语言，用于编写在以太坊区块链上运行的智能合约。它看起来像是 C++、Python 和 JavaScript 的混合体。如果你现在已经学习了几种编程语言，那么你每次去学一门新语言都会变得更容易。由于大多数智能合约都涉及某种货币兑换，因此遵循[适当的标准](https://docs.openzeppelin.com/)和[在安全方面的最佳实践](https://consensys.net/blog/developers/solidity-best-practices-for-smart-contract-security/)至关重要。

 

Solidity 项目地址：https://soliditylang.org/

 

[Truffle](https://trufflesuite.com/docs/truffle/)是一个框架，可以用来编写、测试和部署智能合约。 其网站将其描述为“使用以太坊虚拟机 (EVM) 的区块链开发环境、测试框架和资产管道”。就像 React 帮助你构建 JavaScript 应用程序一样，Truffle 帮助你构建智能合约。使用 Truffle 并不是绝对必要的，但是这个框架将极大地帮助你，因为它抽象了一些开发复杂性。对于 VS Code 用户，[Truffle for VS Code](https://trufflesuite.com/blog/build-on-web3-with-truffle-vs-code-extension/) 扩展会让开发周期更加容易。

 

[Truffle](https://trufflesuite.com/docs/truffle/)项目地址：https://trufflesuite.com/docs/truffle/

 

Ganache 是用于本地开发和测试智能合约的个人区块链。开发人员只需要通过几个简单的命令，就可以创建以太坊区块链的本地实例。Ganache 允许你在本地开发 Web 3 应用，就像在本地或测试环境而非生产环境中开发 Web 2 应用程序一样。

 

[Ganache](https://trufflesuite.com/docs/ganache/)项目地址：https://trufflesuite.com/docs/ganache/

 

[Web3.js](https://web3js.readthedocs.io/) 是一个用于与以太坊交互的 JavaScript 库。你将在前端应用程序中使用 web3.js 来执行诸如连接到用户的钱包、授予对智能合约的访问权限以及调用智能合约上的函数等操作。智能合约可以通过命令行或 UI 访问，因此 web3.js 可以帮助你从 UI 使用智能合约。

 

Web3.js 项目地址：https://web3js.readthedocs.io/en/v1.8.0/

 

MetaMask 是一个 Web 3 钱包，你可以使用它的浏览器扩展程序或移动应用程序。我们之前提到过钱包，但还没有真正描述过钱包是什么。钱包为你的数字资产提供接口。你使用只有你自己知道的私钥保护钱包里的内容。 MetaMask 为用户提供了一种安全的方式，连接到基于区块链的应用程序，并与它们的钱包交互。对于开发人员来说，需要钱包来部署智能合约并与之交互。通常，私钥必须写在代码中才能交互，但 [Truffle Dashboard](https://trufflesuite.com/blog/introducing-truffle-dashboard/)能够将 MetaMask 钱包连接到项目而无需暴露密钥。

 

MetaMask 项目地址：https://metamask.io/

 

[Infura](https://infura.io/)是连接以太坊和其他区块链以及去中心化存储网络（如 IPFS）的基础设施提供商。无需过多介绍，与区块链的任何交互都需要通过 JSON-RPC 或 WebSockets 访问节点。 Infura 提供了基础设施，因此你不必找机器来启动自己的节点。如果你实在想运行自己的节点，Infura 也可以作为备用。 Infura 还提供了一个开发套件和工具包，包括监控、指标、日志记录、事务管理和其他用于构建 dapp 的功能。这是对我们已谈论过的其他一些技术的进一步抽象，可以使 Web3 开发更加容易。

 

[Infura](https://infura.io/)项目地址：https://infura.io/zh

# 结论

Web 3 是支持下一代软件的下一代互联网。区块链是更透明的技术，不但消费者在采用，[主要机构也在采用](https://consensys.net/reports/web3-report-q3-2021/)，这让区块链成为了主流。了解 Web 3 技术以及构建方法，将为你打入市场提供优势。

对于已经拥有强大的 Web 2 基础，又有志于 Web3 的开发人员，我希望现在你对自己充满信心，因为你已掌握的知识就是良好的开端！花一些时间学学上面的技术，你可能会比你想象的更快做好准备，以迎接 Web3 的到来。

