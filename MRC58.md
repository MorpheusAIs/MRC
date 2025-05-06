# MRC 58: Specification for the Agent Registry Smart Contract

## Introduction: Purpose and History
Originally the Agent Registry was included in the Morpheus / Lumerin Router alongside the model registry. 
Due to the added complexity, the decision was made to set the Agent Registry as a standalone Smart Contract.
The following are required, optional, and calculated fields for the design of the Smart Contract.

| Field                                    | Required?  | Notes (why / any nuance)                                                                                           |
|------------------------------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| UUID                                     | Required   | Non-collision identifier of this agent for the registry.                                                          |
| Agent Name                               | Required   | Core identifier for humans.                                                                                       |
| Agent publisher crypto payment address   | Required   | Address to send agent builder proceeds.                                                                           |
| Price of Agent Royalty                   | Required   | Only if it isn’t free.                                                                                            |
| Version                                  | Required   | Needed to track updates.                                                                                          |
| Tags / Keywords                          | Required   | Aids discovery, not strictly required.                                                                            |
| Icon/Logo                                | Optional   | Nice for UIs.                                                                                                     |
| Website                                  | Optional   | Helpful for credibility.                                                                                          |
| Documentation URL                        | Optional   | Highly recommended.                                                                                               |
| Description of Agent Functions           | Required   | Search engine and devs need to know what it does.                                                                 |
| Specification                            | Optional   | A2A contract (YAML/JSON), MCP manifest, OpenAPI 3.1 (YAML/JSON), or custom JSON Schema.                           |
| Specification Version                    | Optional   | Only meaningful when a specification exists.                                                                      |
| Version history / changelogs             | Optional   | Good practice, but agent can register first iteration without history.                                            |
| Status (Alpha/Beta/Stable/Deprecated)    | Optional   |                                                                                                                   |
| Dependencies                             | Optional   | Must be declared if present; otherwise omit.                                                                      |
| Agent Smart Contract Address             | Required   | Registry needs a canonical network address or package locator.                                                    |
| Model Used                               | Optional   | Useful metadata.                                                                                                  |
| List of Intents                          | Optional   | Nice granularity, but agent can give free-text description only.                                                  |
| Tokens Used For Inference / chains / L2s | Optional   | Applies mainly to on-chain or rate-metered agents.                                                                |
| Examples - successful                    | Optional   | Strongly improves onboarding, but not mandatory.                                                                  |
| Examples - failed                        | Optional   | Same rationale.                                                                                                   |
| Agent Reputation                         | Calculated | Calculated by platform or omitted initially.                                                                      |
| Revenue                                  | Calculated | Difficult to cheat reputation metric. Populated later by monitoring.                                              |
| Minimum compute resources required       | Optional   | Important for self-host, but not always known.                                                                    |
| Response time (min spec met)             | Optional   | Covered by latency metrics if provided.                                                                           |
| Certifications (SOC 2, HIPAA, …)         | Optional   | Only relevant for regulated contexts.                                                                             |
| Input Formats                            | Optional   | If omitted, assume natural language.                                                                              |
| Output Formats                           | Optional   | If omitted, assume natural-language response.                                                                     |
| Rate limits                              | Optional   | Only present when throttling exists.                                                                              |
| Supported Languages                      | Optional   | Defaults to en-US if unspecified.                                                                                 |
| Average Latency                          | Calculated | Populated later by monitoring.                                                                                    |
| Uptime                                   | Calculated | Populated later by monitoring.                                                                                    |
| Error Rate                               | Calculated | Populated later by monitoring.                                                                                    |
| Throughput                               | Calculated | Populated later by monitoring.                                                                                    |
| Last Metrics Update                      | Calculated | Only meaningful once metrics exist. Populated later by monitoring.                                                |

## Agent Builders
Agent Builders will interact with the Smart Contract by publishing the records related to their Agent to the Registry.
The address that publishes the information to the Registry will be the sole entity that can edit the information as connected to their Base address.

## Chain
The Agent Registry will be published on Base.
