# Nitro开发公网指南 

为了让大家更容易上手 Arbitrum Nitro 开发公网，我们在 Goerli 测试网上运行了自己的 Arbitrum Nitro Rollup 链。 有关 Arbitrum Nitro 基本的介绍，请参阅我们的[公告](https://medium.com/offchainlabs/arbitrum-nitro-sneak-preview-44550d9054f5)。
随着我们接近主网发布并根据反馈情况，我们可能会重置开发网几次，所以请根据情况作出调整安排。

### 连接到该链

如果您使用 Metamask，请添加自定义 RPC 网络以连接到 Arbitrum 开发网：

- Network Name：Arbitrum Nitro Devnet

- RPC URL：https ://nitro-devnet.arbitrum.io/rpc

- ChainID：421612

- Symbol：ETH

- Block Explorer URL：https ://nitro-devnet-explorer.arbitrum.io

- Retryable Dashboard： http ://retryable-tx-panel-nitro.arbitrum.io/

- Token Bridge：https ://nitro-devnet-bridge.arbitrum.io/

### 浏览交易

如果您想查看您的交易，请查看我们的[区块浏览器](https://nitro-devnet-explorer.arbitrum.io/)。然后你将能够看到在 Arbitrum 中执行的所有交易，还可以准确地看到每笔交易消耗多少Gas。

### 以太币与ERC-20代币的桥接
充值、提取以太币和代币，请访问[https://nitro-devnet-bridge.arbitrum.io/](https://nitro-devnet-bridge.arbitrum.io/)。

你可以访问[推特水龙头](https://twitter.com/intent/tweet?text=ok%20I%20need%20@arbitrum%20to%20give%20me%20Nitro%20devnet%20gas.%20like%20VERY%20SOON.%20I%20cant%20take%20this,%20I%E2%80%99ve%20been%20waiting%20for%20@nitro_devnet%20release.%20I%20just%20want%20to%20start%20developing.%20but%20I%20need%20the%20gas%20IN%20MY%20WALLET%20NOW.%20can%20devs%20DO%20SOMETHING??%20%20SEND%20HERE:%200x-your-eth-address-here)获得测试网的
ETH。 要开始使用Arbitrum链，你需要先从 Goerli 上充值一些以太币进入 Arbitrum 支付L2上的燃气消耗。若想在 Goerli 上获取以太请使用标准水龙头之一。

## 与链的交互
在将 Arbitrum Nitro 开发网络添加至 Metamask 后，你就可以像使用以太坊一样使用 Arbitrum 网络了。 不过还有一些需要注意的地方。

* Arbitrum也使用了EIP-1559类似的 Gas 竞价系统，所以你在交易中指定的是竞价的出价，但实际上的花费可能更低。
* 在 Arbitrum 中所支付的 Gas 费，大部分都用于发布你的交易信息到以太坊链上。

## 部署你的合约
在 Arbitrum 主网上部署合约非常轻松，只需要将RPC节点切换至[https://nitro-devnet.arbitrum.io/rpc](https://nitro-devnet.arbitrum.io/rpc)。

深入了解如何用truffle部署合约请见[合约部署](../开发文档/dapp基础/合约部署.md)。

## 移植前端
将前端移植到 Arbitrum 上与部署合约一样简单。只需要在合约部署后将前端指向我们的RPC
endpoint即可。更多代码示例可见[前端集成](../开发文档/dapp基础/前端集成.md)。

## 已经部署的合约

### Protocol (L1)

|                     | Goerli                                                                                                                |
| ------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Rollup              | [0x767CfF8D8de386d7cbe91DbD39675132ba2f5967](https://goerli.etherscan.io/address/0x767CfF8D8de386d7cbe91DbD39675132ba2f5967) |
| Delayed Inbox       | [0x1FdBBcC914e84aF593884bf8e8Dd6877c29035A2](https://goerli.etherscan.io/address/0x1FdBBcC914e84aF593884bf8e8Dd6877c29035A2) |
| Sequencer Inbox     | [0xb32f4257e05C56C53D46bbEC9e85770eB52425D6](https://goerli.etherscan.io/address/0xb32f4257e05C56C53D46bbEC9e85770eB52425D6) |
| Bridge              | [0x9903A892Da86c1e04522d63B08e5514a921E81Df](https://goerli.etherscan.io/address/0x9903A892Da86c1e04522d63B08e5514a921E81Df) |
| Outbox              | [0xFDF2B11347dA17326BAF30bbcd3F4b09c4719584](https://goerli.etherscan.io/address/0xFDF2B11347dA17326BAF30bbcd3F4b09c4719584) |
| OneStepProver0      | [0x91DDCCc4CccbB7609E045E10D311712789F2010f](https://goerli.etherscan.io/address/0x91DDCCc4CccbB7609E045E10D311712789F2010f) |
| OneStepProverMemory | [0x4A78961010c3A6c587077Efc0CD6BaA22c974E0a](https://goerli.etherscan.io/address/0x4A78961010c3A6c587077Efc0CD6BaA22c974E0a) |
| OneStepProverMath   | [0x8b6dBCA5A16d77333819487143Ad88653E5D2574](https://goerli.etherscan.io/address/0x8b6dBCA5A16d77333819487143Ad88653E5D2574) |
| OneStepProverHostIo | [0xB4dba7DB08fBcF1809ec4A2139d168Fa3f466868](https://goerli.etherscan.io/address/0xB4dba7DB08fBcF1809ec4A2139d168Fa3f466868) |
| OneStepProofEntry   | [0x1c6bA2a2c079Df3608961135E1cdd65d908AE23e](https://goerli.etherscan.io/address/0x1c6bA2a2c079Df3608961135E1cdd65d908AE23e) |



### 代币桥

**重要提示**: **不要**直接发送ETH或者代币到以下地址，不然可能造成资金的损失。

用户应该只能通过跟dapp用户界面进行代币桥接，类似一下网页:
[https://nitro-devnet-bridge.arbitrum.io](https://nitro-devnet-bridge.arbitrum.io).


|                       | Goerli / Nitro Devnet                                                                                                 |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| L1 Gateway Router     | [0x8BDFa67ace22cE2BFb2fFebe72f0c91CDA694d4b](https://goerli.etherscan.io/address/0x8BDFa67ace22cE2BFb2fFebe72f0c91CDA694d4b) |
| L2 Gateway Router     | [0xC502Ded1EE1d616B43F7f20Ebde83Be1A275ca3c](https://nitro-devnet-explorer.arbitrum.io/address/0xC502Ded1EE1d616B43F7f20Ebde83Be1A275ca3c)  |
| L1 ERC20 Gateway      | [0x6336C4e811b2f7D17d45b6241Fd47F2E11621Ffb](https://goerli.etherscan.io/address/0x6336C4e811b2f7D17d45b6241Fd47F2E11621Ffb) |
| L2 ERC20 Gateway      | [0xf298434ffE691400b932f4b14B436f451F4CED76](https://nitro-devnet-explorer.arbitrum.io/address/0xf298434ffE691400b932f4b14B436f451F4CED76)  |
| L1 Arb-Custom Gateway | [0x23D4e0D7Cb7AE7CF745E82262B17eb46535Ae819](https://goerli.etherscan.io/address/0x23D4e0D7Cb7AE7CF745E82262B17eb46535Ae819) |
| L2 Arb-Custom Gateway | [0x7AC493f26EF26904E52fE46C8DaEE247b9A556B8](https://nitro-devnet-explorer.arbitrum.io/address/0x7AC493f26EF26904E52fE46C8DaEE247b9A556B8)  |
| L1 Weth Gateway       | [0x64bfF696bE6a087A81936b9a2489624015381be4](https://goerli.etherscan.io/address/0x64bfF696bE6a087A81936b9a2489624015381be4) |
| L2 Weth Gateway       | [0xf10c7CAA33A3360f60053Bc1081980f62567505F](https://nitro-devnet-explorer.arbitrum.io/address/0xf10c7CAA33A3360f60053Bc1081980f62567505F)  |
| L1 Weth               | [0xB4FBF271143F4FBf7B91A5ded31805e42b2208d6](https://goerli.etherscan.io/address/0xB4FBF271143F4FBf7B91A5ded31805e42b2208d6) |
| L2 Weth               | [0x96CfA560e7332DebA750e330fb6f59E2269f40Dd](https://nitro-devnet-explorer.arbitrum.io/address/0x96CfA560e7332DebA750e330fb6f59E2269f40Dd)  |

### Arbitrum 预编译 (L2, 跟其他Aribrum链一样)

|                  | Address                                                                                                              |
| ---------------- | -------------------------------------------------------------------------------------------------------------------- |
| ArbSys           | [0x0000000000000000000000000000000000000064](https://nitro-devnet-explorer.arbitrum.io/address/0x0000000000000000000000000000000000000064) |
| ArbRetryableTx   | [0x000000000000000000000000000000000000006E](https://nitro-devnet-explorer.arbitrum.io/address/0x000000000000000000000000000000000000006E) |
| ArbGasInfo       | [0x000000000000000000000000000000000000006C](https://nitro-devnet-explorer.arbitrum.io/address/0x000000000000000000000000000000000000006C) |
| ArbAddressTable  | [0x0000000000000000000000000000000000000066](https://nitro-devnet-explorer.arbitrum.io/address/0x0000000000000000000000000000000000000066) |
| ArbStatistics    | [0x000000000000000000000000000000000000006F](https://nitro-devnet-explorer.arbitrum.io/address/0x000000000000000000000000000000000000006F) |
| NodeInterface    | [0x00000000000000000000000000000000000000C8](https://nitro-devnet-explorer.arbitrum.io/address/0x00000000000000000000000000000000000000C8) |
| ArbBLS           | [0x0000000000000000000000000000000000000067](https://nitro-devnet-explorer.arbitrum.io/address/0x0000000000000000000000000000000000000067) |
| ArbInfo          | [0x0000000000000000000000000000000000000065](https://nitro-devnet-explorer.arbitrum.io/address/0x0000000000000000000000000000000000000065) |
| ArbAggregator    | [0x000000000000000000000000000000000000006D](https://nitro-devnet-explorer.arbitrum.io/address/0x000000000000000000000000000000000000006D) |
| ArbFunctionTable | [0x0000000000000000000000000000000000000068](https://nitro-devnet-explorer.arbitrum.io/address/0x0000000000000000000000000000000000000068) |

### 杂项

|              | Nitro Devnet                                                                                                | 
| ------------ | -------------------------------------------------------------------------------------------------------------------- | 
| L2 Multicall | [0x1068dbfcc13f3a22fcAe684943AFA43cc66fA689](https://nitro-devnet-explorer.arbitrum.io/address/0x1068dbfcc13f3a22fcAe684943AFA43cc66fA689) |


← [公开测试网](./公开测试网.md) 

→ [运行节点](./运行节点.md)