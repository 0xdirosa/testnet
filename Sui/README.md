<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/50621007/174559198-c1f612e5-bba2-4817-95a8-8a3c3659a2aa.png">
</p>

# Sui Incentivized Testnet
- [Official Documentation](https://docs.sui.io/build/fullnode)
- [Twitter](https://twitter.com/SuiNetwork)
- [Discord](https://discord.gg/sui)

### Minimum Hardware
- 2 CPU
- 4GB RAM
- 50GB SSD

### Recommended Hardware
- 8 CPU
- 16GB RAM
- 500GB SSD

> Storage requirements will vary based on various factors (age of the chain, transaction rate, etc) although we don't anticipate running a fullnode on devnet will require more than 50 GBs today given it is reset upon each release roughly every two weeks.

## 1. Setup Sui Full Node
### Install (automatic)
You can setup your Sui full node in minutes by using automated script below
```
wget -O sui.sh https://raw.githubusercontent.com/kj89/testnet_manuals/main/sui/sui.sh && chmod +x sui.sh && ./sui.sh

```

### Install (manual)
You can follow [manual guide](https://github.com/kj89/testnet_manuals/blob/main/sui/manual_install.md) if you better prefer setting up node manually

### Make test
Once the fullnode is up and running, test some of the JSON-RPC interfaces.

### Check status of your Node
```
curl -s -X POST http://127.0.0.1:9000 -H 'Content-Type: application/json' -d '{ "jsonrpc":"2.0", "method":"rpc.discover","id":1}' | jq .result.info
```
You should see something similar in the output:
```json 
 { 
   "title": "Sui JSON-RPC", 
   "description": "Sui JSON-RPC API for interaction with the Sui network gateway.", 
   "contact": { 
     "name": "Mysten Labs", 
     "url": "https://mystenlabs.com", 
     "email": "build@mystenlabs.com" 
   }, 
   "license": { 
     "name": "Apache-2.0", 
     "url": "https://raw.githubusercontent.com/MystenLabs/sui/main/LICENSE" 
   }, 
   "version": "0.1.0" 
 } 
 ```

### Get the five most recent transactions 
 ``` 
 curl --location --request POST 'http://127.0.0.1:9000/' --header 'Content-Type: application/json' \ 
 --data-raw '{ "jsonrpc":"2.0", "id":1, "method":"sui_getRecentTransactions", "params":[5] }' | jq . 
 ```

### Get details about a specific transaction
```
curl --location --request POST 'http://127.0.0.1:9000/' --header 'Content-Type: application/json' \ 
 --data-raw '{ "jsonrpc":"2.0", "id":1, "method":"sui_getTransaction", "params":["<RECENT_TXN_FROM_ABOVE>"] }' | jq .
```

## 2. Post installation
After setting up your Sui node you have to register it in the [Sui Discord](https://discord.gg/b5vWu33f): 
- navigate to `#📋node-ip-application` channel 
- post your node endpoint url
```
http://<YOUR_NODE_IP>:9000/
```

## 3. Check your node health status
Enter your node IP into https://node.sui.zvalid.com/

Healthy node should look like this:

![image](https://user-images.githubusercontent.com/50621007/175829451-a36d32ff-f30f-4030-8875-7ffa4e999a24.png)

## 4. Generate wallet
```
echo -e "y\n\n0\n" | sui client
```
> !Please backup your wallet key files located in `$HOME/.sui/sui_config/` directory!

## 5. Top up the wallet
```
sui client active-address
```
