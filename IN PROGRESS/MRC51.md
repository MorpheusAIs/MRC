# MRC51: "Layered Liquidity" Protocol Owned Liquidity Update

## Context: 
Each time the PoL buys tokens from the Uniswap pool on Arbitrum it burns 1/3, locks 1/3 and sets a "full range" LP position in the pool with the last 1/3.
Instead of placing all the new wETH / MOR in the "full range" position, this proposal is to begin setting the LP position at the spot price to 10% higher than the spot price.
The second part of this proposal is to move part of the existing lower range PoL position at the current spot price to 10% lower than the spot price.

## Buy Side Change: Layering Deeper Liquidity Just Above The Spot Price
This will have the effect of "layering" deeper liquidity closer to the current spot price of MOR and enable smoother buying of MOR. 

Example: if the price of MOR is $20 at the time of the Protocol Owned Liquidity LP deployment, the LP range will be set from $20 to $22.
 
## Benefits of Deeper Buy Side Liquidity: 
- 1. Those wanting to buy MOR will have access to more concentrated Liquidity closer to the market place.
- 2. This approach will reduce the slippage for those buying MOR.
  
## Sell Side Change: Layering Deeper Liquidity Just Below The Spot Price
Reset a portion of the lower LP positions say 30% to create deeper liquidity at the current spot price any 10% below the current spot price to enable smoother selling of MOR.

Example: if the price of MOR is $20 at the time of the Protocol Owned Liquidity LP deployment, the LP range will be set from $20 to $18.

## Benefits of Deeper Sell Side Liquidity: 
- 1. The full range approach is leaving Liquidity too spread out, this change makes liquidity more accessable near the spot price.

## Clarifications & Trade Offs:
- The change will happen gradulally with new value that flows each week into the Protocol Owned Liquidity.
- The second change will move only part of the PoL liquidity to just below the current MOR price.
- The update to the PoL has two potential costs: 
A: Dealing with added complexity managing the PoL of figuring out/managing those concentrated positions.  
B: Has the effect of placing a "sell wall" & "buy wall" very near the current price which will make any price appreciation effect from buying MOR more muted. 
