## MRC 53: Add Block Reward Emitted to Compute Subnets To Bootstrap Usage

### Status: **Proposal**

## Version 2 of Compute Emissions Smart Contract with Block Reward modeled after Builders Style Staking System + Compute Sessions
**Summary:** 
Today MOR emissions to Compute Subnets are based 100% on usage of AI models / agents as recorded in "sessions" between a Subnet and a user that opens the session. Without a block reward, their is a cold start problem where not enough Compute is being offered at a low price to attract Inference users to access the Morpheus Compute. As a result the Compute contributors have earned by far the least of any Contributor type in Morpheus.

![ComputeColdStart](https://github.com/user-attachments/assets/e178beeb-c08b-4086-9e3b-ba7c16f000ac)

This proposal is to introduce a "block reward" split between Compute Subnets based on the number / length of sessions they host, only limited by the amount of MOR Staked toward their Subnet. The intent is to increase the incentive for Compute Subnets to compete for these generous emissions of MOR and thus bootstrap the network into a robust number of Compute Subnets, Stakers, and users.

![V2 Compute Diagram](https://github.com/user-attachments/assets/01a035f9-8baf-4bb1-8b05-81ecb13cae81)

## Emissions Model: 
https://docs.google.com/spreadsheets/d/1gUV5r-ERVBLbF0dHLl66NXtKU6K2WxtUhoflT_o4mbM/edit?usp=sharing
![ComputePoolMorlord](https://github.com/user-attachments/assets/61c5782f-d9df-49c2-a22f-d7b103cb2923)

## Step 1. Changes to Existing Compute Smart Contracts to start Compute usage competition:
The existing Compute Smart Contract does most of the functions required for this updated version. The functions of Staking MOR or paying MOR to open sessions will all stay the same. The main aspect that will be updated is to compare the total sessions of all Subnets to generate a "weight" for each Subnet.

**Functions:**
- The Smart Contract records the "total session time" (aggregate session legnth of all sessions by Subnet) for each Subnet during a fixed period (1 day) as a "weight".
- The Smart Contract records the of total session time per day for ALL Subnets and calculates their "total weight".
- This Smart Contract calcualtes the percentage of weight for each Subnet based on their weight divided by the total weight. 

- Example: 10,000 seconds of total session length provided by Subnet XYZ out of 100,000 seconds of total session length hosted by all Subnets on March 15th.
Thus 10% of the block reward goes to Subnet XYZ.
3,231 daily emissions go to Compute Subnets.
10% of 3,254 equals 323 MOR rewarded for the daily period to Subnet XYZ.

## Step 2. Staking Alignment Check via Compute Smart Contract Modeled on Builder Type Staking
The existing Builder Smart Contract has all the logic for users Staking toward Subnets and rewarding MOR emissions on this basis. The change for Compute will be to simply pull these emissions from the Compute pool instead of the Builder one.

**Formula:** Amount Staked divided by total Compute MOR emitted since February 8th 2024.
- Example: 120,000 MOR is Staked divided by the 1,200,000 total MOR emitted for Compute equals 10% of 3,231 MOR per day, which is 323 MOR per day.
- Maximum Distribution: After staking equals aggregate amount emitted the total Compute pay out will be equal to the daily emissions of 3,231 to compute providers in proportion to their stake within the compute bucket. In other words when Staking of MOR exceeds 1,200,000 the daily emissions are capped at 3,231 MOR per day.
- In this example the say Subnet XYZ is Staking 120,000 MOR out of 1,200,000 total Staked by ALL Subnets, then their able to earn up to 323 MOR per day.

## Calculator Smart Contract: 
This new Calculator Smart Contract will look at the MOR emissions earned by Subnets from Step #1 as the maximum MOR it can recieve and check the amount from Step #2.
- If the amount of MOR Staked in Step #2 by Subnet XYZ are equal to or greater than the MOR available from Step #1 then ALL MOR credited in Step #1 are emitted to the Subnet by the Distribution Contract.
- If the amount of MOR Staked is Step #2 by Subnet XYZ are less than the MOR available from Step #1, then only the amount of MOR credited in Step #2 are emitted to the Subnet by the Distribution Contract.

## Addressing Self Hosted Sessions:
There’s been much discussion about how to mitigate the self hosted sessions the last year however, at the end of the day, the best solution may be to address this with token economics. 
- First there is a cost of hosting sessions carries with it on chain fees, and so there’s a drag to self hosted sessions. This will create a real on chain cost to self hosting sessions. Meaning it will be expensive to self host sessions, and over time real third party sessions will be more profitable and replace self hosted sessions over time. 
- Second, even self hosted sessions, imply, "proof of capacity", which has some value as it proves XYZ models / agents are hosted and available for those that have large scale demand for inference of models / agents.
- Third by checking the stake of MOR exceeds annual rewards at a minimum, the system creates an economic alignment and driving demand for the token by all compute subnets Staking more MOR.

## Conclusion:
This model creates a robust competition between Compute Subnets to open lots of sessions with users, but caps their MOR emissions to the amount of MOR they have Staked to their Subnet. Thus anyone creating synthetic sessions will at a minimum be creating demand for MOR via Staking greater than their potential rewards over 1 year, as APY on Compute Staking will start at around 75% APY.

## Additional Notes:
This means that there will be three ways to earn MOR as a Compute Subnet.
1. Compute emissions Proportional to the Staked MOR block reward / usage.
2. Compute Treasury pays emissions for usage of Compute sessions in addition.
3. Compute Smart Contracts / Router allows for direct payments of MOR for a session in addition.

## Benefits & Costs: 
1. Design allows for current Smart Contracts to stay the mostly same as deployed for payments of MOR based on usage and direct payments of MOR.
2. The Compute Smart Contract for Staking based MOR emissions is very similar to Builders V2 Smart Contract. With the only change being the pool ID the MOR is emitted from.
3. Thus only one new Smart Contract is required to do the calcuation of the usage weight & the Staked amount.
4. This proposal will release more MOR tokens into circulation than the current set of emissions to Capital, Code, & Builders. However this can be off set by the demand for MOR Staking and usage of Compute that this incentive will create. See the Emissions Model above for detailed estimates.
