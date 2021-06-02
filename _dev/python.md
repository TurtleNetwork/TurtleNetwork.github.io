---
layout: default
title: "How to interact with Python"
---
# Pywaves

The easiest way to interact with the node is currently by using Python.
The most convenient library for this is Pywaves or PyCWaves.


## How to configure my pywaves instance to connect with Turtle Network

You can select between mainnet and testnet. For mainnet we use network char L, for testnet 'l'.

Below snippet shows how to properly setup pywaves for Turtle Network.

```
import pywaves as py

py.setNode('https://cluster.testnet.tnnode.turtlenetwork.eu', 'testnetTN', 'l')
py.setMatcher('https://testnet.matcher.turtlenetwork.eu')
py.DEFAULT_CURRENCY='TN'
```

Following snippet show how to use 2 networks at the same time, could be waves and TN, but also TN and TN-testnet

```
pw1 = pw.ParallelPyWaves()
address = pw.Address(address='3PCdNCULgjM9ZMLEt61M45qxV26ro6o48Jj',pywaves=pw1)
print(address.address)

pw2 = pw.ParallelPyWaves()
pw2.setNode("https://tnnode2.turtlenetwork.eu","TN MAINNET",'L')
address2 = pw.Address(privateKey='privatekey',pywaves=pw2)
print(" address: "+address2.address)
```

## Git repo's

[PyWaves](https://github.com/pywaves/pywaves)
[PyCWaves](https://github.com/iammortimer/PyCWaves)