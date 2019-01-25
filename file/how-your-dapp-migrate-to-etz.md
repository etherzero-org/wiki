#### How Your DAPP Migrate To ETZ
* In Etherzero, use solidity, and we supply Remix ,Goetz, to help DAPP deployed in ETZ.

####  Install Goetz 
* Goetz is a Etherzero browser wallet, equivalent to metamask of Ethereum. You may find how to  install Goetz in this [link](https://github.com/etherzero-org/wiki/blob/master/file/Install-GoETZ.md).

 #### Remix 
 * Remix is ​​an open source Solidity smart contract, it has development environment for  solidity, basic compilation, deploy to a local or test network, and execution of the contract. Solidity is a smart contract language supported by ETZ.You may  deploy solidity contract on http://remix.etherzero.org. Remix as an online development environment, no need to install, you could start Remix directly in any browser. The first time when opening the website, it will take more time. It will take a while to wait patiently, and then it will open very quickly. After installing GoETZ, it will automatically get GoETZ's web3 object.

#### Instance an web3
 * Instantiating an web3 is the last step of DAPP in ETZ. If you don't use power to send high-frequency transaction related, you can follow the web3 of Ethereum. You only need to modify the provider of web3 to be an Etherzero node.
```
npm i -S git+https://github.com/etherzero-org/web3.js.git
var web3 = new Web3(web3_etz.givenProvider);
```
