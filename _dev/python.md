---
layout: default
title: "How to interact with Python"
---
# Pywaves

The easiest way to interact with the node is currently by using Python.
The most convenient library for this is Pywaves or PyCWaves.


## How to configure my pywaves instance to connect with Turtle Network

You can select between mainnet and testnet. For mainnet we use network char L for testnet 'l'.

Below snippet shows how to properly setup pywaves for Turtle Network.

```
import pywaves as py

py.setNode('https://cluster.testnet.tnnode.turtlenetwork.eu', 'testnetTN', 'l')
py.setMatcher('https://testnet.matcher.turtlenetwork.eu')
py.DEFAULT_CURRENCY='TN'
```