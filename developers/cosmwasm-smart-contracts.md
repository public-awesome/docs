---
cover: ../.gitbook/assets/Stargaze_new_logo_black_bg_padding.png
coverY: 0
---

# CosmWasm Smart Contracts

Stargaze runs community-governed CosmWasm. All this means is that custom smart contracts have to be uploaded via governance.

### Why community-governed CosmWasm?

Because Stargaze has zero gas, smart contracts have to be designed to not exceed compute or storage limits.&#x20;

Without going through governance, it would be easy to upload a malicious contract that exploits having zero gas (such as a state bloat attack). By going through governance, custom contracts can be reviewed by the community and core team.

### How do I write a contract that works with Stargaze?

1. Write your contract, deploy it on [testnet](https://testnet.publicawesome.dev/marketplace), and make sure it works as intended.
2. If the contract charges any fees, be sure to take advantage of Stargaze’s Developer Royalties. Developer Royalties enables developers to earn 50% of all fees that go through their custom contracts.
3. Submit a [Commonwealth](https://gov.stargaze.zone) post, explaining what your contract does, with a link to the source code. Smart contracts on Stargaze are required to be open source. Non-contract code such as frontend and backend may be private.
4. Contact the Core Team for a review and audit of your code.
5. After validating the project with the community and team, submit a governance proposal with the contract code. See the following command to submit your proposal: `starsd tx gov submit-proposal wasm-store -h`.

{% hint style="info" %}
Join [Discord](https://discord.gg/stargaze) for more information on deploying on testnet. The testnet is completely permissionless. A faucet is also available in Discord.
{% endhint %}

{% hint style="warning" %}
Developer Royalties cannot be combined with bounties or Community Pool funding. For example, if you receive Community Pool funding for your contract, it cannot also receive Developer Royalties.
{% endhint %}
