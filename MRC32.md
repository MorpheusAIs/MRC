# MRC32: Improved Strategy for MOR Multichain Token

---

### Status: [UNDER DISCUSSION](https://discord.com/channels/1151741790408429580/1230197408345096222)

---

## Author
Kelvin Thai - Rivalz.ai

## Introduction
The MOR token stands as the primary currency within the Morpheus ecosystem. The team transforms it into a multichain token by integrating the Open Framework for Tokenization (OFT) from LayerZero. 
LayerZero boasts being one of the pioneering messaging protocols globally, renowned for its seamless integration capabilities, offering "plug-and-play" code snippets for facilitating message transmission across various chains.

## Issue at Hand
Nevertheless, the adoption of OFT LayerZero poses potential single-point-of-failure concerns, wherein the inability to transfer tokens may occur if LayerZero experiences downtime or performance lag. Anticipated challenges include those outlined in LayerZero's GitHub repository (https://github.com/LayerZero-Labs/LayerZero/issues), and the necessity for continuous maintenance efforts due to platform upgrades. The need for MOR token migration to align with LayerZero's standards is detailed in their documentation (https://docs.layerzero.network/v2/home/v2-migration).

## Proposed Resolution
Given the diversity of approximately 50 Omnichain messaging protocols available, each with its merits and drawbacks, we propose a flexible approach within the MOR token architecture. This entails integrating a mechanism to accommodate various messaging protocols. Moreover, we suggest employing an AI-driven agent to evaluate the efficacy of each protocol dynamically, recommending the optimal choice for message transmission based on real-time conditions.

## Implementation Plan
Market Analysis: Research top OFT protocols such as Axelar (https://axelar.network/interchaintokens).

Contract Refactoring: Modify MOR OFT contracts to support multiple interfaces.

Enhanced Flexibility: Introduce functions for dynamic interface management, such as: `addMultichainInterface(uint ID)` and `removeMultichainInterface(uint ID)`.

Performance Evaluation: Conduct comprehensive stress testing to assess system performance under varying conditions.

AI Integration: Develop and deploy an AI agent capable of analyzing on-chain data from multichain messaging platforms, enabling informed decision-making.

Deployment: Finalize the MOR token and AI agent deployment, ensuring seamless multichain functionality.

## Anticipated Outcomes

The MOR token will evolve into a versatile multichain asset, empowering users with the freedom to transfer it across chains at any time. Leveraging AI-driven decision-making, transfers will occur via the most efficient route determined by our intelligent agents, thereby optimizing user experience and transaction speed.
