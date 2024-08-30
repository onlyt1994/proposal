# Wallet

You are able to use either Wallet UI Web or wallet-cli

### Wallet UI Web <a href="#wallet-ui-web" id="wallet-ui-web"></a>

*
* Create new wallet
* Save your seed phrase

### Wallet CLI <a href="#wallet-cli" id="wallet-cli"></a>

* SSH to your VPS
* Install dependencies

```
sudo apt install git-all -y
git --version
```

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"
rustc --version
```

Install Ubuntu required system

```
sudo apt update -y
sudo apt upgrade -y
sudo apt install build-essential -y
sudo apt install pkg-config -y
sudo apt install libssl-dev -y
sudo apt install clang -y
sudo apt install protobuf-compiler -y
```

* Install Dusk wallet

```
git clone https://github.com/dusk-network/wallet-cli.git
cd wallet-cli
make install
```

* If you get here with no error, you done installing wallet cli

### Wallet CLI Usage <a href="#wallet-cli-usage" id="wallet-cli-usage"></a>

#### Create new wallet <a href="#create-new-wallet" id="create-new-wallet"></a>

#### Restore wallet if you already have <a href="#restore-wallet-if-you-already-have" id="restore-wallet-if-you-already-have"></a>

#### Check Balance <a href="#check-balance" id="check-balance"></a>

#### Get address <a href="#get-address" id="get-address"></a>

PreviousDUSKNextFaucet

