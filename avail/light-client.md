# Light Client

Finally, the Avail Light Client Challenge has officially begun. Let's hunt for NFTs of the project together.

Time: April 2, 2024 - April 9, 2024

Note: DYOR and consider before running, because this challenge costs VPS rental and only receives NFT, not sure if this NFT has any price or benefit from the project.

Ok. If you decide to join the challenge, let's get started!

### Prepare <a href="#prepare" id="prepare"></a>

* Polkadot wallet (can use PolkadotJS or SubWallet)
* A little AVL testnet. If you don't have one, faucet [here](https://faucet.avail.tools/).
* VPS or PC with permanent connection

### How <a href="#how" id="how"></a>

To participate in the challenge, you need to follow these steps

Install and run Tmux

```
sudo apt install tmux -y
tmux
```

Create script to run avail continuously even if it was down due to bugs/errors

Then copy-patse the running script of Avail

```
#!/bin/bash

# official script command of Avail
COMMAND="curl -sL1 avail.sh | bash" 

# Here is script making LC restart if getting errors
while true; do
    echo "Starting command: $COMMAND"
    # Chạy lệnh trong background
    bash -c "$COMMAND" &
    
    # Lấy ID quá trình của tiến trình vừa chạy
    PID=$!
    
    # Đợi tiến trình con hoàn thành
    wait $PID
    EXIT_STATUS=$?

    if [ $EXIT_STATUS -eq 0 ]; then
        echo "Command exited successfully. Restarting..."
    else
        echo "Command failed with status $EXIT_STATUS. Restarting..."
    fi
    # Chờ một khoảng thời gian trước khi khởi động lại, để tránh khởi động lại quá nhanh
    sleep 10
done
```

Run script

Light CLient will log a **\`random public key\`** the first time it launches. Please save this public key. It will display like this:

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

Visit: https://lightclient.availproject.org

* Connect wallet (polkadotjs or subwallet)
* Complete social tasks
* For task 4.Complete Light-client Lift-Off challenge, take the public key obtained above, paste it into the input box and submit.

<figure><img src="../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

After completing all the tasks, the system will allow you to Mint NFT

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

NFT Image should be

![](<../.gitbook/assets/image (39).png>)
