# Tesnet

### Explorer

{% embed url="https://testnet-explorer.publicawesome.dev/stargaze" %}

### Faucet

Join our discord and request tokens in our #faucet channel, you will need the developer role from #pick-a-role



### Endpoints

RPC: https://rpc.elgafar-1.stargaze-apis.com

LCD: https://rest.elgafar-1.stargaze-apis.com



### Building starsd binary

```
git clone git@github.com:public-awesome/stargaze.git
cd stargaze
make install
```



### Deploying a contract&#x20;

1- Create an stars address

```

starsd keys add testnet-key
- name: testnet-key
  type: local
  address: stars1e9rf2y807g32jv88j9ydpe7082rk9ck8w79xtz
  pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"Aidseu5Pl9DYHGZpCE2CkqLckQ6KSgC5IJvLL1yc+lpo"}'
  mnemonic: ""

  
```

2- Request funds through the #faucet channel

3- Deploy a contract

```


starsd tx wasm store conctract.wasm --from testnet-key \
    --gas-prices 0.025ustars --gas-adjustment 1.7 \
    --gas auto --chain-id elgafar-1 --node https://rpc.elgafar-1.stargaze-apis.com:443
    

```



