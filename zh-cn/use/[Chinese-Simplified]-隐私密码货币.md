
### 6. 隐私密码货币

隐私密码货币需要货币发行者在线下预先生成公私钥对，并将公钥和发行代币总量的密文写入合约中

```shell
# generate zk proof
./nizkpail
cmd> 1
```



部署代币合约

```shell
ctool deploy --code /home/wxuser/temp/PlatONE-Workspace/chain/PlatONE_linux/conf/contracts/token.wasm --abi /home/wxuser/temp/PlatONE-Workspace/chain/PlatONE_linux/conf/contracts/token.cpp.abi.json --config ../config.json


ctool invoke --addr "0x0000000000000000000000000000000000000011" --func 'cnsRegister' --param "token" --param "1.0.0.0" --param "0x03925d0a4a97f40b3023ce5a83217e3b72693b89"  --abi /home/wxuser/temp/PlatONE-Workspace/chain/PlatONE_linux/conf/contracts/cnsManager.cpp.abi.json --config ../config.json 


```




+ 转账

  转账需要发送者在线下生成零知识证明，并将该证明作为交易的输入参数，以便系统中的节点进行验证。

```shell
# generate zk proof
./nizkpail
cmd> 6

#invoke transfer function

ctool invoke --addr 0x47a9d57158a9aea543b39a4076f29b79affa76fc --func transfer --param ${pai} --param ${fromAmountCipher} --param ${toAmountCipher} --param 0x6ad59206c82cfb9e0a8f2b6cdc876a8f684421db --abi /home/wxuser/temp/PlatONE-Workspace/chain/PlatONE_linux/conf/contracts/token.cpp.abi.json --config ../ctool.json
```



+ 查询用户余额

```shell
ctool cnsInvoke --cns "token" --func 'getBalance("0xd2df1004e5b695da27a50dcd61c59fceaf128453")'  --abi /home/wxuser/temp/PlatONE-Workspace/chain/PlatONE_linux/conf/contracts/token.cpp.abi.json --config ../config.json
```
 