---
description: >-
  This page covers some of the Studio's features and its rules to upload a
  collection.
---

# Upload Assets and Metadata

## Upload Options

There are two ways to provide your collection files to Stargaze Studio.

You can either

* Upload assets & metadata through Stargaze Studio by providing an API key
* Use an existing base URI by uploading your files manually

Either way, you must follow some naming rules:

{% hint style="info" %}
Asset and metadata names must be in numerical order starting from 1 and must only be consisted of numbers. Symbols or letters are not allowed.

**This rule also applies to the metadata (JSON) files.**

<mark style="color:green;">**Valid**</mark>

* 1.png
* 2.png

<mark style="color:red;">**Invalid**</mark>

* 1-punk.png
* 2-punk.png
{% endhint %}

{% hint style="info" %}
You must upload a corresponding JSON file containing the metadata for each asset and the names of the asset and metadata files must match.

<mark style="color:green;">**Valid**</mark>

**images**

* 1.png

**metadata**

* 1.json

<mark style="color:red;">**Invalid**</mark>

**images**

* 1.png
* 2.png

**metadata**

* 1.json
{% endhint %}

### 1) Upload Assets and Metadata using Stargaze Studio (Recommended)

First of all, to upload assets and metadata, an API key to store your collection must be provided. Stargaze Studio currently supports **NFT.Storage** and **Pinata**.

#### Obtain an API Key

Refer to [3.-add-assets-and-metadata.md](../../../creators/readme/3.-add-assets-and-metadata/3.-add-assets-and-metadata.md "mention") or [pinata-upload.md](../../../creators/readme/3.-add-assets-and-metadata/pinata-upload.md "mention") to learn how to obtain an API key to store your collection.

After you obtain the API key, simply paste it and proceed to the asset selection part.

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

#### Asset Selection

Now is the time to upload your assets, you can either upload using **Choose Files** button or simply by dragging and dropping to the asset selection area.

{% hint style="info" %}
**Supported asset formats are**

Image: JPG, PNG, SVG, and GIF.

Audio: MP3 and WAV.

Video: MP4.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption><p>After uploading assets</p></figcaption></figure>

#### Metadata Selection

After you upload the assets, a metadata selection box will appear as seen in the image above. There you can upload the metadata for your collection in JSON format.

Here is the example metadata file designed for the first token in the collection used in this guide:

```json
{
  "attributes": [
    {
      "trait_type": "hat",
      "value": "bandana"
    },
    {
      "trait_type": "glasses",
      "value": "sunglasses"
    },
    {
      "trait_type": "personality",
      "value": "chill"
    },
    {
      "trait_type": "shirt_color",
      "value": "purple"
    },
    {
      "display_type": "number",
      "trait_type": "generation",
      "value": 1
    }
  ],
  "description": "Just some guy that likes to code_1.",
  "external_url": "https://example.com/?token_id=1",
  "name": "Shane Stargaze"
}
```

{% hint style="info" %}
Notice that \*\*\*\* the **image** key value is missing, which is needed while uploading assets manually. However, Stargaze Studio handles it by using your API key and fills it automatically.
{% endhint %}

#### Update Metadata

Stargaze Studio lets you update the metadata through the interface. Simply click on one of your assets after uploading the metadata files.

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Click on one of the assets to edit</p></figcaption></figure>

A pop-up will appear and you'll be able to update the metadata

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

If you have successfully uploaded assets and metadata, you can skip the rest of this page and proceed to the [configure-collection-and-minting-details.md](configure-collection-and-minting-details.md "mention") page.

### 2) Use an Existing Base URI

If you have already uploaded your assets and metadata to IPFS or you want to handle it manually, first make sure that the folder structure is as follows:

```markdown
Project Folder:
  - images
    - 1.png
    - 2.png
    - 3.png
  - metadata
    - 1.json
    - 2.json
    - 3.json
```

If you want to learn how to upload your files manually, have a look at the [3.-add-assets-and-metadata](../../../guides/readme/3.-add-assets-and-metadata "mention") section or use [NFTUp](https://nft.storage/docs/how-to/nftup/) to handle the upload.

{% hint style="warning" %}
Providing a different folder structure for your NFT collection can cause unexpected behavior.
{% endhint %}

If you choose to use an existing base URI and completed the steps above, you can proceed to the [configure-collection-and-minting-details.md](configure-collection-and-minting-details.md "mention") step.
