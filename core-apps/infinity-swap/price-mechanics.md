# Price Mechanics

The price for selling and buying varies according to the selected bonding curve for the pool (linear, exponential, or constant). The owner can deposit or withdraw assets into the pool at any time. They can also change the parameters of the pool at any time. Below, the pricing algorithm for each pool is described in detail:

#### Linear

Linear pools begin with a price equal to the **spot price** set by the user. After an NFT is purchased from the pool, the price will change to **spot price + delta**, where delta is an integer value set by the user. After an NFT is sold to the pool, the price will change to **spot price - delta.**

#### Exponential

Exponential pools also begin with a price equal to the **spot price** set by the user. After an NFT is purchased from the pool, the price will change to **spot price \* (1 + delta)**, where delta is a percentage value set by the user. This could represent for example a 5% increase in price. After an NFT is sold to the pool, the price will change to **spot price / (1 + delta).**

#### XYK

XYK pools have their buy and sell prices determined by the amount of STARS and NFTs held by the pool at any given moment. The traditional XY = K formula is used to determine pool pricing. Pricing roughly equals **number of tokens / number of NFTs.**
