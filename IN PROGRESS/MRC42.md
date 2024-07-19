# MRC 42: MOR Staking Available To All Contributor Types
## The Time & Dilution Based Power Factor Method For Calculating Proportionality of Emissions

### Authors / Discord Name: 
Anon 866, David Johnston (Smart Agents), Anton (antonb), Anon (lachsbagel), Christopher (storm.father), Jon (jonisjon), Maxwell (scott_b_), Jeff (Jabo38), Luke (lukestokes), Erik Voorhees (erikvoorhees)
   
### Authors of Proposals On Related Subjects / MRCs: 
- Mechaverse with [MRC 36](https://github.com/MorpheusAIs/MRC/blob/main/MRC36.md) 
- Kehndry - Extensive feedback and alternative proposals on Time Curves.
- David Johnston - With [MRC22](https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC22.md)

### Status:
In Progress

### Link to Discord: 
https://discord.com/channels/1151741790408429580/1251996042929639434

## Introduction - Rational / General Description
This proposal sets forth a method by which Contributors can Stake MOR reward claims to a time in the future.
In exchange for Staking MOR for a period of time, the Contributor gets a "Power Factor" applied to the calculation of their MOR rewards each UTC second. 
This Power Factor mirrors the the Delution rate the Contributor experiences while Staking the MOR. 

> [!IMPORTANT]
> - None of these MOR Staking proposals increase the amount of MOR token emissions that are created. Rather, it changes a Contributors proportional rights to the amount of tokens that are being emitted during a period they contribute their value. In a similar way that increasing a miner's hash rate increases the amount of the portion of Bitcoin they mine.  
>
> - **For Capital Providers:** nothing in this proposal changes the ability of a Contributor to withdraw their stETH (beyond the normal 7 days), only the claiming of MOR rewards is delayed. However when a Contributor withdraws their stETH their reward factor no longer applies after the UTC second time of their withdraw.

## List of Staking Types & Descriptions
- MRC38 & MRC39: MOR Reward Staking (emissions in the future) Types (Code & Capital)
- MRC40 & MRC41: MOR Staking of Existing MOR (Compute & Builders)
- Whitepaper: Morpheus Users. Stake MOR for access to Compute.

### [MRC 38: Code Providers](/IN%20PROGRESS/MRC38.md)
- A. Add Code Contributions to earn MOR.
- B. Staking of MOR rewards into the future to increase proportionality.

### [MRC 39: Contributing Capital](/IN%20PROGRESS/MRC39.md)
- A. Deposits of stETH and the resulting yield contributed to Morpheus earn MOR.
- B. Staking of MOR rewards into the future to increase proportionality.

### [MRC 40: Compute Providers](/IN%20PROGRESS/MRC40.md)
- A. Existing MOR Staked to qualify to earn MOR. Stake 100 MOR for 1 Year. Earn up to 100 MOR.
- B. Staking of MOR rewards into the future to increase reputation ranking.

### [MRC 41: App / Smart Agent Builders](/PENDING/MRC41.md)
- A. Existing MOR Staked to qualify to earn MOR rewards.
- B. Staking of MOR rewards into the future to increase proportionality.

### [Whitepaper: Morpheus Users](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/WhitePaper.md)
- A. “Inference Staking”. Stake MOR for access to Compute.
- B. Nominating Smart Agents / Dapps. Stake 100 MOR for 1 Year. Earn up to 100 MOR. 

## Example Chart of Power Factors Over Time
![ExampleMORPowerFactor](https://github.com/MorpheusAIs/MRC/assets/1563345/be4492a8-e050-4deb-8270-2029e39386d9)

> [!NOTE]
> **Charts shows example power factor if the Contributor Staked their MOR token claims the 25th of July 2024.**

## The Time Curve General Principles for MRCs 38, 39, 40, & 41.
- The Power Factor principle mirroring Dilution rates can be used across Contributor types. 
- The answer to "Life, the Universe and Everything" is Time.
- How to make contributions to Morpheus **accretive** vs **extractive**.
- The concept is that All Contributions (Code, Capital, Compute or Builders) take Time for them to benefit the network, the longer the Time the greater the benefit. 
- Time seperates the Builders from the tourists. The HODLers from the day traders. 
- In the Morpheus context, Time seperates the real Contributors from short term opportunists.

## The Time Power Factor (Shortened "Power")
Rather than pick a "magic" number for the "Power Factor" function, this number can best be set by looking at the actually Dilution Rate the person experiences from Staking their MOR tokens for a specific period of time.

**For example:**
- On July 25th 2024 2,384,564 MOR will have been emitted.
- On July 25th 2025 7,338,234 MOR will have been emitted.
- Thus 4,953,670 MOR have been emitted since the Time delay for claims began.
- In the case the user choses to Stake their MOR claims for this 12 month period, they experience 207% dilution.  
- So the Time Power Factor should be around the same 2X. 

In other words the Base reward as calculated by the number of stETH staked in the case of capital or the weights held in the case of a Code Contributor is mulipled by the Power Factor.   

The result of this multiplication is then divided by the total stETH * Power or Weights * Power of ALL Contributors in that group to determine the individual Contributors proportionality of the MOR rewards that UTC second.

**For Example:**
- 1 stETH with a 207% Power Factor would have a result of 2.07
- This 2.07 sum would be divided by the total stETH staked (or yield provided in a future yield agnostic version) post Power Factor.
- If 100 stETH were already staked the porportion of rewards for the 1 stETH staker after his deposit would be equal to 2.07 out of 102.07 
- Which equals 2.02% of the MOR emissions during that UTC second.

![ProportionalityEquationMORStaking](https://github.com/MorpheusAIs/MRC/assets/1563345/6e6c1cc5-826a-42be-bbb7-b7c4a9d65cf9)

![Emission Earned Chart 2](https://github.com/MorpheusAIs/MRC/assets/1563345/1d8e7e73-22ed-44ed-82e8-934370fe58cd)

## MRCs 38, 39, 40, & 41 
These MRCs stand for how to implement Time as a function for each of the four core proofs of Morpheus.  
Code, Capital, Compute and Builders. However the principle is the same across all four and should hold generally.

- **Code MRC 38:** https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC38.md
- **Capital MRC 39:** https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC39.md
- **Compute MRC 40:** https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC40.md
- **Builders MRC 41:** https://github.com/MorpheusAIs/MRC/blob/main/PENDING/MRC41.md

## Conclusion: To quote Paul Graham:
- "If your opponents are opportunists, one way to beat them is to outlast them. 
- "Opportunists almost by definition lack staying power."
- https://x.com/paulg/status/1802094669628625272?s=46&t=iOyqtKddsZp1sSUXOguocA

## Appendix Section

## Supply Curve Comparison Based On Different Staking Time Averages
![Supply Curve Comparison](https://github.com/MorpheusAIs/MRC/assets/1563345/3af26946-6b61-4e14-9b54-038dc49175d2)

## Supply Curve Presuming 4 Year Average Staking Time
![Staking Curve 4 Year to 2040](https://github.com/MorpheusAIs/MRC/assets/1563345/b8eeda6b-aacc-4286-957f-64d69fc0e07d)

## Zoom in of Supply Curve First 6 Years, With 3 Year Average Staking Time
![6 year chart with 3 year average](https://github.com/MorpheusAIs/MRC/assets/1563345/3b044dcc-2dec-4591-8057-311ae35959e9)
