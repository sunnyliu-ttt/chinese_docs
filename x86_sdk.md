首先我们清空sqlite：
```cmd
$ rm trustnote_light.sqlite
```

然后与hub同步
```
$ ../ttt.exe sync

refresh history done
```

打印记录

```
$ ../ttt.exe log

#1        -1.000 MN     2018-08-14 10:09:22

#2       -30.000 MN     2018-08-14 09:41:08

#3        -2.000 MN     2018-08-13 19:28:10

#4        -1.120 MN     2018-08-13 19:22:12

#5        -1.120 MN     2018-08-13 18:38:11

#6        -3.000 MN     2018-08-13 17:40:32
```

显示第一条记录
```

$ ../ttt.exe log -v1

TO       : FNJAITGTNB2IHLXHHKPVT3LJXP6ASOOJ

UNIT     : e/Y2NIjSG0Hy7bTTRVxis7JQXjWm8E41ugRb0JYaH1Y=

AMOUNT   : -1.000 MN

DATE     : 2018-08-14 10:09:22

CONFIRMED: true


```

显示钱包信息

```
$ ../ttt.exe info

current wallet info:

device_address: 0XIN26WQCCWDVWWA4Y6QPSLCAUSIIEUHT

wallet_public_key:

xpub6DLLRkRUQaJy3uwaKXVbkY1k3xk1jh4acdBkeaiMgLDqxKmzC9JxtU43QVYsfpTT8kVS43TMWxs3sA64rhikKYS5YtroBShmHJGERGQbSk4

└──wallet_id(0): NoyA6JCWejxjBdMk4pZJVdCbZqSZ/I66KePC45ddnho=

   └──address(0/0): SDGURVRIPUZDM6OCG447IVJDU2HXBSYE
   
      ├── path: /m/44'/0'/0'/0/0
      
      ├── pubkey: AoeKAK3Urfk2FOV9/F2b4es6pVvMjIpovouuLtCxHnvi
      
      └── balance: 55.752MN

```

发送交易

```

$ ../ttt.exe send -p FNJAITGTNB2IHLXHHKPVT3LJXP6ASOOJ 0.1

spendable = 'SDGURVRIPUZDM6OCG447IVJDU2HXBSYE'

input_and_amount = InputsAndAmount { input_with_proofs: [InputWithProof { spend_proof: None, input: Some(Input { address: None, amount: None, from_main_chain_index: None, serial_number: None, message_index: Some(0), kind: None, output_index: Some(1), to_main_chain_index: None, unit: Some("EgfmXwJctPTmaWRqY9+fNC19WvWn+42YBPilm3KhnzI="), blinding: None }) }], amount: 758377 }

FROM  : SDGURVRIPUZDM6OCG447IVJDU2HXBSYE

TO    : FNJAITGTNB2IHLXHHKPVT3LJXP6ASOOJ

UNIT  : Some("aLZSwhv1iEmgP95peefFHd0mh9CinB4qBzXI66Dq0AI=")

AMOUNT: 0.1

DATE  : 1534213172183
```

同步：

```
$ ../ttt.exe sync

refresh history done
```

打印记录：

```
$ ../ttt.exe log

#1        -0.100 MN     2018-08-14 10:19:31

#2        -1.000 MN     2018-08-14 10:09:22

#3       -30.000 MN     2018-08-14 09:41:08

#4        -2.000 MN     2018-08-13 19:28:10

#5        -1.120 MN     2018-08-13 19:22:12

#6        -1.120 MN     2018-08-13 18:38:11

#7        -3.000 MN     2018-08-13 17:40:32

```

显示第一条：

```
$ ../ttt.exe log -v1

TO       : FNJAITGTNB2IHLXHHKPVT3LJXP6ASOOJ

UNIT     : aLZSwhv1iEmgP95peefFHd0mh9CinB4qBzXI66Dq0AI=

AMOUNT   : -0.100 MN

DATE     : 2018-08-14 10:19:31

CONFIRMED: false

```


帮助信息：
```
$ ../ttt.exe -h

ttt 0.1

ttt wallet command line tool

USAGE:

   ttt.exe [FLAGS] [SUBCOMMAND]

FLAGS:

    -h, --help       Prints help information
    
    -V, --version    Prints version information
    
    -v               Sets the level of verbosity
   

SUBCOMMANDS:

    help    Prints this message or the help of the given subcommand(s)
    
    info    Show the wallet info
    
    log     Show the history of this wallet account
    
    send    Pay TTT to an address
    
    sync    Sync a ttt wallet

```

如何转账？

```
$ ../ttt.exe send -h

ttt.exe-send

Pay TTT to an address

USAGE:

    ttt.exe send [OPTIONS]

FLAGS:

    -h, --help       Prints help information
    
    -V, --version    Prints version information

OPTIONS:

    -p, --pay <ADDRESS> <AMOUNT>    pay <AMOUNT> TTT to <ADDRESS>
    
    -t, --text <text>               encode a text message in the unit to send
    
```


如何显示？

```
$ ../ttt.exe log -h

ttt.exe-log

Show the history of this wallet account

USAGE:

   ttt.exe log [OPTIONS]

FLAGS:

    -h, --help       Prints help information
    
    -V, --version    Prints version information

OPTIONS:

    -v <INDEX>        show details of specified history transaction
   
```
