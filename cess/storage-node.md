# Storage Node

### OS Requirement <a href="#os-requirement" id="os-requirement"></a>

| Recommended OS           | # of CPUs | Memory | Bandwidth | Public Network IP |
| ------------------------ | --------- | ------ | --------- | ----------------- |
| Linux 64-bit Intel / AMD | ≥ 4       | ≥ 8    | ≥ 5 Mbps  | required          |

### Installation <a href="#installation" id="installation"></a>

#### Docker <a href="#docker" id="docker"></a>

```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

#### Firewall Configuration <a href="#firewall-configuration" id="firewall-configuration"></a>

#### Prepare your CESS Wallet <a href="#prepare-your-cess-wallet" id="prepare-your-cess-wallet"></a>

* **Earning Account**: Used to receive mining rewards.
* **Staking Account**: Used to pay for staking TCESS.
* **Signature Account**: Used to sign blockchain transactions. If no staking account is specified, this account will also be used to pay staking TCESS.

For this section, I recommend you to create 2 wallets. One for earning and one for staking.

#### Install Cess Client <a href="#install-cess-client" id="install-cess-client"></a>

Please go to [https://github.com/CESSProject/cess-nodeadm/tags](https://github.com/CESSProject/cess-nodeadm/tags) to check the stable version of CESS client. For now, **v0.5.3** is the stable version. I will guide you to install this version, if project update a new stable version, please change version.

**Download and install**

```
wget https://github.com/CESSProject/cess-nodeadm/archive/vx.x.x.tar.gz
tar -xvzf vx.x.x.tar.gz
cd cess-nodeadm-x.x.x/
./install.sh
```

You should see the last line is

```
Install cess nodeadm success
```

**Stop and remove current services**

If you are new, skip this.

**Change CESS to testnet**

```
sudo cess profile testnet
```

**Set up configuration**

You have some questions to answer here, please follow

```
Enter cess node mode from 'authority/storage/watcher': storage
Enter cess storage listener port (current: 15001, press enter to skip): # click enter to skip
Enter cess storage earnings account: # enter the account to earn reward, should start from "c..."
Enter cess storage signature account phrase: # enter your signature account mnemonic (12 words)
Enter cess storage disk path: # the disk path, choose your biggest folder
Enter cess storage space, by GB unit (current: 300, press enter to skip): # if your vps has 3TiB, type 3000, it means 3000 GiB
Enter the number of CPU cores used for mining; Your CPU cores are 4
  (current: 3, 0 means all cores are used; press enter to skip): 
Enter the staker\'s payment account if you have another (if it is the same as the signature account, press enter to skip): # Just press enter to skip
Enter the reserved TEE worker endpoints (separate multiple values with commas, press enter to skip): # Enter to skip
Set configurations successfully
```

You should see `Set configurations successfully` in the end of those questions

#### Start the Node <a href="#start-the-node" id="start-the-node"></a>

You should see somethings similar as

```
[+] Running 3/0
 ✔ Container chain       Running                                                0.0s
 ✔ Container bucket      Running                                                0.0s
 ✔ Container watchtower  Running                                                0.0s
```

#### Check your bucket <a href="#check-your-bucket" id="check-your-bucket"></a>

#### Check your chain <a href="#check-your-chain" id="check-your-chain"></a>

Your chain will be sync in 1 or 2 days

#### Check bucket status <a href="#check-bucket-status" id="check-bucket-status"></a>

You will see the table showing your bucket status when your chain synchronized successfully

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
