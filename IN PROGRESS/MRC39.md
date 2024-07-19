# MRC 39: Staking MOR for Capital Providers
## The Time & Dilution Based Power Factor Method 

### Link for Discord: 
https://discord.com/channels/1151741790408429580/1251995170178596966

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

## Rationale: Time Equals Alignment
In the case of Capital, a negative feedback loop is possible in the current mechanism that has been revealed via the real world data. That is to say, if the price goes down, the amount of stETH goes down. Because the stETH declines the competition to earn MOR declines. Thus reducing the cost to acquire MOR. So the remaining stETH still gets MOR for 74% less than the ETH it took to earn it. And because there is no time delay function, an attacker can play out this game theory and benefit from the declining price and still be making ETH returns regardless of if MOR is $100, $50, $10, $1. Selling all their MOR every week when the Protocol Owned Liquidity buys. It's not about the price being up or down, it's a negative feedback loop in being able to withdraw more ETH than contributed instantly. 

It's clear in the data The Time element closes this negative feedback loop as the price moves up and down over Time make the game of selling all the MOR for ETH too risky for short-term holders.

During the bootstrapping period from February 8th 2024 to May 8th 2024, when there was a 90 day delay in the MOR claiming and the tokens were not trading yet, it prevented this negative feedback loop.

**Decision Tree:**
- Is there a real architecture issue to address? Yes or No. **Clearly Yes.**
- If yes, then what is the best mechanism to address the issue? **Time is the only objective function proposed.**
- What should the incentive be to delay MOR claims over time? **The Dilution Rate based Power Factor is the only objective function proposed.**
- How long should the Delay function be set for? **6 Years being long enough to signal time committment**

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
4 weeks from June 21st 2024

## Analysis & Models:
- **Emissions Curve Calculator 7.21.2024**
https://docs.google.com/spreadsheets/d/1xTY7keBdPo2Nzm35Wdmu7ngP3NVIDebR/edit?usp=share_link&ouid=108805586783812761772&rtpof=true&sd=true

- **MOR Power Table**
https://docs.google.com/spreadsheets/d/1uEjozAcnEt-IWaSsu_BbYPRMUCkbwjwv/edit?usp=share_link&ouid=108805586783812761772&rtpof=true&sd=true

## General Description
It is necessary to implement a functionality where users can specify for what period they want to Stake their MOR tokens, in return the user will receive an increased portion of the MOR emissions while they have their stETH deposited in the Morpheus smart contract.

It is worth emphasizing that, none of these MOR Staking proposals increase the amount of MOR token emissions that are created. Rather, it changes a Contributors proportional rights to the amount of tokens that are being emitted during a period they contribute their value. In a similar way that increasing a miner's hash rate increases the amount of the portion of Bitcoin they mine.

![ProportionalityEquationMORStaking](https://github.com/MorpheusAIs/MRC/assets/1563345/a6b32722-ccb8-400e-85ca-d97a4a7e4c3e)

![Emission Earned Chart 2](https://github.com/MorpheusAIs/MRC/assets/1563345/d4e1d376-b16e-4691-9060-95add8dd043d)

## Applying the Power Factor
A power factor can be applied at deposit, if the user specifies MOR Staking period. Or with a separate function on the smart contract - StakeClaim(). 
The MOR Staking period is specified in seconds, it can be any interval.
When a power factor is applied, the user's "protion" of the stETH pool increases, depending on the power factor.

## Example MOR Power Factor
![ExampleMORPowerFactor](https://github.com/MorpheusAIs/MRC/assets/1563345/b44153b0-021b-4095-b52a-2c121f4bb5ac)
**Chart examples based on July 25th as the date the Contributor executes the MOR Staking function.**

## Restrictions
To implement such functionality, we need to carry a number of constraints and understand the important points:

- MOR Staking period can be set by the user or administrator (for non-automatic groups) at any time;
- MOR Staking period cannot be decreased; 
- MOR Staking period can be increased. At the time of the transaction, the new multiplier will be applied.
- until the end of MOR Staking period, the user will not be able to withdraw their MOR rewards.

## Changes to Smart Contracts
The Distribution contract and related interfaces will change. Updates to the smart contract on the network will need to be made.

## Timelines
4 weeks from June 21st 2024

## Appendix Of Analysis:

## Secondary Effects Such The Rise of Liquidity Staking Tokens for MOR

### Liquid Locker at the protocol level:
- (1) Most important fundamental piece of allowing for this at the protocol level would mean having some sort of receipt token(s) that whoever owns it at the time of the claim can use to claim the underlying MOR rewards. This would preferably be a form of fungible token (e.g. if you lock rewards for 100 stETH for 1 year you get 100 veMOR1yr or something along those lines), but it could also be an NFT of the claim position. If you sell 50 of your 100 veMOR1yr before the unlock time whoever has the other 50% gets to claim 50% of the rewards etc, at unlock.

- (2) This does get a little complex because if you get your receipt token and then withdraw your stETH 7 days later, the unlock will only be worth 7 days of rewards + multiplier instead of 1 year worth so its difficult in this context to make them fungible vs NFTs.

- (3). Maybe a way to solve this would be to have “lock periods” e.g. every month there is a 30 day period in which locks can be made and then the time locks are bundled together for the receipt tokens and the amount of receipt tokens you get is proportional to your lock time (similar to how something like veCRV is generated). This would allow fungibility among locks at least in terms of monthly “vintage” of that lock.

- (4). If done correctly the receipt tokens should trade for approximately about what they will be worth at unlock date in MOR (unknown, but more knowable as you get closer to the date) but pro-rated to the point of time +/- some amount of speculative/market discount for the illiquidity of the claim at the time.

- (5). The existence of something like this also lets people speculate and buy the “early vintage” receipt tokens if they want to get a Power factor that is no longer available and someone is willing to sell.

- (6). One big issue to solve with fungible (preferred) vs NFT receipt token is how to handle if the stETH has been pulled or not (not much incentive to keep stETH in the system once receipt tokens are sold).

- (7) A way to handle this that may solve some of the above discussed issues would be to setup a new smart contract that will serve as the protocol liquid locker for MOR (and this would not affect the initial power factor lock code/smart contract as it could be built up a level from that afterwards). This could work by setting up standard unlock dates (like Dec 2024/Dec2025/Dec 2026 etc) requiring stETH that gets locked in the liquid locker locking up their stETH until that unlock date that is chosen and then issuing those who lock up their stETH in this way receipt tokens like MORstETHdec2024 (or something akin to that). You would get a proportional amount of MORstETHdec2024 based on how much stETH you locked until the unlock date based on the power multiplier and then it would = your locked principal (in stETH) + all MOR rewards accumulated during that time at time of unlock.

- (8) This (7) is a pretty cool solution because it allows for users to optionally lock up their stETH for the period of time and get the liquid receipt asset without being forced to lock up their stETH if they don’t want to (since they can still do the normal lock which allows for withdraw after 7 days but does not come with the liquid receipt token) which solves one of the aspects Anon866 was talking about, guaranteeing an amount of yield to the protocol for some period of time.

- (9) Additionally, it allows the splitting up of the underlying principal (the stETH which can be withdrawn at maturity) and the “yield” (the MOR rewards accumulated during the time period) in a Pendle like manner. So people could actually trade these assets separately such that when you redeem PTMORstETHdec2024 you get the underlying stETH (and you may have been able to buy these at a steep discount creating fixed ETH “yield” during the time frame which may be above standard market rates) and the YTMORstETHde2024 separately (which would let you claim all the proportional MOR rewards at maturity).

- This allows for some really cool dynamics where someone can also split off their YT and sell it in advance at a discount (all without ever selling any MOR that hits the market) if you want to “yield farm” in some way without it being a net negative to the protocol necessarily.
