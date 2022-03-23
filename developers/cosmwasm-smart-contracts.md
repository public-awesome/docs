# CosmWasm Smart Contracts

Stargaze is one of the first, if not the first protocol to run CosmWasm in a community-governed environment. This means that smart contracts on Stargaze have to be voted on by the community and uploaded via governance.

### Why not permissionless CosmWasm?

If Stargaze allowed completely permissionless smart contracts, it would no longer be an application-specific chain for NFTs, and would be a general-purpose blockchain. If you’re looking to deploy a DeFi protocol, or something that doesn't integrate with Stargaze, you’re probably better off deploying on Juno or Terra.

### Why community-governed CosmWasm?

Because Stargaze is an application-specific chain, custom contracts have to integrate with the rest of the protocol. By going through governance, custom contracts can be verified and reviewed before they are uploaded and become part of the Stargaze protocol.

### How do I write a contract that works with Stargaze?

1. Fork Stargaze smart contracts at: [https://github.com/public-awesome/stargaze-contracts](https://github.com/public-awesome/stargaze-contracts).
2. Write your contract, deploy it on testnet, and make sure it works as intended.
3. Add your contract as a draft pull request. If it charges any fees, be sure to use Stargaze’s [Fair Burn](https://github.com/public-awesome/stargaze-contracts/blob/main/packages/sg-std/src/fees.rs#L10) mechanism, which burns STARS and rewards stakers.
4. Submit a signaling proposal on [Commonwealth](https://commonwealth.im/stargaze/), detailing what your contract does, and how it plans to integrate with and provide value to the Stargaze protocol and community. Also include a request for funds to get your contract audited.
5. After validating your project with community support, submit a governance proposal requesting funds for an audit.&#x20;
6. Following the audit, submit a pull request to be included as part of Stargaze’s contracts.
7. Once merged in, submit your contract to on-chain governance. See the following command to submit your proposal: `starsd tx gov submit-proposal wasm-store -h`.
