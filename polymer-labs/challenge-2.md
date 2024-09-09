---
description: >-
  Here is the next challenge for dev to dive into Polymer Labs with Universal
  Channel
---

# Challenge 2

If you haven't finish the first phase, come to Challenge 1. This section is the following phase

You need to pull the newest source from [Github](https://github.com/open-ibc/ibc-app-solidity-template/tree/main)

### Let's send package by op-client through UC <a href="#lets-send-package-by-op-client-through-uc" id="lets-send-package-by-op-client-through-uc"></a>

First, in the first phase, you were using `sim-client` to create channel then send package through Polymer infrastructure.

Now, you need to change client to `op-client` which is more secured with proofs

Set UC contracts in config project

```
just set-contracts optimism XCounterUC true && just set-contracts base XCounterUC true
```

Deploy contracts

```
just deploy optimism base
```

Sanity check to verify that configuration files match with your deployed contracts

If you get here with no error, you are in set. Let's send the package using `op-client` though `Universal channel`

```
just send-packet optimism
```

The result should be below: `channel-16` and `channel-17`

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Check your package with TxHash with [Polymer zone](https://sepolia.polymer.zone/packets)

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
