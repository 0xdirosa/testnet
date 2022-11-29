## Manta Incentivized Testnet

- [Official Docs](https://docs.manta.network/docs/guides/TrustedSetup)
- [Twitter](https://twitter.com/MantaNetwork)
- [Fiscord](https://discord.gg/mantanetwork)

### Update packages
```
sudo apt update && sudo apt upgrade -y
```

### Install packages
```
sudo apt install pkg-config build-essential libssl-dev curl jq -y
```

### Download and install Rust
```
curl https://sh.rustup.rs/ -sSf | sh -s -- -y
```
```
source $HOME/.cargo/env
```

### Download manta-rs
```
git clone https://github.com/Manta-Network/manta-rs.git
```

### Setup Manta Trust
```
cd manta-rs
```
```
cargo run --release --package manta-trusted-setup --all-features --bin groth16_phase2_client register
```


