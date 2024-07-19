# MRC 41: MOR Staking For Builders
## The Time & Dilution Based Power Factor Method For Calculating Proportionality of Emissions

### Link for Discussion on Discord: 
https://discord.com/channels/1151741790408429580/1251995756332843189

### Status: 
Pending

### Authors / Discord Name: 
Anon 866, David Johnston (Smart Agents), Anton (antonb), Anon (lachsbagel), Christopher (storm.father), Jon (jonisjon), Maxwell (scott_b_), Jeff (Jabo38), Luke (lukestokes)   

### Authors of Proposals On Similar Time Related Subjects: 
- mechaverse specifically from [MRC 36](/CLOSED/MRC36.md)
- With extensive feedback and alternative proposals from: kehndry
- Builds on MRC22: [A Free Market Mechanism To Direct MOR Rewards Toward Smart Agent & End User Application Builders](https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC22.md)

## Diagrams

### Diagram 1 Builders Register Address and Staking Duration
![Diagram1MORStakingBuilders](https://github.com/user-attachments/assets/153048b5-7b61-4f62-8ebf-aa972f623be2)

### Diagram 2 End Users Stake MOR Toward Projects
![MORBuilderStakingDiagram2](https://github.com/user-attachments/assets/21539a33-d96b-4390-9777-38ec6eb3f070)

### Diagram 3 MOR Emissions Go To Builders Based on MOR Staking times Power Factor
![MOREmissionsDiagram3](https://github.com/user-attachments/assets/cd2439f0-4952-4996-8eb7-765c8d1ccb6e)

### Category: 
MRI #1 Smart Contracts Reference Implementation

## Rationale: Time Equals Alignment
To implement economic alignment of Builders, it is necessary to implement a functionality where users can specify for what period they want to Stake their MOR tokens. It is necessary to implement a functionality where users can specify for what period they want to Stake the MOR tokens, in return the user will receive an increased reputational signal to their project.

## Dependencies: 
None.

## New Weights Requested: 
30,000 Weights

## Existing Weights: 
None.

## Deliverables: Smart Contract Updates 
The Distribution Smart Contract specifically with have a the two functions added.
1. MOR Staking function (delay MOR claims during certain UTCsecond heights).
2. Power Factor Added To MOR Reward Calculation.

## Qualification:
Same open source developers that developed the Morpheus Smart Contracts thus far.

## Analysis & Models:
- **Emissions Curve Calculator 7.21.2024**
https://docs.google.com/spreadsheets/d/1xTY7keBdPo2Nzm35Wdmu7ngP3NVIDebR/edit?usp=share_link&ouid=108805586783812761772&rtpof=true&sd=true

- **MOR Power Table**
https://docs.google.com/spreadsheets/d/1uEjozAcnEt-IWaSsu_BbYPRMUCkbwjwv/edit?usp=share_link&ouid=108805586783812761772&rtpof=true&sd=true

## Proportionality Equestion For MOR Staking
![ProportionalityEquationMORStaking](https://github.com/MorpheusAIs/MRC/assets/1563345/da21a701-60e7-4aba-87c1-dfe9278000bd)

## Emissions Earned By Realative Power
![Emission Earned Chart 2](https://github.com/MorpheusAIs/MRC/assets/1563345/88608be1-3199-48d0-8e08-2d7de633e241)

## Example Chart
![ExampleMORPowerFactor](https://github.com/MorpheusAIs/MRC/assets/1563345/8ff10a90-cdd3-4d65-9915-59f20fc55dbf)
Presumes a July 25th 2024 start date

## Applying the Power Factor
A power factor can be applied at deposit, if the user specifies MOR Staking period. Or with a separate function on the smart contract - `StakingClaim()`.  
The MOR Staking period is specified in seconds, it can be any interval. 
When a power factor is applied, the user's "protion" of the stETH pool increases, depending on the power factor.

## Restrictions
To implement such functionality, we need to carry a number of constraints and understand the important points:

- MOR Staking period can be set by the user or administrator (for non-automatic groups) at any time;
- MOR Staking period cannot be decreased; 
- MOR Staking period can be increased. At the time of the transaction, the new multiplier will be applied.
- Until the end of MOR Staking period, the user will not be able to withdraw their MOR rewards.

## MOR Rewards for Builders in Plain English
Example For MOR20 & MRC21 Projects
- 1. Builder projects add their address to the decentralized registry (permissionless back end).
- 2. Projects listed (community run front ends) by decision of the Front end maintainer.
- 3. Users or the project itself can Stake existing MOR toward the project’s address, for 1 year for example.
- 4. The Project picks the length of its Staking period of its MOR rewards (future emissions) setting its Power Factor.
- 5. Rewards equal the weight of the project calculated by number of MOR Staked times the Power Factor.
- 6. Builders get rewards out of the 24% of emissions are paid out in proportion to the total weight.
- 7. Builders get rewards up to the amount of MOR Staked to their project over a 1 year period.

## Outcomes of This Design:
- Open competition by Builders to get as many MOR Stakers toward their project as they can.
- Open competition by Builders to Stake their future MOR emissions over time (get a higher power factor).
- Leaves it up to Builders how to incentivize their users to Stake MOR (Venice Pro accounts MOR Stakers for example).
- Permissionless. Anyone can register but Front End Maintainers decide what to highlight.
- Self Stakers will get little rewards unless they Stake up their MOR for years, in which case its also for Morpheus.

## The Builder Receives MOR as a Payment or Staking Example
- A. 0.35% Fees from MOR payments to Builders goes to the Morpheus protocol owned liquidity.
- B. 0.35% Fees on all Staked MOR withdrawn from a project goes to the Morpheus protocol owned liquidity.

## MOR Staking in Relation to Builder Rewards - Rank & Reputation in "Morpheus Agent Router"
Projects are listed on the decentralized registry with their MOR20 or MRC21 addresses.
- A. Projects Staking of MOR rewards into the future.
- B. Staking time length results in Power Factor applied to the Staked MOR. 
- C. Weight from MOR Stake times Power equals Total Rank Weight or reputation in the system.
- D. Total Rank Weight compared to all others determines rank in the Morpheus Agent Router (Corrdinator Agent / Front Ends).

## Changes to Smart Contracts
The Distribution contract and related interfaces will change. Updates to the smart contract on the network will need to be made.

## Timelines
10 weeks from June 21st 2024.
