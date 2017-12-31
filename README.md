# dapp-voting

How to run this project

1. Run npm install ethereumjs-testrpc web3@0.20.1 to start test blockchain (Check npm & node version)
> npm install ethereumjs-testrpc web3@0.20.1
(After the testrpc installation, run testrpc for creating 10 accounts and open up new terminal tab to continue)
2. Checkout Voting.sol file
3. To compile the solidity code, install solc module
> npm install solc
4. Open up node console by running node in your terminal
5. Write all code snippets below in your terminal
> Web3 = require('web3')

> web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"));
6. Let web3 object to initialize the blockchain and query all the accounts
> web3.eth.accounts
7. Let compiler load the code to compile the contract
> code = fs.readFileSync('Voting.sol').toString()

> solc = require('solc')

> compiledCode = solc.compile(code)
8. Lets deploy the contract
> abiDefinition = JSON.parse(compiledCode.contracts[':Voting'].interface)

> VotingContract = web3.eth.contract(abiDefinition)

> byteCode = compiledCode.contracts[':Voting'].bytecode

> deployedContract = VotingContract.new(['Rama','Nick','Jose'],{data: byteCode, from: web3.eth.accounts[0], gas: 4700000})

> deployedContract.address

> contractInstance = VotingContract.at(deployedContract.address)
9. Checkout index.html and index.js files
10. Go to index.js file, follow the line 4 instruction
11. Open up new terminal tap to continue
12. Install geth and syn the blockchain
> brew tap ethereum/ethereum

> brew install ethereum
13. Run following command to check either geth installed successfuly or not
> geth
14. Install truffle Framwork
> npm install -g truffle
15. Set up the truffle project
> truffle unbox webpack
16. Copy over Voting.sol to contracts directory
17. Replace all the contents of 2_deploy_contracts.js in the migrations directory with the followings
var Voting = artifacts.require("./Voting.sol");
module.exports = function(deployer) {
  deployer.deploy(Voting, ['Rama', 'Nick', 'Jose'], {gas: 6700000});
};
18. Add gas in truffle.js
require('babel-register')
module.exports = {
  networks: {
    development: {
      host: 'localhost',
      port: 8545,
      network_id: '*',
      gas: 470000
    }
  }
}
19. Checkout replaced contents of app/javascripts/app.js
20. Checkout replaced contents of app/index.html
21. Change the port to :8545 in truffle.js
22. Depoly the contrac to Ropsten test network
> truffle console

truffle(default)> web3.personal.newAccount('verystrongpassword')
'{You will get your own address}'

truffle(default)> web3.eth.getBalance('Your own address')
{ [String: '0'] s: 1, e: 0, c: [ 0 ] }

truffle(default)> web3.personal.unlockAccount('Your own address', 'verystrongpassword', 15000)

23. Migration
> truffle migrate

24. Open up new terminal
> npm run dev

25. Go to http://localhost:8080/









