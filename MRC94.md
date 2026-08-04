# MRC94: Capital MOR Mint / Claim Destination — Arbitrum or Base (Preferred Dual Path)

### Status: Under Discussion

### Category: MRI — Smart Contracts
- Maintainer Discord: SmartAgents
- Implementation repo: https://github.com/MorpheusAIs/SmartContracts

### Author(s)
- **EnergyHound** — requestor / product owner of scope  
- **BowtiedBlueFin** — technical inputs (capital / compute interface constraints; dual-L2 mint complexity)  
- **Request for Bids** target: **Smart Contract Developer** as assigned by **SmartAgents** (responds to the bid request in this MRC; not named personally)

---

## Summary

Capital-side MOR is claimed/minted through the capital distribution pipeline. Users who need MOR on **Base** (where activity and staking/gateway ops have concentrated) still face post-claim bridging friction from **Arbitrum**. At the same time, Arbitrum remains a real home for liquidity and for users who want to stay there.

This MRC does three things:

1. **Defines two explicit mint-destination options** the protocol may ship:
   - **Option A — Base-only mint:** claims mint to **Base** only (fallback if dual path is too costly).
   - **Option B — Dual mint (preferred):** at claim time, mint to **either Arbitrum or Base** (user-selectable; one destination per claim).
2. **Records the thought process** for why dual support is the **preferred** product outcome, and when Base-only remains an acceptable fallback.
3. **Defines a Request for Bids** to the **Smart Contract Developer** so maintainers choose on **hours, risk, and dependencies** — not on slogans.

**Preferred outcome: Option B** — ability to mint capital claims to **Arbitrum or Base**. Option A is retained only as a cost/complexity fallback after written bid bids.

This capital change is **not** part of any concurrent **compute** upgrade (e.g. bugs + hot/cold wallet). Separate contract surface, separate deployment.

**Numbering note:** MRC91–MRC93 are claimed by open PRs on this repo for unrelated compute/runtime work ([#85](https://github.com/MorpheusAIs/MRC/pull/85), [#86](https://github.com/MorpheusAIs/MRC/pull/86)). This proposal takes the next free number that does not collide: **MRC94**.

**Scope freezes only after Option A and Option B bid responses are returned in writing under the Request for Bids.** Identity in this document uses **public aliases / role titles only** (no legal names).

---

## 1. Problem statement

| Today | Pain |
|---|---|
| Claim/mint path often lands MOR where the user does **not** primarily operate | Extra bridge step before stake / trade / gateway use |
| Bridge UX is uneven | Cheap paths exist when chosen correctly; dust and high-fee routes still hit operators |
| Activity has shifted toward **Base** | Arb-only mint then bridge is inverted for many users |
| Dropping **Arbitrum** without a dual option | Strands Arb-native users and Arb liquidity |

We are **not** proposing a full multichain redesign, OFT/NTT re-architecture, emission change, or liquidity-pool migration. We are proposing **where capital emissions mint at claim**, with a mandatory developer bid before choosing breadth.

### Related existing MRCs (not duplicates)

A repo review found **no open or merged MRC that already specifies capital claim mint destination = Base and/or Arbitrum as user choice**. Related but **different**:

| MRC | What it does | Why not this work |
|---|---|---|
| [MRC43](IMPLEMENTED/MRC43.md) (Implemented) | Protocol-owned liquidity on Base + Arbitrum | Liquidity placement, not capital **claim mint destination** |
| [MRC56](MRC56.md) | Builders V2 / multichain Base + Arbitrum tradeoffs | Builder staking design, not capital claim mint routing |
| [MRC64](MRC64.md) | MVM / registries converging on Base | Agent/registry deployment chain, not capital emissions claim |
| [MRC16](IMPLEMENTED/MRC16.md) / [MRC32](MRC32.md) / [MRC33](MRC33.md) | Multichain MOR / OFT / NTT interoperability | General token movement standards, not capital distribution claim destination |
| [MRC89](MRC89.md) | Public list of chains MOR is on | Inventory, not mint routing |
| [MRC72](MRC72.md) | Reduce capital claim lock minimum time | Claim **timing**, not claim **chain** |

---

## 2. Options

### Option B — Preferred: Mint to **Arbitrum or Base** (user-selectable)

**End state:** At claim time, the claimer selects destination chain:

| Selection | Result |
|---|---|
| **Arbitrum** | MOR minted / received on Arbitrum |
| **Base** | MOR minted / received on Base |

**Product defaults (subject to maintainer vote after bid responses):**
- **Both destinations are first-class.** Prefer shipping dual mint over Base-only.
- A **UI default** may still lean Base for new claimers if volume warrants it, but **Arbitrum must remain a one-click / one-parameter choice**, not a “bridge after claim” path.
- Exactly **one** chain receives the mint per claim (**no double-mint**).

**Intended user journey:**
1. User claims with an explicit destination (or accepts the published default).
2. MOR lands on the chosen chain only.
3. Frontend (follow-on) exposes the selector; contract is source of truth for destination.

**Technical caveat (requestor-side, not final design):** dual destination may require **one L1-side sender coordinating multiple L2 receivers** and a **where-to-mint field** through the capital message path (deposit pool → reward pool → distribution / related contracts). The bid response from the Smart Contract Developer must confirm, correct, or replace this model.

### Option A — Fallback: Mint only to Base

**End state:** Capital claims mint/receive on **Base** only.

**When A is acceptable:** only if Option B’s written bid shows materially higher hours, calendar slip, or residual risk that maintainers judge unacceptable under current resources.

**Intended user journey:** claim → MOR on Base → optional bridge to Arb for Arb-native users (explicitly worse UX for that cohort).

### Explicitly out of scope for both options

- Provider-stake reduction, model registry, compute hot/cold wallet  
- Changing emission rates, power factor, or capital deposit assets  
- Migrating all AMM / LP inventory from Arb to Base  
- Selecting a new bridge vendor (OFT vs NTT, etc.) as the core of this MRC  
- Automatic split of a single claim across two chains  

---

## 3. Thought process: why dual (Arbitrum **or** Base) is preferred

### 3.1 Why dual mint is the preferred product (Option B)

| Line of thought | Implication |
|---|---|
| **Two real homes, not one.** Base has concentrated recent ops/volume; Arbitrum retains liquidity and long-standing users. | Protocol should mint where the user lives, not force a bridge. |
| **Bridge is a product failure mode.** “Claim then figure out a bridge” exports complexity to users and support. | Prefer claim-time destination = Arb **or** Base. |
| **Fairness to early-chain users.** Evolution should **add** Base without **erasing** Arbitrum as a claim destination. | Dual path is the integrity-preserving option. |
| **Weighting without deletion.** Ops can still **default** UX toward Base (~majority weight) while keeping Arb selectable. | Default ≠ sole destination. |
| **One claim, one chain.** Dual does **not** mean split mint; it means choice. | Clear invariant for the Smart Contract Developer and auditors. |

### 3.2 Why still bid Base-only (Option A)

| Line of thought | Implication |
|---|---|
| **Request is simple; dual implementation may not be.** Dual may touch the full capital message bus. | Need a costed fallback. |
| **Resource constraint.** If B is a large multiple of A in hours/risk, stalling forever helps no one. | Ship A only if B is untenable. |
| **Simplicity doctrine.** Fewer parameters when dual is not affordable. | A remains the “minimum ship.” |

### 3.3 Decision rule after bids return

1. **Safety invariants** (no double-mint, pause, upgrade path) — either option must pass.  
2. **Prefer Option B** when hours/calendar/risk are acceptable.  
3. **Hours + calendar** to mainnet-ready.  
4. **Residual risk / audit need** (capital contracts → high bar).  
5. **Weights** proportional to the **accepted** option only.

**Default maintainer recommendation:**  
- If B is within a reasonable multiple of A and risk is comparable → **accept B** (Arbitrum or Base).  
- If B is a large multiple of A or multi-month slip → **accept A**, file follow-on for dual later.

---

## 4. Process: requesting minting to Arbitrum and to Base

### Step 0 — Preconditions

- [ ] This MRC is opened as a PR on `MorpheusAIs/MRC`.  
- [ ] Discord MRC discussion thread created; `discussion_url` filled in metadata.  
- [ ] Confirm this work is **capital** contracts only.  
- [ ] **SmartAgents** names the **Smart Contract Developer** (single bid respondent) before the Request for Bids is treated as binding.

### Step 1 — Publish both options publicly

- [ ] Post Option B (preferred) and Option A (fallback) in Discord + PR.  
- [ ] State: **both are priced; preferred acceptance is B** unless the bid response shows B is untenable.

### Step 2 — Issue Request for Bids (Section 5)

- [ ] Send Request for Bids packet on this PR + engineering channel of record.  
- [ ] **Deadline: 5 business days** (extend once if unavailability is known).  
- [ ] Require **separate line items** for A and B.

### Step 3 — Normalize bid

- [ ] Smart Contract Developer returns filled bid template (§5.4).  
- [ ] Technical counterparty (**BowtiedBlueFin** and/or Smart Contracts maintainer) sanity-checks architecture.  
- [ ] Discovery spike only if needed (cap **≤ 4–8 hours**), then re-bid.

### Step 4 — Maintainer decision

- [ ] Side-by-side comparison in Discord + PR.  
- [ ] Apply §3.3; record **Accepted: B | A | A now + B later | Reject**.  
- [ ] Set weights for accepted option only; move Pending / In Progress per MRC00.

### Step 5 — Implementation handoff

- [ ] Freeze to accepted option.  
- [ ] Design note → testnet → review → mainnet.  
- [ ] Frontend selector follow-on if B ships (contract may land first with default + parameter).

### Step 6 — Acceptance

- [ ] Tests in §6 pass; MRC Implemented only when live path matches accepted option on SmartContracts MRI.

---

## 5. Request for Bids (Smart Contract Developer)

### 5.1 Purpose

This section is the **Request for Bids**. Comparable written bid responses for:

| ID | Name | Preference |
|---|---|---|
| **B** | Dual: mint to **Arbitrum or Base** per claim | **Preferred** |
| **A** | Mint to **Base only** | Fallback |

### 5.2 Roles (aliases / titles only)

| Role | Who | Responsibility |
|---|---|---|
| **Requestor** | EnergyHound or designee | Issues Request for Bids; owns product priority; does not invent hours |
| **Technical counterparty** | BowtiedBlueFin and/or Smart Contracts maintainer | Architecture sanity-check |
| **Bidder (Smart Contract Developer)** | Assigned by SmartAgents | Submits bid responses for A and B |
| **Acceptor** | SmartAgents / capital maintainers | Chooses A or B; sets weights |

### 5.3 Request for Bids packet

**Subject:** MRC94 Request for Bids — capital claim mint destination (preferred dual Arb/Base vs Base-only fallback)

> We have filed **MRC94**. This is a **Request for Bids** to the **Smart Contract Developer**. Before freezing scope, we need written bid responses for **two options**. Do not blend A and B into one number.
>
> **Preferred product outcome: Option B** — capital claims can mint to **Arbitrum or Base** (one destination per claim).  
> **Option A** (Base only) is a fallback if B is not viable on hours/risk/calendar.
>
> **Context**
> - Surface: **capital** distribution / claim / mint only.  
> - **Not in scope:** compute upgrades, provider stake redesign, model registry, emission math.  
> - Goal: claim-time destination choice (Arb or Base); reduce forced post-claim bridging.
>
> **Option B (preferred) — Mint to Arbitrum or Base**  
> Each claim specifies **Arbitrum** or **Base**; no double-mint; one destination per claim. Recommend supporting a default + override.
>
> **Option A (fallback) — Mint only to Base**  
> Capital MOR claims mint/receive on **Base** only.
>
> **For EACH option provide:**
> 1. Contracts touched (named)  
> 2. Design approach (≤15 lines); for B confirm/correct L1 sender / multi L2 receiver / where-to-mint field model  
> 3. Hours: low / likely / high  
> 4. Calendar: start → testnet → mainnet-ready  
> 5. Dependencies  
> 6. Risks (double-mint, message loss, upgrade breakage, pause, wrong-chain UX)  
> 7. Test plan  
> 8. Audit recommendation  
> 9. Open questions  
> 10. Optional weights suggestion for that option only  
>
> **Deadline:** 5 business days from Request for Bids post on the PR.  
> **Format:** reply on the MRC94 GitHub PR.
>
> **Decision rule:** safety first; **prefer B** when viable; then hours/calendar; residual risk; weights for accepted option only.

### 5.4 Bid response template (Smart Contract Developer fills)

```markdown
## MRC94 Bid Response — Smart Contract Developer — [Alias or role] — [Date]

### Option B — Dual mint (Arbitrum or Base) [PREFERRED]
- Contracts touched:
- Design approach (≤15 lines):
- Hours (low / likely / high):
- Calendar (testnet / mainnet-ready):
- Dependencies:
- Risks:
- Test plan:
- Audit recommendation:
- Open questions:
- Suggested weights (optional):

### Option A — Base-only mint [FALLBACK]
- Contracts touched:
- Design approach (≤15 lines):
- Hours (low / likely / high):
- Calendar (testnet / mainnet-ready):
- Dependencies:
- Risks:
- Test plan:
- Audit recommendation:
- Open questions:
- Suggested weights (optional):

### Comparison (required)
- Hour ratio B/A (likely):
- Single biggest risk that differs between A and B:
- Recommendation from Smart Contract Developer (B / A / A now B later) and one-sentence why:
- Discovery spike needed? (no / yes — hours and questions):
```

### 5.5 Comparison table (requestor fills after bid responses)

| Criterion | Option B (Arb or Base) **preferred** | Option A (Base-only) fallback |
|---|---|---|
| Hours (likely) | | |
| Calendar to mainnet-ready | | |
| Contracts touched (count) | | |
| Double-mint residual risk | | |
| Frontend required for MVP? | | |
| Audit recommendation | | |
| Arb user coverage | Native | Bridge required |
| Base user coverage | Native | Native |
| **Decision** | | |

### 5.6 Escalation if bid does not return

1. Day 0: Request for Bids posted on PR.  
2. Day 3: ping + confirm receipt.  
3. Day 5: deadline; SmartAgents assigns alternate Smart Contract Developer or time-boxes discovery.  
4. Do not implement without written bid response or recorded maintainer waiver.

---

## 6. Deliverables (after option accepted)

1. Written bid responses under Request for Bids for **B and A**.  
2. Maintainer decision (**prefer B**).  
3. Design note for accepted option only.  
4. Implementation: testnet → review → mainnet capital upgrade.  
5. Acceptance tests:
   - Correct amount on intended chain  
   - **No double-mint** across Base and Arbitrum  
   - Pause / failure documented  
   - Gas envelope vs current claim  
   - For B: **both** Arbitrum and Base paths verified  
6. Ops checklist: signers, verifiers, rollback owners.  
7. Follow-on (if B): claim UI chain selector + mor.org docs.

## 7. Value proposition

- Claimers land MOR on **Arbitrum or Base** without a forced bridge.  
- Base-only remains available only as a costed fallback.  
- Capital-dev hours spent on a **chosen** path after public bids.  
- Compute ship work stays unblocked.

## 8. Dependencies

- Smart Contract Developer bandwidth + completed Request for Bids response (hard gate).  
- Multisig / capital upgrade process.  
- Frontend if B accepted (can lag if parameterizable).  
- No dependency on compute hot/cold + bugs batch.

## 9. New weights requested

**TBD** — proportional to the **accepted** option after bid responses.

## 10. Existing weights

Existing capital distribution / claim pipeline under SmartContracts MRI. This MRC changes **destination routing of mint/claim**, not the capital-provider product definition.

## 11. Background

Maintainer operating discussion: capital mint destination treated as a **separate capital** workstream from compute upgrades; dual-path complexity called out; **preferred product is claim-time mint to Arbitrum or Base**; Base-only retained as fallback if dual is not viable on hours/risk (per bid). Identity on this MRC uses public aliases / roles only.

## 12. Status

Under Discussion — Request for Bids is part of the MRC. **Preferred acceptance: Option B.**

## Metadata

---
id: MRC94
title: Capital MOR Mint / Claim Destination — Arbitrum or Base (Preferred Dual Path)
authors: ["EnergyHound", "BowtiedBlueFin"]
category: Smart Contracts
summary: >
  Preferred: capital MOR claims mint to either Arbitrum or Base (user-selectable,
  one destination per claim). Fallback: Base-only if dual-path bid is untenable.
  Gate on Request for Bids responses for both options. Aliases only in author fields.
  Separate from compute contract upgrades. Numbered MRC94 due to open PRs on 91–93.
status: Under Discussion
discussion_url: ""
contact: "EnergyHound; BowtiedBlueFin (technical); SmartAgents (maintainer)"
keywords: ["capital", "mint", "claim", "Base", "Arbitrum", "distribution", "request-for-bids", "L2", "MOR", "dual"]
---

## References

- MRC00: https://github.com/MorpheusAIs/MRC/blob/main/MRC00.md
- MRC_TEMPLATE: https://github.com/MorpheusAIs/MRC/blob/main/MRC_TEMPLATE.md
- SmartContracts: https://github.com/MorpheusAIs/SmartContracts
- MRC16: https://github.com/MorpheusAIs/MRC/blob/main/IMPLEMENTED/MRC16.md
- MRC43 (PoL on Base — related, not duplicate): https://github.com/MorpheusAIs/MRC/blob/main/IMPLEMENTED/MRC43.md
- Open number reservations (not capital mint): https://github.com/MorpheusAIs/MRC/pull/85 · https://github.com/MorpheusAIs/MRC/pull/86
