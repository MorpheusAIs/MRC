# Title: MRC 45 - Morpheus stETH Referral System

### Authors / Discord Name: 
Jeff McDonald (Jabo38), David Johnston (Smart Agents), Sergey Kozlov, Christopher (storm.father), Jon (jonisjon), Rene (rene9386)

### Link for Discord: https://discord.com/channels/1151741790408429580/1283848717392154737

### Status: IN PROGRESS

### Summary: 
Morpheus community members can create a referral address. Any other user can use the referral address when depositing stETH and earn a 1% bonus.

Additionally, since a capital depositor added stETH with a referral address, the community member who created the referral will receive up to a 5% bonus in MOR.

### Rationale: 
As a decentralised project with no centralised foundation, LLC, or core team entity, many of the traditional marketing strategies that other blockchain platforms and decentralised apps take to bring awareness to a project are not applicable.

Referral programs have traditionally been cost-effective marketing strategies. Businesses have often used them to successfully incentivize customers to refer new customers, thus aiding in word-of-mouth and peer-to-peer marketing.

Considering these points, a referral program is a rational and logical fit for the Morpheus community to explore. With advances in smart contracts, this can be entirely on-chain in a trustless and transparent model.  

### Mechanics of a Referral System:

**Referral address creation:** Community Member A (Alice) creates a referral that contains her wallet address. She is the referrer. 

**Staking stETH:** Community Member B (Bob) uses the referral wallet address created by Alice when sending a stETH staking transaction. Bob is the referee. Bob gets a 1% bonus for using Alice’s referral. 

**Claiming MOR:** Bob can claim MOR when he wants. 

**Claiming the referral bonus:** Alice can claim her referral bonus as she pleases, even if Bob has locked his MOR in accordance with the power factor curve.  

If the referral field in a staking transaction is empty, it means that no referral reward is applied.

### Rates for Referrals: 
A community member can earn up to 5% as a bonus when community members using their address deposit stETH.  This will come in four tiers of 3%, 4%, 4.5%, and 5%:

**Tier 0:** Community members with referrals that have less than 3.5 ETH deposited by addresses of all their referees will get a bonus of 3%.

**Tier 1:** With a minimum of 3.5 stETH having been deposited across all the capital depositors totaled, a referrer maker can get a bonus of 4%.

**Tier 2:** With a minimum of 35 stETH having been deposited across all the capital depositors totaled, a referrer maker can get a bonus of 4.5%.

**Tier 3:** With a minimum of 350 stETH having been deposited across all the capital depositors totaled, a referrer maker can get a bonus of 5%
