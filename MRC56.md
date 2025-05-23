# MRC 56: Design Options For Builders V2 Migration
The testing community has identified some fundamental trade offs with the version 2 of the Morpheus Smart Contracts.
These are important trade offs to consider as the introduction of a trusted third party goes against the values of Morpheus as a project.
For these reasons Migration of the Subnets to V2 should be moved to after these issues have been addressed.

## The 4 functions / features / trade offs of Builders V2 are:
- Multichain Support (Base + Arbitrum L2s on Ethereum)
- Requirement for an Oracle (multisig proposed)
- Requirement for an Escrow (multisig proposed)
- Power Factor

In order to gain Multi chain support requires the introduction of an Oracle & an Escrow.
The use of the Power Factor also adds complexity and re-enforces these requirements.

I've proposed a simplified scenario. 
However to achieve it the trade off is to only deploy to Base instead of multiple L2s and the Power Factor has to removed. 
Until Ethereum has cross L2 support for transactions, I think that is the best set of trade offs.

# Technical Options to be Revisited 
Worth revisting the single chain approach when ERC 7683 is implemented in mainnet Ethereum and L2s.
Details at this website: https://www.erc7683.org/

## Design Options Details:
![DesignSpaceV2](https://github.com/user-attachments/assets/31d3a03f-b4ee-4218-acdc-942fa2db622c)

## Real World Data on Chain Usage For Builders:
- 1. Most of the Subnets are Building / bootstrapping an agent, app, website, service.
- 2. To my knowledge only Coincap is using the Builders for payment as access to a product and Venice however not at a meaningful scale.
- 3. As for which chain the vast majority of Builders are on Base, again with the exception of Coincap & Venice.
- 4. Of the Stakers 300,000 are to a Builder Subnet (mostly on Base), 600,000 are self Stakers (mostly on Arbitrum).
- 5. If the goal is NEW people buying / using MOR to Stake to Builders most of that is on BASE. As is Venice. As are Coinbase's Agent tools and all the agent tools, as are the largest volumes.

## Conclusion on Question about Multichain Support

## Plan for Multi Chain Support:
- Stage 1: Support Arbitrum and Base (manual calculation) for May 15th (testing dependent).
- Stage 2: Coincap to help with Script and Hosting for June 15th / July 15th (testing depending).
- Stage 3: Switch to automated intents when available on Ethereum L2s (when ERC 7683 is implemented in mainnet Ethereum and L2s. Details at this website: https://www.erc7683.org/)
