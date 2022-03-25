# NFT.storage

NFT.storageIn this guide, we will be using [NFT.storage](https://nft.storage) which works with IPFS.

## Creating and uploading metadata <a href="#creating-and-uploading-metadata" id="creating-and-uploading-metadata"></a>

We will create directories to hold our images and metadata, and then compile them into a single IPFS CAR (Content Addressable aRchive) file that can be uploaded.

### Uploading images

Copy all your images into the `/images` folder. Two sample images have been provided in this repo, but obviously you should replace these with the images for your collection.

Pack them into an IPFS .car file:

```
yarn pack-images
```

The command will output the root CID (Content IDentifer) for your image folder.

```
root CID: bafybeih3ykpa42eipgtzcrfkeo5nvazcdqhj3oh3ztju44tcoipzsdaauy
  output: images.car
```

Create an account with NFT.storage if you don't have one already, and navigate to your Files directory. Click on "Upload" and select `images.car`.

![](<../../../.gitbook/assets/Screen Shot 2022-01-30 at 10.16.35 PM.png>)

![](<../../../.gitbook/assets/Screen Shot 2022-01-30 at 10.17.47 PM.png>)

After uploading you should be able to see the CID and click through to see your images.&#x20;

![](<../../../.gitbook/assets/Screen Shot 2022-01-30 at 10.24.40 PM.png>)

![](<../../../.gitbook/assets/Screen Shot 2022-01-30 at 10.25.24 PM.png>)

{% hint style="info" %}
Your browser may not be able to click through to your images if it doesn't have IPFS support. We recommend using the [Brave](https://brave.com) browser since it has native IPFS support.
{% endhint %}

### Uploading metadata

Now let's do the same thing for metadata.

A few sample metadata files are available in `/metadata`. Let's take a look at one of them.

```
// 1
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

{% hint style="info" %}
Make sure `image` links map to the right IPFS links when you uploaded your images in the previous step.
{% endhint %}

Using a similar command to the images, let's pack the metadata into another .car file.

```
yarn pack-metadata
```

It should generate another CID, this time for the metadata. This root CID is the base URL for your collection.

```
root CID: bafybeigemuqa4ddnexclmc633qghcrbd34ne2jq6aym6udubldxzmss6ma
  output: metadata.car
```

Follow the same steps as you did for images to upload the `metadata.car` file to NFT.storage.

{% hint style="info" %}
If you run into issues with this step, it is mostly likely because you uploaded metadata files with a .json extension. Metadata files used with .car archives do not have a file extension. Yes it's weird.
{% endhint %}

### Base URL

After getting the CID for metadata, you set it as the base URL in your contract. This way, the contract knows how to associate each token ID with an individual token URI without having to send the contract a list of URIs. All token URIs can be determined by appending the token ID to the base URL.

For this example, the `baseUrl` would be:

```
ipfs://bafybeigemuqa4ddnexclmc633qghcrbd34ne2jq6aym6udubldxzmss6ma/metadata
```

{% hint style="info" %}
Note the word `metadata` after the URL. Without this your token URIs will be incorrect.
{% endhint %}

