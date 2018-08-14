# Getting Started with the TTT Wallet iOS SDK
---

* [Before you start](#start)
* [Install](#ImportProject)
* [Api Details](#apiDetails)

### <a name="start">Before You Start</a>
TTT wallet is Fast, Light, Sweet crypto wallet, We recommend below document to understand the basic idea of TTT wallet
- [TrustNote White Paper](https://github.com/trustnote/document)
- [Bip39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)
- [Bip44](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki)
- [Bip32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki)


### <a name="ImportProject">Install</a>  

Integrating the SDK into your project manually

* [Download the latest SDK](https://github.com/TrustNoteDevelopers/iOS_sdk/raw/master/ttt_wallet_sdk_v0.1.zip)
* Extract the ttt_wallet_sdk_v**.zip package from the zip file
* Copy the `WalletSDK.framework` and `WalletSDK.bundle` to module's libs folder
* `import WalletSDK` module in your project.

### <a name="apiDetails">API Details</a>  

> TTTWalletSDK summary

```
/**
* SDK entry point, include all api method.
* 1. Api method must be called from non UI thread.
* 2. Simulator is not supported.
*/
public class WalletApi

```


> createMnemonic

```
/**
* @method  generate random bip39 mnemonic
* @param   void
* @return  string with 12 words, separated by space.
* @Ref: https://github.com/bitcoin/bips/blob/master/bip-0039/bip-0039-wordlists.md
*/
static open createMnemonic() -> String
```

> createPrivateKey

```
/**
* @method  generate private key from mnemonic
* @param   mnemonic
* @return  private key
*/
static open createPrivateKey(String mnemonic) -> String
```

> createWallet

```
/**
* @method  create wallet with private key
* @param   seed or pri-key
* @return  wallet pub-key
*/
static open createWallet(String privkey) -> String
```

> createPublickey

```
/**
* @method  create a pub-key from wallet pub-key
* @param   walletPubkey
* @return  pub-key
*/
static open createPublickey(String walletPubkey) -> String
```

> createAddress

```
/**
* @method  create an address from wallet pub-key
* @param   walletPubkey
* @return  address
*/
static open createAddress(String walletPubkey) -> String
```

> isValidAddress

```
/**
* @method  check address is valid TTT address
* @param   address
* @return  boolean
*/
static open isValidAddress(String address) -> Bool
```

> sign

```
/**
* @method  sign unit hash with pri-key
* @param
* @return  signature
*/
static open sign(String priKey, String unitHash) -> String
```

> verify

```
/**
* @method  verify the signature
* @param
* @return  boolean -- true: signature is ok, otherwise false.
*/
static open verify(String publicKey, String signature, String unitHash) -> Bool
```

