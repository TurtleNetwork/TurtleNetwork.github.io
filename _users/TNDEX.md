---
layout: default
title: "TNDex"
---
## TN-Dex

General info about wallet.turtlenetwork.eu

### What is a Turtle Network address and where to find my address?

A Turtle Network mainnet address always starts with 3Jxxxxx.
A user can find it in the right upper corner from the client.

![tnAddy](https://user-images.githubusercontent.com/16037736/115995003-bd754e80-a5d9-11eb-95a8-25c63105ba1f.png)

### What trading fees are supported?

Currently trades can be paid in 3 assets:
- BTC
- WAVES
- TN

### How to change fees?

In the trade box there is a small dropdown behind the default 0.04TN fee.
This dropdown shows BTC/WAVES depending if a user has the assets available.

![dropdownFees](https://user-images.githubusercontent.com/16037736/115995012-cc5c0100-a5d9-11eb-87ee-44ab096c49b0.png)

### Is Ledger currently supported?

No currently it's not possible to use any hardware wallet.

### What do inactive pairs mean?

It means that the pair didn't had volume for the past 24 hours. However the market might be active and there might be juicy offers.

### Can I recover my account when I lost my seed?

No this is not possible. TNDex is like the name says a DEX. This means you and only you can access your account with the seed.
This also means you need to keep the seed safely stored offline.


### How do I get my funds in polarity.exchange or vice versa

Both polarity.echange and wallet.turtlenetwork.eu are build on top from $TN, this means they use the same seed.
This means one seed can be used for multiple wallets, but it also means to send funds to another $TN wallet, you can use the send function and use the native $TN address,
instead withdraw through a gateway.

### How does my asset get listed on wallet.turtlenetwork.eu
There are 3 options how you asset can be available on the dex:
- You create a native project on Turtle Network, as a result your asset is immediately available for any pair
- You have already a project and will create a proxy asset on Turtle Network, this means you need to build some kind of swap service.
- Get polarity.exchange to list your asset, it will make it available through Turtle Network

#### How to build a swap service
There are multiple examples available from such a service, called a gateway:

[WAVES-ERC20](https://github.com/PyWaves/Waves-ERC20-Gateway)
[TN-ERC20](https://github.com/iammortimer/TN-ERC20-Gateway)
[TN-ARRR](https://github.com/iammortimer/TN-ARRR-Gateway)
[TN-BTC](https://github.com/iammortimer/TN-BTC-Gateway)
[TN-ETH](https://github.com/iammortimer/TN-ETH-Gateway)