---
description: >-
  Whitelist and Royalty settings are completely optional but can add value to
  your project
---

# Whitelist and Royalty Options

### Whitelist

Whitelisted addresses have different permissions than other addresses over the collection they are whitelisted.

They can mint tokens from a collection

* At reduced prices
* Before the start time
* At a quantity defined by you
* In up to 3 stages with different prices and member lists

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

<figure><img src="../../../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

Everything about the whitelist is ready. You can publish the collection in its current state or add a royalty percentage by following the next step.

### Whitelist Types

<figure><img src="../../../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

There are four different whitelist contracts available for creators, each with different utility.

**1) Standard Whitelist**

The Standard Whitelist allows for up to 10000 addresses. In the Standard Whitelist, settings are universal meaning that all addresses will be eligible to mint the same amount of tokens at the same price as dictated by creator settings.

**2) Whitelist Flex**

The Whitelist Flex allows for up to 10,000 addresses. Whitelist Flex allows for different token mint limits per address.\
\
**3) Merkle Tree Whitelist**\
\
The Merkle Tree whitelist allows for a large amount of addresses to be added. The maximum file size of a Merkle Tree Whitelist is 20 Mb, approximately 400,000 addresses!\
\
**4) Merkle Tree Flex**\
\
The Merkle Tree Flex whitelist allows for a large amount of addresses to be added with different token limits per address. It has the same size limitations as the Merkle Tree Whitelist.

### Whitelist Stages

Whitelists can be arranged in up to 3 stages with different unit prices and address mint limits in each. Different addresses can be added to each stage, providing creators with a robust tool for rewarding select community members with early access to mints and other launch structures.

<figure><img src="../../../../.gitbook/assets/image (65).png" alt=""><figcaption><p>Stage 1 of a mint in action on launchpad.</p></figcaption></figure>

* Addresses for each stage should be arranged in separate files prior to upload.&#x20;
* Stages are arranged dictated by time, with the start of stage 1 dictating the start of stage 2 and so on. The end of the final stage dictates the start of the public mint phase.
* When instantiating the contract, the total number of addresses from all stages cannot exceed 10,000. More addresses up to 30,000 can be added as an execution on the whitelist contract afterward in Studio at [https://studio.stargaze.zone/contracts/whitelist/execute](https://studio.stargaze.zone/contracts/whitelist/execute)

<figure><img src="../../../../.gitbook/assets/image (66).png" alt=""><figcaption><p>Selecting the settings for stage 2 of a whitelist.</p></figcaption></figure>

### Royalty

Royalties are payments that are transferred to an address every time an NFT from that collection is sold in the marketplace.

You only need to set two parameters:

* **A payment address** that will receive the funds
* **The** **share percentage** you want from each sale

<figure><img src="../../../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

If you are done with the configurations, press the **Create Collection** button and sign the pop-up transactions.

{% hint style="info" %}
Unlike the previous section, you will receive **two different transactions** to sign. The first one is to instantiate the whitelist contract and the second one is to publish the collection.
{% endhint %}

An info box will appear at the top of the page when the transactions are confirmed.

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption><p>All addresses related to your collection, now with Whitelist contract</p></figcaption></figure>

{% hint style="info" %}
It is important to save all the printed information as you'll need the addresses to interact with the collection. Visit the [interact-with-a-collection](../../interact-with-a-collection/ "mention") page to learn about the interactions you can have with the collection after the launch.
{% endhint %}

{% hint style="success" %}
Congrats! You have successfully learned how to create a collection with whitelist and royalty configurations.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Your collection page</p></figcaption></figure>
