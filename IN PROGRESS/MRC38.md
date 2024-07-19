# MRC 38: Staking MOR for Code Contributors
## The Time & Dilution Based Power Factor Method 

### Link for Discussion on Discord:
https://discord.com/channels/1151741790408429580/1251994932688719922

### Status: In Progress
Confirmation from open source devs they can:
- 1. Develop these functions based on the existing Smart Contracts.
- 2. Solidity / EVM supports the math functions required to calculate the Power factor.

### Authors / Discord Name: 
Anon 866, David Johnston (Smart Agents), Anton (antonb), Anon (lachsbagel), Christopher (storm.father), Jon (jonisjon), Maxwell (scott_b_), Jeff (Jabo38), Luke (lukestokes)     

### Authors of Proposals On Similar Time Related Subjects: 
- mechaverse specifically from [MRC 36](/CLOSED/MRC36.md)
- With extensive feedback and alternative proposals from: kehndry

### Category: 
MRI #1 Smart Contracts Reference Implementation

## Summary: Fair Stake for MOR
All contributors should have equal access to build MOR by staking their weights. Currently this long-term return is only a natural function of capital rewards.

Fair Stake allows all contributors to be rewarded if they agree not to claim tokens for a set period of time. When instituted, contributors will have the ability to indicate the length of Fair Stake as part of a bid for weights.

Contributors who stake for long periods of time will see a better return on their weights. See below for a description of economic mechanisms.

## Rationale: Time Equals Alignment
Those Contributors of Code should have a way to express their committment to the project. Time is the logical way to express this alignment with the project.

## Dependencies: 
None.

## New Weights Requested: 
30,000 Weights

## Existing Weights: 
None.

## Deliverables: Smart Contract Updates 
The Distribution Smart Contract specifically with the two functions added.
1. MOR Staking function (delay MOR claims during certain UTCsecond heights).
2. Power Factor Added To MOR Reward Calculation.

## Qualification:
Same open-source developers that developed the Morpheus Smart Contracts thus far.

## Timelines
3 to 4 weeks from June 21st 2024

### Mini-FAQ:
- Am I required to stake my weights? **No.**
- Are my existing weights automatically staked? **No.**
- Can existing weights be staked? **Yes.**
- Can any amount of weights be staked? **Yes.**

**Example:**
>Developer A is bidding on a specific MRC deliverable. They don’t want to undervalue their contribution or be forced to compete with the lowest bidder.  They would rather stand behind good work that they are fairly compensated for.  So, Developer A requests a fair-but-competitive reward in weights, but adds a 48 month Fair Stake of the weights to their bid. Now the MRI maintainer can clearly see a new dimension of value when considering Developer A’s proposal.
>>>

### Value signaling.
Fair Stake allows all contributors to clearly and equally indicate their commitment to growing with Morpheus.  

## Analysis & Models:
- **Emissions Curve Calculator 7.21.2024**
https://docs.google.com/spreadsheets/d/1xTY7keBdPo2Nzm35Wdmu7ngP3NVIDebR/edit?usp=share_link&ouid=108805586783812761772&rtpof=true&sd=true

- **MOR Power Table**
https://docs.google.com/spreadsheets/d/1uEjozAcnEt-IWaSsu_BbYPRMUCkbwjwv/edit?usp=share_link&ouid=108805586783812761772&rtpof=true&sd=true

## General Description - Weight X Power = Proportion of MOR Rewards
It is necessary to implement a functionality where users can specify for what period they want to Stake the MOR tokens, in return the user will receive an increased proportionality in the MOR rewards. It is worth emphasizing that, none of these MOR Staking proposals increase the amount of tokens that are created. Rather, it changes your proportional rights to the amount of tokens that are being created in that SnapShot in a similar way that increasing your hash rate increases the amount of the portion of Bitcoin one mines.

Fair Stake intervals will be posted on GitHub. 

## Example MOR Power Factors
![ExampleMORPowerFactor](https://github.com/MorpheusAIs/MRC/assets/1563345/120f89c4-a497-469c-a15d-e8c5955feabd)
**Chart shows examples if the Contributor set time curves starting July 25th 2024**

![ProportionalityEquationMORStaking](https://github.com/MorpheusAIs/MRC/assets/1563345/4bcb4ef4-0f52-41e8-8449-b5832e94f639)

![Emission Earned Chart 2](https://github.com/MorpheusAIs/MRC/assets/1563345/7b8adc04-5da2-4ad9-9dd1-bd9060f90fed)

## Applying the Power Factor
A power factor can be applied at deposit, if the user specifies MOR Staking period. Or with a separate function on the smart contract - StakeClaim(). 
The MOR Stake period is specified in seconds, it can be any interval. When the Power Factor is applied in the context of Coding contributors it serves as part of the calculation for weights translating into MOR emissions. The longer a Contributor Stakes their MOR emissions into the future, the greater the proportion of the emissions they will earn.

## Restrictions
To implement such functionality, we need to carry a number of constraints and understand the important points:

- MOR Staking period can be set by the user or administrator (for non-automatic groups) at any time;
- MOR Staking period cannot be decreased; 
- MOR Staking period can be increased. At the time of the transaction, the new multiplier will be applied.
- until the end of MOR Staking period, the user will not be able to withdraw their MOR rewards.

## Changes to Smart Contracts
The Distribution contract and related interfaces will change. Updates to the smart contract on the network will need to be made.
