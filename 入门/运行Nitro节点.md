# 为Aribrum Goerli 开发网运行完整的 Nitro 节点

### 构件要求

- 最新的Docker镜像: offchainlabs/nitro-node:v2.0.0-alpha.2

### 参数要求

- `--l1.url=<Layer 1 Ethereum RPC URL>`
  - 必须提供标准的以太坊 RPC 节点

### 重要端口

- RPC: `8547`
- WebSocket: `8548`
- Sequencer Feed: `9642`

### 所有组合在一起

- 在运行docker镜像时，数据库应挂载到外部磁盘，以便在重启时能永久保存数据。 这个挂载点是`/home/user/.arbitrum/goerli`。
- 以下是如何运行 goerli Nitro 节点的示例：
  ```
    docker run --rm -it  -v /some/local/dir/arbitrum-goerli/:/home/user/.arbitrum/goerli -p 0.0.0.0:8547:8547 -p 0.0.0.0:8548:8548 offchainlabs/nitro-node:v2.0.0-alpha.2 --l1.url https://l1-goerli-node:8545  
  ```
  需要注意的是，如果你在本地主机运行L1节点，你可能需要在 docker run 后面加上 network host参数，以使用docker托管的网络。

### 权限说明

- Docker 镜像默认配置是以非 root 权限 UID 1000运行。这意味着如果你在 Linux 或 Mac OSX 上运行 docker 镜像时遇到权限错误，请输入如下命令以允许所有用户更新持久文件夹。
  ```
  mkdir /some/local/dir/arbitrum-goerli
  chmod -fR 777 /some/local/dir/arbitrum-goerli
  ```
  ```
  mkdir /some/local/dir/arbitrum-rinkeby
  chmod -fR 777 /some/local/dir/arbitrum-rinkeby
  ```

### 可选参数

- `--http.api`
  - 通过 HTTP-RPC 接口提供的 API（默认net,web3,eth
  - 添加`debug`以启用跟踪
  
- `--http.corsdomain`
  - 接受跨域请求的域用逗号分隔列表（浏览器强制要求）
  
- `--http.vhosts`
  - 接受请求的虚拟主机名用逗号分隔列表（服务器强制要求）。接受*通配符（默认localhost）
  
-`--node.archive`
  - 保留过去的块状态
  
- `--node.feed.input.url=<feed address>`
  - 默认为 `wss://nitro-devnet.arbitrum.io/feed`. 如果运行多个节点，你需要为每个数据中心提供一个回馈中继，请参阅下面的进一步说明。
    
- `--node.forwarding-target=<sequencer RPC>`
  - 默认为`https://nitro-devnet.arbitrum.io/rpc`
- `--node.rpc.evm-timeout`
  - 默认为5s, 超时用于eth_call（0 == 无超时）
- `--node.rpc.gas-cap`
  - 默认为50000000, 可用于计算`eth_call`/`estimateGas` Gas 的上限（0 =
    无上限）
    
- `--node.rpc.tx-fee-cap`
  - 默认为1, 可以通过 RPC API 发送的交易费用上限（以太币）（0 = 无上限）
 
 
### Arbitrum 中继

- 当运行多个节点时，你希望运行一个 Arbitrum 中继并为所有节点提供回馈。Arbitrum 中继位于同一个 docker 镜像中。
  
- 以下是如何为 goerli 运行 nitro 中继的示例:
  ```
    docker run --rm -it  -p 0.0.0.0:9642:9642 --entrypoint relay offchainlabs/nitro-node:v2.0.0-alpha.2 --node.feed.input.url wss://nitro-devnet.arbitrum.io/feed
  ```
- 以下是如何使用自定义中继为 goerly 运行 nitro 节点示例：
  ```
    docker run --rm -it  -p 0.0.0.0:8547:8547 -p 0.0.0.0:8548:8548 offchainlabs/nitro-node:v2.0.0-alpha.2 --l1.url https://l1-goeri-node:8545 --feed.input.url ws://local-relay-address:9642
  ```

   ← [运行节点](./运行节点.md) 
   
   → [安装](./安装.md)