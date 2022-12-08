# <p align="center">Celestia Incentivized Testnet</p>

<p align="center">
  <img alt="text" src="https://docs.celestia.org/assets/images/mamaki-d63b2fa8215b512b0703a12df0d7d05d.png?s=09">
  </a>
</p>

Depending on the kind of node you are operating, this tutorial provides the essential sections for connecting to **Mamaki**. The **Mamaki** Testnet was created to assist validators in testing their node software and architecture on the test network.

## What is Mamaki?

Mamaki is a turning point for Celestia since it gives users the chance to test out the network's essential features.

The best way to participate is to choose which node you want to run first. Each node guide will include a link to the appropriate network and instructions on how to connect to it.

Now we will install the Validator Node and Full Storage Node. You can find the **Official Document** [here](https://docs.celestia.org/nodes/mamaki-testnet/).

Follow Celestia:

[Twitter](https://twitter.com/CelestiaOrg)

[Discord](https://discord.gg/fTMARTwfg4)

[Telegram](https://t.me/CelestiaCommunity)

[Forum](https://forum.celestia.org/)

---

### Hardware requirements:

- CPU 4 CORE
- RAM 8GB
- STORAGE 250GB
- UBUNTU 20.04 (LTS) x64

## Installation

Update dependencies.

```
sudo apt update && sudo apt upgrade -y
```

Install dependencies.

```
sudo apt install curl tar wget clang pkg-config libssl-dev jq build-essential git make ncdu -y
```

### Install Golang

Due to the fact that celestia-app and celestia-node are Golang-based, Golang must be installed in order to develop and use them.

- For Ubuntu AMD.

```
ver="1.18.2"
cd $HOME
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz"
rm "go$ver.linux-amd64.tar.gz"
```

- For Ubuntu ARM.

```
ver="1.18.2"
cd $HOME
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz"
rm "go$ver.linux-arm64.tar.gz"
```

Add the `/usr/local/go/bin` directory to `$PATH`.

```
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile
source $HOME/.bash_profile
```

Run this command to see if Go was installed properly.

```
go version
```

