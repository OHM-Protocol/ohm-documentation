# OHM Protocol – Technical Whitepaper (Evolving Draft)

> **Status:** Draft – evolving alongside the design and implementation.  
> **Audience:** Developers, protocol designers, researchers, and mission-aligned collaborators.

This document translates the vision of *The Abundance Protocol* into a concrete protocol and economic design for OHM. It is meant to evolve as we build, test, and learn.

---

## 1. Introduction

### 1.1 Problem Statement

The current global economic “operating system” is built around:

- Competition for scarce resources.
- Externalised ecological and social costs.
- Centralised control over capital and coordination.

This produces:

- Ecological overshoot (climate, biodiversity, pollution).  
- Structural precarity and inequality.  
- Fragmented efforts to do good that struggle to scale.

### 1.2 OHM’s Goal

OHM Protocol aims to provide:

- A **public, open-source coordination layer** for global good.  
- A **regenerative economic engine** that funds Universal Basic Income (UBI) from real, verifiable impact.  
- A **governance system** where power is earned by contribution and goodwill, not capital alone.

---

## 2. High-Level Architecture

OHM is composed of five main layers:

1. **Identity & Profiles** – on-chain representation of contributors and communities.  
2. **Impact Credits & Projects** – measurement and tracking of verifiable acts of good.  
3. **Treasury & Economic Engine** – capital allocation, UBI, and regenerative investments.  
4. **Verification & Oracles** – bridging physical-world impact into digital trust.  
5. **Intelligence & UX** – AI guidance and user-facing interfaces.

We aim for:

- **Modular contracts** – clear separation of concerns.  
- **Composable interfaces** – front ends, bots, and other UIs can plug in without breaking core guarantees.  
- **Upgrade paths** – governance-controlled upgrades, with strong constraints to protect contributors.

---

## 3. Identity & Profiles

### 3.1 User Profile Contract

Each participant has an on-chain **Profile** that acts as:

- A stable identifier (linked to a wallet or aggregate of wallets).  
- A **Digital Legacy Ledger** of contributions and roles.  
- The anchor for governance rights and UBI eligibility.

Key fields (conceptual):

- `profile_id` – unique identifier.  
- `wallets[]` – associated addresses.  
- `global_good_credits` – aggregated, verifiable impact score.  
- `reputation_signals[]` – endorsements, badges, roles.  
- `metadata_uri` – pointer to off-chain profile data (e.g. IPFS/Arweave).

### 3.2 Community / Project Profiles

Communities (e.g. OHB) and organisations can also have profiles:

- Represent multi-person entities (DAOs, collectives, projects).  
- Hold their own contribution and impact histories.  
- Interact with the protocol as “first-class citizens”.

---

## 4. Impact Credits & Projects

### 4.1 Global Good Credits

**Global Good Credits (GGCs)** are the primary measure of positive impact in the system.

Properties:

- **Non-transferable** (soulbound-style): cannot be sold or traded.  
- **Earned, not bought**: only issued on verified acts of good.  
- **Pillar-aware**: tracked across the three pillars:
  - Environment  
  - Animal welfare  
  - Humanity

Usage:

- Input into **governance rights** (Proof-of-Goodwill).  
- Eligibility and weighting for **UBI**.  
- Signal for matching in the **AI guidance layer**.

### 4.2 Project Contracts

Each significant initiative is represented by a **Project Contract**.

Key concepts:

- **Lifecycle**:
  - Draft → Active → Completed → Archived.  
- **Fields** (conceptual):
  - `mission` – human-readable description.  
  - `owner / steward` – responsible profile(s).  
  - `milestones[]` – key goals with verification criteria.  
  - `funding_allocations[]` – amounts and sources from the treasury.  
  - `impact_events[]` – recorded, verified outcomes.

When a milestone is verified:

- The project contract:
  - Emits an **Impact Event**.  
  - Triggers **GGC issuance** to relevant contributors.  
  - May trigger **additional funding** (stigmergic micro-investment).

---

## 5. Treasury & Economic Engine

### 5.1 Treasury Contract

The **DAO Treasury** is the central capital pool governed by contributors.

Responsibilities:

- Hold protocol-owned assets (native tokens, stablecoins, LP positions, etc.).  
- Allocate funds to:
  - Regenerative projects.  
  - UBI distributions.  
  - Operational costs (security, infrastructure, etc.).

Guarantees we aim for:

- Transparent, on-chain accounting.  
- Governance-controlled parameters.  
- Clear separation between:
  - **Principal capital** for long-term investments.  
  - **Distributable flows** for UBI and grants.

### 5.2 UBI Mechanism (Conceptual)

UBI is powered by:

- Returns from regenerative investments.  
- Protocol fee income and impact markets (see below).  
- Potential external philanthropic inflows (e.g. VPO).

Key ideas:

- **Eligibility**: based on presence in the system + a minimum Proof-of-Goodwill (GGCs).  
- **Distribution**: periodic (e.g. monthly), with caps and rate parameters set by governance.  
- **Adaptivity**: can adjust as treasury health, impact returns, and user count evolve.

### 5.3 Impact Market & Fees

Potential components:

- **Micro-transaction protocol fee**:  
  - Very small percentage on transactions within the ecosystem, routed to the treasury.

- **Algorithmic Impact Market**:  
  - Verified impact units (e.g. tonnes of CO₂ sequestered) are tokenized.  
  - The treasury automatically buys and “retires” these tokens to:
    - Support impact projects.  
    - Create a price signal for tangible regeneration.

Design goal:

- Make **healing the planet economically rewarding** and structurally favoured.

---

## 6. Verification & Oracles

### 6.1 The Oracle Problem

We must answer:

> How can the protocol trust that a claimed act of good really happened in the physical world?

Challenges:

- Manipulable, single data sources.  
- Adversarial behaviour (gaming for GGC/UBI).  
- Latency and ambiguity in ecological data.

### 6.2 Multi-Source, Multi-Layer Verification

Approach:

- **Endogenous verification** wherever possible (protocol-internal checks).  
- **Multi-source oracles** for physical-world events.

Components:

- **Sensor data**:
  - Satellite imagery.  
  - IoT sensor networks.  
  - Bio-acoustic and other environmental streams.

- **Community & expert attestations**:
  - Reputation-weighted attestations from trusted roles.  
  - Slashing / penalty mechanisms for provable fraud.

- **AI modelling**:
  - Baseline models of ecosystem health.  
  - Anomaly detection and consistency checks between independent data sources.

Issue pattern:

- A project milestone defines **verification conditions**.  
- A verifier module / oracle network:
  - Aggregates relevant signals.  
  - Reaches a decision on whether the conditions are met.  
- On success:
  - Emits an **Impact Event** to the project contract.  
  - Triggers GGC issuance and any associated financial flows.

---

## 7. Governance

### 7.1 Governance Principles

- **Proof-of-Goodwill**:  
  Governance weight must be closely tied to **verifiable contribution**, not just capital.

- **One contributor, one voice (weighted)**:  
  We aim for:
  - Protection against plutocratic capture.  
  - Recognition of sustained, high-quality contribution.

- **Upgradability with constraints**:  
  The protocol must evolve, but core guarantees (e.g. non-transferability of GGCs, transparency of treasury) should be hard to weaken.

### 7.2 Governance Mechanisms (Draft)

Potential structure:

- **Governance token(s)**:
  - Could be partially derived from GGCs (e.g. some function of lifetime/active contribution).  
  - Could also include stake components to ensure skin-in-the-game.

- **Proposal types**:
  - Parameter changes (e.g. UBI rate, fee rates).  
  - Treasury allocations (project funding, grants).  
  - Contract upgrades (via upgrade proxies or new deployments).

- **Voting**:
  - Off-chain signalling (e.g. Snapshot-style) for low-risk decisions.  
  - On-chain execution for treasury and contract changes.

- **Safeguards**:
  - Quorum and supermajority thresholds for critical changes.  
  - Time-locks and veto / delay mechanisms to allow community review.

---

## 8. Intelligence & User Experience

### 8.1 Global Good AI Agent

Role:

- **Matchmaker** between:
  - People (skills, passions, locations).  
  - Needs (projects, communities, ecosystems).

Inputs:

- On-chain data:
  - Profiles, GGCs, project records, impact events.  
- Off-chain signals:
  - User preferences, availability, learning goals.

Outputs:

- Personalised suggestions:
  - “Here is a project where your skills have outsized leverage.”  
  - “Here is a small action you can take this week to move a milestone.”  
- Contextual education:
  - Explanations of how protocol components work.  
  - Suggestions for upskilling paths.

### 8.2 Front-End & Integration

- **MVP Frontend**:
  - Web app that allows:
    - Profile management.  
    - Project discovery and participation.  
    - Viewing one’s Living Impact Ledger.

- **Integrations**:
  - Discord bots, Notion integrations, and other tools that bring OHM into existing community workflows.

Design goals:

- Minimise cognitive load for newcomers.  
- Make contribution pathways clear and inviting.  
- Expose protocol primitives without forcing users to think in low-level blockchain terms.

---

## 9. Security, Risks, and Open Questions

### 9.1 Security Considerations

- Smart contract security:
  - Formal audits, bug bounties, and conservative upgrade policies.  
- Oracle and data-integrity risks:
  - Mitigate single points of failure.  
  - Design economic and technical disincentives for fraud.

### 9.2 Economic & Social Risks

- Gameability of GGC and UBI:
  - Designing issuance rules that privilege genuine, high-quality impact.  
- Governance capture:
  - Ensuring broad contributor participation.  
  - Avoiding over-concentration of influence.

### 9.3 Open Questions (Evolving List)

- Exact formulae for converting GGCs into governance weight.  
- Optimal balance between automated (sensor) and human (community/expert) verification.  
- Best primitives for the impact market to avoid perverse incentives.

*(This section should expand over time as we discover more design questions.)*

---

## 10. Roadmap (Technical Milestones – High Level)

1. **MVP Phase**
   - Implement core profile contracts.  
   - Implement initial project contract and basic GGC issuance.  
   - Wire an MVP frontend to these contracts.  

2. **Gulf Pilot Integration**
   - Migrate OHB manual records into on-chain or hybrid storage.  
   - Trial early verification flows with community attestations.  

3. **Verification Layer Expansion**
   - Prototype multi-source oracle integration for at least one use case.  

4. **Treasury & UBI Prototype**
   - Stand up a minimal treasury and test small-scale, governance-controlled distributions.  

5. **Impact Market & Fees**
   - Design and test basic impact tokenisation and treasury buyback behaviour.  

6. **Refinement and Audit**
   - Harden contracts, run audits, refine governance.  

This roadmap is intentionally high-level and will be fleshed out with concrete issues and implementation details in the code repositories.

---

## 11. Conclusion

OHM Protocol is an attempt to encode, in open-source infrastructure, a new way of organising human effort:

- Contribution and goodwill as primary sources of power.  
- Regeneration as the core economic activity.  
- Radical transparency and community ownership by design.

This technical whitepaper is a living document. As the community builds, tests, and refines OHM, this text should track the **real** protocol—capturing both what exists and what we are aiming toward.

Contributions and critiques are welcome via:

- GitHub issues and pull requests.  
- Community discussions in Discord and shared design spaces.
