# Execute Messages

## Collection Actions <a href="#creating-and-uploading-metadata" id="creating-and-uploading-metadata"></a>

A set of actions can be executed by the admin of the collection. Executable actions are as follows:

* **Mint**

Mint a token from the collection to the caller's address.

* **Purge**

Purge the minter address data stored inside the minter contract. This action is irreversible and requires the collection to be sold out.

* **Update Mint Price**

Updates the public minting price of the collection. It can't be raised, only lowered.

* **Mint To**

Mints a token for the inputted address.

* **Batch Mint**

Mints multiple tokens for the inputted address.

* **Mint For**

Mints the token with the given ID for the inputted address.

* **Batch Mint For**

Takes an address and list of token IDs (separated by commas), then mints all of the tokens to the address.

{% hint style="info" %}
The token IDs must be separated by commas:

e.g., 2, 4, 8.

Alternatively, you can give a range of IDs separated by a colon:

e.g., 8:13
{% endhint %}

{% hint style="info" %}
Mint actions don't have time restrictions and thus can be executed before the start time.
{% endhint %}

* **Set Whitelist**

Sets a new whitelist contract address for the collection

* **Update** **Minting** **Start** **Time**

Updates the **** minting start time with the new date.

* **Update Trading Start Time**

Updates the trading start time with the new date.

* **Update Tokens Per Address Limit**

Sets a new limit for the mint per address.

* **Update Collection Info**

Updates the information related to your collection such as collection description, cover image, external link, royalty address, and royalty share percentage.

* **Freeze Collection Info**

Freezes the collection information. Once this is executed, **Update Collection Info** is no longer usable.

* **Withdraw Tokens**

Withdraws all the tokens from the collection. They will no longer be mintable.

* **Transfer Tokens**

Takes an address and a token ID, then transfers that token to the address.

* **Batch Transfer Tokens**

Takes an address and multiple token IDs (separated by commas), then transfers all of the tokens to the address. The format for listing token IDs is the same as **Batch Mint For** operation.

* **Burn Token**

Burns the token with the given ID.

* **Batch Burn Tokens**

Takes multiple token IDs and burns them at once. The format for listing token IDs is the same as **Batch Mint For** operation.

{% hint style="danger" %}
Burn actions are irreversible. The burned tokens will never be accessible again.
{% endhint %}

* **Shuffle the token IDs**

Shuffles all of the token IDs inside the collection. Collections are created in the same order as they are sent by the user, by default. Executing this message will shuffle all the IDs to make the orders random.

{% hint style="info" %}
The shuffling price is 500 $STARS.
{% endhint %}

* **Airdrop Tokens**

Takes a CSV file that contains Stargaze addresses and airdrops the specified number of tokens for each address.

The expected file is a simple .csv file where each line consists of one Stargaze address then a comma followed by the number of tokens to airdrop. The file should look like the following:

```
address,amount
stars1arkrg6nydm9k6d2hwzn9rdqtjtfes58hfqhena,3
stars1d90w4s4pcup6qceyrvckj35zwwy2j4u2rqa43t, 1
```

* **Burn Remaining Tokens**

Burns all the tokens remaining from the collection.
