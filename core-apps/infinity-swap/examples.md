# Examples

### **From a pool owner's perspective (buy and sell):**

Ana holds a lot of NFTs from the same collection (Sneaky Animals).

She wants to earn swap fees, so she creates a pool with both Sneaky Animals + STARS. That means she is offering to buy AND sell NFTs to/from the pool.

Knowing the royalties of the collection you are creating the pool of is very important.

Sneaky Animals royalties for Infinity is 0.5%.

Protocol fee is 0.5%.

Any user can come to Ana’s pool and buy a Sneaky Animal from it. The STARS get sent either to the pool or to her account. (depends on her settings) Any user can also sell a Sneaky Animal to Ana’s pool. Similarly, the NFT can get sent to the pool or to her account.

On each of those transactions, she will earn a Swap Fee. Let’s say Ana set the swap fee as 3%. That means on each transaction:

* 0.5% goes to Sneaky Animals
* 0.5% goes to the protocol
* 2% is hers (goes to her wallet)

The price gets adjusted according to the bonding curve.

### **From a pool owner’s perspective (buy):**

Bob wants to buy many Sneaky Animals. He sets a pool to only buy NFTs and add STARS to the pool. Creating a buy pool with linear bonding curve and 0 delta is equivalent to making many collection offers.

Bob may also set the bonding curve in which after every new buy, his offer is lower than the last one.

### **From a pool owner’s perspective (sell):**&#x20;

Chris wants to sell Sneaky Animals, without creating a wall on the floor price at the marketplace. He sets the pool to only sell NFTs and picks the ones he wants to sell. He can decide to sell all NFTs at the same price (with 0 delta).

Chris can also set the bonding curve to raise prices at each sell he makes.

### **From a user perspective (buy):**

Dan wants to buy a Sneaky Animal. He can check the Swap page for the best deal on that collection, while getting a random NFT from the pool. He can also pick and choose the Sneaky Animal of a specific pool, going to the “Buying NFTs” under “Pools” and selecting one of the pools available.

### **From a user perspective (sell):**

Eve wants to sell her Sneaky Animal. She can use the Swap for instant liquidity, selling her NFT to a buy-pool. The most interesting deal to Eve will be picked (as in, the pool that is buying for the highest price).
