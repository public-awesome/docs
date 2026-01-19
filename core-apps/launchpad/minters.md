# Minters

#### Vending Minter&#x20;

* Consists of a predetermined number of NFTs, already uploaded on IPFS, where the user can mint on Launchpad and sell on Marketplace.
* It has random / non-sequential minting that prevents sniping and MEV.
* Default time for Marketplace trading is two weeks upon launch. However, this can be changed after minter creation.
* Max number of tokens: 10,000.

#### 1/1 Minter

* For smaller/fine art collections. Tokens are minted on demand. That means you can create a collection and add new NFTs over time to that same collection.
* The NFTs are minted to the creator's wallet at the moment of the collection creation. That means there is no mint revenue; the token can be added immediately for trading on Marketplace.

#### Public Works / Generative Art Minter

* publicworks.art is a generative platform similar to Art Blocks and fx(hash). It is the first of its kind on Stargaze.
* &#x20;It generates the NFT image in real-time during the mint: neither the user nor the creator know what combination will be created.

#### Mutable Minter

* Allows updating the IPFS metadata/image of any NFT in a collection.
* Migrating a vending collection to a mutable collection is possible.

#### Free Minter

* With this minter, the minimum mint price is wavered. You may create a full free mint collection or a free whitelist collection with a paid public mint.

**Open Edition Minter**

* A single NFT that can be minted multiple times, within a time period. After the minter countdown ends, no more editions can be minted, including airdrops.
* An accessible way for creators to experiment, and for users to collect art pieces at an affordable price.

#### Badges

* Badges are NFTs POAPs. You may reward your community for participating in an event, or activity through badges.
* They can be either non-transferable or transferable.
* Badges are not sellable on Marketplace (yet).
* You may create a claimable badge that requires an action from the user, such as for an airdrop.
* Metadata for badges is written on-chain.
