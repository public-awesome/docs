---
description: Instructions for joining the Stargaze Mainnet
cover: ../.gitbook/assets/Stargaze_new_logo_black_bg_padding.png
coverY: 0
---

# Running a Full Node

### Mainnet binary version

The correct version of the binary for mainnet at genesis is `v1.1.0`. Its release page can be found [here](https://github.com/public-awesome/stargaze/releases/tag/v1.1.0). Follow the directions on Getting Setup for installation of the `starsd` binary.

### Mainnet chain-id

Below is the list of Stargaze mainnet id's and their current status. You will need to know the version tag for installation of the `starsd` binary.

| chain-id   | Description                                        |  Status | Block Start | Block Finish |
| ---------- | -------------------------------------------------- | :-----: | ----------- | ------------ |
| stargaze-1 | This is the first chain-id from the genesis event. | current | 0           | N/A          |

### Recommended Minimum Hardware

The minimum recommended hardware requirements for running a validator for the Stargaze mainnet:

| Chain-id   | Requirements                                                                                   |
| ---------- | ---------------------------------------------------------------------------------------------- |
| stargaze-1 | <ul><li>8 Cores (modern CPU's)</li><li>16GB RAM</li><li>1TB of storage (SSD or NVME)</li></ul> |

{% hint style="warning" %}
Note that the mainnet will accumulate data as the blockchain continues. This means that you will need to expand your storage as the blockchain database gets larger with time.
{% endhint %}

### Configuration of Shell Variables

For this guide, we will be using shell variables. This will enable the use of the client commands verbatim. It is important to remember that shell commands are only valid for the current shell session, and if the shell session is closed, the shell variables will need to be re-defined.

If you want variables to persist for multiple sessions, then set them explicitly in your shell .profile, as you did for the Go environment variables.

To clear a variable binding, use `unset $VARIABLE_NAME` . Shell variables should be named with ALL CAPS.

#### Choose the required mainnet chain-id

Choose the `<chain-id>` for the mainnet you would like to join from here. Set the `CHAIN_ID`:

```bash
CHAIN_ID=<chain-id>

# Example
CHAIN_ID=stargaze-1
```

You can also set this in your `.profile` file:

```bash
export CHAIN_ID=stargaze-1
```

Then source it:

```bash
source .profile
```

#### Set your moniker name

Choose your `<moniker-name>`, this can be any name of your choosing and will identify your validator in the explorer. Set the `MONIKER_NAME`:

```bash
MONIKER_NAME=<moniker-name>

# Example
MONIKER_NAME="Validatron 9000"
```

#### **Set persistent peers - OPTIONAL**

Persistent peers will be required to tell your node where to connect to other nodes and join the network. However, the stargaze repository comes with seed values already pre-populated. To retrieve the peers for the chosen mainnet, optionally:

```bash
# Set the base repo URL for mainnet & retrieve peers
CHAIN_REPO="https://raw.githubusercontent.com/public-awesome/mainnet/main/$CHAIN_ID" && \
export PEERS="$(curl -s "$CHAIN_REPO/peers.txt")"
```

{% hint style="info" %}
If you are unsure about this, you can ask in discord for the current peers and explicitly set them in `~/.starsd/config/config.toml` instead.
{% endhint %}

#### **Set seed nodes**

Seed nodes are available for your local node to quickly receive network address book entries. This will provide your node with addresses to dial and begin to build the peer book. These seed values are pre-populated within your \``~/.starsd/config/config.toml`

#### Set minimum gas prices

In `$HOME/.starsd/config/app.toml`, set minimum gas prices:

```
sed -i.bak -e "s/^minimum-gas-prices *=.*/minimum-gas-prices = \"1ustars\"/" ~/.starsd/config/app.toml
```

### Setting up the Node

These instructions will direct you on how to initialize your node, synchronize to the network and upgrade your node to a validator.

#### **Initialize the chain**

```bash
starsd init $MONIKER_NAME --chain-id $CHAIN_ID
```

This will generate the following files in `~/.starsd/config/`

* `genesis.json`
* `node_key.json`
* `priv_validator_key.json`

#### Download the genesis file

```
curl -s  https://raw.githubusercontent.com/public-awesome/mainnet/main/$CHAIN_ID/genesis.tar.gz > genesis.tar.gz
tar -C ~/.starsd/config/ -xvf genesis.tar.gz
rm genesis.tar.gz
```

This will replace the genesis file created using `starsd init` command with the mainnet `genesis.json`.

Verify the genesis.json file is correct. The output of the command should return the same shasum as shown below:

```
wget https://raw.githubusercontent.com/public-awesome/mainnet/main/normalize.jq
jq -S -f normalize.jq  ~/.starsd/config/genesis.json | shasum -a 256

a8f1c085b48d1c62d3634f5d49cf2432ef7832fa2b629f6bd3feba20ee554475
```

#### **Set persistent peers - OPTIONAL**

Using the peer variable we set earlier, we can set these values in `~/.starsd/config/config.toml`:

```bash
sed -i.bak -e "s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" ~/.starsd/config/config.toml
```

#### **Create (or restore) a local wallet key pair**

Either create a new key pair, or restore an existing wallet for your validator:

```bash
# Create new keypair
starsd keys add <key-name>

# Restore existing stargaze wallet with mnemonic seed phrase.
# You will be prompted to enter mnemonic seed.
starsd keys add <key-name> --recover

# Query the keystore for your public address
starsd keys show <key-name> -a
```

Replace `<key-name>` with a key name of your choosing.

{% hint style="danger" %}
After creating a new key, the key information and seed phrase will be shown. It is essential to write this seed phrase down and keep it in a safe place. The seed phrase is the only way to restore your keys.
{% endhint %}

#### **Get some Stargaze tokens**

You will require some Stargaze tokens to bond to your validator. To be in the active set you will need to have enough tokens to be in the top 100 validators by delegation weight. You can view the current delegator set at [mintscan.io](https://www.mintscan.io/stargaze/validators).

If you do not have any STARS for you validator you can purchase/exchange tokens on Osmosis or Emeris.

### Setup Cosmovisor

[Follow these instructions](setting-up-cosmovisor.md) to setup cosmovisor and start the node.

{% hint style="info" %}
Using cosmovisor is completely optional. If you choose not to use cosmovisor, you will need to be sure to attend network upgrades to ensure your validator does not have downtime and get jailed.
{% endhint %}

### Syncing the node

After starting the starsd daemon, the chain will begin to sync to the network. The time to sync to the network will vary depending on your setup and the current size of the blockchain, but could take a very long time. To query the status of your node:

```bash
# If not using cosmovisor, start the node with the following command in a tmux or screen session
starsd start

# Query via the RPC (default port: 26657)
curl http://localhost:26657/status | jq .result.sync_info.catching_up
```

If this command returns `true` then your node is still catching up. If it returns `false` then your node has caught up to the network current block and you are safe to proceed to upgrade to a validator node.

If you are syncing from the block 0 (genesis), and are not using cosmovisor through upgrades, the node will stop when reaching an upgrade height. From this point you will have to swap the `starsd` binary with the requested upgraded version to continue the sync to the top of the chain.

### Upgrade to a validator

{% hint style="danger" %}
**Do not attempt to upgrade your node to a validator until the node is fully in sync as per the previous step.**
{% endhint %}

Once the node is synced and you have the required STARS to be in the validator set, you can initiate the upgrade.

To upgrade the node to a validator, you will need to submit a `create-validator` transaction:

```bash
starsd tx staking create-validator \
  --amount=1000000ustars \
  --commission-max-change-rate "0.1" \
  --commission-max-rate "0.20" \
  --commission-rate "0.05" \
  --min-self-delegation "1" \
  --details "validators write bios too" \
  --pubkey=$(starsd tendermint show-validator) \
  --moniker $MONIKER_NAME \
  --chain-id $CHAIN_ID \
  --gas-prices=0.025ustars \
  --from <key-name>
```

{% hint style="info" %}
The above transaction is just an example. There are many more flags that can be set to customize your validator, such as your validator website, or keybase.io id, etc. To see a full list:

```bash
starsd tx staking create-validator --help
```
{% endhint %}

### Backup critical files

There are certain files that you need to backup to be able to restore your validator if, for some reason, it damaged or lost in some way. Please make a secure backup of the following files located in `~/.starsd/config/`:

* `priv_validator_key.json`
* `node_key.json`

It is recommended that you encrypt the backup of these files.
