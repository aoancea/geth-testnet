# geth-testnet

This is an already working private ethereum testnet

To be able to run it, follow the bellow steps:
1. install `geth` from https://geth.ethereum.org/downloads/
2. open and cmd and run `geth --datadir=.\chaindata` to start the private chain from the already created one
3. open a second cmd and attach to the running chain `geth attach ipc:\\.\pipe\geth.ipc`

# Creating your private test chain from scratch
1. install `geth` from https://geth.ethereum.org/downloads/
2. create a new folder `chaindata` - this will be the folder in which the chain data will be stored(you want it to be in a directory of your choosing)
3. create a new file `genesis.json` and fill it with the `genesis.json` found in this repository - read more about it here https://github.com/ethereum/go-ethereum/wiki/Private-network#creating-the-genesis-block
4. open a cmd and run `geth --datadir=.\chaindata init .\genesis.json` - this will create the private chain at the directory we're just created at 2.
5. in the same cmd run `geth --datadir=.\chaindata --rpc --rpccorsdomain="*" --rpcport="8545" --minerthreads="1" --mine --nodiscover --maxpeers=0 --unlock 0 console --rpcapi="eth,net,web3,personal,miner"` which will start the private chain
6. open another cmd and run `geth attach http://127.0.0.1:8545` which will attach to the current running chain

Note: You can also import your geth accounts into MetaMask by using the file stored inside the `keystore` folder and with your passphrase. The passprash for the accounts on this blockchain is `test1`

# Resources
- https://www.youtube.com/watch?v=1sskorISHic
- https://github.com/ethereum/go-ethereum/wiki/Private-network
- https://github.com/ethereum/go-ethereum/issues/15746
