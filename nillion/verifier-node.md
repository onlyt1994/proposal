# Verifier Node

### Install Dependencies <a href="#install-dependencies" id="install-dependencies"></a>

#### Install Docker <a href="#install-docker" id="install-docker"></a>

```
# Add Docker's official GPG key:
sudo apt update -y
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update -y
apt-cache policy docker-ce
sudo apt install docker-ce -y
```

#### Docker without sudo <a href="#docker-without-sudo" id="docker-without-sudo"></a>

```
sudo usermod -aG docker ${USER}
su - ${USER}
groups
```

#### Docker version <a href="#docker-version" id="docker-version"></a>

`Docker version 27.1.1, build 63125853e3`

### Faucet <a href="#faucet" id="faucet"></a>

Go to: [https://faucet.testnet.nillion.com/](https://faucet.testnet.nillion.com/)

Faucet with your nillion address, remember address will start from `nillion...`

### Initialize Accuser Image <a href="#initialize-accuser-image" id="initialize-accuser-image"></a>

```
docker pull nillion/retailtoken-accuser:v1.0.0
```

#### Run Init <a href="#run-init" id="run-init"></a>

```
docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 initialise
```

You will see somethings like below

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

#### Verify On Website <a href="#verify-on-website" id="verify-on-website"></a>

*
* Connect your Nillion wallet then approve
* Log Verifier, you will see the docs open then
* Expand the fifth step
* You will need to verify your `Account ID` and `Public Key` in 2 red boxes when you run initilizing docker image above

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

#### Faucet your Accuser wallet <a href="#faucet-your-accuser-wallet" id="faucet-your-accuser-wallet"></a>

* Remember Accuser wallet is different as your Nillion wallet
*
* Faucet with your Accuser wallet which is `Account ID`

#### Check your Accuser wallet <a href="#check-your-accuser-wallet" id="check-your-accuser-wallet"></a>

Remember your address MUST have NIL token

Check token at explorer: [https://testnet.nillion.explorers.guru/](https://testnet.nillion.explorers.guru/)

### Run Accuser Node <a href="#run-accuser-node" id="run-accuser-node"></a>

YOU MUST WAIT 30-60 MINUTES TO CONTINUE WITH THE STEPS BELOW. The secret verification is designed wait for a period of time before fully registering the accuser.

```
docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 accuse --rpc-endpoint "https://testnet-nillion-rpc.lavenderfive.com" --block-start 5098767
```

When it was registered successfully, you will see somethings like

<figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

`Ctrl + C` three times to stop logs

* Check Container ID with command `docker ps`
* Find Container with Image of `Nillion` in the list then get `Container ID` in the first word of line

<figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

* Check by command `docker logs CONTAINER_ID -n 200 -f`

### Save your keys <a href="#save-your-keys" id="save-your-keys"></a>

Your keys will be in `~/nillion/accuser`

Show it by `cat ~/nillion/accuser/credentials.json`

Then must save all, if you lost, you will never access your Accuser wallet again.
