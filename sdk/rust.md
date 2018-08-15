## RUST版本的SDK

其源码位于：https://github.com/trustnote/rust-trustnote/archive/0.3.0.zip

目前编译好两种操作系统的可执行文件：

1. ubuntu

https://github.com/trustnote/rust-trustnote/releases/download/0.3.0/ubuntu_ttt.zip

2. windows

https://github.com/trustnote/rust-trustnote/releases/download/0.3.0/windows_ttt.zip


### 体验：


> 以ubuntu 系统为例子

### 获取

1. 下载

```
wget https://github.com/trustnote/rust-trustnote/releases/download/0.3.0/ubuntu_ttt.zip
```

2. 解压缩：

```
unzip ubuntu_ttt.zip
```

3. 更改其权限为可执行：

```
chmod +x ttt
```

### 配置

1. 在ttt所在的同级目录中，新建一个名为settings.json的文件，输入以下信息：

```json
{
  "hub_url": [
    "dev.trustnote.org:6616"
  ],
  "mnemonic": "select initial pet jazz alone stamp copper vault private slight rocket stock",
  "genesis_unit": "V/NuDxzT7VFa/AqfBsAZ8suG4uj3u+l0kXOLE+nP+dU=",
  "witnesses": [
      "6LDM27ELDDAJBTNTVVQQYW7MWOK3F6WD",
      "BP2NYKORMOB5SEUTFSVPF2CMSQSVEZOS",
      "C6D4XKXDO4JAUT3BR27RM3UHKYGILR3X",
      "CGCU5BBDWY2ZU3XKUXNGDTXDY7VXXJNJ",
      "E45DPZHBPI7YX3CDG7HWTWBWRNGBV6C3",
      "EPG47NW4DDKIBUFZBDVQU3KHYCCMXTDN",
      "FF6X4KX3OOAAZUYWXDAHQJIJ5HDZLSXL",
      "JVFHPXAA7FJEJU3TSTR5ETYVOXHOBR4H",
      "MWJTSFCRBCV2CVT3SCDYZW2F2N3JKPIP",
      "NJSDFSIRZT5I5YQONDNEMKXSFNJPSO6A",
      "OALYXCMDI6ODRWMY6YO6WUPL6Q5ZBAO5",
      "UABSDF77S6SU4FDAXWTYIODVODCAA22A"
  ]
}
```

2. 替换助忆词

你可以把你的助忆词放在 mnemonic 处。

其余的，都不要做任何变更。

配置完 mnemonic 后，执行sync以和hub同步。

### 同步

```
./ttt sync
```

出现类似的提示
```
refresh history done
```

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

默认钱包是没有钱的，因此可以去 http://dev.trustnote.org/getTTT 领币。

领完币后，再同步一次：

```
./ttt sync
```

然后继续查询信息：

```
./ttt info
```

需要注意的是，一定要保持sync的好习惯。


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

### rust 版本的命令行钱包还可以做哪些事情？

rust 版本的wallet可以放在服务器中，通过其他脚本如php、python、ruby、nodejs等调用这个rust的命令行钱包，可以制作基于web的多账户在线钱包。
