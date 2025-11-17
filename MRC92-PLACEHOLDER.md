# MRC 92: Subnet Service Registry

- **Author:** Robert Christian (@robertjchristian)
- **Category:** Service Registry / Router Integration
- **Status:** Discussion
- **Discussion:** <https://discord.gg/morpheusai>

---

## Abstract

This proposal defines a canonical on-chain registry for services hosted by Morpheus subnets. The registry provides standardized discovery, pricing, and access for APIs and runtimes hosted through the compute framework introduced in MRC 91. It establishes the bridge between subnet-deployed services and Morpheus Core (MCP, Router, Agents), enabling community-built APIs to integrate with consistent accounting, provenance, and governance.

---

## Motivation

Subnets can host workloads via MRC 91, but without a shared registry, integration into MCP tooling and Morpheus Core processes remains manual and fragmented. There is no standardized way to discover, price, monetize, or govern subnet-hosted services, limiting composability and network effects. A canonical registry transforms isolated services into composable network primitives.

---

## Specification

**Create an on-chain registry with standardized schema for subnet services:**

- **Core schema:** service_id, namespace (MRC-59), version, spec_type (MCP/OpenAPI/A2A), endpoint, pricing_model, payment_address
- **Pricing models:** fixed, subscription, metered (denominated in MOR, MCU, or MEU)
- **Access control:** public, allowlist, token-gated (ERC-20/721/1155)
- **Reputation scoring:** Router-verified telemetry (uptime, latency, success rate, session volume)
- **Network Programs (RFPs):** Governance or core teams publish RFPs with objective acceptance criteria; providers submit services; Router canary tests validate; escrow releases on SLA achievement
- **Revenue splits:** `beneficiaries` array enables protocol-level royalty distribution

---

## Economic Flow

1. Subnet registers service → stakes MOR (anti-spam)
2. Service listed in registry → discoverable via MCP/Router
3. Usage metered via Router → MEU burn or MOR payment
4. Router telemetry updates reputation score
5. Revenue settles via escrow → split per `beneficiaries`

---

## Governance Parameters

- **Registration stake:** Tiered by service type (public: 100 MOR, allowlist: 50 MOR, subnet-internal: 10 MOR)
- **Rate limits:** Default 50 registrations per namespace per epoch (tunable)
- **Reputation thresholds:** MCP visibility tiers (score < 200: hidden, 200-600: "New", > 600: "Verified")
- **Slashing conditions:** False metadata, malicious endpoints, persistent downtime
- **Schema versioning:** `schema_version` field; registrars reject unknown major versions

---

## Dependencies

- **MRC 91:** Runtime execution layer (service hosting)
- **MRC 58:** Agent Registry (schema alignment for spec_type)
- **MRC 59:** Subnet Namespace (naming and resolution)
- **MRC 25:** Router (telemetry and settlement)
- **MRC 54:** MCU accounting (metered pricing)

---

## Network Programs (RFPs)

Governance or Core teams may publish RFPs specifying:
- Required spec_type (MCP/OpenAPI/A2A)
- Capability requirements (TEE, determinism, GPU)
- SLA targets (uptime %, p95 latency, error rate)
- Funding escrow and payout model (fixed, metered, milestone, stream)

**Acceptance flow:**
1. Provider submits service_id satisfying RFP
2. Router canary tests validate functionality and SLA
3. On pass, escrow releases; registry emits `RfpFulfilled(rfp_id, service_id)`

This transforms protocol needs into open market opportunities.

---

## Risks & Mitigations

| Risk | Mitigation |
|------|-----------|
| Spam registrations | Stake requirement + 30-day lock + rate limits |
| Reputation manipulation | Router-verified telemetry only; governance-versioned weighting |
| Duplicated services | Namespace collision prevention via MRC-59 |
| Malicious endpoints | Stake slashing (50% burn, 50% treasury) + transparent moderation |

---

## Open Questions

1. Should MCP auto-surface all public services or apply reputation thresholds by default?
2. Deprecation policy for superseded service versions?
3. Privacy controls for allowlisted/subscription services?
4. RFP selection criteria when multiple providers qualify (first-to-deliver, governance vote, performance trial)?

---

## Summary

MRC 92 establishes the Subnet Service Registry, linking sovereign compute (MRC 91) to Core orchestration (MCP, Router, Agents). It provides a canonical structure for subnets to publish, price, and monetize services, transforming autonomy into composability. The RFP system enables the network to procure capabilities with verifiable SLAs, creating a two-way marketplace between Core and community.

The registry transforms Morpheus from a compute protocol into an open service economy. Subnets don't just run workloads: they advertise, transact, and evolve under shared accounting. MOR becomes the coordination layer for a self-improving network, where every useful service becomes an on-chain primitive others can build on.

**Velocity through coordination.**

---

## Compatibility

MRC 92 composes with existing components without modification:
- Router (MRC-25): consumes telemetry for reputation and settlement
- Agent Registry (MRC-58): aligns spec_type enum (MCP/OpenAPI/A2A)
- Subnet Namespace (MRC-59): binds services to `.mor` identities
- Tools Marketplace (MRC-60): may use registry as backend

No changes to MRC-25 contracts assumed; hooks delivered as additive modules.

---

**Non-normative.** Reference implementations may be contributed by community maintainers; details live in the runtime/registry repos.

---

## Metadata

```yaml
id: MRC92
title: Subnet Service Registry
authors: ["Robert Christian (@robertjchristian)"]
category: "Service Registry"
summary: "Canonical on-chain registry for subnet-hosted services with Router-verified reputation, RFP procurement, and MCP integration."
status: "Discussion"
discussion_url: "https://discord.gg/morpheusai"
contact: "@robertjchristian"
keywords: ["registry","service","router","namespace","mcp","subnet","mcu","meu","mrc25","mrc54","mrc58","mrc59","mrc91"]
```
