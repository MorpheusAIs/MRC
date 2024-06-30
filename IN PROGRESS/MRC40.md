# Title: MRC 40 "Staking MOR For Compute Providers"
## Sub Title: "The Time & Dilution Based Power Factor Method For Calculating Reputation Rank"

### Link for Discussion on Discord: 
https://discord.com/channels/1151741790408429580/1251995364693774336

### Status: 
In Discussion

## Authors / Discord Name: 
Anon 866, David Johnston (Smart Agents), Anton (antonb), Anon (lachsbagel) Christopher (storm.father), Jon (jonisjon), Maxwell (scott_b_), Jeff (Jabo38), Luke (lukestokes) , Nebuchadnezzar Crew 

### Authors of Proposals On Similar Time Related Subjects: 
- mechaverse specifically from [MRC 36](/CLOSED/MRC36.md)
- With extensive feedback and alternative proposals from: kehndry

## Category: 
MRI #1 Smart Contracts Reference Implementation

## Rationale: Time Equals Alignment
To implement economic alignment of Compute Providers, it is necessary to implement a functionality where users can specify for what period they want to Stake the MOR token, in return the user will receive an increased MOR reward and more reputation.

- 1. Staked MOR can inform the likelihood of the Compute provider being selected. Weight in Compute Provider Reputation.
- 2. Stake MOR can inform the maximum reward a Compute Provider can earn. So, for example, if 100 MOR are Staked for 1 Year, then the most the Compute Provider can earn is 100 MOR during 1 year of providing Compute.

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
4 weeks from June 21st, 2024.

## Analysis & Models:
- **Emissions Curve Calculator 7.21.2024**
https://docs.google.com/spreadsheets/d/1xTY7keBdPo2Nzm35Wdmu7ngP3NVIDebR/edit?usp=share_link&ouid=108805586783812761772&rtpof=true&sd=true

- **MOR Power Table**
https://docs.google.com/spreadsheets/d/1uEjozAcnEt-IWaSsu_BbYPRMUCkbwjwv/edit?usp=share_link&ouid=108805586783812761772&rtpof=true&sd=true

## Proportionality Equation
![ProportionalityEquationMORStaking](https://github.com/MorpheusAIs/MRC/assets/1563345/85cbddaf-1388-45b9-868a-5e3a64d6ab68)

## Emissions Earned Relative Power
![Emission Earned Chart 2](https://github.com/MorpheusAIs/MRC/assets/1563345/e10c604d-7b48-4060-92a1-6622c58937d4)

## Applying the Power Factor to Compute
A power factor can be applied at deposit, if the user specifies a MOR Staking period. Or with a separate function on the smart contract - StakeClaim(). 
The MOR Stake period is specified in seconds, it can be any interval. In the Compute context, this can be used to weight the reputation of Compute Providers more heavily for those with a longer time committment to the project expressed in the higher Power factor.

## Example Power Factor in Chart
![ExampleMORPowerFactor](https://github.com/MorpheusAIs/MRC/assets/1563345/4dd834fa-d901-48a3-b3a5-e4451c8c1665)
**Presumes a July 25th 2024 Start Date**

## Restrictions
To implement such functionality, we need to carry a number of constraints and understand the important points:

- MOR Staking period can be set by the user or administrator (for non-automatic groups) at any time.
- MOR Staking period cannot be decreased. 
- MOR Staking period can be increased. At the time of the transaction, the new multiplier will be applied.
- until the end of MOR Staking period, the user will not be able to withdraw their MOR rewards.

## Changes to Smart Contracts
The Distribution contract and related interfaces will change. Updates to the smart contract on the network will need to be made.

## Timelines
4 to 6 weeks from June 21st, 2024.

## APPENDIX: Reference Materials Including Analysis Reviewed For MRC
In order to design the optimal system, it is important to identify the key objectives to be accomplished. A properly designed system should focus its efforts on these objectives that it is meant to control and not expand outside its scope.

## MOR Compute Tokenomics - or the design by which Compute Providers are determined eligible - notes the following objectives:
- Fidelity
- Accuracy
- Precision 
- Consistency
- Reliability
- Faithful to requests
- Deter Adversarial Conditions - remove incentive or ability for the system to be gamed and non-value added.
- Align Compute Providers with the long-term success of Morpheus.
- Create a fair environment that encourages participation from a variety of Compute Providers.
- Design a system that has the ability to scale up over time, as outlined in the phased approach below.
- When demand increases, high-quality compute resources are incentivized to join the network. As a result, competition drives prices downward.

To ensure that proper analysis is conducted in determining the optimal system, this paper serves to identify a broad scope of viable methods, defining the basics of how they would operate, and laying out the pros and cons of each. Only after ample efforts have been taken to explore as many possibilities as possible, can a thoughtful recommendation be made.

### As such, the following options are ones that have been identified and will be explored throughout this paper:
- Minimum requirement stake (# of MOR) 
- Minimum requirement stake (% of supply)
- Top X stakers 
- Top X stakers, inclusive of multiplier
- Proportional to IPS
- Equal to X month earnings - variable
- **Fixed Staking Amount Equal to Eligible Earnings - Judged Most Fair, Scalable and Simplest To Implement**
- Entrance Fee - flat rate, scaled option, or bidding
- Add-On: No rewards for first X number of days
- Add-On: Stake + Burn

As each of the above items has its own pros and cons, the ultimate design may likely be a combination of several of these approaches. As much development is still underway, it allows Morpheus to take a slow and calculated approach to roll-out. This ensures that ample testing is conducted, and sufficient feedback is digested, that by the ultimate design will evolve over time as the ecosystem grows and matures. Not to mention, the design decisions made here will impact a wide variety of other aspects of Morpheus, and also be impacted by those other aspects as well. All of this requires thoughtful consideration of not only the direct impacts, but the second, third, and fourth order effects. Morpheus could consider a phased roll-out, something similar to the outline noted in the table below.

### Exploration of Viable Methods
In the following section, each method will be briefly described, additional notes will be added, and finally pros and cons will be documented. These outlines are meant to provide the general background of each method in consideration. Subsequent efforts will dive much deeper into each, and ultimately reach an overall recommendation as to which method, or methods, provide Morpheus with the best outcome.

### Minimum Requirement Stake (# of MOR)
**Brief Description:** A specific amount of MOR is noted as the requirement to be eligible as a Compute Provider. 

**Additional Notes:** None.

**Pros:** Simplistic approach. Static amount that gives Compute Providers certainty of if they’ll be eligible or not.

**Cons:** Doesn’t differentiate between large-scale and small-scale Compute Providers
Sets a cap on the number of Compute Providers, i.e. if 10,000 MOR stake is required and only 1,000,000 MOR are circulating, you could only have 100 providers.

### Minimum Requirement Stake (% of MOR)
**Brief Description:** A specific amount of MOR is noted as the requirement to be eligible as a Compute Provider. This amount will increase alongside the emission schedule of MOR, ensuring that Compute Providers must maintain their relative share of the MOR tokens in order to be eligible.

**Additional Notes:** None.

**Pros:** Simplistic approach. Static amount that gives Compute Providers certainty of if they’ll be eligible or not. Provides constant buy pressure as Compute Providers must obtain MOR at the inflation rate.

**Cons:** Doesn’t differentiate between large-scale and small-scale Compute Providers
Sets a cap on the number of Compute Providers, i.e., if 1% MOR stake is required, you could only have 100 providers.

### Top X Stakers
**Brief Description:** No specific amount of MOR is defined to be considered eligible. Willing Compute Providers stake MOR and the ones who are the top X stakers are the ones considered eligible Compute Providers.  

**Additional Notes:** This would be at the Compute Provider level, i.e., the sum of all nodes they operate.

**Pros:** Creates a competitive environment which operates as a free market
Consistent demand for MOR from Compute Providers.

**Cons:** Discourages, or outright eliminates, the ability for small-scale providers to participate. No incentive for providers to stake more than needed,i.e., if the top 10 stakers are eligible, they will do their best to always be 1 MOR ahead of the 11th highest staker. Would Compute Providers who stake, but don’t make the ‘active set’ get their MOR unstaked?

### Top X Stakers with Multiplier
**Brief Description:** No specific amount of MOR is defined to be considered as eligible. Willing Compute Providers stake MOR and the ones who are the top X stakers are the ones considered eligible Compute Providers. The only difference here is that the length of the staking matters, i.e., A provider who stakes 100 MOR for 1 year may be higher ranked than one who stakes 200 MOR for 1 month.

**Additional Notes:** This would be at the Compute Provider level, i.e., the sum of all nodes they operate.

**Pros:** Creates a competitive environment which operates as a free market 
Consistent demand for MOR from Compute Providers. Encourages longer term lockups.

**Cons:** Discourages, or outright eliminates, the ability for small-scale providers to participate. No incentive for providers to stake more than needed, i.e., if the top 10 stakers are eligible, they will do their best to always be 1 MOR ahead of the 11th highest staker. Would Compute Providers who stake, but don’t make the ‘active set’ get their MOR unstaked?

### Proportional to IPS (or some other Compute Metric)
**Brief Description:** The IPS (or some other Compute Metric) will determine the relative size of potential earnings that a Compute Provider will be bringing to the network. This directly ties to the earning power of that particular provider.

**Additional Notes:** None.

**Pros:** Net reduction in circulating supply during the lockup period as an amount equal to expected earnings would be immediately locked up. Proportional to size, allowing large and small providers to participate.

**Cons:** Based on estimate - as IPS does not necessarily translate directly to earnings.

### Proportional to Potential X Month Earnings - Variable
**Brief Description:** Compute Providers are required to stake MOR equal to the amount they anticipate earning based on a calculation when they bring a new node online. 

**Additional Notes:** This would be similar to the Proportional to IPS method, but would differ depending on some open questions regarding the pricing and inference cost procedures.

**Pros:** Net reduction in circulating supply during the lockup period as an amount equal to expected earnings would be immediately locked up. Proportional to size, allowing large and small providers to participate.

**Cons:** Based on an estimate - Providers could wind up earning less, or more, than the staked amount based on a variety of factors.

### Fixed MOR Staking Equal to Earnings
**Brief Description:** Compute Providers are required to stake MOR equal to the amount they want to be eligible to earn in an X month period. For example, a Compute Provider who stakes 10,000 MOR can earn up to 10,000 MOR from the Compute bucket.

**Additional Notes:** Providers could continue to add to their stake if they realize they are nearing their capped amount.

**Pros:** Whereas the proportional methods are based on future estimates that may not be realized (or may be over realized), this fixed approach ensures that a Compute Provider does not earn more than they have staked. Net reduction in circulating supply during the MOR Staking period as an amount equal to expected earnings would be immediately Staked.

**Cons:** If a Compute Provider earns all the allowable MOR quickly, then they may not want to stake additional, and less capacity is available making the remaining capacity more expensive… however, a profitable environment would likely encourage Compute Providers to obtain and stake additional MOR.

### Entrance Fee
**Brief Description:** Pay to play… it would cost X amount of MOR (which goes to the Protection Fund, PoL, or gets burned) in order to obtain a ‘license’ to operate. Could be different tiers as well - i.e., 100 MOR for a week, 1000 MOR for a year. Another consideration could be that it is reward based… Pay 100 MOR and you get to be a provider until you earn 200 MOR. 

**Additional Notes:** This could be a flat fee or a dynamic one based on a variety of metrics.

**Pros:** Reduction of supply of MOR, enhancing the scarcity and value.

**Cons:** Might discourage Compute Providers to outlay the upfront cost, given that the return is less certain than in other methods.

### Add-On: No Rewards for First X Days
**Brief Description:** Compute Providers must operate for X days successfully before they become eligible for rewards.

**Additional Notes:** Providers would be constantly, or randomly sampled, for testing during this process. This would likely be just an add-on to a more robust method.

**Pros:** Proving ground that doesn’t require payment of MOR while Compute Providers are tested. 

**Cons:** Similar to all other methods, but ongoing testing would be needed to ensure compliance doesn’t stop after the testing phase.

### Add-On: Stake + Burn
**Brief Description:** While not a standalone concept, this could be implemented as an add-on to any other methodology.

**Additional Notes:** Creates a burn mechanism for shorter staked duration (i.e. Stake for 52 weeks and no burn, but each week less than 52 you stake, you burn 0.1% of the MOR).

**Pros:** Encourages long-term staking.

**Cons:** Potentially makes spikes in demand harder to track - in situations where more providers may come online during a spike in demand, those same providers might be discouraged to lock up for extended periods thus increasing cost of inference to users.
