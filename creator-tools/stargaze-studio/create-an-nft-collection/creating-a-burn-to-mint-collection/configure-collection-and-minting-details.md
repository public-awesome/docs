# Configure Collection and Minting Details: Standard Collection

### Collection and Minting Details

Now that the assets and metadata are ready, you need to decide on the collection and minting details. These are the essential information related to your collection, we suggest you double-check them as some of them are not changeable after the collection is published.

The following information is needed:

#### Collection Details

* **Name:** The title of your collection
* **Description:** The detailed explanation of your collection
* **Symbol:** A symbol for your collection.
* **Cover Image:** The cover image that will be shown on the collection page. GIFs are supported.
* **External Link (optional):** A link you can provide on your collection page such as a webpage.

#### Minting Details

* **Number of Tokens:** Number of tokens (images) in your collection. (Filled automatically if you provided an API key)
* **Burn Configuration:** Burnable collections and number of tokens required to be burned.
  * The SG721 address for the collection from which tokens are burned and the required number of tokens must be set.
  * Multiple collections can be selected as the burn condition.
  * All burn conditions must be met by users in order to mint, e.g. if 2 collections are selected, users must burn tokens from both.
* **Per Address Limit:** Maximum number of tokens an address is allowed to mint from your collection.
* **Start Time:** Start time for the minting

<figure><img src="../../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>A filled collection details page.</p></figcaption></figure>

Now that the essential details are filled, the collection is ready to be published. However, if you want to create a whitelist for your collection or set a royalty percentage, proceed to the [Whitelist and Royalty Options](../creating-a-standard-collection/whitelist-and-royalty-options.md).

If you don't want to set any whitelist or royalty, press the **Create Collection** button and sign the pop-up transaction. An info box will appear at the top of the page when the transaction is confirmed.

<figure><img src="../../../../.gitbook/assets/image (8) (1).png" alt=""><figcaption><p>All addresses related to your collection</p></figcaption></figure>

{% hint style="info" %}
It is important to save all the printed information as you'll need the addresses to interact with the collection. Visit the [interact-with-a-collection](../../interact-with-a-collection/ "mention") page to learn about the interactions you can have with the collection after the launch.
{% endhint %}

{% hint style="success" %}
Congrats! You have successfully learned how to create and publish an NFT collection.

It may take a little time until your collection appears on Stargaze.
{% endhint %}
