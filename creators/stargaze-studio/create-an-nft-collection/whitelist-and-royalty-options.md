---
description: >-
  Whitelist and Royalty settings are completely optional but can add value to
  your project
cover: ../../../.gitbook/assets/Stargaze_new_logo_black_bg_padding.png
coverY: 0
---

# Whitelist and Royalty Options

### Whitelist

Whitelisted addresses have different permissions than other addresses over the collection they are whitelisted.

They can mint tokens from a collection

* At reduced prices
* Before the start time
* More tokens

Using Stargaze Studio you can provide a whitelist and specify their permissions. You can set the following information:

* **Unit Price:** Token price for whitelisted addresses.
* **Member Limit:** Maximum number of whitelisted addresses.
* **Per Address Limit:** Maximum number of tokens a whitelisted address can mint
* **Start Time:** Start of minting time for whitelisted addresses
* **End Time:** End of minting time for whitelisted addresses
* **Whitelist File:** The txt file that contains whitelisted addresses.

{% hint style="info" %}
The start and end time for whitelisted minters must be before the public start time.
{% endhint %}

The whitelist file is a simple .txt file where each line consists of one Stargaze address. The file should look like the following:

```
stars1arkrg6nydm9k6d2hwzn9rdqtjtfes58hfqhena
stars1d90w4s4pcup6qceyrvckj35zwwy2j4u2rqa43t
```

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Everything about the whitelist is ready. You can publish the collection in its current state or add a royalty percentage by following the next step.

### Royalty

Royalties are payments that are transferred to an address every time an NFT from that collection is sold in the marketplace.

You only need to set two parameters:

* **A payment address** that will receive the funds
* **The** **share percentage** you want from each sale

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

If you are done with the configurations, press the **Create Collection** button and sign the pop-up transactions.

{% hint style="info" %}
Unlike the previous section, you will receive **two different transactions** to sign. The first one is to instantiate the whitelist contract and the second one is to publish the collection.
{% endhint %}

An info box will appear at the top of the page when the transactions are confirmed.

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>All addresses related to your collection, now with Whitelist contract</p></figcaption></figure>

{% hint style="info" %}
It is important to save all the printed information as you'll need the addresses to interact with the collection. Visit the [interact-with-a-collection](../interact-with-a-collection/ "mention") page to learn about the interactions you can have with the collection after the launch.
{% endhint %}

{% hint style="success" %}
Congrats! You have successfully learned how to create a collection with whitelist and royalty configurations.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Your collection page</p></figcaption></figure>
