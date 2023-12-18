# Deploy to Testnet

### Explorers

{% embed url="https://testnet-explorer.publicawesome.dev/stargaze" %}
Ping Explorer
{% endembed %}

### Faucet

Join our [Discord](https://discord.gg/stargaze) and request tokens in the `#faucet` channel. You will need the developer role from `#pick-a-role`.

### Endpoints

RPC: [https://rpc.elgafar-1.stargaze-apis.com](https://rpc.elgafar-1.stargaze-apis.com)

LCD: [https://rest.elgafar-1.stargaze-apis.com](https://rest.elgafar-1.stargaze-apis.com)

GRPC: [http://grpc-1.elgafar-1.stargaze-apis.com:26660](http://grpc-1.elgafar-1.stargaze-apis.com:26660)

GRPC2 : [http://grpc-2.elgafar-1.stargaze-apis.com:26660](http://grpc-1.elgafar-1.stargaze-apis.com:26660)

### Building starsd binary

```shell
git clone git@github.com:public-awesome/stargaze.git
cd stargaze
make install
```

### Deploying a contract

Stargaze testnet is permissionless and does not require a governance proposal to deploy new contracts. You may use Stargaze Studio web interface or the CLI to deploy new contracts

### Deploying a contract through Stargaze Studio

1\. Create a new wallet or import an existing one through the wallet extension on your browser

2\. Request testnet STARS to the wallet address through the `#faucet` channel on Discord\
\
3\. Visit [https://studio.publicawesome.dev/contracts/upload/](https://studio.publicawesome.dev/contracts/upload/) to deploy your contract on testnet

4\. Upon successful deployment of your contract, a summary containing the code ID, transaction hash and other data will be displayed.

### Deploying a contract through CLI

1\. Create a stars address

```shell
starsd keys add testnet-key
- name: testnet-key
  type: local
  address: stars1e9rf2y807g32jv88j9ydpe7082rk9ck8w79xtz
  pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"Aidseu5Pl9DYHGZpCE2CkqLckQ6KSgC5IJvLL1yc+lpo"}'
  mnemonic: ""
```

2\. Request funds through the `#faucet` channel

3\. Configure RPC endpoint and Chain ID

```shell
starsd config node https://rpc.elgafar-1.stargaze-apis.com:443
starsd config chain-id elgafar-1
```

4\. Check your account has balance

```shell
starsd query bank balances [address]
```

5\. Deploy a contract

```shell
starsd tx wasm store contract.wasm --from testnet-key --gas-prices 0.025ustars --gas-adjustment 1.7 --gas auto
```

After executing this transaction you will have a code id that you can use to instantiate the contract.

```shell
starsd q tx [hash] | jq 

# or use sed to return just the code_id

starsd q tx [hash] | sed -n 's/.*"key":"code_id","value":"\([^"]*\)".*/\1/p'

# or check the block explorer
https://testnet-explorer.publicawesome.dev/stargaze/tx/[hash]
```

### Instantiating a contract

You may use the CLI to instantiate the deployed contract with the custom instantiation message the contract expects.

```shell
INSTANTIATE_MSG=$(cat <<EOF
{
  "contract_param": "something"
}
EOF
)

starsd tx wasm instantiate [code_id] $INSTANTIATE_MSG --label "StargazeContract" --admin [my-address] --from testnet-key --amount "100000000ustars" --gas-prices 0.025ustars --gas-adjustment 1.7 --gas auto

```
