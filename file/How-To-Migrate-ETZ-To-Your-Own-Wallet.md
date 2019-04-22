# How To Migrate ETZ To Your Own Wallet

* If, as a tech geeker want to make your own mobile APP ,(Android Or IOS,not Blackberry),You may need to read this post.

## Deploy your own geth nodes

* Step one ,first ,you may have your own server machine ,no matter it is an VPS from aws,or vultar, or digital ocean,or you have your own physical machine placed on a good bandwidth server house,you may need to git clone our geth nodes,then deploy geth as following:

```etherzero-geth
git clone https://github.com/etherzero-org/go-etherzero
cd go-etherzero && make
screen -dmS etherzero-geth ~/go-etherzero/build/bin/geth --rpc
```

* Then,waiting for geth sync the etherzero node data, since Unix timestamp(unit second),1531551970,etherzero geth has already generated more than 10GB data under fast sync mode.When your geth finished syncing,you need to do Step two ,also ,you may use some rpc APIS we offered used your own APP.

**http://sg.etznumberone.com:9646/**
**http://usa.etznumberone.com:9646/**
**https://sg.etznumberone.com:443/**
**https://usa.etznumberone.com:443/**
**http://etzrpc.org:80/**

### Step two, use the web3js to connect your node, the default rpc port is 9646, so you may connect your own node by http://IP:9646/ in web3js as following

```web3js
npm i -S git+https://github.com/etherzero-org/web3.js.git
var web3 = new Web3(web3_etz.givenProvider);
web3.eth.getBalance("0x407d73d8a49eeb85d32cf465507dd71d507100c1").then(console.log);
```

* Congratulation,finally you get the balance of one certain address,enjoy the surfe of web3js

* Also ,you may read about the docs of [web3js](https://github.com/etherzero-org/web3j).
