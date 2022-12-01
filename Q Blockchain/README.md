<h1 align="center">Q Blockchain Incentivized Testnet</h1>

<p align="center">
<img alt="text" src="https://miro.medium.com/max/1100/1*7JV-UT1CDknzvVuHq7ACYw.webp">
</a>
</p>

## What is Project Q?

Q is a novel blockchain that combines the benefits of a public, open and decentralized ledger with the transparency and predictability of enforceable private contracts, thereby enabling adoption by a great variety of use cases that desire decentralization but require scalability and dependability.

## How to Setup a Q Validator Node

### Setup Your Server

Your server or machine needs to be ready before you start. Utilizing a local workstation is one option; otherwise, you may utilize, for instance, a cloud instance on AWS.

### Installation

```
sudo apt update && sudo apt upgrade -y
```

Clone this repository

```
git clone https://gitlab.com/q-dev/testnet-public-tools
```

Then go to `testnet-validator` directory

```
cd testnet-public-tools/testnet-validator
```

The `docker-compose.yaml` file for the blockchain explorer using `.env` and the validator node with preconfigurations on rpc may both be launched quickly from this directory (which can be created from `.env` example)

### Generate a Keypair for Validator

A validator needs a keypair in order to sign blocks and collect payment. Make a keystore directory, then enter the password that will be used to encrypt the private key in a text file called `pwd.txt` in the `/keystore` directory. To create a keypair, execute this command while in the `/testnet-validator` directory

```
docker-compose run --rm --entrypoint "geth account new --datadir=/data --password=/data/keystore/pwd.txt" testnet-validator-node
```

This command's output should appear as follows

```
Your new key was generated

Public address of the key:   0xb3FF24F818b0ff6Cc50de951bcB8f86b52287dac
Path of the secret key file: /data/keystore/UTC--2021-01-18T11-36-28.705754426Z--b3ff24f818b0ff6cc50de951bcb8f86b52287dac

- You can share your public address with anyone. Others need it to interact with you.
- You must NEVER share the secret key with anyone! The key controls access to your funds!
- You must BACKUP your key file! Without the key, it's impossible to access account funds!
- You must REMEMBER your password! Without the password, it's impossible to decrypt the key!
```

In this manner, a fresh private key is created and encrypted with the password from the `pwd.txt` file, then saved in the `/keystore` directory. The address for the freshly created private key in our case is _0xb3FF24F818b0ff6Cc50de951bcB8f86b52287DAc_ (**you will have a different number**)

You can also manually create a secret key pair and the corresponding file on this [website](https://vanity-eth.tk/), then save it to the `/keystore` directory. Also you may use `create-geth-private-key.js` script in `/js-tools` folder.

### Get Q tokens

You will need Q tokens for this because you must stake some money in the validators contract in order to become one. You can use the [faucet](https://faucet.qtestnet.org/) to obtain some Q for the testnet. For more details, consult the [faucet's instructions](https://docs.qtestnet.org/how-to-install-metamask/#faucet). Finally, kindly check [Block Explorer](https://explorer.qtestnet.org/) for your address to ensure that tokens were received.

### Configure Setup

Edit the file located in the `/testnet-validator` directory by copying `.env.example` to `.env`

```
cp .env.example .env
nano .env
```

Put your address without the leading 0x from step 3 into ADDRESS, your public IP address into IP (please make sure your machine can be reached at the relevant IP), and you can optionally select a port for peer-to-peer communication (or just leave default value). This is how the final `.env` file ought to appear

```
# docker image for q client
QCLIENT_IMAGE=qblockchain/q-client:1.2.1

# your q address here (without leading 0x)
ADDRESS=b3FF24F818b0ff6Cc50de951bcB8f86b52287DAc

# your public IP address here
IP=193.19.228.94

# the port you want to use for p2p communication (default is 30313)
EXT_PORT=30313

# extra bootnode you want to use
BOOTNODE1_ADDR=enode://c610793186e4f719c1ace0983459c6ec7984d676e4a323681a1cbc8a67f506d1eccc4e164e53c2929019ed0e5cfc1bc800662d6fb47c36e978ab94c417031ac8@79.125.97.227:30304
BOOTNODE2_ADDR=enode://8eff01a7e5a66c5630cbd22149e069bbf8a8a22370cef61b232179e21ba8c7b74d40e8ee5aa62c54d145f7fc671b851e5ccbfe124fce75944cf1b06e29c55c80@79.125.97.227:30305
BOOTNODE3_ADDR=enode://7a8ade64b79961a7752daedc4104ca4b79f1a67a10ea5c9721e7115d820dbe7599fe9e03c9c315081ccf6a2afb0b6652ee4965e38f066fe5bf129abd6d26df58@79.125.97.227:30306
```

The next step is to change `config.json`, which is necessary for staking. In the address field, enter the address listed above, and in the password field, enter the password listed in the `/keystore/pwd.txt` file. The final `config.json` file should resemble this

```
    {
      "address": "b3FF24F818b0ff6Cc50de951bcB8f86b52287DAc",
      "password": "supersecurepassword",
      "keystoreDirectory": "/data",
      "rpc": "https://rpc.qtestnet.org"
    }
```

### Put Stake in Validators Contract

As was previously indicated, in order to become a validator, you must stake your validators contract.

You can utilize the "Your HQ" dApp, which is accessible at `https://hq.qtestnet.org`. To obtain incentives, you must eventually **Join Validator Ranking**. The relevant capability may be found in the "Manage Balance" box under **Consensus Services -> Validator Staking**. You are not operating the dApp UI in advanced mode if you cannot see the menu item **Consensus Services**. Open **Settings** and turn it on.

### Add your Validator to `https://stats.qtestnet.org`

You can add an extra flag to the node entrypoint within file `/validator/docker-compose.yaml` if you want your validator to report to the [network statistics](https://stats.qtestnet.org/). It should look like this

```
testnet-validator-node:
  image: $QCLIENT_IMAGE
  entrypoint: ["geth", "--ethstats=<Your_Validator_Name>:<Testnet_access_key>@stats.qtestnet.org", "--datadir=/data", ...]
```

`<Your_Validator_Name>` can be chosen at random. In the statistics, it will be shown. This may say something like "OurCoolCompany - Don't trust, verify" if you wish to reveal your identity. Emojis, special characters, and spaces are all acceptable. We would appreciate it if you left your validator Q address blank if you would rather remain anonymous so that there is a connection between your client and your address.

In order to find out the `<Testnet_access_key>` please join [Q Discord Server](https://discord.gg/YTgkvJvZGD) and find stats key in [🔑│testnet-key channel](https://discord.com/channels/902893347239247952/1042401601639432212).

### Launch Validator Node

Using the docker-compose file located in the `/testnet-validator` directory, launch your validator node now

```
docker-compose up -d
```

Use the following command to view the real-time logs from our nodes

```
docker-compose logs -f --tail "100"
```

---

## Useful Commands

### Find additional peers

If your client cannot connect using the default setup, we advise you to add a flag in the `docker-compose.yaml` file pointing to one of our additional peers (`$BOOTNODE1 ADDR`, `$BOOTNODE2 ADDR`, or `$BOOTNODE3 ADDR`)

```
testnet-validator-node:
  image: $QCLIENT_IMAGE
  entrypoint: ["geth", "--bootnodes=$BOOTNODE1_ADDR,$BOOTNODE2_ADDR,$BOOTNODE3_ADDR", "--datadir=/data", ...]
```
### Updating Q-Client & Docker Images

You will need to update the validator files and configurations in the event that the Q-Client undergoes significant revisions. Use the following commands to accomplish this under directory `/testnet-validator` (for validator), `/testnet-rootnode` (for rootnode), or `/testnet-fullnode` (for fullnode)

Stash your changes and pull the latest configs

```
git stash && git pull
```

Apply your stashed changes and pull (and overwrite) the latest docker images

```
git stash apply && docker-compose pull
```

Restart with new configs & images

```
docker-compose up -d
```

---
