# Run Node

Node will be run on Ubuntu 22.04

Before you start, please check your wallet to see you already have at least 1000 tDUSK (or you already stake DUSK on ERC20). If not, please go Faucet or Wallet

### Install ITN Dusk <a href="#install-itn-dusk" id="install-itn-dusk"></a>

```
cd
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.6/itn-installer.sh | sudo sh
```

You should see the result

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

### Export consensus key <a href="#export-consensus-key" id="export-consensus-key"></a>

```
rusk-wallet export -d /opt/dusk/conf -n consensus.keys
```

Enter your wallet password

Enter encryption password

You should remember all pwd you just set

The keys should be placed in `/opt/dusk/conf`

### Set password to environment variable <a href="#set-password-to-environment-variable" id="set-password-to-environment-variable"></a>

```
sh /opt/dusk/bin/setup_consensus_pwd.sh
```

Enter your encryption pwd you just set above

### Start your node <a href="#start-your-node" id="start-your-node"></a>

You would see nothing, it's correct

### Check log <a href="#check-log" id="check-log"></a>

#### Check accepted block if your node is synchronizing <a href="#check-accepted-block-if-your-node-is-synchronizing" id="check-accepted-block-if-your-node-is-synchronizing"></a>

```
grep "block accepted" /var/log/rusk.log
```

You would see somethings like below

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

#### For success log <a href="#for-success-log" id="for-success-log"></a>

```
tail -f /var/log/rusk.log
```

#### For error log <a href="#for-error-log" id="for-error-log"></a>

```
tail -f /var/log/rusk.err
```
