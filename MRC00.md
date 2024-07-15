# MRC 00: Morpheus Request for Comment (MRC)  Introduction

## Status: Implemented

## Summary
MRC, meaning Morpheus Request for Comments, is integral in suggesting and executing changes within the Morpheus ecosystem.  
This document is designed to make the submission process more transparent, fair, and efficient. The MRC process generally follows the monthly timing of the weight snapshot Smart Contract updates. So that weights included in MRCs advanced to the "In Progress" stage can be included in the next Smart Contract update which takes place around the 8th of each month.

## Purpose and Scope
This guide is crafted for contributors and users within the MOR ecosystem, facilitating structured proposals for standards and **material changes to one of the ten** [Morpheus Reference Implementations (MRIs).](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Morpheus%20Reference%20Implementations%20(MRI).md)  

There is an active forum on [Discord](https://discord.com/channels/1151741790408429580/1215401416659832842) for all MRCs currently under discussion.

![MRIslist](https://github.com/MorpheusAIs/MRC/assets/1563345/c5333b52-709d-4c7b-9a68-2f2e06e7bb63) 

> [!IMPORTANT]  
> 1. If your contributions is a small incremental improvement to an existing Code base, just Contribute the code, no MRC required. 
> 2. If you are seeking to build a Smart Agent and deploy it on Morpheus, no MRC is required, just register it on [MOR.Software](https://mor.software/) and follow the [guidance](https://github.com/MorpheusAIs/moragents/blob/main/AGENTABILITIES.md).
> 3. If you have a general proposal for a Morpheus feature its best to discuss it on [Discord](https://discord.gg/morpheusai) first. The MRC process is for technical proposals regarding HOW to implement improvements to Morpheus rather than general discussion of ideas.

## Submission Timeline and Platforms
Proposals are welcome on GitHub during the Fair Launch phase, eventually moving to [MOR.Software](https://mor.software/) for broader community interaction.

## Life Cycle of an MRC
**1. Pull Request Creates MRC:**  
The author creates a pull request with the details of their new MRC.
  
**2. Merged into "Discussion":**  
The MRC is merged into Discussion by a Maintainer, this indicates the repo maintainer believes the MRC is at least worth discussion and has basic merit to their Reference Implementation.
  
**3. Review:**  
Maintainers should seek to review and provide feedback to MRC authors once a week. So authors can get a sense of the next steps/current state of their MRC.
  
**4. "Pending":**  
Much of the feedback to MRC authors is often about understanding dependencies and what technical hurtles exist for the MRC to be implemented. If a maintainer identifies a technical dependency they can move the MRC into "Pending" status. This indicates they accept the MRC in principle but there is a blocker that needs to be resolved first. The author can then wait on that dependcy and re-open their MRC once it is resolved or help work on resolving the dependency.
  
**5. "In Progress":**  
Once all technical dependencies have been addressed and weights agreed, only then can an MRC be accepted into the "In Progress" stage.
  
**6. "Implemented":**  
For the MRC to be considered "Implemented" the code proposed must be contributed and merged by the maintainer into the correct MRI repository.

## Writing a Well-Formed MRC
- To draft a compelling MRC, study existing examples to grasp the expected format and substance. 
- Use the provided template for standards and changes to Morpheus structure your proposal.
- **Keep the scope of your proposal as narrow as possible.** The broader the proposal, the more technical dependencies and complexity will block its path forward.

> [!IMPORTANT]  
> **In MRCs, where external sources of information or information from any of the Morpheus repositories are used, it is crucial to include proper references to authors, collaborators, contributors, and documents. Submissions without references will not be accepted. Providing sources not only strengthens your MRC but also ensures accuracy and credibility.**

## MRC Request Template
To create a new MRC, please refer to the template provided in the [MRC_TEMPLATE.md](./MRC_TEMPLATE.md) file. This template includes all necessary sections and metadata required for a well-formed MRC submission. Ensure that you fill out each section comprehensively to facilitate the review process.

## Merged or Closed:
- First, it's important understand that MRCs are a competitive process.  
Someone who proposes better implementation/lower weights/shorter timelines can be chosen (understand that submitting an MRC does not equal that MRC being accepted).
- Second, if the maintainers' feedback wasn't addressed by an author for two weeks, the MRC is considered closed and can't be re-submitted for one month. 
- Third, a maintainer may close a MRC pull request if there is a technical hurtle that can't be currently addressed in the near term to implement the MRC, or not enough weights being available from that maintainer to accept the MRC, or the maintainer judges the MRC proposal too expensive vs the value of the change / improvement proposed.

## Submission Guidelines
Properly document your MRC in the repository and list it in the README for community review. Fork the relevant template and select the most pertinent category.

## Meta MRCs about MRCs
- For most MRCs in general this MRC00 is the first Meta MRC about how to submit an MRC.
- For MRCs about adding new assets, yield sources, chains, see this [MRC guide.](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Capital%20Providers%2C%20MOR20%2C%20TCM/The%20Morpheus%20Asset%20Integration%20Framework.md)

## Select the Affected Morpheus Reference Implementation
Choose the matching MRI that your MRC impacts. Reach out to the repo Maintainer you think the MRC is most related to if you are uncertain. List below.

## [Morpheus Reference Implementation (MRI) List](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Morpheus%20Reference%20Implementations%20(MRC).md) 
#### Smart Contracts: Changes to Morpheus smart contracts.
- Maintainer's Discord Handle: smartagents
- Link to Repo: https://github.com/MorpheusAIs/SmartContracts
#### Smart Agent Tools & Examples: Development and deployment aids for smart agents.
- Maintainer's Discord Handle: lachsbagel
- Link to Repo: https://github.com/MorpheusAIs/moragents
#### Morpheus Local Desktop/Mobile: Desktop and mobile application proposals.
- Maintainer's Discord Handle: scott_b_
- Link to Repo: https://github.com/MorpheusAIs/Morpheus
#### TCM / MOR20 (Token and Financial Models): TCM/MOR20 standard-related proposals.
- Maintainer's Discord Handle: storm.father
- Link to Repo: https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Capital%20Providers%2C%20MOR20%2C%20TCM/Techno%20Capital%20Machine%20(TCM).md#atomic-governance
#### Protection Fund: Enhancements to protection funds and security.
- Maintainer's Discord Handle: storm.father 
- Link to Repo: https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Protection%20Fund%20Details.md
#### Capital Proofs Extending: Capital proofs improvements.
- Maintainer's Discord Handle: smartagents
- Link to Repo: https://github.com/MorpheusAIs/MRC/blob/main/IMPLEMENTED/MRC15.md
#### Compute Proofs MOR/Lumerin: Computational proofs improvements.
- Maintainer's Discord Handle: rcondron
- Link to Repo: https://github.com/MorpheusAIs/Morpheus-Lumerin-Node
#### Code Proofs and Examples 
- Maintainer's Discord Handle: scott_b_
- Link to Repo: https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Coder%20Guide.md
#### Frontend Proofs & Examples: Frontend resource, proofs, and functionality enhancements.
- Maintainer's Discord Handle: erikvoorhees
- Link to Repo: https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC08.md
#### Interoperability: Proposals for improving ecosystem interoperability.
- Maintainer's Discord Handle: urklan
- Link to Repo: https://github.com/MorpheusAIs/MRC/blob/main/IMPLEMENTED/MRC16.md

## Competition Among MRI Repo Maintainers To Increase Decentralization
[The Morpheus Atomic Governance system](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Capital%20Providers%2C%20MOR20%2C%20TCM/Techno%20Capital%20Machine%20(TCM).md#atomic-governance) aims to be a free marketplace even for the Morpheus Reference Implementations themselves and thus the repo maintainers are not static but compete and are dynamic.

**What this will look like in practice is:**
- Anyone can start a fork of an existing [Morpheus Reference Implementation.](https://github.com/MorpheusAIs/Docs/blob/main/!KEYDOCS%20README%20FIRST!/Code%20Providers/Morpheus%20Reference%20Implementations%20(MRC).md)
- They can set their own weights for how they choose to reward those contributing to their version of the repository.
- Their code / version of the MRI is a MRC21 Non Fungible Agent with a reward address.
- The protocol MOR emissions gauge an on chain metric to understand usage of that fork vs all other options.
- MOR rewards are sent accordingly (as part of the 24% Coding bucket).
- This on chain mechanism could leverage a lot of the [MOR Staking on chain signaling already being developed.](https://github.com/MorpheusAIs/MRC/blob/main/IN%20PROGRESS/MRC22.md)
- If MOR token holding does end up being the mechanism for Signaling then a free market will develop for MRIs.
- This structure leaves the MRI system open for new forks, new contributors, and free competition over time.
- Instead of ending up with 1 version the Morpheus network will have multiple competing versions.

