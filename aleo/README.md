<h1 align="center">Aleo Incentivized Testnet III</h1>

<p align"center">
<img alt="text" src="https://camo.githubusercontent.com/973307a6c53e7088805c6fabbde538c8242f5ce8bbd4b0937b176b4e6df87b69/68747470733a2f2f63646e2e616c656f2e6f72672f736e61726b6f732f62616e6e65722e706e67">
</a>
</p>

## What is SnarkOS?
An operating system for zero-knowledge applications is called **snarkOS**. The **Aleo** network's foundation is made up of this code, which validates transactions and securely saves apps' encrypted state for public inspection.

**Follow Aleo:**

[Website](https://aleo.org)

[Twitter](https://twitter.com/AleoHQ)

[Discord](https://discord.gg/AleoHQ)

### Hardware requirements
- **CPU** 16 Cores (32 cores are preferable)
- **RAM** 16 GB (32 GB are preferable)
- **Storage** 128 GB

## Installation

Install Rust
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Clone this Repository
```
git clone https://github.com/AleoHQ/snarkOS.git --depth 1
```
Enter the sanrkOS directory
```
cd snarkOS
```
Inside the `snarkOS` directory, run
```
./build_ubuntu.sh
```
Lastly, install `snarkOS`
```
cargo install --path .
```

## Run an Aleo Node

### Start Aleo Client

To start a client node, from the `snarkOS` directory, run
```
screen -S aleo-client
```
```
./run-client.sh
```
> press **CTRL A+D**

### Start Aleo Prover

Next, create an Aleo account address
```
snarkos account new
```
The following is an example output
```
Attention - Remember to store this account private key and view key.

  Private Key  APrivateKey1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx  <-- Save Me And Use In The Next Step
     View Key  AViewKey1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx  <-- Save Me
      Address  aleo1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx  <-- Save Me
```
> Note: Please keep in mind to save the view key and private key for the account.

To start a proving node, from the `snarkOS` directory, run
```
screen -S aleo-prover
```
```
./run-prover.sh
```
Enter your Aleo private key when requested
```
Enter the Aleo Prover account private key:
APrivateKey1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### Check your Node status

- To check your Node status, click [here](https://aleo.network)

<img alt="text" src="https://miro.medium.com/max/1100/1*kF77ntBB5yGH-v345jVkRg.webp"></a>

- And if you experience an error message like this

<img alt="text" src="https://miro.medium.com/max/1100/1*BszP7kxypV9JkRgbn55KnQ.webp"></a>

There is an official message pinned on Discord

<img alt="test" src="https://miro.medium.com/max/1100/1*m4K3unLnjcunp6KTggk6TA.webp"></a>

---
