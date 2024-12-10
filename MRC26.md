## MRC26: Decentralised Architecture Definition and API specification

---

## Status
**April 3, 2024: UNDER DISCUSSION**


---

### 1. Problem definition

Currently there is no well defined architecture of how node is supposed to connect and work with any user interface or external agents, marketplace or any other definition, which makes it difficult to create new node software or adapt current one as there is no API specs defined (or at least minimum API specification). This creates a challenge for new code contributors as they are not sure what features their node implementation needs to support. 

Current Yellow paper described some parts of the architecture but is lacking some details, which makes it difficult for newcomers to just start contributing (similiar problem that Ethereum was facing at the start, where small team was doing all the contributions to Geth client).


### 2. Solution definition
#### 2.1 Abstract

General overview of architecture needs to be created, based on current idea of how Morpheus is gonna work. This overview needs to include the following:
 - API specification for all parts of the architecture (Currently: Web UI, Node, Marketplace ?, Smart Agents)
I propose using swagger.io as they provide open source tools for creating API documentation and even testing software
- Definitions of pillars of the architecture and what are the minimum requirements for them
Examples: 
1. Web UI needs to allow users to connect with their Web3 wallet and sign transactions for MOR payments to nodes
2. Node must be able to connect to smart agents via predefined API, also needs to respond to any API requests from Web UI

#### 2.2 Delivery strategy

My plan is to write an initial draft and attach it to this MRC and put it up for discussion. Any interested users that want to contribute will also be added to Discord discussion and if needed we can even organise separate meetings to discuss the ideas and details.

#### 2.3 Tech stack

As this is purely documentation based MRC not a lot of technologies will be used. For discussion we will use Google docs and Github issues, together with Discord. Swagger will be used for generating API specifications.

### 3. End result

End result will be an expanded Yellow paper + API specification for all parts of decentralised Morpheus ecosystem. This will help existing and new developers to plan new features or new clients more easily and prevent node compatibility issues in the future. It will also make it easier to test new implementations as there will be a testing suite defined based on the API specification.
Success of this MRC will be judged based on the details of specification and adoption of API specs into exsisting Node implementations. Later, when there will be more community apps they will all need to follow this specification.

### 4. Value proposition

Having a well defined architecture and API specification will increase productivity, decrease time spent on developing features without testing capabilities and also allow more people to work as code contributors, which will speed up development of Morpheus. This is important as Morpheus is not the only open source project racing to become the leader in Network of AI smart agents. Without this, every new developer needs to read all the existing code and ask a lot of questions on Github and Discord to avoid designing and coding incompatible features or node implementations.


### 5. Reference implementations

This MRC will mainly adapt/improve current Yellow paper and add new documents. It does not influence tokenomics, Token distribution or anything connected with MOR token, except for the parts which describe implementation of marketplace and payment system for decentralised implentation of Morpheus.

### 6. Dependencies

MRC25 is a direct dependency as it also proposes architecture, but it is currently not talking about technical implementation and API specifications. There is a possibility to combine both MRCs into a larger, well defined one.

### 7. New weights requested

I belive this adds a lot of value to Morpheus projects for reasons mentioned earlier (Speed up development, easier developer onboarding, diversify client and node implementations,...). If accepted, this will take quite some time (and MP) to deliver, this is why weights requested will depend on final deliverables, which needs to be discussed.

### 8. Existing weights

There has been no weights requested.

### 9. Time to complete

I believe architecture definition is crucial for further development this is why I propose the following timeline:
1. Initial draft - 3 days
2. Comments from community and improvements - maximum 2 weeks
3. Api specification and Yellow paper improvements - 2 weeks

If accepted this MRC can be completed in 1 month time from start.

### 10. Deliverables

1. Improved Yellow paper
2. API specification (Github doc and Swagger site)

### 11. Why me

I have 10+ experience with development in different companies (Banking and Crypto sector) with experience leading teams and preparing specifications for projects. As I do believe Morpheus has a really good chance of becoming one of the most successful decentralised AI projects I would like to contribute and be a part of this.

### 12. Status
UNDER DISCUSSION
https://docs.google.com/document/d/1fSSaotcF_jyFID6u4BEO-cm2r31lw3pdqf3gwUJfkMY/edit?usp=sharing
























