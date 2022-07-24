---
cover: ../.gitbook/assets/OGImage1200x630.png
coverY: 0
---

# CosmWasm Smart Contracts

Stargaze runs community-governed CosmWasm. All this means is that custom smart contracts have to be uploaded via governance.

### Why community-governed CosmWasm?

Because Stargaze has zero gas, smart contracts have to be designed to not exceed compute or storage limits.&#x20;

If Stargaze was completely permission-less, it would be easy to upload a malicious contract that exploits zero gas. By going through governance, custom contracts can be reviewed by the community and core team.

### How do I write a contract that works with Stargaze?

1. Write your contract, deploy it on [testnet](https://testnet.publicawesome.dev/marketplace), and make sure it works as intended.
2. If the contract charges any fees, be sure to use Stargaze’s developer-incentivized [Fair Burn](https://github.com/public-awesome/stargaze-contracts/blob/main/packages/sg-std/src/fees.rs#L10) mechanism. Developers can earn 10% of all fees that go through their custom contracts.
3. Submit a [Commonwealth](https://gov.stargaze.zone) post, explaining what your contract does.
4. After validating the project with the community, submit a governance proposal with the contract code. See the following command to submit your proposal: `starsd tx gov submit-proposal wasm-store -h`.

{% hint style="info" %}
Join [Discord](https://discord.gg/stargaze) for more information on deploying on testnet. The testnet is completely permission-less. A faucet is also available in Discord.
{% endhint %}
