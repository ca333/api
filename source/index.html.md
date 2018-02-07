---
title: barterDEX API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell #  - ruby - python - javascript - c - cpp - go - http


toc_footers:
  - <a href='#'>Get in touch with us if you have any questions!</a>
  - <a href='https://komodoplatform.com/developers'>Komodo Developers</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the barterDEX API documentation! This documentation includes the API reference for the Komodo Platform decentralized exchange
barterDEX (marketmaker). You can use this API to access the barterDEX network and trade hundreds of different coins in a decentralized
and blockchainbased way.

We have language bindings for almost all script and programming languages since we are using an abstract JSON-RPC interface for komodod and barterDEX! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


## Getting started

### Installation

Install all required dependencies to build the barterDEX client "marketmaker".
After updating and successful installation clone the barterDEX sourcecodes from
github and run the marketmaker makefile in the shell.

> To build the barterDEX client "marketmaker", use this commands:

```shell
# update
sudo apt-get update && sudo apt-get upgrade
# install dependencies
sudo apt-get install git libcurl4-openssl-dev build-essential libnanomsg-dev
# clone repository
git clone https://github.com/jl777/supernet
cd supernet/iguana
# build marketmaker for linux
./m_mm
# build marketmaker for OSX
./m_mm_osx
```

> The barerDEX binary "marketmaker" is compiled into the iguana folder.


### barterDEX scripts "dexscripts" (optional)

The following steps are not mandatory.
After building the barterDEX client "marketmaker" you can launch it up
with the required parameters and start using it. But in addition it is possible
to install the barterDEX scripts "dexscripts" into the folder `dexscripts`.
This set of scripts contains the most needed barterDEX API calls for easy and
quick shell usage.

> To install the optional barterDEX scripts use this commands:

```shell
# install the dexscripts
cd exchanges && ./install
cd ../dexscripts
```

> The installed set of scripts contains various API call examples.


# Running the barterDEX client

Run the `client` script after storing the eviroment variable `passphrase` into
a `passphrase` file inside the `dexcripts` directory.
The file contains:
  `export passphrase=YOUR_SECURE_PASSPHRASE`

<aside class="notice">
You must replace <code>YOUR_SECURE_PASSPHRASE</code> with your personal seed/passphrase!
</aside>

The optional parameters `netid` and `seednode` will allow you to connect to various parallel
barterDEX networks.

If you are running the barterDEX client "marketmaker" for the first time you only have to set the
passphrase.


> The client startup script is in the dexscripts folder.

```shell
# start the client up
./client
```
> Your marketmaker client is running now

Instead of starting the barterDEX client via script you can also do it one level lower and
directly start the marketmaker binary with the appropriate parameters.

> Start the marketmaker with the needed parameters

```shell
# start the marketmaker up manually
./marketmaker "{\"gui\":\"nogui\",\"client\":1, \"userhome\":\"/${HOME#"/"}\", \"passphrase\":\"$passphrase\", \"coins\":$coins}" &
```
> Your marketmaker client is running now

You will now see the barterDEX client "marketmaker" starting up. After successful launch issue any rpc call to fire up the keypairs and netconns.

# Authentication

Due to security reasons the barterDEX client will start with a default hardcoded passphrase resulting
in the static userpass `1d8b27b21efabcd96571cd56f91a40fb9aa4cc623d273c63bf9223dc6f8cd81f` after the first call has been issued.
Use this userpass to set your desired passphrase/seed which will result in your base58 pubkeys (your smartaddresses).

For this purpose issue the `passphrase` call to set your own passphrase which generates your desired keypair.

> Start the marketmaker with the needed parameters

```shell
# issue the passphrase call and json-format it
curl --url "http://127.0.0.1:7783" --data "{\"method\":\"passphrase\",\"userpass\":\"1d8b27b21efabcd96571cd56f91a40fb9aa4cc623d273c63bf9223dc6f8cd81f\",\"passphrase\":\"YOUR_SECURE_PASSPHRASE\",\"gui\":\"beerDEX\"}" | python -m json.tool```

> Your marketmaker client uses the seed generated keypairs now


> The above command returns a JSON structured like below:

```json
{
    "BTC": "1QHdoNayTfjuYPrg2XUePKM2D5Wqbh5pnz",
    "KMD": "RYZpstUG4VYUcQDsVhTmUqgDyLySKznuLW",
    "NXT": "NXT-QKF4-5SCD-JRAJ-CGE4F",
    "coins": [
        {
            "KMDvalue": 0,
            "balance": 0,
            "coin": "BTC",
            "height": 0,
            "installed": true,
            "p2shtype": 5,
            "pubtype": 0,
            "rpc": "127.0.0.1:8332",
            "smartaddress": "1QHdoNayTfjuYPrg2XUePKM2D5Wqbh5pnz",
            "status": "inactive",
            "txfee": 18446744048109551616,
            "wiftype": 128
        },
        {
            "KMDvalue": 0,
            "balance": 0,
            "coin": "KMD",
            "height": 0,
            "installed": true,
            "p2shtype": 85,
            "pubtype": 60,
            "rpc": "127.0.0.1:7771",
            "smartaddress": "RYZpstUG4VYUcQDsVhTmUqgDyLySKznuLW",
            "status": "inactive",
            "txfee": 1000,
            "wiftype": 188,
            "zcredits": 0,
            "zdebits": {
                "pendingswaps": 0,
                "swaps": []
            }
        },
        {
            "balance": 0,
            "coin": "PIZZA",
            "height": -1,
            "installed": false,
            "p2shtype": 85,
            "pubtype": 60,
            "rpc": "127.0.0.1:11116",
            "smartaddress": "RYZpstUG4VYUcQDsVhTmUqgDyLySKznuLW",
            "status": "inactive",
            "txfee": 1000,
            "wiftype": 188
        },
        {
            "balance": 0,
            "coin": "BEER",
            "height": -1,
            "installed": false,
            "p2shtype": 85,
            "pubtype": 60,
            "rpc": "127.0.0.1:8923",
            "smartaddress": "RYZpstUG4VYUcQDsVhTmUqgDyLySKznuLW",
            "status": "inactive",
            "txfee": 1000,
            "wiftype": 188
        },
        {
            "balance": 0,
            "coin": "BTCH",
            "height": -1,
            "installed": false,
            "p2shtype": 85,
            "pubtype": 60,
            "rpc": "127.0.0.1:8800",
            "smartaddress": "RYZpstUG4VYUcQDsVhTmUqgDyLySKznuLW",
            "status": "inactive",
            "txfee": 1000,
            "wiftype": 188
        },
        {
            "balance": 0,
            "coin": "ETOMIC",
            "height": -1,
            "installed": false,
            "p2shtype": 85,
            "pubtype": 60,
            "rpc": "127.0.0.1:10271",
            "smartaddress": "RYZpstUG4VYUcQDsVhTmUqgDyLySKznuLW",
            "status": "inactive",
            "txfee": 1000,
            "wiftype": 188
        },
        {
            "balance": 0,
            "coin": "QTUM",
            "height": -1,
            "installed": false,
            "p2shtype": 50,
            "pubtype": 58,
            "rpc": "127.0.0.1:3889",
            "smartaddress": "Qjtcufsge8ciyXwhSro8Wb8eiLTYtbJR93",
            "status": "inactive",
            "txfee": 400000,
            "wiftype": 128
        },
        {
            "balance": 0,
            "coin": "KV",
            "height": -1,
            "installed": false,
            "p2shtype": 85,
            "pubtype": 60,
            "rpc": "127.0.0.1:8299",
            "smartaddress": "RYZpstUG4VYUcQDsVhTmUqgDyLySKznuLW",
            "status": "inactive",
            "txfee": 1000,
            "wiftype": 188
        },
        {
            "balance": 0,
            "coin": "CEAL",
            "height": -1,
            "installed": false,
            "p2shtype": 85,
            "pubtype": 60,
            "rpc": "127.0.0.1:11116",
            "smartaddress": "RYZpstUG4VYUcQDsVhTmUqgDyLySKznuLW",
            "status": "inactive",
            "txfee": 1000,
            "wiftype": 188
        },
        {
            "balance": 0,
            "coin": "MESH",
            "height": -1,
            "installed": false,
            "p2shtype": 85,
            "pubtype": 60,
            "rpc": "127.0.0.1:9455",
            "smartaddress": "RYZpstUG4VYUcQDsVhTmUqgDyLySKznuLW",
            "status": "inactive",
            "txfee": 1000,
            "wiftype": 188
        }
    ],
    "mypubkey": "7a9c9dce245b69cfac30d9f3ac804b45807bd812ed774cc21508a341210a497c",
    "pubsecp": "020d9944939fd7526b0db190fea67cae49d056e950b1586ff25206717e60280b6d",
    "result": "success",
    "userpass": "103761802884e4decd2eeda76ef95ffa655be6bb59fa5b81dec78daa75fc9014"
}
```

# network API calls

You are connected to the network and can add the coins you want to trade or receive/send.
The barterDEX gives you two options to do so:

1) native (coindaemon with full blockchain sync)
This means the blockchain information that is needed by barterDEX will be parsed from the
local blockchain copy on your harddisk. This is (depending on the used coins) memory and
time consuming.

2) SPV (lightweight network, electrum based)
Thanks to Komodos unique electrum server based barterDEX integration the needed blockchain
information gets fetched from electrum servers all over the world which do provide the data
from full blockchain copies on their infrastructure. This safes a lot of memory and time.

## add native coin

## add electrum coin


# trading API calls

Below you will find all calls that are needed to trade via barterDEX and their relation and relevance
to each other.

## buy
## sell
## orderbook
## balance
## listunspent
