# Whitelists

**Standard Whitelist**

* Adds a whitelist phase to the minter.
* Duration, mint price, max tokens, and whitelist addresses are added to this whitelist.&#x20;
* New addresses can be added after creation, or when the whitelist is live. You cannot remove addresses once the whitelist is live.
* Maximum of 10k addresses.

**Whitelist Flex**

* Adds a whitelist phase to the minter, and can be tailored individually by each wallet.
* The max number of tokens is determined individually. (One wallet can mint 1, another can mint 2, etc).
* Duration and mint price are the same for everyone on the whitelist flex.
* New addresses can be added after creation, or when the whitelist is live. You cannot remove addresses or change allocation of a wallet once the whitelist is live.
* Maximum of 10k addresses.

**Merkle Tree Whitelist**

* Ideal for a large amount of addresses. This whitelist leverages merkle tree system to allow for a large data, which would not be possible (or too expensive) on-chain.&#x20;
* Duration, mint price, max tokens, and whitelist addresses are added to this whitelist.&#x20;
* You cannot change the whitelist once it is deployed, due to how it's constructed. Merkle Tree validates through a unique hash, and because of that, it is not "editable".
* Maximum of 20 Mb (around 400k addresses)
