# MRC 55: Morpheus User Personas For Builders, Compute, Capital & Their Effects on V2 Designs

## Premise: Who is the primary persona Morpheus is serving with Builders, Compute & Capital? 
And what data do we have from the first 90 days in the real world of the Builder rewards being live.

## Primary Builders Persona
Thus far the primary persona Builders has seen emerge is that of an Agent Builder / early stage project seeking to rally community support to their effort. 
To draw the comparison to the early days of Ethereum, the killer applicatoin was crowd sales / token sales. This was by far the most popular use case for Ethereum from 2015 to 2019 before DeFi / Stablecoins matured. 

Builders in the Morpheus context is the 2.0 version of this early stage capital / community formation for projects building in Web3. 
Morpheus Builder rewards effectively extends the Capital mechanism from stETH yield to those holding MOR and wanting to direct its yield. 

## Implecations for V2 of Builders
This leads to an important design consideration for Builders V2. 
It would indicate that it is best remove the "power factor" (MOR claim delay reward multiplier) in the case of Builders.
Firstly, zero Subnets have decided to use the Power Factor and it stands to obvious reason why.
Imagine trying to raise support via a Builder Subnet and you have to push out the rewards to 1 year, 2 years, 4 years from now. 
It doesn't make any sense at that point as a capital mechanism, given the rewards would only show up years from now.

Also if Morpheus wants to see Builders actually use their MOR for Compute via the Morpheus Compute Units. 
Then the rewards for Builders can't remain locked for years or the Builder will not be able to get the access to Compute they need. 
A second strong reason to remove the Power Factor from Builders.

With the Power Factor removed, anyone wanting to Stake to a Builder can do it with low friction, the Subnet will get the rewards right away. 
The Subnet can then claim MOR and Stake it for Morpheus Compute Units. Thus fulfilling the primary utility of Morpheus.

## Other Personas

### 1. The Subscription Payment Persona would be a popular one.
However given the high volatility of the MOR price its hard to see Builders Rewards being used as a "payment mechanism". 
The Staking amount of MOR would need to be constantly changed based on USD / BTC / ETH prices. 
It feels like the payment persona is far outside the current feature set.
Instead Capital V2 with its support for aUSDC, wBTC, wETH, yield payment rail and can serve those users and we can determine the best tie in for the MOR token.

### 2. The Builder as Inference User Persona. 
This is an excited area of work, and the MRC to support Morpheus Compute Units will bring about the easier means of serving this persona.
And having Builder rewards pay out without a massive time delay (Power Factor) will suppor this persona.

### 3. Lastly the Capital and Code Provider Personas are the best understood. 
Offer Yield or Code, earn MOR, bootstrap the platform. The Power Factor seems to make sense for these two types of emissions.

## In short. Three personas best served by removing the Power Factor from the Builder Smart Contracts in V2.
The New Project Builder persona is best served by Builder V2.
The Inference user persona is served by Compute V2 with MCUs.
The Operator / Payment rail via yield is served by Capital V2.
