---
cover: ../../../.gitbook/assets/stargaze.banner.lg.png
coverY: 0
---

# 3. Add assets and metadata

Stargaze's sg721 contract allows for off-chain metadata storage. We recommend using a decentralized storage solution such as IPFS.

In this guide, we will cover basic project structure as well as using [NFT.storage](https://nft.storage) or [Pinata](https://www.pinata.cloud) to upload your project to IPFS.

## Project Structure

Add your NFT images and metadata `.json` files to the respective `images` and `metadata` folders. Your project should be structured like this:

```
Project Folder:
  - images
    - 1.jpg
    - 2.jpg
    - 3.jpg
  - metadata
    - 1.json
    - 2.json
    - 3.json
```

Files should be numbered sequentially and there should be a matching metadata file for each image.

{% hint style="info" %}
NOTE: It is _very important_ that each of the images are numbered sequentially and have corresponding metadata files.
{% endhint %}

{% hint style="info" %}
NOTE: If using NFT.storage, remove the .json extension from metadata files or switch to the branch `nft.storage`.
{% endhint %}

{% hint style="info" %}
NOTE: Images can be JPG, PNG, SVG, GIF. We are adding support for other formats soon.
{% endhint %}



### Structuring metadata

Stargaze NFT metadata follows the [OpenSea metadata standards](https://docs.opensea.io/docs/metadata-standards).

Sample metadata files are available in `/metadata`. Let's take a look at one of them.

```
// 1.json
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
  "description": "Just some guy that likes to code.",
  "external_url": "https://example.com/?token_id=1",
  "image": "ipfs://bafybeih3ykpa42eipgtzcrfkeo5nvazcdqhj3oh3ztju44tcoipzsdaauy/images/1.png",
  "name": "Shane Stargaze"
}
```

### Uploading to IPFS and getting the Base URL

After setting up your project, upload the files to IPFS using one of our guides:

* [NFT.storage](nft.storage.md) (manual upload via UI)
* [NFT.storage](broken-reference) (with script)
* [Pinata](pinata-upload.md) (with script)

{% hint style="info" %}
NFT.storage is free to use. The UI can be used to upload assets, but a script is also provided for convenience.
{% endhint %}

After following the steps in the guides above, you'll receive a `baseTokenUri` for your project. This way, the contract knows how to associate each token ID with an individual token URI without having to send the contract a list of URIs. All token URIs can be determined by appending the token ID to the base URL.

Be sure to update your `config.js` with this `baseTokenUri`.
