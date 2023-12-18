# Deploy to Mainnet

### How do I deploy to Stargaze mainnet?

Stargaze is a permissioned chain, meaning there is a governance process to adhere to. After familiarizing yourself with the [governance process](../../stars/protocol-governance.md), here's a template to follow for submitting an on-chain proposal.

To submit a governance proposal via the `starsd` CLI, you may follow the example below.

{% hint style="info" %}
If you don't have `starsd` on your machine, please follow [this guide](../../nodes-and-validators/getting-setup.md).
{% endhint %}

```shell
title="Smart contract you're proposing"
desc=$(cat desc.md | jq -Rsa | tr -d '"')
deposit="50000000000ustars"

starsd tx gov submit-proposal wasm-store your_contract_binary.wasm \
    --title "$title" \
    --description "$desc" \
    --deposit $deposit \
    --run-as $CREATOR \
    --from $PROPOSER \
    --gas 30000000 \
    --gas-prices 1ustars \
    --instantiate-anyof-addresses <stars addresses comma-separated> -y
```

**Note**: the `--instantiate-anyof-addresses` flags is particularly important, as it denotes which address or addresses are allowed to instantiate the stored code. This will likely be an EOA and a multisig, or something similar. It may be helpful to read the descriptions of all the flags by running: `starsd tx gov submit-proposal wasm-store --help`.

{% hint style="info" %}
Celatone is a tool a bit like Remix for Ethereum that enables querying and interaction with contracts. Give it a try at [https://stargaze-celatone-frontend-staging.vercel.app/mainnet](https://stargaze-celatone-frontend-staging.vercel.app/mainnet).
{% endhint %}
