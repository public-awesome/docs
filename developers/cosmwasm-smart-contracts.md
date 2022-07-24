---
cover: ../.gitbook/assets/OGImage1200x630.png
coverY: 0
---

# CosmWasm Smart Contracts

Stargaze runs community-governed CosmWasm. All this means is that custom smart contracts have to be uploaded via governance.

### Why community-governed CosmWasm?

Because Stargaze is an application-specific chain for NFTs, custom contracts should target NFT use cases and integrate with the rest of Stargaze. By going through governance, custom contracts can be reviewed by the community before they are uploaded and become part of Stargaze.

### How do I write a contract that works with Stargaze?

1. Write your contract, deploy it on [testnet](https://testnet.publicawesome.dev/marketplace), and make sure it works as intended.
2. If the contract charges any fees, be sure to use Stargaze’s developer-incentivized [Fair Burn](https://github.com/public-awesome/stargaze-contracts/blob/main/packages/sg-std/src/fees.rs#L10) mechanism. Developers can earn 10% of all fees that go through their custom contracts.
3. Submit a [Commonwealth](https://gov.stargaze.zone) post, explaining what your contract does.
4. After validating the project with the community, submit a governance proposal with the contract code. See the following command to submit your proposal: `starsd tx gov submit-proposal wasm-store -h`.

{% hint style="info" %}
Join Discord for more information on deploying on testnet. The testnet is completely permission-less. A faucet is also available in Discord.
{% endhint %}
