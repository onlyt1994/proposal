# Karnot AppChain (Closed)

Setup AppChain and Pull request to register

### Install dependencies <a href="#install-dependencies" id="install-dependencies"></a>

Please go [Ubuntu Dependencies](../ubuntu-dependencies.md) to install

### Initialize Madara CLI <a href="#initialize-madara-cli" id="initialize-madara-cli"></a>

#### Clone repo <a href="#clone-repo" id="clone-repo"></a>

```
git clone https://github.com/karnotxyz/madara-cli
```

#### Build <a href="#build" id="build"></a>

```
cd madara-cli
cargo build --release
```

#### Initialize a new appchain <a href="#initialize-a-new-appchain" id="initialize-a-new-appchain"></a>

```
./target/release/madara init
```

Enter your app chain name

Mode: `Sovereign`

DA layer: `Avail`

You will see the result

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

#### Restore your old AppChain <a href="#restore-your-old-appchain" id="restore-your-old-appchain"></a>

If you are new, please skip this. This section is for someone who accidentally removed vps or got error and have to reinstall vps

If you want to use your old appchain information, please update data in `~/.madara/app-chains/{your appchain name}/da-config.json`

You should change the `address` and `seed` in there corresponding to your old information

#### Faucet <a href="#faucet" id="faucet"></a>

You must have 20 point in gitcoin in order to get faucet at [Discord channel](https://discord.com/channels/1065831819154563132/1171414018028740698)

Go to [faucet-access](https://discord.com/channels/1065831819154563132/1180612223010357268) in discord to get role

When you have role to access [goldberg-faucet](https://discord.com/channels/1065831819154563132/1171414018028740698), the syntax to faucet is `/deposit` then choose the first item in **Modal** displayed then patse `your address` you have in [Register your AppChain](https://about/avail/karnot-appchain#register-your-appchain)

#### Register your AppChain <a href="#register-your-appchain" id="register-your-appchain"></a>

Before you register your AppChain, please get [faucet](https://about/avail/karnot-appchain#faucet)

Go to [register page](https://app-id-gen.vercel.app/)

* If you already have old app chain and restored at [Restore your old AppChain](https://about/avail/karnot-appchain#restore-your-old-appchain), just find your app chain by name. You will see the app chain id, replace it at `da-config.json` in `~/.madara/app-chains/{your appchain name}/da-config.json`
* If you are new, Import the appchain wallet to Pokadot{js} extension by seed phrase.
  * Click on `Detect extension` then choose the wallet you just imported.
  * Name your app chain, then click `Send tx` and wait until successful
  * Then replace app chain id at `da-config.json` in `~/.madara/app-chains/{your appchain name}/da-config.json`

#### Run your AppChain <a href="#run-your-appchain" id="run-your-appchain"></a>

You need to install `tmux` first in order to keep AppChain running

Then run session `tmux`

Run AppChain

```
./target/release/madara run
```

If you get any questions in installing progress, just press Y then enter

You should see the result in the end

<figure><img src="../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

Press `Ctrl + B` then press `D` to exit `tmux session`

#### Run explorer <a href="#run-explorer" id="run-explorer"></a>

```
./target/release/madara explorer
```

#### Check your AppChain Explorer <a href="#check-your-appchain-explorer" id="check-your-appchain-explorer"></a>

Go to the link `http://{your vps IP}:4000`

#### Create PR to register your AppChain <a href="#create-pr-to-register-your-appchain" id="create-pr-to-register-your-appchain"></a>

* Go to [Avail listing github](https://github.com/karnotxyz/avail-campaign-listing)
* Fork it

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

* Then clone it in your computer
* Create a JSON file named `{uuid}.json` in the `app_chains` folder with the syntax:

```
{
  "name": "your app chain name",
  "logo": "url of your logo",
  "rpc_url": "http://{your vps ip}:9944",
  "explorer_url": "http://{your vps ip}:4000",
  "metrics_endpoint": "http://{your vps ip}:9615/metrics",
  "id": "{uuid} that match with the name of JSON file"
}
```

* Submit github (In this step, you shoudl search on google if you do not know how to do)
* Create Pull Request on Github with titled `✨ Adding app_chain_name`
* Wait for approving (Should be in 30 seconds)
* If succesful, you will see the tag of your PR similar to

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>
