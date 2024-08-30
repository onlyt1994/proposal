# Ubuntu Dependencies

Almost Node would need to install and upgrade the dependencies in order to setup the environment

### Git <a href="#git" id="git"></a>

```
sudo apt install git-all
git --version
```

You should see the last line similar to `git version x.x.x`

### Rust <a href="#rust" id="rust"></a>

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
rustc --version
```

You should see the last line similar to `rustc x.x.x (...)`

### Docker <a href="#docker" id="docker"></a>

Install

```
# Add Docker's official GPG key:
sudo apt update -y
sudo apt install apt-transport-https ca-certificates curl software-properties-common
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update -y
apt-cache policy docker-ce
sudo apt install docker-ce
```

Docker without sudo

```
sudo usermod -aG docker ${USER}
su - ${USER}
groups
```

### Docker Compose <a href="#docker-compose" id="docker-compose"></a>

Install

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

### Ubuntu Dependencies <a href="#ubuntu-dependencies" id="ubuntu-dependencies"></a>

```
sudo apt update
sudo apt upgrade
sudo apt install build-essential

sudo apt install pkg-config
sudo apt install libssl-dev
sudo apt install clang
sudo apt install protobuf-compiler
```

[PreviousMy Name is](broken-reference)[NextSECURE YOUR RPC](broken-reference)

