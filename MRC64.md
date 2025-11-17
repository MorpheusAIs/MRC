# MRC 64: Morpheus Virtual Machine (MVM)

Proposal to describe the Morpheus Infrastructure as: "The Morpheus Virtual Machine" or the "MVM" for short.

## 2. Introducing The Morpheus Virtual Machine (MVM)
The Morpheus Virtual Machine (MVM) provides this substrate by functioning as the control plane for the emerging Agent Internet. MVM enables decentralized discovery, authorization, task execution, and settlement for a global network of AI agents and service providers. Heavy operations—such as data storage, inference, fine-tuning, training, multimodal processing, and RAG indexing—execute off-chain in a competitive marketplace of service providers, while MVM maintains the minimal on-chain state required for trust, coordination, and economic alignment. MVM introduces four core protocol primitives:

Service Registry — onchain identities and capability manifests for agents, tools, models, storage nodes, and compute providers (inference, fine-tune, training).

Intent Layer — programmable, verifiable tasks submitted by users or agents to request actions from any registered service.

Session Layer — user-controlled authorization contexts defining tool permissions, spending limits, data access, and cross-chain capabilities.

Execution Records — verifiable receipts that capture completed work, proofs, costs, and performance metrics, enabling payments and MOR-indexed incentives tied directly to real usage.

By separating the control plane (onchain coordination and verification) from the data plane (offchain computation, storage, and tooling), MVM achieves global interoperability, censorship resistance, and horizontal scalability. Agents—digital or physical—can securely coordinate across systems and chains, call compute and data services, access user-owned memory, initiate cross-chain actions, and settle outcomes through a unified, open protocol.
The Morpheus Virtual Machine establishes the foundational, decentralized infrastructure for the Agent Internet—a world where users, applications, and increasingly real-world autonomous systems own their agents, their data, and their digital autonomy, and where AI actions are as permissionless and composable as smart contracts are today.

To deliver on this vision, we are consolidating our efforts and narrative around the Morpheus Virtual Machine (MVM). The MVM is not a single piece of software but an integrated protocol stack that provides developers with a one-stop-shop for all the primitives needed to deploy, and operate smart agents, namely inference, agentic tools, and context / memory storage. The MVM is our answer to the fragmented landscape of AI infrastructure, where developers must stitch together disparate solutions for inference, data, and tooling.

![RoadmapforZionEra](https://github.com/user-attachments/assets/98db75c9-8e1f-4c46-9a0c-cbd2f6828b5d)

The MVM is defined by three core principles and three core marketplaces:

### 2.1 MVM Core Principles
Composability: Every component within the MVM is an on-chain, lego-like brick. Developers can inspect, trust, and combine these components in novel ways without fear of a centralized provider changing the rules or breaking their integrations. This is the primary advantage over the "black box" models of centralized AI. 

To implement this, Morpheus is contributing to the ERC-8004 process which establishes on-chain registries for agent identity, validation, and reputation. These registries are key to discovering agents, defining their capabilities and knowing how well they perform. These are all prerequisites for composability.   

Ownership: Through the control of a private key, a user has persistent, verifiable ownership of their AI assets. This includes their agent's logic, its memory and context, and its ability to execute. This ownership is secured by the network, making it resistant to censorship or takedown by any single entity.

To implement this Morpheus has integrated LIT protocol and AgentKit to allow Agents granular permissions and access to a users on-chain assets, without exposing the users private key. Building on this the advent of x402 as a web native and on-chain payments standard is quickly gaining adoption and will add a wealth of new agentic endpoints and for smart agents to access, all controlled via a users individual private key / wallet. 

Open Access: The MVM is a permissionless network. Anyone can provide inference, publish an agentic tool, or provide data storage. Our role is to provide the protocol-level framework that allows these participants to discover each other and transact securely on-chain.

To implement this, the MVM is built with open-source code, on-chain smart contracts and peer to peer nodes that make its claims of neutrality and permissionless access verifiable.

### 2.2 MVM Core Marketplaces
Inference: This was the first marketplace built by the Morpheus community as described in the 1.0 whitepaper in 2023. Access to powerful models was the logical starting place as they provide the brainpower at the foundation of the MVM. The full node peer-to-peer architecture of the Morpheus Router allows anyone to permissionlessly host a model and offer it to those wanting to consume inference. This is an incredibly flexible and future-proof approach to scaling the supply and demand for inference. 

The value here is the open source LLMs are more affordable because there is no company charging a premium and no monopoly is possible because it is a permissionless free marketplace that can't be censored or stopped by any central entity.

However, in order to move from information to action, inference isn't enough. The LLM must be able to call agentic tools and use context / memory to complete complex tasks autonomously.
 
Agentic Tools: The next logical step is to provide access to agents and tools which we will refer to generally as "agentic tools". Before a marketplace can be established there needs to be a registry where these agentic tools can be recorded on-chain so they can be discovered, qualified and programmatically accessed. This is where the work on ERC-8004 comes in, this provides registries for identity, validation of agent capabilities and finally the reputation of that agent in completing the jobs its claims to execute. 

The Morpheus Agentic Tools Marketplace will index and aggregate agentic tools from the ERC-8004 and other onchain and offchain registries and based on demand providers can offer to run these Agents. With the advent of x402, A2P, and other Agentic payment options Morpheus can enable these transactions between providers and consumers of the agentic tools.

For smart agent builders the Morpheus Virtual Machine solves discovery, distribution, execution and handles agentic payments all in one place. Because smart agents once deployed on the MVM are hosted with staking of MOR and thus are always available. Just as one expects with deploying a smart contract on Ethereum.

Context & Memories: The last key marketplace covers the storage of context and memories, which allows generalized models to become hyper-personalized given the detailed history of a user. The need to store and access private data is key to creating a persistent personal AI experience for those owning their AI. For this to be meaningful people need the ability to take their smart agent with them across platforms, devices and time. 

While the Morpheus full node already has integrated IPFS, a full blown marketplace for any type of data storage for developers to select the best type of storage and storage provider is necessary to complete our vision.

The completion of these three core registries / marketplaces for the MVM comprise the key goals of the Zion Era of Morpheus' development.

### 2.3 MVM Smart Contract Deployment Converging on BASE
An important note on focusing the deployment of the registries and marketplaces smart contracts on BASE.

While the MOR token can move across many chains via LayerZero (Ethereum, Arbitrum, Base, Solana), there are no mature methods for "cross chain intents" for complex smart contract states to be validated between layer 2s. So these registries and marketplaces will start on BASE, the Ethereum layer 2, where much of the agentic infrastructure (ERC-8004, x402, AgentKit) is aggregated. 

The Ethereum community is actively working on cross chain intents (though timing is to be determined) the Morpheus community will evaluate how to best leverage these development when they are deployed in a future Ethereum upgrade.

In the mean time, the benefits of focusing on BASE is that the smart contracts can much more easily check the state of other smart contracts. So for example the MOR distribution smart contract would be able to validate not only if a Builder Subnet had MOR Staked towards it, but also how much inference it is consuming from the inference marketplace. This can lead to greatly improved focusing of MOR emissions towards those creating the most value on Morpheus.

![InferenceMarkeplace](https://github.com/user-attachments/assets/aebaeb66-35ef-4f33-8207-289f693cc255)

### 2.4 The API Gateway
The Morpheus Inference Router processes requests and provides access to models on a peer to peer basis, however it requires deep technical knowledge, and running a full node is often more time consuming than many developers are prepared to commit. Enter the "API Gateway" which is built on top of the Router and abstracts the complexities of the underlying inference marketplace, allowing developers to easily generate an API key and pay in familiar ways (e.g., per-token) while inference providers are compensated via the Morpheus token. This is a critical infrastructure for bridging our decentralized infrastructure with the expectations of the broader market.

All the API Gateway's code is open-source, so think of it as a reference implementation that any one can run and operate this abstraction layer and provide it as a service to others. We welcome the community to leverage the API Gateway either directly or to spin up your own.

### 2.5 Intent Settlement Layer
As mentioned above "the next evolution of AI will be defined by agents that act on a user's intent. These agents will not simply answer questions; they will execute complex, multi-step tasks autonomously by composing various services and tools. A user's interaction will shift from, tell me about X, to go do X for me." 

In order to match and settle their intents there needs to be an Intent Layer that is, "programmable, verifiable tasks submitted by users or agents to request actions from any registered service."

While only covered briefly in this whitepaper one of the key areas of the MVMs development will be the intent settlement layer for the Morpheus nodes. This is discussed in much greater detail in the V2 of the Morpheus yellow paper.
---
