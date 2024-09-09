# Validator

### Install Dependencies <a href="#install-dependencies" id="install-dependencies"></a>

```
sudo apt update
sudo apt install curl git make jq build-essential gcc unzip wget lz4 aria2 pv -y
```

### Install Go Language <a href="#install-go-language" id="install-go-language"></a>

```
cd $HOME && \
ver="1.22.0" && \
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz" && \
sudo rm -rf /usr/local/go && \
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz" && \
rm "go$ver.linux-amd64.tar.gz" && \
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> ~/.bash_profile && \
source ~/.bash_profile && \
go version
```

### Install Story Geth <a href="#install-story-geth" id="install-story-geth"></a>

```
wget https://story-geth-binaries.s3.us-west-1.amazonaws.com/geth-public/geth-linux-amd64-0.9.2-ea9f0d2.tar.gz
tar -xvf geth-linux-amd64-0.9.2-ea9f0d2.tar.gz
cp geth-linux-amd64-0.9.2-ea9f0d2.tar.gz/geth /usr/local/bin/
```

### Install Story <a href="#install-story" id="install-story"></a>

```
wget https://story-geth-binaries.s3.us-west-1.amazonaws.com/story-public/story-linux-amd64-0.9.11-2a25df1.tar.gz
tar -xvf story-linux-amd64-0.9.11-2a25df1.tar.gz
cp story-linux-amd64-0.9.11-2a25df1.tar.gz/story /usr/local/bin/
```

### Install tmux <a href="#install-tmux" id="install-tmux"></a>

### Init Node <a href="#init-node" id="init-node"></a>

#### Init Geth <a href="#init-geth" id="init-geth"></a>

```
tmux
geth --iliad --syncmode full
```

* Detach the session by `Ctrl+B` following by D

#### Init Story <a href="#init-story" id="init-story"></a>

```
tmux
story init  --network iliad --moniker {NAME}
```

### Sync Node by snapshot <a href="#sync-node-by-snapshot" id="sync-node-by-snapshot"></a>

In this section, thanks to `Joseph Tran`, you can refer [here](https://service.josephtran.xyz/testnet/story/installation#download-story-binary)

#### Download Snapshot Geth <a href="#download-snapshot-geth" id="download-snapshot-geth"></a>

```
cd $HOME
if curl -s --head https://vps5.josephtran.xyz/Story/Geth_snapshot.lz4 | head -n 1 | grep "200" > /dev/null; then
    echo "Snapshot found, downloading..."
    aria2c -x 16 -s 16 https://vps5.josephtran.xyz/Story/Geth_snapshot.lz4 -o Geth_snapshot.lz4
else
    echo "No snapshot found."
fi
```

#### Download Snapshot Story <a href="#download-snapshot-story" id="download-snapshot-story"></a>

```
cd $HOME
if curl -s --head https://vps5.josephtran.xyz/Story/Story_snapshot.lz4 | head -n 1 | grep "200" > /dev/null; then
    echo "Snapshot found, downloading..."
    aria2c -x 16 -s 16 https://vps5.josephtran.xyz/Story/Story_snapshot.lz4 -o Story_snapshot.lz4
else
    echo "No snapshot found."
fi
```

#### Stop Geth and Story Node <a href="#stop-geth-and-story-node" id="stop-geth-and-story-node"></a>

```
tmux ls
tmux a -t {id}
Ctrl+C
```

Remember must stop both nodes

#### Remove old data <a href="#remove-old-data" id="remove-old-data"></a>

```
rm -rf ~/.story/story/data
rm -rf ~/.story/geth/iliad/geth/chaindata
```

Add snapshot Geth

```
sudo mkdir -p /root/.story/geth/iliad/geth/chaindata
lz4 -d Geth_snapshot.lz4 | pv | sudo tar xv -C /root/.story/geth/iliad/geth/
```

#### Add snapshot Story <a href="#add-snapshot-story" id="add-snapshot-story"></a>

```
sudo mkdir -p /root/.story/story/data
lz4 -d Story_snapshot.lz4 | pv | sudo tar xv -C /root/.story/story/
```

#### Rerun the nodes <a href="#rerun-the-nodes" id="rerun-the-nodes"></a>

Then run each node by command [above](https://about/story/validator#init-node)
