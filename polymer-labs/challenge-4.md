---
description: >-
  Here is the next challenge for dev to dive into Polymer Labs with Universal
  Channel
---

# Challenge 4

Here is the next challenge for dev to dive into Polymer Labs with Universal Channel

The challenge will get you to find out to mint NFT Challenge 4

### Prepare <a href="#prepare" id="prepare"></a>

Clone the Polymer's helper source code

```
git clone https://github.com/polymerdevs/testnet-challenge-3-template.git
cd testnet-challenge-3-template
cp .env.example .env
```

Then, you need to change the keys like the challenge 1

### Doing <a href="#doing" id="doing"></a>

Run install

In `config.json` file, please change the address of Optimism portAddr to `0x691B9bB9f262f997263FBF47F968d2B08bb5a6B8`

In `Justfile`, add the script

```
run-challenge-4:
    echo "Running the challenge 4 flow..."
    just deploy base base
    just sanity-check
    just send-packet optimism
    echo "Thank you for participating in Challenge!"
    echo "Submit your evidence in the #proof channel in our Discord Server!"
```

Open your editor with the project you just cloned above, try to edit your `contracts/CCQueryUC.sol`

In function `onRecvUniversalPacket` try to write the code in side

```
recvedPackets.push(UcPacketWithChannel(channelId, packet));

(address sender, string memory query) = abi.decode(packet.appData, (address, string));

bytes memory payload = abi.encode(sender, "mint");

return AckPacket(true, payload);
```

### Just do it <a href="#just-do-it" id="just-do-it"></a>

Run the command

### Results <a href="#results" id="results"></a>

You should see somethings in the end of your command

Go the [explorer of Optimism](https://optimism-sepolia.blockscout.com/)

Check your wallet which you add secret key

Check your `Token transfer`, if you see Challenge 4 NFT with ID, you are done, please don't run the script again

### Proof <a href="#proof" id="proof"></a>

You go to [OP Sepolia Explorer](https://optimism-sepolia.blockscout.com/) to find your wallet address

Find your first tx `sendUniversalPacket` then click on it

Copy that TxHash, then go [Polymer Packet Zone](https://sepolia.polymer.zone/packets), Paste it

Click on row, you just filtered, you will see somethings like below picture, screenshot it

You go to [OP Sepolia Explorer](https://optimism-sepolia.blockscout.com/) to find your wallet address

Click on Tab Token transfer to get NFT Challenge 4 Token, then copy the url. It should be like `https://optimism-sepolia.blockscout.com/token/0x691B9bB9f262f997263FBF47F968d2B08bb5a6B8/instance/1`

Proof will go

```
Wallet: {your wallet}
QueryMint: Your full url for txhash above
NFT: your full url NFT 
```

And the screenshot you took above, send to Proof channel

### End here, Good Luck! <a href="#end-here-good-luck" id="end-here-good-luck"></a>
