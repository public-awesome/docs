# NFT.storage

NFT.storageIn this guide, we will be using [NFT.storage](https://nft.storage) which works with IPFS.

## Creating and uploading metadata <a href="#creating-and-uploading-metadata" id="creating-and-uploading-metadata"></a>

We will create directories to hold our images and metadata, and then compile them into a single IPFS CAR (Content Addressable aRchive) file that can be uploaded.

### Uploading images <a href="#uploading-images" id="uploading-images"></a>

Copy all your images into the `/images` folder. Two sample images have been provided in this repo, but obviously you should replace these with the images for your collection.Pack them into an IPFS .car file:1yarn run pack-imagesCopied!The command will output the root CID (Content IDentifer) for your image folder.1root CID: bafybeih3ykpa42eipgtzcrfkeo5nvazcdqhj3oh3ztju44tcoipzsdaauy2output: images.carCopied!Create an account with NFT.storage if you don't have one already, and navigate to your Files directory. Click on "Upload" and select `images.car`.![](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2Fo3OlOgqvfr4UgT37r0bW%2Fuploads%2Fg5hqjqiOlFJdDoGLjTxN%2FScreen%20Shot%202022-01-30%20at%2010.16.35%20PM.png?alt=media\&token=55bba62d-05f3-4f69-80f9-febc72e08d22)![](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2Fo3OlOgqvfr4UgT37r0bW%2Fuploads%2FWhbFXgf2u5C5ezGhzCUl%2FScreen%20Shot%202022-01-30%20at%2010.17.47%20PM.png?alt=media\&token=5460fd2a-d25c-479b-9b90-41423a4af64f)After uploading you should be able to see the CID and click through to see your images.
