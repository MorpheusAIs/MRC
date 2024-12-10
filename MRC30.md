# MRC30: Passive PMAs. Portfolio Management Agents for Passive Fund Management

---

### Status: [UNDER DISCUSSION](https://discord.com/channels/1151741790408429580/1227120287825526844)

---

## Author
64bits.eth

## Summary
This proposal introduces Portfolio Management Agents (PMAs) utilizing Large Language Models (LLMs) for fund management within the Morpheus ecosystem. Active PMAs will autonomously manage investment portfolios, executing trades and reallocating funds based on predefined user preferences or real-time market analysis. However, This MRC will focus on Passive PMAs, who perform actions only when being requested. 

## Rationale
With the increasing complexity of financial markets and the growing interest in decentralized finance (DeFi), there's a need for more intelligent and adaptive portfolio management solutions. PMAs powered by LLMs can analyze vast amounts of market data, predict trends, and execute investment strategies with higher efficiency than traditional models. This initiative aims to enhance portfolio management services, offering Morpheus users tailored investment strategies that adapt to market changes, thereby maximizing returns and minimizing risks.

## Value Proposition
Implementing PMAs will significantly enhance the value Morpheus provides to its users by:

1. Offering advanced portfolio management services accessible to all users, regardless of their financial expertise.
2. Enabling personalized investment strategies that cater to the individual risk profiles, preferences, and goals of users.
3. Increasing the efficiency and performance of investment portfolios through the use of cutting-edge LLMs for market analysis and prediction.
4. Strengthening the Morpheus ecosystem by attracting a broader user base interested in sophisticated investment tools.

## Definitions
Portfolio Management Agents (PMAs): PMAs are specialized smart agents within the Morpheus ecosystem designed to autonomously manage investment portfolios by executing trades, reallocating funds, and implementing strategies based on predefined criteria or real-time market analysis. These agents leverage Large Language Models (LLMs) to analyze financial data, predict market trends, and make informed decisions, aiming to maximize returns and minimize risks for the investors.

Passive Portfolio Management Agents (Passive PMAs): Passive PMAs operate on a directive basis, meaning they perform actions and manage funds only when explicitly requested by the user. These agents are designed for investors who prefer to set their own investment strategies and make adjustments manually. Passive PMAs can execute specific tasks such as rebalancing the portfolio to a predetermined asset allocation or investing a set amount of funds into specified assets or protocols. The primary role of passive PMAs is to assist users in maintaining their investment strategies.

Active Portfolio Management Agents (Active PMAs): Active PMAs autonomously execute investment strategies without requiring direct instructions from the user for every transaction. These agents are embedded with advanced algorithms and use real-time market data, analysis, and predictions to actively manage and adjust the investment portfolio. Active PMAs aim to outperform the market or achieve specific investment objectives by automatically adjusting asset allocations, entering or exiting positions, and employing hedging strategies based on evolving market conditions. They cater to users who wish to leverage the agent’s capabilities for active portfolio management, relying on the agent's AI-driven insights and strategies for investment decisions.

## New Weights Requested
Passive PMAs: 50000

## Existing Weights
Not applicable.

## Deliverables:
We will be focusing on implementing Passive PMAs in this MRC while exploring solutions of Strategy Definition, Risks Control, and Auto Tx Execution for Active PMAs.

- Passive PMAs (CLI version):
  - Smart Contract Sub-agent: capable of interacting with (reading and writing to) any open sourced contract onchain
  - Integration with Existing Smart Contracts (Uniswap, Lido, Stargate, etc) with Smart Contract Sub-agent
  - Market Data Oracles
  - Security and Risk Management
- Documentation and User Guides: Comprehensive documentation and step-by-step guides on how to use passive PMAs, including examples of common investment strategies.
- Security Audits and Testing for Passive PMAs

## Risks
- Market Risk: The potential for PMAs, especially active ones, to make erroneous predictions or fail to adapt to sudden market changes, leading to portfolio underperformance.
- Security Risk: The risk of security vulnerabilities within the PMA frameworks or interfaces that could be exploited, jeopardizing user funds and data.
- Regulatory Risk: Uncertainties surrounding the regulatory environment for automated investment services, which could impact the deployment and operation of PMAs.
- Technical Risk: The challenge of integrating PMAs with existing Morpheus infrastructure and ensuring reliable performance, especially given the complexity of active PMAs.
- User Adoption Risk: The potential for low user adoption if PMAs do not meet user expectations or if users find them too complex to use.
- Operational Risk: Risks associated with the ongoing maintenance, updates, and support of the PMA platform, which are critical for both passive and active PMAs.

## Background
- ETHDenver 2023 Finalists
- Optiver - Trading at the Close
- Experiences with LLMs, Finetuning LLaMA, Langchain
