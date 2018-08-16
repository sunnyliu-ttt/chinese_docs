# TrustNote 开发文档（中文）

## 介绍 

> TrustNote 是一个DAG公链，交易速度快，交易费用低。

![](developers.png)

## 开发

### 源码级开发工具 headlessRPC

headlessRPC是一个轻节点的提供RPC服务的无界面钱包。该钱包具备钱包的一切功能，可以远程调用，但不建议远程调用。建议开发者在本地调用，如果架设在服务器上，RPC端口建议不对外开放。

headlessRPC默认端口为633

### sdk

* python

  用于服务器、PC及物联网设备。
  
  使用pythonSDK开发的例子有：
  
  投票系统：https://github.com/TrustNoteSamples/VotingSystem
  
  web本地钱包：https://github.com/TrustNoteSamples/web_wallet
  
  花盆土壤状况上链：https://github.com/TrustNoteSamples/temp-humi
  
* js

  适用于通用钱包，开发者只需构建H5页面，通过jssdk调用钱包完成转载，通过回调函数处理支付成功后的业务逻辑。可广泛用于开发各种付费应用。
  
  jssdk例子：付费阅读
  
  https://github.com/TrustNoteSamples/paid_reading
  
* [rust](/sdk/rust.md)

  用于x86架构的PC及开发板(x86架构的物联网主板)。
  
  目前支持的x86开发板有：
  1. 野火
  2. LattePand
  3. UP Squared
  4. intel Edison Breakout Board
  5. Dev-14281 SparkFun
  n. ......






