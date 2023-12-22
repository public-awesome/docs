# Token Factory

The Token Factory module on Stargaze enables the creation of native fungible tokens. The feature allows projects to use the functions provided by the Cosmos SDK Bank Module for token distribution. The tokens are denominated as `factory/{creator_address}/{subdenom}` and a single account can create multiple tokens, by providing a unique subdenom for each created token. Once a token is created, the original creator is given "admin" privileges over the asset. The creator can mint and burn tokens or transfer the admin privileges to another address.

### Token Factory Denom Restrictions

* Token Factory denoms are of form `factory/{creator_address}/{subdenom}`
* The maximum `subdenom` length is 44 characters
* The maximum `creator_address` length is 75 characters

## Interacting with the Token Factory module

### Prerequisites

#### Building the <mark style="color:purple;">starsd</mark> binary

```sh
git clone git@github.com:public-awesome/stargaze.git
cd stargaze
make install
```

#### Creating or Importing a wallet account

You may create a new wallet account with the following command

```sh
starsd keys add local-wallet
```

or import an existing one with

```sh
starsd keys add local-wallet --recover
```

#### Configuring RPC Endpoint and Chain ID

Testnet Configuration

```shell
starsd config node https://rpc.elgafar-1.stargaze-apis.com:443
starsd config chain-id elgafar-1
```

Mainnet Configuration

```
starsd config node https://rpc.stargaze-apis.com:443
starsd config chain-id stargaze-1
```

#### Checking your account balance

You may check your wallet balance with the following command:

```
starsd query bank balances <local_wallet_address>
```

{% hint style="info" %}
Creating a new token denom costs 10000 STARS + fees. The following transactions may fail if the wallet balance is not sufficient to cover the required cost and fees.
{% endhint %}

You may join our Discord server and request testnet STARS on the #faucet channel.

### Creating a New Token

Executing the following command will create a token with the following denom: `factory/<local_wallet_address>/<token_subdenom>`

```sh
starsd tx tokenfactory create-denom <token_subdenom> --from local-wallet --fees 2000ustars
```

The result of the transaction can be queried using the transaction hash received as follows:

```
starsd q tx <tx_hash_received>
```

The following blockchain explorers can also be utilized to follow transaction results:

* Testnet Explorer: [https://testnet-explorer.publicawesome.dev/stargaze/](https://testnet-explorer.publicawesome.dev/stargaze/)
* Mainnet Explorer: [https://dev.mintscan.io/stargaze/](https://dev.mintscan.io/stargaze/)

### Checking the tokens created by an account

To see a list of tokens created by a specific account, you may use the following command:

```sh
starsd q tokenfactory denoms-from-creator <creator_wallet_address>
```

### Minting Tokens

You may use the following command to mint tokens of a denom you created to your wallet:

```sh
starsd tx tokenfactory mint <amount_to_mint>factory/<local_wallet_address>/<subdenom> --from local-wallet --fees 2000ustars
```

### Burning Tokens

You may burn tokens of a denom you created from your wallet with the following command:

```
starsd tx tokenfactory burn <amount_to_burn>factory/<local_wallet_address>/<subdenom> --from local-wallet --fees 2000ustars
```

### Transferring Tokens

You may utilize the Bank module as follows to distribute tokens after minting them:

```sh
starsd tx bank send <local_wallet_address> <recipient_address> <amount_to_transfer>factory/<local_wallet_address>/<subdenom> --fees 2000ustars
```

### Changing the admin for a token

You may transfer the admin privileges to another address for a token you previously created as follows:

```
starsd tx tokenfactory change-admin factory/<local_wallet_address>/<subdenom> <new_admin_address> --from local-wallet
--fees 2000ustars
```

### Querying the admin for a token

You may query the address that holds the admin privileges over a token as follows:

```
starsd q tokenfactory denom-authority-metadata factory/<creator_address>/<subdenom>
```
