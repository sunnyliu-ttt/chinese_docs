## RUST版本的SDK

目前编译好两种操作系统的可执行文件：

1. ubuntu

https://github.com/trustnote/rust-trustnote/releases/download/0.3.0/ubuntu_ttt.zip

2. windows

https://github.com/trustnote/rust-trustnote/releases/download/0.3.0/windows_ttt.zip

你可以自己下载源码，编译成你目标平台的sdk。其源码位于：https://github.com/trustnote/rust-trustnote/archive/0.3.0.zip


### 说明

> 本文档以 ubuntu 系统为例子

### 获取

1. 下载

```
wget https://github.com/trustnote/rust-trustnote/releases/download/0.3.0/ubuntu_ttt.zip
```

2. 解压缩

```
unzip ubuntu_ttt.zip
```

3. 更改其权限为可执行

```
chmod +x ttt
```

### 初始化钱包

1. 初始化一个新钱包

```
./ttt init
```

2. 通过助记词导入钱包

引号中的12个单词，就是助记词。你可以把你自己的助记词导入进来。

```
./ttt init "select initial pet jazz alone stamp copper vault private slight rocket stock"
```

如果你没有助记词，你可以通过先初始化一个新钱包，然后在同级目录中打开一个名为settings.json的文件，其中关键字mnemonic的后面，就是助记词。你还可以通过 http://developers.trustnote.org/fancy-address/index.html 获得个性化的地址，生成的地址后面有该地址的助记词。

### 配置（非必须）

在ttt所在的同级目录中，有一个名为settings.json的文件，打开后样子大致如下：

```json
{
  "hub_url": [
    "dev.trustnote.org:6616"
  ],
  "mnemonic": "select initial pet jazz alone stamp copper vault private slight rocket stock"
}
```

其中，hub_url是hub的地址，mnemonic是助忆词。


1. 替换助忆词

你可以手动更换助忆词。

2. 替换hub

dev.trustnote.org:6616 是开发者用的testNet的hub。如果想切换到主链上，则需要配置 hub_url 为 bob.trustnote.org


### 查看信息

```
./ttt info
```

得到类似的信息：

```
current wallet info:

device_address: 0IKB7F3DAVIB3YHKJYWWVSBC6CSK76IE7
wallet_public_key: xpub6D9Xmp2Y9XTpZYZ5xk4cNxSQoBufvQ5SWLATBwyaSh38G6aiCrUzUGuEtMoRMPy3a3wKJ8B6obtpUvu89sBbadqah9iXLWohTZi9FWj7JML
└──wallet_id(0): UYwIQm+PIzvY5lceD6uX+yAc86LfaC3RFobSdxGfHmk=
   └──address(0/0): HU475BN5CEEPYL3WPLK5KA3FKXXN5NAD
      ├── path: /m/44'/0'/0'/0/0
      ├── pubkey: A3OTtemVlcteNZafJyXoCbE0UJ5SL74UI0cIjyJC4bCe
      └── balance: 299.999MN

```

其中address 后面，是该钱包的地址。

默认钱包是没有钱的，因此可以打开 http://dev.trustnote.org/getTTT 输入钱包地址领取测试用的TTT。

领完币后，再查询一次：

```
./ttt info
```

通常3-5秒钟，有时会1-2分钟（视网络状况）就会有结果。

### 转账

可以去 http://developers.trustnote.org/fancy-address/index.html 生成一些用来转账的测试地址

我使用了生产的 OKLGMIWBCFITVWKZF3JASA23OMZLICSH 地址作为转账的测试地址

```
./ttt send -p OKLGMIWBCFITVWKZF3JASA23OMZLICSH 9.99 -t hello
```

返回如下数据：

```
refresh history done

FROM  : HU475BN5CEEPYL3WPLK5KA3FKXXN5NAD
TO    : 
      address : OKLGMIWBCFITVWKZF3JASA23OMZLICSH, amount : 9.99
UNIT  : ly1DYqhjP/QngSCHP6t1NqumabOZQdR5bSiqzDDt7bc=
TEXT  : hello
DATE  : 2018-08-15 15:59:27.973
```

参数 -t hello 是在转账时上链一个备注信息。当然也可以去掉。即：

```
./ttt send -p OKLGMIWBCFITVWKZF3JASA23OMZLICSH 9.99
```

### 查询

1. 查询余额（包括稳定和不稳定的）
```
./ttt balance
```

2. 查询稳定的余额

```
./ttt balance -s
```

3. 查询不稳定的余额
```
./ttt balance -p
```

小知识：

> TrustNote没有账户体系，使用的是UTXO模型，因此假设转出100个TTT，很可能实际上是转的是150个TTT，然后需要有50个TTT返回，这样pending的可能就是50。这里可能比较难以理解，因为每次转多少回来多少与实际转账金额是没有规律可言的。

### rust 版本的命令行钱包还可以做哪些事情？

在不同目录运行该sdk，都会在当前目录生成 settings.json 的文件。这意味着，你可以用过python、php、或其他脚本来构建多用户的钱包系统。你可以

把该 sdk 放在服务器中，通过其他脚本如php、python、ruby、nodejs等调用这个rust的命令行钱包，提供基于web的多账户在线钱包服务。
