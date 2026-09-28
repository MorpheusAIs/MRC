# MRC 91: Token Native Docker Compute

- **Author:** Robert Christian (@robertjchristian)
- **Category:** Runtime Infrastructure / Router Extension
- **Status:** Discussion
- **Discussion:** <https://discord.gg/morpheusai>

---

## Abstract

This proposal defines a Router-integrated runtime layer that enables Morpheus subnets to execute Docker and OCI workloads using MOR-denominated resources. Execution capacity derives from stake via Morpheus Compute Units (MCUs), which convert to Morpheus Execution Units (MEUs) at runtime: temporary, non-tokenized ledger entries tracked by the Router.

MEUs are epoch-scoped and expire at epoch boundaries, functioning as reserved capacity guarantees rather than transferable credits. This "use it or lose it" model ensures provider headroom for burst demand, prevents capacity hoarding, and maintains predictable availability (similar to GCP committed use or AWS reserved instances, but trustlessly coordinated through the Router). Unused MEUs reset daily, allowing stakers to right-size their reservations while enabling compute lending markets (MRC-48) for dynamic capacity allocation.

By treating stake as capacity reservation rather than speculative credit, subnets operate fully within MOR's trust and coordination boundary while remaining modular and provider-agnostic. MOR becomes infrastructure: not just a governance token, but the economic substrate for reserved, verifiable, on-chain compute capacity.

---

## Motivation

Subnets require a secure and accountable way to run general-purpose compute (APIs, web services, schedulers, data pipelines) without leaving the MOR economy. External infrastructure fragments settlement, weakens token alignment, and prevents unified accounting across inference and execution workloads. Providing a Router-managed runtime closes the operational loop: stake → execution → settlement → burn.

---

## Specification

**Extend the Router to support Docker/OCI workloads priced via MEUs:**

- **MCU → MEU conversion:** Stakers earn MCUs (1 MCU = 1 MOR staked per epoch). At session start, MCUs convert 1:1 to MEUs, which are consumed by runtime execution.
- **Epoch-scoped accounting:** MEUs expire at epoch boundaries (default: 24h). Unused MEUs do not roll over unless governance enables auto-renewal.
- **Provider adapters:** Minimal interface (provision, start, stop, meter, attest) enables decentralized backends (Akash, Flux, Edge).
- **Capability profiles:**
  - `d.strict` - deterministic execution (pinned images, m-of-n validation)
  - `t1.confidential` - TEE attestation (SGX, SEV-SNP, TDX)
- **Resource classes:** Governance-defined CPU/GPU/RAM/IO tiers (e.g., c1.small, g1.small).
- **Privacy by design:** Router records only metadata (service handle, duration, provider ID) with no payloads.

---

## Economic Flow

1. Subnet stakes MOR → earns MCUs
2. Session initiates → MCUs convert to MEUs
3. Runtime burns MEUs per resource-hour
4. Provider receives MOR escrow on verified completion
5. Burn reduces supply; staking increases demand

---

## Governance Parameters

- `EPOCH_LENGTH` - Default: 86400s (24h); tunable for testnets
- `ROLLOVER_POLICY` - Auto-terminate vs. auto-renew across epochs
- `MIN_PROVIDER_BOND` - MOR bond required for provider participation
- `BURN_RATE_CURVE` - MEU cost per resource class (initially fixed, transitions to dynamic pricing based on utilization)

---

## Dependencies

- **MRC 54:** MCU framework (staking entitlement)
- **MRC 25:** Router contracts (session and settlement)
- **MRC 59:** Subnet namespace (service naming)
- **MRC 48:** Compute lending (delegation and borrowing)

---

## Risks & Mitigations

| Risk | Mitigation |
|------|-----------|
| Provider centralization | Adapter interface enables permissionless provider addition |
| Long-running sessions | Auto-terminate T-5min before epoch boundary with prorated refunds |
| Provider failure | Bond requirement + slashing for non-performance |
| MEU price discovery | Phase 1: fixed rates; Phase 2: dynamic pricing via Router telemetry |

---

## Open Questions

1. Should cross-epoch sessions auto-rollover (opt-in) or always terminate?
2. Refund policy for interrupted sessions (full, partial, none)?
3. MEU attestation standard for confidential workloads?
4. Cross-subnet composability and shared state semantics?

---

## Summary

MRC 91 converts staking entitlement into execution capacity, grounding general-purpose compute inside the Router. It extends MOR's economic model from inference to full application stacks, enabling subnets to run APIs, schedulers, and data jobs with unified on-chain accounting.

**Autonomy through protocol.**

---

## Compatibility

This proposal extends MRC-25 (Router) without replacing existing functionality. MEU accounting, adapter interfaces, and namespace resolution are additive modules. Any modifications to Router contracts should be proposed via focused MRC-25 amendments.

---

**Non-normative.** Reference implementations may be contributed by community maintainers; details live in the runtime/registry repos.

---

## Metadata

```yaml
id: MRC91
title: Token Native Docker Compute
authors: ["Robert Christian (@robertjchristian)"]
category: "Runtime Infrastructure"
summary: "Router-integrated runtime layer converting MCU stake to MEU execution capacity for general-purpose Docker/OCI workloads."
status: "Discussion"
discussion_url: "https://discord.gg/morpheusai"
contact: "@robertjchristian"
keywords: ["docker","oci","runtime","router","subnet","mcu","meu","mrc25","mrc48","mrc54","mrc59"]
```
