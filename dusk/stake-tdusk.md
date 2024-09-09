# Stake tDUSK

Note: If you have not done any steps above, please go to the first topic [Wallet](wallet.md)

### Stake tDUSK <a href="#stake-tdusk" id="stake-tdusk"></a>

```
rusk-wallet stake --amt 1000 # Or at least 1000, however much you want to stake
```

You should see the result below

![](https://docs.daningyn.xyz/\~gitbook/image?url=https%3A%2F%2F3757123888-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252Ff9qd7vpO0PsmY4EQvGgS%252Fuploads%252F6MWfeG1KUBe12zYhNqva%252FScreenshot%25202024-02-16%2520at%252012.17.32.png%3Falt%3Dmedia%26token%3D1413b935-64d8-497c-b21c-57ec299cbd64\&width=768\&dpr=4\&quality=100\&sign=3b632b72\&sv=1)

### Check stake information <a href="#check-stake-information" id="check-stake-information"></a>

```
rusk-wallet stake-info
```

Check your node is participating in consensus and creating blocks when **it finished sync**

```
grep "execute_state_transition" /var/log/rusk.log | tail -n 5
```

