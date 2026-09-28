# Dynamic Claim Difficulty Mechanism for Inference Providers and Beyond - MRC 91
Drafted: 2026-09-28

## Problem Statement:
Today the Staking of MOR is set to a static 1 year parameter for the claim lock time. 
So only a few longterm bullish inference providers are willing to offer Inference are in marketplace.

Morpheus needs more Inference providers to scale, however if we arbitrarily lower the claim time to Stake MOR to say 7 days, we may see more Inference providers flood in, but on the other hand this would create a strong incentive for providers to open sessions to themselves and thus game the system.

## Proposal For Dynamic Claim Lengths:
So rather than a static time parameter I propose a feedback mechanism similar to a traditional difficulty mechanism. If during a 1 week period the claiming of MOR by increases for example by 50%, then the withdrawal time period also increases by 50% in the next 1 week period. If the claiming of MOR decreases by 50%, then withdrawal time period decreases by 50%. 

The thesis here is that this dynamic system will create a competition and balance the system toward those who will hold MOR longer without excluding those that want to do some shorter term claims as long as the two are in balance.

## Anchoring The Target With MOR Demand:
What sets the base line? In other words, the dynamic parameter has to have an objective. In BTC blocks are targeting 10 minutes in length, the difficulty adjustment is used in Bitcoin to increase or decrease miner hash power difficulty to target 10 minute blocks averaged over 2 weeks.

It’s been said “there is only one liquidity pool”. So I propose the anchor ought to be based on demand for MOR. The system can’t pay out for value than it creates so it logically follows that using the yield buys of MOR from the Capital contributors as the basis for the target. So the difficulty will adjust based on if MOR buys by capital providers increases or decrease thus also adjusting than the MOR emissions to Inference providers.

So if buys of MOR are 1,000 MOR per week then MOR inference emissions should decrease or increase toward a lower target than that. Using the MOR claim time as the adjustment mechanism to shift claims to equal buys.

For example if 1,000 MOR are bought and a 500 MOR are burned and 500 locked for 16 years than up to 500 could be earned by Inference providers. Thus the target is 50% of demand.

Thus capital buys of MOR and Inference provider sells of MOR will balance over time with a bias toward more scarcity.

## Extending The Solution To Builders / Coders:
Following the same logic, the demand sink of using Inference generates a fee of 5% of the sessions emissions which should be burned and locked. This can set the reward level for the Coders. Builder demand balanced by Coder sales.

Break down the Builder / Code wall. If Inference is used the Coder / Builder gets emissions in 50% proportion. Builder subnets become purely mechanisms for directing Inference rewards, and Coders get those rewards. 

Extending The Mechanism to Capital Providers:
The same mechanism should be applied to Capital MOR claims. With 90 days we saw it was too long, and at 7 days is too short. Rather than just moving it to 30 days and making more future manual adjustments add the same MOR dynamic claim mechanism.

Benefits of this design. Everything is balanced toward real demand of MOR either from yield or from Inference and supply emissions is a reward that can’t be gamed as it produces less than it costs to no one will make MOR by burning / locking 1 MOR to earn 0.5 MOR.

## Implementation:
Review smart contacts for the parameter that will need to read MOR claims over time to calculate the emissions rates.

## Conclusions:
We can finally move to a self adjusting system of MOR emissions that balances across Inference, Capital, Builders, and Coders.

This proposal aims to make Morpheus Inference supply responsive to increases in demand without having the emissions exceed the liquidity available to pay for it.
