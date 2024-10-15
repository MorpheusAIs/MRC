# MRC49: MRI Weights Decentraliation Via MRI Specific Multisigs & Simplied Weight Accounting

## Status: In Progress

## Objective & Proposal:
As with all Morpheus Contribution types, the Morpheus Reference Implementations are designed and intended to move toward a free market approach where MRI maintainers can independently manage Coding weights for their specific MRI.

### 1. Create a Multisig address for each of the 10 MRIs.
### 2. Assign excess weights for each MRI to its Multisig address.
### 3. Assign all 100 Million weights between the 10 MRIs now.

## History & Context
- Morpheus began with a single community run Multisig that assigned weights each month towards the addresses as selected by each Maintainer. 
- This system bootstrapped the Code Contributor category to its first 300 addresses based on Contributions of Code to 10 MRIs.

## 3 Key Challenges with Previous Weights Management System:

### Race Condition Created For Weights Assignment
- The first game theory issue that emerged has been that with regards to the Coding Weights for each Maintainer, effectively ALL have to be assigned every month.
- As not assigning the weights would disproportionately disadvantage the Maintainer's MRI due to the dilution from other MRIs assigning weights that month.
- This has led to a race condition and added a lot of overhead as Maintainers have to try and perfectly balance requests for weights every month. 
- Instead of just assigning the weights they need to get Coding work done that month.

### Complexity In Accounting
- The second game theory issue is that the weights distribution curve over time has added a monthly dynamic weights element to an already dynamic token distribution curve.
- This has compounded complexity and led to a lot of overhead with trying to account for the ever changing number of weights available to Maintainers.

### Only Weights Available To Reward Coders
- Lacking any MOR to distribute the Maintainers have had to only work with Coders able to accept weights for their Contributions.
- This has narrowed the number Code Contributors that can participate in providing Code to improve the Morpheus Reference Implementations.

## Advantages Of This New Simplified Weights System
### 1. Maintainers can "save" weights that are unassigned for future use in their MRI specific Multisig. 
### 2. Weights assigned to the MRI specific multisig will gain MOR emissions over time. Creating an MRI specific pool of MOR token resources of the Maintainer to use.
### 3. Accounting can be simplified as each MRI will have a static set of weights to assign. 

## MRI Multisig Details
- 10 Multisigs created, one for each of the 10 MRIs, and all require 2 of 3 signatures for approval to send MOR from their address.
- This creates the basic structure that can be updated over time as MRI maintainers change and new signers assigned.
- Community multisig still updates weights / addresses in the Smart Contract once per month based on Maintainer assignments.
- Future versions of the Morpheus Smart Contracts will need to allow for individual MRI multisigs to direct MOR distribution (likely via 721 style Contract).

