# Worker Node

I will guide you setup worker node predicting all topics

#### Install Dependencies <a href="#install-dependencies" id="install-dependencies"></a>

If you already installed docker, docker-compose, go lang and some common libs, skip this section

```
curl -H 'Cache-Control: no-cache' https://raw.githubusercontent.com/daningyn/Nodes/main/Allora/install-requirement.sh | bash
```

#### Install Worker Node <a href="#install-worker-node" id="install-worker-node"></a>

```
curl -H 'Cache-Control: no-cache' https://raw.githubusercontent.com/daningyn/Nodes/main/Allora/install-top246-24h.sh > install-hugging-face-worker.sh && chmod +x install-hugging-face-worker.sh && ./install-hugging-face-worker.sh {YOUR NAME}
```

* At the last of line, you must replace {YOUR NAME} by your username

Follow the instruction of script

**Faucet your wallet**

Faucet at: [https://faucet.testnet-1.testnet.allora.network/](https://faucet.testnet-1.testnet.allora.network/)

Check your balance: [https://explorer.testnet-1.testnet.allora.network/allora-testnet-1/account/{](https://explorer.testnet-1.testnet.allora.network/allora-testnet-1/account/allo15cjyc87eu7wdrcy4je2k8kkjdmfcq586q5y76e)allora wallet}

**Setup Model**

```
cd allora-huggingface-walkthrough/
mkdir -p ./worker-data
chmod +x init.config
```

**Run Worker**

```
docker compose up --build -d
```

**Check Logs**

Remember that you need to cd to the huggingface folder first `cd allora-huggingface-walkthrough/`

```
docker compose logs -f -n 50
```

#### Check Points <a href="#check-points" id="check-points"></a>

**Check Worker's transactions**

Link: [http://worker-tx.nodium.xyz/](http://worker-tx.nodium.xyz/)

**Check Worker's points**

Link: [https://app.allora.network/points/leaderboard](https://app.allora.network/points/leaderboard)

[PreviousAllora](broken-reference)[NextChainBase](broken-reference)

