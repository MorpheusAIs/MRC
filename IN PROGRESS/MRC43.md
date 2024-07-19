# Protocol Owned Liquidity Upgrade to 2.0 Post Bootstrapping

### Status: IN PROGRESS 

### Discussion on Discord: https://discord.com/channels/1151741790408429580/1251996463127593141

## Update to "Building the Foundation: Phased AMM Deployment in Morpheus"
This MRC builds on a great work from MRC 9 to describe the phases of deploying the Protocol Owned Liquidity into the Uniswap AMM just after the bootstrapping period. 
https://github.com/MorpheusAIs/MRC/blob/main/IMPLEMENTED/MRC09.md

For the bootstrapping period the POL providing liquidity positions of both ETH and MOR made sense. 
But given there is now plenty of MOR tokens claimed & generally available for trading, it would seem logical to move toward the following POL pattern.

## Upgraded Protocol Owned Liquidity Pattern
- 1. stETH is collected and swapped to wETH.
- 2. 75% of the resulting wETH is used to swap for MOR from the Uniswap pool.
- 3. The remaining 25% of wETH would be paired with the 33.3% MOR as a full range liquidity position on Uniswap.
- 4. The 66.6% remaining MOR that were purchased are held in the Multisignature account and NOT deposited back into liquidity. 

## Burning & Tail Emissions
- This approach is the basis for implementing the Burn Function described in the white paper.
- The 50% of the MOR left after Protocol owned Liquidity Generation Event in the Multisignature account will be locked for 16 years. In order to function as the basis for the [the #2 epochs Tail Emissions](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/WhitePaper.md#tail-emissions-of-mor).
- The other 50% of the MOR held in the Multisignature account are sent to a permanent burn address and destroyed forever.

## Transitions In Phases Toward Ever More Scarcity Once Liquidity Is Established
- Bootstrap phase swapped 50% to add liquidity depth when it started.
- Moving to 75% MOR buy now that depth is solid, to add more emphasis on demand driver and scarcity.
- Eventually move to 100%  if it’s deemed that liquidity is sufficient (when adding more liquidity wouldn’t really do much) it’s time to move entirely to demand driver and scarcity. 

## Conclusion
This would seem to be most aligned with the spirit of the original design and white paper, as it would provide liquidity for MOR sellers.  
Both short term with the immediate buy of MOR, and long term with the full range wETH liquidity position.  
By withdrawing MOR purchased by POL and perodically removing MOR resulting from the wETH LP position it makes MOR ever more scarce.  
This way the PoL to would continue to deepen, and would add even more demand pressure as 75% would be swapped, and make it more scarce.  
