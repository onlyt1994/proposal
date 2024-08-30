# Operator Node

#### Install Dependencies <a href="#install-dependencies" id="install-dependencies"></a>

**Dependencies**

```
# Update & Install Packages
sudo apt update & sudo apt upgrade -y
sudo apt install ca-certificates zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev curl git wget make jq build-essential pkg-config lsb-release libssl-dev libreadline-dev libffi-dev gcc screen unzip lz4 -y
```

**Docker and Docker compose**

```
# Install Docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
docker version

# Install Docker-Compose
VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)

curl -L "https://github.com/docker/compose/releases/download/"$VER"/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose
docker-compose --version

# Docker Permission to user
sudo groupadd docker
sudo usermod -aG docker $USER
```

**Go Language**

```
# Install Go
sudo rm -rf /usr/local/go
curl -L https://go.dev/dl/go1.22.4.linux-amd64.tar.gz | sudo tar -xzf - -C /usr/local
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile
echo 'export PATH=$PATH:$(go env GOPATH)/bin' >> $HOME/.bash_profile
source .bash_profile
go version
```

#### Install EigenLayer CLI <a href="#install-eigenlayer-cli" id="install-eigenlayer-cli"></a>

```
curl -sSfL https://raw.githubusercontent.com/layr-labs/eigenlayer-cli/master/scripts/install.sh | sh -s

export PATH=$PATH:~/bin

eigenlayer --version
```

#### Setup Chainbase AVS <a href="#setup-chainbase-avs" id="setup-chainbase-avs"></a>

```
git clone https://github.com/chainbase-labs/chainbase-avs-setup

cd chainbase-avs-setup/holesky
```

#### Install new Eigenlayer wallet <a href="#install-new-eigenlayer-wallet" id="install-new-eigenlayer-wallet"></a>

```
eigenlayer operator keys create --key-type ecdsa opr
```

* Password: Should include lowercase, uppercase, symbol, number ...
* After success, please save PK
* Then, `Ctrl+C` + `Enter` + `Enter`
* Save all data in image

#### Import old Eigenlayer wallet <a href="#import-old-eigenlayer-wallet" id="import-old-eigenlayer-wallet"></a>

```
eigenlayer operator keys import --key-type ecdsa opr {PRIVATE KEY}
```

* Replace {PRIVATE KEY} by your private key

#### Faucet Holesky ETH to wallet <a href="#faucet-holesky-eth-to-wallet" id="faucet-holesky-eth-to-wallet"></a>

#### Config and Register <a href="#config-and-register" id="config-and-register"></a>

```
eigenlayer operator config create
```

* `operator address`: Eigenlayer wallet address
* `earnings address`: Just enter
*
* `network`: choose holesky
* `signer type`: local\_keystore
* `ecdsa key path:`: /root/.eigenlayer/operator\_keys/opr.ecdsa.key.json

#### Edit metadata.json <a href="#edit-metadata.json" id="edit-metadata.json"></a>

* Go to your github => Create new repo
* Create new file `metadata.json to the repo`

```
{
  "name": "",
  "website": "",
  "description": "",
  "logo": "",
  "twitter": ""
}
```

* Logo is a must, you should upload png file to github and get its raw url and put it on `logo` object

#### Edit operator.yml <a href="#edit-operator.yml" id="edit-operator.yml"></a>

* You will see the json missing `metadata_url` data
* Put `metadata.json` 's raw data you created above, get it as image below

#### Run Holesky Eigenlayer <a href="#run-holesky-eigenlayer" id="run-holesky-eigenlayer"></a>

```
eigenlayer operator register operator.yaml
```

Enter your password you set above

Wait until you see as below

**Check Eigenlayer status**

```
eigenlayer operator status operator.yaml
```

#### Configure Chainbase AVS <a href="#configure-chainbase-avs" id="configure-chainbase-avs"></a>

**Create .env**

**Patse below**

```
# Chainbase AVS Image
MAIN_SERVICE_IMAGE=repository.chainbase.com/network/chainbase-node:testnet-v0.1.7
FLINK_TASKMANAGER_IMAGE=flink:latest
FLINK_JOBMANAGER_IMAGE=flink:latest
PROMETHEUS_IMAGE=prom/prometheus:latest

MAIN_SERVICE_NAME=chainbase-node
FLINK_TASKMANAGER_NAME=flink-taskmanager
FLINK_JOBMANAGER_NAME=flink-jobmanager
PROMETHEUS_NAME=prometheus

# FLINK CONFIG
FLINK_CONNECT_ADDRESS=flink-jobmanager
FLINK_JOBMANAGER_PORT=8081
NODE_PROMETHEUS_PORT=9091
PROMETHEUS_CONFIG_PATH=./prometheus.yml

# Chainbase AVS mounted locations
NODE_APP_PORT=8080
NODE_ECDSA_KEY_FILE=/app/operator_keys/ecdsa_key.json
NODE_LOG_DIR=/app/logs

# Node logs configs
NODE_LOG_LEVEL=debug
NODE_LOG_FORMAT=text

# Metrics specific configs
NODE_ENABLE_METRICS=true
NODE_METRICS_PORT=9092

# holesky smart contracts
AVS_CONTRACT_ADDRESS=0x5E78eFF26480A75E06cCdABe88Eb522D4D8e1C9d
AVS_DIR_CONTRACT_ADDRESS=0x055733000064333CaDDbC92763c58BF0192fFeBf

###############################################################################
####### TODO: Operators please update below values for your node ##############
###############################################################################
# TODO: Operators need to point this to a working chain rpc
NODE_CHAIN_RPC=https://rpc.ankr.com/eth_holesky
NODE_CHAIN_ID=17000

# TODO: Operators need to update this to their own paths
USER_HOME=$HOME
EIGENLAYER_HOME=${USER_HOME}/.eigenlayer
CHAINBASE_AVS_HOME=${EIGENLAYER_HOME}/chainbase/holesky

NODE_LOG_PATH_HOST=${CHAINBASE_AVS_HOME}/logs

# TODO: Operators need to update this to their own keys
NODE_ECDSA_KEY_FILE_HOST=${EIGENLAYER_HOME}/operator_keys/opr.ecdsa.key.json

# TODO: Operators need to add password to decrypt the above keys
# If you have some special characters in password, make sure to use single quotes
NODE_ECDSA_KEY_PASSWORD={PASSWORD HERE}
```

**MUST replace {PASSWORD HERE} in the last line with your password you set above**

**Edit docker-compose.yml**

```
rm -rf docker-compose.yml

nano docker-compose.yml
```

**Patse Data**

```
services:
  prometheus:
    image: ${PROMETHEUS_IMAGE}
    container_name: ${PROMETHEUS_NAME}
    env_file:
      - .env
    volumes:
      - "${PROMETHEUS_CONFIG_PATH}:/etc/prometheus/prometheus.yml"
    command: 
      - "--enable-feature=expand-external-labels"
      - "--config.file=/etc/prometheus/prometheus.yml"
    ports:
      - "9091:9090"
    networks:
      - chainbase
    restart: unless-stopped

  flink-jobmanager:
    image: ${FLINK_JOBMANAGER_IMAGE}
    container_name: ${FLINK_JOBMANAGER_NAME}
    env_file:
      - .env
    command: jobmanager
    networks:
      - chainbase
    restart: unless-stopped

  flink-taskmanager:
    image: ${FLINK_JOBMANAGER_IMAGE}
    container_name: ${FLINK_TASKMANAGER_NAME}
    env_file:
      - .env
    depends_on:
      - flink-jobmanager
    command: taskmanager
    networks:
      - chainbase
    restart: unless-stopped

  chainbase-node:
    image: ${MAIN_SERVICE_IMAGE}
    container_name: ${MAIN_SERVICE_NAME}
    command: ["run"]
    env_file:
      - .env
    ports:
      - "8080:8080"
      - "9092:9092"
    volumes:
      - "${NODE_ECDSA_KEY_FILE_HOST:-./opr.ecdsa.key.json}:${NODE_ECDSA_KEY_FILE}"
      - "${NODE_LOG_PATH_HOST}:${NODE_LOG_DIR}:rw"
    depends_on:
      - prometheus
      - flink-jobmanager
      - flink-taskmanager
    networks:
      - chainbase
    restart: unless-stopped

networks:
  chainbase:
    driver: bridge
```

**Create folder for docker**

```
source .env && mkdir -pv ${EIGENLAYER_HOME} ${CHAINBASE_AVS_HOME} ${NODE_LOG_PATH_HOST}
```

**Create execution file**

```
chmod +x ./chainbase-avs.sh
```

#### Edit **prometheus.yml** <a href="#edit-prometheus.yml" id="edit-prometheus.yml"></a>

* You will see `operator: ${YOUR_OPERATOR_NAME}`, please replace `${YOUR_OPERATOR_NAME}` with your eigenlayer address

#### Run register Chainbase AVS <a href="#run-register-chainbase-avs" id="run-register-chainbase-avs"></a>

```
./chainbase-avs.sh register
```

#### Run Chainbase AVS <a href="#run-chainbase-avs" id="run-chainbase-avs"></a>

#### Check node health <a href="#check-node-health" id="check-node-health"></a>

```
docker compose logs chainbase-node -f
```

**Check Eigenlayer operator**

```
export PATH=$PATH:~/bin

eigenlayer operator status operator.yaml
```

**Check operator by requesting**

```
# If your port is 8080
curl -i localhost:8080/eigen/node/health
```

Status code should be 200

#### Go to discord and register your node <a href="#go-to-discord-and-register-your-node" id="go-to-discord-and-register-your-node"></a>
