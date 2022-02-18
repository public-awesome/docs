# Pinata Upload

In this guide, we'll be using [Pinata](https://www.pinata.cloud) to upload NFT project files to IPFS.

## Get Pinata Account and API Keys

Create a Pinata account. The sign up page can be found here: [_Sign Up_](https://pinata.cloud/signup)_._

Go to the [API keys page](https://app.pinata.cloud/keys), and click the "New Key" button. Give the key a name and select "create".

![Creating an API key.](../../../.gitbook/assets/createKey.png)

This will create an API key pair for you. Take note of both the API Key and API Secret, you will need to add these to your `config.js` file.



![](../../../.gitbook/assets/keys.png)

Open your `config.js` file in your favorite text editor and add the corresponding keys to `pinataApiKey` and `pinataSecretKey`. For example:

```
// Pinata API Key
  pinataApiKey: "",
  // Pinata Secret Key
  pinataSecretKey: "",
```

You're now ready to upload your project to IPFS! Simply run:

```
yarn run pinata-upload
```

This will output a `baseTokenUri`. Be sure to add it to your `config.js` file.
