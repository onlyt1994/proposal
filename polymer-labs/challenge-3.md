---
description: >-
  Here is the next challenge for dev to dive into Polymer Labs with Universal
  Channel
---

# Challenge 3

The challenge will get you to find out the secret message from Polymer Contract

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

Open your editor with the project you just cloned above, try to edit your `contracts/CCQueryUC.sol`

In function `sendUniversalPacket` try to encode the message with `crossChainQuery` then send packet through universal channel

```
bytes memory payload = abi.encode(msg.sender, "crossChainQuery");

uint64 timeoutTimestamp = uint64((block.timestamp + timeoutSeconds) * 1000000000);

IbcUniversalPacketSender(mw).sendUniversalPacket(
    channelId, IbcUtils.toBytes32(destPortAddr), payload, timeoutTimestamp
);
```

In function `onUniversalAcknowledgement` write some code to get and log `secretMessage`

```
ackPackets.push(UcAckWithChannel(channelId, packet, ack));

// decode the counter from the ack packet
(string memory _secretMessage) = abi.decode(ack.data, (string));

emit LogAcknowledgement(_secretMessage);
```

### Just do it <a href="#just-do-it" id="just-do-it"></a>

Run the command

### Results <a href="#results" id="results"></a>

You should see somethings in the end of your command

Go server discord and show your proof

### Proof <a href="#proof" id="proof"></a>

It will be in the tempalte

```
Wallet: (Your wallet address here)
Contract: (Find the title in console log "PACKET IS ACKNOWLEDGED", show the txHash url)
```

You also will need to send 2 images:

* Go [Packet Zone](https://sepolia.polymer.zone/packets): Paste your "PACKET HAS BEEN SENT" Txhash to here, then click the row then take a screenshot
* Use the url contract above: go to `Logs` tab and take a screenshot

### End here, Good Luck! <a href="#end-here-good-luck" id="end-here-good-luck"></a>
