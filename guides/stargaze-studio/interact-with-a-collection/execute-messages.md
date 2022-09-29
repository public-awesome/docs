# Execute Messages

## Collection Actions <a href="#creating-and-uploading-metadata" id="creating-and-uploading-metadata"></a>

A set of actions can be executed by the admin of the collection. Executable actions are as follows:

* **Mint To**

Mints a token for the inputted address.&#x20;

* **Mint For**

Mints the token with the given ID for the inputted address.&#x20;

* **Batch Mint**

Mints multiple tokens for the inputted address.&#x20;

{% hint style="info" %}
Mint actions don't have time restrictions and thus can be executed before the start time.
{% endhint %}

* **Set Whitelist**

Sets a new whitelist contract address for the collection

* **Update Start Time**

Updates the start time with the new date.

* **Update Tokens Per Address Limit**

Sets a new limit for the mint per address.

* **Withdraw Tokens**

Withdraws all the tokens from the collection. They will no longer be mintable.

* **Transfer Tokens**

Takes an address and a token ID, then transfers that token to the address.

* **Batch Transfer Tokens**

Takes an address and multiple token IDs (separated by commas), then transfers all of the tokens to the address.

{% hint style="info" %}
The token IDs must be separated by commas:

e.g., 2, 4, 8.

Alternatively, you can give a range of IDs separated by a colon:

e.g., 8:13
{% endhint %}

* **Burn Token**

Burns the token with the given ID.

* **Batch Burn Tokens**

Takes multiple token IDs and burns them at once. For the input format, check out the information box under the **Batch Transfer Tokens**.

{% hint style="danger" %}
Burn actions are irreversible. The burned tokens will never be accessible again.
{% endhint %}

* **Shuffle the token IDs**

Shuffles all of the token IDs inside the collection.&#x20;

* **Airdrop Tokens**

Takes a TXT file that contains Stargaze addresses and airdrops a token for each address.

The expected file is a simple .txt file where each line consists of one Stargaze address. The file should look like the following:

```
stars1arkrg6nydm9k6d2hwzn9rdqtjtfes58hfqhena
stars1d90w4s4pcup6qceyrvckj35zwwy2j4u2rqa43t
```
