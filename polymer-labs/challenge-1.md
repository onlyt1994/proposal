# Challenge 1

Polymer provides Inter-Blockchain Community (IBC) as a feature to the Ethereum ecosystem enabling modular security and permissionless expansion of the IBC network.

For now, Polymer labs lives the dev phase that enable enthusiastic devs to contribute their work to the project

First, you need to send the packages to get verify that you know technical skills to be devs and get dev role in discord

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

#### Packages <a href="#packages" id="packages"></a>

Git

*

Nodejs v18+

* Should install node from [nvm](https://github.com/nvm-sh/nvm)

Foundry

```
curl -L https://foundry.paradigm.xyz | bash
foundryup
```

Just

* Ubuntu 22.04

```
sudo apt update
apt install just
```

* MacOs

Forge (It will be installed if you installed Foundry successfully)

#### API Keys <a href="#api-keys" id="api-keys"></a>

*
*
*

#### Faucet <a href="#faucet" id="faucet"></a>

* SepoliaETH in Optimism at least 0.1
* SepoliaETH in Base at least 0.1

### Folk the IBC app template <a href="#folk-the-ibc-app-template" id="folk-the-ibc-app-template"></a>

Go to [repo](https://github.com/open-ibc/ibc-app-solidity-template/tree/main)

Create new repo from the template without any commits in the main repo

### Installation <a href="#installation" id="installation"></a>

After you create repo based on the repo above, clone it with recurse submodules

```
git clone --recurse-submodules -j8 [your git ssh url]
```

Go to your repo folder

Install the packages

Create file environment

Open your editor then fill [your keys](https://about/polymer-labs/challenge-1#api-keys) created above

* 1: Your wallet's private key
* 2: Alchemy API Key
* 3: OP and Base blockscout API Key

### Usage <a href="#usage" id="usage"></a>

If you come here without any error, let's try to create channel and send the packages

If you get the final results like image below, you are done. Capture your results, send proof to [Polymer Labs Discord](https://discord.com/channels/839903468750635039/1213267408370794506)

PreviousPolymer LabsNextChallenge 2

Last updated 5 months ago
