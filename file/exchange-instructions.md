# How To Run Etherzero Node For An Exchange

```make special node for exchanges
git clone https://github.com/etherzero-org/go-etherzero
cd go-etherzero && make
nohup ~/go-etherzero/build/bin/geth --maxpeers 50 --rpc --rpcport 9645 --rpcaddr 127.0.0.1 --rpcvhosts "*" --rpccorsdomain "*" --rpccorsdomain "*" --rpcapi "db,eth,net,web3,personal"  --ws --wsport 9646 --wsorigins "*" --wsaddr 127.0.0.1 &
```

> The golang version should >= 1.10.

> The ```--rpcaddr 127.0.0.1 ``` and ``` --wsaddr 127.0.0.1 ```,allow you use this rpc and ws in this geth node only,when you want to use the geth node from other nodes, you may use ```--rpcaddr 0.0.0.0 ``` and  ``` --wsaddr 0.0.0.0 ``` and then  set the IP access limitations . 

> As Etherzero is instant payments, for your assets' safety, we recommand strongly that you may set your confirmations by 120 blocks.
