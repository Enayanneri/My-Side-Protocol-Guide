# My-Side-Protocol-Guide ![icons8-финн](https://github.com/user-attachments/assets/e65f086e-c914-4f61-8716-36dee2535095)

Guide to starting a node

# Testnet
|key|value|
|:-:|:---:|
|Chain ID|grimoria-testnet-1|
|Block Explorer|https://testnet.ping.pub/side|
|Faucet|https://station-test.side.one/faucet|
|RPC|https://testnet-rpc.side.one|
|Rest|https://testnet-rest.side.one|
|gRPC|https://testnet-grpc.side.one:443|
|Persistence Nodes|6bef0693d7a31fed473b95123ad19b544b414093@202.182.119.24:26656,44f8009ed91fddd7ee51117482ede20fb4f33e78@149.28.156.79:26656|

# Install
## Hardware Req
|key|value|
|:-:|:---:|
|CPU|4 cores|
|RAM|8 GB|
|Storage|500 GB|
|Network|1 Gbps|

## Build from source code
```
git clone https://github.com/sideprotocol/side.git
cd side
git checkout v0.9.0

make install
```
The provided command will compile the sided binary and save it in your $GOBIN directory. If $GOBIN is included in your $PATH, you should be able to execute the sided binary.
```
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
```
```
sided version
```

## Add keys
```
sided keys add test --key-type="segwit"
```

## Init the Node
```
sided init <VALIDATOR_name> --chain-id=grimoria-testnet-1
```

## Download Genesis
```
wget https://raw.githubusercontent.com/sideprotocol/testnet/main/grimoria-testnet-1/genesis.json -O $HOME/.side/config/genesis.json
```

## Adding seeds
```
cd $HOME/.side/config
nano config.toml
```
```
persistent_peers = "6bef0693d7a31fed473b95123ad19b544b414093@202.182.119.24:26656,44f8009ed91fddd7ee51117482ede20fb4f33e78@149.28.156.79:26656"
```

## Setup minimum gas prices
```
# app.toml
minimum-gas-prices = "0.005uside"
```

## Start Node
```
sided start
```
