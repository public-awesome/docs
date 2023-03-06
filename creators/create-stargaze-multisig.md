---
description: How to Create a Multisig Wallet on Stargaze
---

# Create a Multisig Wallet

To create a Stargaze Multisig, you will need to use the command line (for now). 🎉\
\
Don't worry, it's not too difficult and the team is always happy to assist if needed.

## Install `starsd`

First you'll need to get the `starsd` binary. This is the program that is used to run the chain, as well as do a bunch of other useful things like signing transactions and managing keys. If you feel technically competent, checkout the source code on the [Stargaze GitHub repository](https://github.com/public-awesome/stargaze) and build it yourself.

Otherwise, you can do it the easy way and download a pre-built binary. To do that, open a terminal and copy and paste the following:

#### Linux

```
wget https://github.com/public-awesome/stargaze/releases/download/v7.5.0/stargaze_7.5.0_linux_amd64.tar.gz
tar -C /usr/local -xvf stargaze_7.5.0_linux_amd64.tar.gz
```

This downloads the file and copies it to `/usr/local`.

#### Mac

Build from source:

```
git clone https://github.com/public-awesome/stargaze && cd stargaze
git fetch origin --tags
git checkout v7.5.0
make install
```

Verify it's working with:

```

starsd version

```

You should see it respond with 1.0.0. Now you're ready to make some keys.

## STARS address and pubkey

Note, we _highly recommend_ that you use a ledger for this. All commands will assume you are using one.

Add your key (replace `<your-key-name>` with your desired key name):

```
starsd keys add <your-key-name> --ledger
```

This should output some information about the key that was added, including your STARS address and pubkey.

```
- name: <your-key-name>
  type: local
  address: stars15pu8urf623epskfravug2kr3az4cd8twdtjjfr
  pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"A7KWJjHeJpLKwSC7lsPMeQYngdI87x5etEDoNtH5aHKW"}'
  mnemonic: ""
```

**Take note of your pubkey. We'll use it later to create the multisig.** The pubkey looks like this: `'{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"A7KWJjHeJpLKwSC7lsPMeQYngdI87x5etEDoNtH5aHKW"}'`

Each member of your team that wants to join a multisig should create a key, take note of their public keys, and share them with each other. _Write them down in a list or in a shared document._

If you want to show your key info again: `starsd keys show <your-key-name>`

If you want to list all your keys: `starsd keys list`

## Create the Multisig

To create the multisig, you'll need to add everyone's pubkey to the keyring:

```
starsd keys add <teammate> --pubkey <their-pubkey>
```

Finally, when you have everyone's pubkey, you can create the multisig:

```
starsd keys add multisig --multisig <your-key>,<teammate>,<teammate-2> --multisig-threshold 2
```

Note the `--multisig-threshold` flag. This controls how many of the keys have to sign in order for a transaction to be valid. If the `multisig` account had a threshold of 1, anyone on the multisig could sign. However, the threshold is 2, so 2 out of 3 have to sign.

For larger multisigs (more than 3 people), it may make sense to not to have to require everyone to sign, but rather some majority of key holders. Think about this number before you set it.

## Configure the Chain

These commands will make the rest of the commands in this tutorial simpler. They set a global config which is used by all future commands.

Set the default node to talk to (so you don't have to run your own):

```
starsd config node https://rpc.stargaze-apis.com:443
```

Set the default chain ID:

```
starsd config chain-id stargaze-1
```

## Sign Transactions

Let’s say you want to spend some of your funds.

When making a transaction, use the `--generate-only` flag.

This will not submit the transaction to the chain, but rather generate a JSON file for everyone to sign on their respective machines with their private keys. When one team member generates a transaction like this, they need to share the JSON file with the entire group.

**Generate example spend proposal**:

```
starsd tx bank send $(starsd keys multisig -a) stars123408DestinationAddress 10000000ustarx --generate-only > tx.json
```

Everyone should take that `tx.json` file and sign it on their own machines with their private keys. The both specify the address of the multisig account using the `--multisig` flag.

You:

```
starsd tx sign --from $(starsd keys show -a <your-key-name>) --multisig $(starsd keys show -a multisig) tx.json --sign-mode amino-json --output-document signed-alice.json
```

Your teammate:

```
starsd tx sign --from $(starsd keys show -a <your-key-name>) --multisig $(starsd keys show -a multisig) tx.json --sign-mode amino-json --output-document signed-alice.json
```

Alice and Bob take their respective JSON files and use them to create a single transaction JSON file containing both of their signatures.

```
starsd tx multisign --from alice-bob-multisig tx.json alice-bob-multisig signed-alice.json signed-bob.json > signed.json
```

Finally, one of them broadcasts the transaction to the chain!

```
starsd tx broadcast signed.json
```

Alice and Bob just sent their developer friend funds from their multisig. 🎉

## More Transactions

Often you want to do more than just send tokens! Here are some other transaction examples you can generate and then multisign using the steps above.

### Staking

You'll want to stake you multisig assets to earn staking rewards. Figure out which validator you want to delegate to from the [list of validators](https://app.stargaze.zone/stake) and use their address where it says `<validator-address>`. For example, `starsvaloper1jxv0u20scum4trha72c7ltfgfqef6nscdghxyx`.

```
starsd tx staking delegate <validator-address> 500000000000ustars --from $(starsd keys multisig -a) --generate only > tx.json
```

### Withdraw Rewards

This will withdraw your staking rewards so you can actually spend or stake them.

```
starsd tx distribution withdraw-all-rewards --from $(starsd keys show multisig -a) --generate-only
```
