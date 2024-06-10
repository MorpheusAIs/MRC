# Waterloo Community Apps Builder Model

---

## Status 
**April 1, 2024: In Progress via MRC22**

---

## Introduction
The Morpheus whitepaper describes the intent of having the Community Builder rewards go towards those front ends, websites, apps and tools that make the Morpheus network more accessible. The rewards for the Morpheus Community Builders are outlined as 24% of MOR emissions. In this proposal, additional details describe how the emissions will be distributed based on the different proofs.

The Web3 community has long suffered from a lack of front-end development. This is mostly due to protocols only offering a reward for proof of work (Compute) or proof of Stake (Capital), thus there are normally no resources directed toward those building at the application layer. The Morpheus network is unique in that it rewards developers of the Protocol, Network, Smart Contracts, Smart Agents, Websites & Dapps the Community uses. In this way Morpheus is a truly full-stack project, extending its rewards beyond the back-end functions, right up to front ends that serve the end users.

## Types of Rewards
By using the weights below, the community rewards will make each of the core functions of the Morpheus Network more broadly accessible and increase the Morpheus Code, Compute, and Capital resources.

## 1. MOR Staking - A Free Market Mechanism To Direct MOR Rewards Toward End User Applications
Builders of Smart Agents and other End User Applications will receive 8% of all MOR emissions.

These rewards will be directed in proportion to the MOR holders who "Stake" their MOR into the MOR20 Smart Contract for a specific Smart Agent.

So for example if a MOR holder has 1% of the MOR in circulation and Stakes it toward "DeFiAgent 420 (DA420)", then for as long as that MOR is Staked, the Morpheus protocol will direct 1% of the 8% of MOR emissions (0.08% of all 14,400 daily MOR emissions = 11.52 MOR per day) toward the DeFiAgent 420's AMM Uniswap pool. In return MOR Stakers earn new tokens in the projects they Stake towards.

**This MOR Staking approach has some compelling benefits:**
- Thus the MOR token will become the common trading pair for the Protocol Owned Liquid of every project launched on Morpheus (like ETH is for projects on Ethereum).
- This effectively extends the model Morpheus has already proven with stETH to MOR as the means of bootstrapping projects on top of its platform.   
- Holders of the MOR token get to individually express which projects they think are most worthy of support.
- Holders of the MOR token gain tokens in projects building on Morpheus without having to sell their MOR. 
- The Morpheus protocol sends all rewards directly to the project & the Stakers and so no central points of failure are created in the new projects.
- The project creates a straight forward path to rewarding Coders and thus attracts builders to maintain / expand its Code base.
- Projects get access to Compute (as MOR holders have access to Inference on Morpheus) since the project is holding MOR in the Protocol Owned Liquidity.  This will power their Smart Agent interactions.

## 2. Capital Front Ends
Builders of front ends for the Capital Providers will receive 8% of all MOR emissions.  

For example, a developer that creates an easy to use app or website that funnels Capital into the Morpheus Capital Provider smart contract would get a part of the 8% emissions pro-rata to the capital their public key tagged to the capital provision transaction.  

“Capital” is defined as the real-time Ethereum (ETH) value of a deposited asset.  

In determining the best method for allocation emissions for Capital Front Ends, Morpheus considered three alternatives. Each focuses on a pro-rata distribution methodology, but differ in the time horizon considered:  
- **Daily** - Emissions are distributed based on daily capital deposits. The primary benefit of this methodology is that it continually encourages and rewards new depositors. However, there are a couple of downsides. First, capital deposits won't be smooth - 10 stETH could be deposited on one day and 100 stETH the next. As such, the Community Capital Front End emissions would be greatly disproportionate to the capital contributed as a full day’s emissions would be provided for 10 stETH one day and 100 stETH the next. Second, this could result in a manipulation of the system. Since it would be limited to a one day time horizon, users could repeatedly deposit to earn the Community Capital Front End emissions, then withdraw funds and deposit a day or two later to earn more again.
- **Cumulative** - Emissions are distributed based on the cumulative capital deposits to date. This methodology distributes emissions based on the value of capital provided, regardless if that capital was contributed on a particular day, or months/years in the past, so long as it remains deposited. The downside to this approach is that it could discourage builders to develop new front ends. If a large amount of capital is already allocated, then incremental amounts will be relatively insignificant - meaning builders are less incentivized to continue building for an ever smaller piece of the pie.
- **1 Year Duration** - Capital deposits through a front-end are relevant for one year so long as they remain deposited. Emissions are distributed based on the pro rata share of the trailing one year deposits. The length of the timeline could be set to any number of days/years. The goal would be to find the appropriate balance which encourages new front end development to solicit capital while removing unnecessary transactions and potential exploitation.

**Multi-Asset Considerations.**  
stETH on Ethereum is the only capital currently allowed to be contributed. Over time, more assets and more chains may be added. With additional assets deposited as capital, it raises several complexities that must be accounted for:  
- **Price Feeds** - All currencies must be denominated into a comparable asset in order to determine relevant value. This will occur by translating all currencies into the equivalent ETH value at the time of the transaction. This function is available through the Layer Zero API.
- **Relative Movements across Assets** - Currencies will move relative to each other after being deposited. For example, if token A is deposited when its price is $100, and Token B is deposited when its price is $200, then at the time of deposit, it is a 1:2 ratio. A user who deposites 1 Token A will be credited with half the value of a user who deposites 1 Token B. However, if a week later, Token A’s price has stayed at $100, while Token B’s price has increased to $300, the ratio is now at 1:3 for those same deposits. Prices will need to be updated on a regular basis to ensure that the user’s deposited value represents actual prices. 
- **Asset Movements across Time** - A similar situation arises when two users deposit the same asset at different times. If User 1 deposits a single Token B at $200 and User 2 deposits a single Token B a week later at $300. They both have deposited 1 Token B and contributed equally at any time moving forward - the MOR rewards generated will only be considered equal if the token prices are routinely updated and not focused on price at the time of entry.
- **Yields Differ across Deposited Assets** - Different assets earn different yields. Those assets depend on the asset, protocol, and market conditions among other factors. The yield on the deposited asset is ultimately what is contributed to Morpheus. At first glance, the only thing Morpheus would care about would be the benefit it receives regarding yield. However, a wide variety of assets and chains strengthens the health of Morpheus. It helps to protect Morpheus via diversification. There are a variety of analyses out there, but generally speaking, a higher yield, by default, implies a higher risk. Therefore, assets that may have a lower yield attached to them should still be encouraged as the underlying assets might be viewed as ‘safer’ or have a better likelihood of appreciation in value. Therefore, a blended approach would balance the difference and reward across the capital deposited and yield generated. 

The below example shows, using random assets and numbers for presentational purposes only, the blended pro-rata approach where a 50% weight is applied to the TVL and a 50% weight is applied to the daily yield.

| Deposited Asset Details | Deposited TVL | TVL (% of Total) | Daily Yield $ | Daily Yield (% of Total)| Community Capital MOR Emissions |
|----------------------------------------|---------------|------------------|----------------|-------------------------|-------------------|
Lido - stETH | $100,000,000 | 74% | $9,315 | 61% | 67.5% | 
Lido - stMATIC | $5,000,000 | 4% | $548 | 4% | 4% |
Jito - JitoSOL | $20,000,000 | 15% | $4,164 | 27% | 21% |
GMX - GMX | $10,000,000 | 7% | $1,208 | 8% | 7.5% | 
Total | $135,000,000 | 100% | $15,235 | 100% | 100% |

### Summary of Capital Front Ends
All of this analysis to say that the only method for fairly compensating yield contributed is based on a common denomination of ETH and measuring the yield based on the actual amount of ETH transferred to the Morpheus Protocol Owned Liquidity vs emitting rewards based on the asset creating the yield.

## 3. Compute Front Ends
Builders of front ends for the Compute Providers will receive 8% of all MOR emissions.

For example, a developer builds a Software Development Kit, API or website that makes it easier to provide Compute to the Morpheus Network. In doing so, they qualify to receive a pro-rata amount based on the amount of Compute they helped to enroll.  

## Order of operations for bootstrapping the Morpheus Network.
The 24% of the MOR emissions for Community Builders will begin to accrue to the Community Builder Smart Contract when it reaches Ethereum mainnet (February 8th 2024). The Community Builder smart contracts should enter into operation after the other three smart contracts (Code, Capital & Compute) are already functional.

**Step #1.**
Code & Capital Rewards go live February 8th 2024 with their respective smart contracts.
MOR rewards begin to be earned by participating addresses. MOR begins accruing in the Compute & Community Smart Contracts.

**Step #2.**
Day 90 the bootstrapping period is complete, the AMM pool is launched. 
Day 91 the MOR are claimable/sendable.

**Step #3.**
Compute Smart Contract and Router software goes live and Compute Provide begins earning MOR from the bidding system.

**Step #4.**
Community Builder Smart Contact goes live and front-end builders begin earning MOR from the accrued emissions available.
https://docs.google.com/spreadsheets/d/1qW20-C6VLw5eX3Wjrz-JeEbsvakFIojyZv9c9OIoU7E/edit?usp=sharing

## Protecting Against Exploits
The key idea is to quantify on-chain activity as a means to avoid exploits and make the activity easier to prove.

## Why is this important? 
Without a protocol-level reward, a community member would be required to form traditional entities and other means of coordinating efforts. This would cause friction within the construct of Morpheus’s use of the Techno Capital Machine; it's critical that the rewards be able to cover the full stack of developers involved.

With this in place, every aspect of the Morpheus community is rewarded for their contribution of effort, not just capital or compute. 

## Conclusion:
While there is a perception that rewarding front end developers is subjective, the examples above are all based on provable on-chain activity. Thus contributions from the front-end developers in the Community are just as provable as Compute or Capital.

The question becomes defining the metrics. It’s worth the extra work to define these rewards. Consider Lido, the creator of stETH, which has a “reward sharing program” that has driven much of its success in onboarding large amounts of ETH onto its protocol.  

