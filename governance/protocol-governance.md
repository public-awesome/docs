---
cover: ../.gitbook/assets/Stargaze_new_logo_black_bg_padding.png
coverY: 0
---

# Stargaze Governance

Community governance is a key part of Stargaze. Governance is performed via on-chain proposals and stake-weighted voting. Based on proposal outcomes, the blockchain performs automated actions.

Because blockchain operations are non-reversible, proposals should be first discussed before being submitted as an on-chain proposal. Proposals submitted to the chain should be well-written, comprehensive, and leave no room for ambiguity or misinterpretation.

On-chain proposals should follow the following process:

1. Gauge community support for your proposal by bringing it up on Stargaze’s social media such as [Discord](https://discord.gg/stargaze), [Twitter](https://twitter.com/stargazezone), and [Reddit](https://www.reddit.com/r/stargaze).
2. Write a post on [Commonwealth](https://commonwealth.im/stargaze/). This is where you can fine-tune the parameters and specific asks for your proposal. Software upgrades and contract uploads by the core team do not need to be posted to Commonwealth first.
3. For smart contract uploads, contact the Core Team for a free review and audit of your code.
4. Create an on-chain proposal with very clear, specific, and actionable items. At this point, all issues have been flushed out in the previous steps. This is considered the definitive version of a proposal and results in an on-chain action upon passing.

Proposals that don’t go through these steps will get a de-facto **No With Veto** vote by Stargaze Foundation.

## CLI

To submit a governance proposal via the `starsd` CLI, you may follow the example below.

{% hint style="info" %}
If you don't have `starsd` on your machine, please follow [these instructions](../nodes-and-validators/getting-setup.html).
{% endhint %}

```shell
title="Smart contract you're proposing"
desc=$(cat desc.md | jq -Rsa | tr -d '"')
deposit="20000000000ustars"

starsd tx gov submit-proposal wasm-store your_contract_binary.wasm \
    --title "$title" \
    --description "$desc" \
    --deposit $deposit \
    --run-as $CREATOR \
    --from $PROPOSER \
    --gas 30000000 --gas-prices 0ustars -y
```
