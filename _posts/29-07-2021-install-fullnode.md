# Infrastructure


## Virtual currency nodes setup

### Ethereum

#### Install

``` bash
sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install ethereum
```

#### Run

```bash
/usr/bin/geth --cache 2048 --rpc --datadir "/path/to/folder"
```

### Bitcoin

#### Install

``` bash
sudo apt-add-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get install bitcoind
```

#### Run

```bash
/usr/bin/bitcoind -datadir=/path/to/folder -server -rpcallowip=127.0.0.1 -rpcuser=user -rpcpassword=password -txindex
```

### Bitcoin cash

#### Install

``` bash
curl https://download.bitcoinabc.org/0.19.0/linux/bitcoin-abc-0.19.0-x86_64-linux-gnu.tar.gz --output bitcoin-abc-0.19.0-x86_64-linux-gnu.tar.gz
tar xvzf bitcoin-abc-0.19.0-x86_64-linux-gnu.tar.gz 
```

#### Run

``` bash
/home/yves-pkstd/bitcoin-abc-0.19.0/bin/bitcoind -datadir=/venti/.bitcoincash -server -rpcallowip=127.0.0.1 -rpcuser=rpc -rpcpassword=rpc -txindex -rpcport=8335 -port=8336
```

### Litecoin

#### Install
``` bash
 curl https://download.litecoin.org/litecoin-0.16.3/linux/litecoin-0.16.3-x86_64-linux-gnu.tar.gz --output litecoin-0.16.3-x86_64-linux-gnu.tar.gz
 tar xvzf litecoin-0.16.3-x86_64-linux-gnu.tar.gz
 
```

#### Run
``` bash
./litecoind  -datadir=/venti/.litecoin -server -rpcallowip=127.0.0.1 -rpcuser=rpc -rpcpassword=rpc -txindex -rpcport=8337 -port=8338
```

### Monacoin

#### Install
``` bash
curl -L https://github.com/monacoinproject/monacoin/releases/download/monacoin-0.16.3/monacoin-0.16.3-x86_64-linux-gnu.tar.gz --output monacoin-0.16.3-x86_64-linux-gnu.tar.gz
tar xvzf monacoin-0.16.3-x86_64-linux-gnu.tar.gz
```

#### Run
``` bash
./monacoind -datadir=/venti/.monacoin -server -rpcallowip=127.0.0.1 -rpcuser=rpc -rpcpassword=rpc -txindex -rpcport=8339 -port=8340
```