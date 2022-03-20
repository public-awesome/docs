# CosmWasm Smart Contracts

Stargaze is one of the first, if not the first protocol to run CosmWasm in a permissioned environment. This means that smart contracts on Stargaze have to be approved by governance before being deployed.

### Why not permissionless CosmWasm?

If Stargaze allowed permissionless smart contracts, it would no longer be an application-specific chain for NFTs, and would be a generalized blockchain. If you’re looking to deploy a DeFi protocol, or another non-NFT related protocol, you’re probably better off deploying on Juno or Terra.

### Why permissioned CosmWasm?

Because Stargaze is an application-specific chain, custom contracts have to integrate with the rest of the protocol. By going through governance, custom contracts can be verified and reviewed before they are uploaded and become part of the Stargaze protocol.

### How do I built a contract that works with Stargaze?

1. Fork Stargaze smart contracts at: [https://github.com/public-awesome/stargaze-contracts](https://github.com/public-awesome/stargaze-contracts).
2. Add your smart contract as a Draft Pull Request, and tag members of the Core Team, including the Chief Intern. If your contract charges any fees, be sure to use Stargaze’s [Fair Burn](https://github.com/public-awesome/stargaze-contracts/blob/main/packages/sg-std/src/fees.rs#L10) mechanism, which burns STARS and rewards stakers.
3. Submit a signaling proposal on [Commonwealth](https://commonwealth.im/stargaze/), detailing what your contract does, and how it plans to integrate with and provide value to the Stargaze protocol and community.
4. After validating your project with community support, submit a Pull Request to be included as part of Stargaze’s contracts.
5. Once merged in, submit your contract to on-chain governance. See the following command to submit your proposal: `starsd tx gov submit-proposal wasm-store -h`.
