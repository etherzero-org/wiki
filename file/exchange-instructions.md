# How To run etherzero node from an exchange

```make special node for exchanges
git clone https://github.com/etherzero-org/go-etherzero
cd go-etherzero && make
nohup ~/go-etherzero/build/bin/geth --maxpeers 50 --rpc --rpcport 9645 --rpcaddr 127.0.0.1 --rpcvhosts "*" --rpccorsdomain "*" --rpccorsdomain "*" --rpcapi "db,eth,net,web3,personal"  --ws --wsport 9646 --wsorigins "*" --wsaddr 127.0.0.1 &
```

* The golang version should >= 1.10
