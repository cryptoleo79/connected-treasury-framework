# Connected Treasury Framework — Phase 1 Pilot

**Treasury Withdrawal Governance Action · 2026 Cycle**

## Problem

The Cardano on-chain treasury holds 1.621B ADA generating zero yield, while annual withdrawals run at ~350M ADA. At current pace the treasury is depleted by Q3 2033. The treasury's USD purchasing power has fallen ~80% since November 2024 — value destruction driven not by spending, but by single-asset price exposure on a depreciating reserve. Every other large Cardano-aligned treasury (notably the Cardano Foundation) has already begun diversifying and earning yield. The on-chain treasury has not.

## Scope

This pilot deploys 50M ADA (~3.1% of treasury) over 18 months to prove a self-sustaining treasury model. It tests three of the five Connected Treasury Framework components:

- **Yield loop:** delegation to a curated stake pool network with mandatory auto-abstain on votes
- **Strategic reserve:** a small structured BTC + stablecoin position to back USD operating costs
- **Open reporting:** a public dashboard tracking every flow, delegation, and yield event on-chain

The loan-first and spending-cap components are addressed through separate Info Actions and are not part of this withdrawal.

## Out of scope

- No protocol or constitutional changes (these belong in a future CIP — see attached outline)
- No allocation to any pool operated by the proposer or affiliated entities
- No discretionary investment outside the published pool criteria
- No use of treasury voting power on any governance action

## Deliverables

1. **Curated pool network** of 10–25 stake pools meeting published criteria: independent infrastructure, pledge ≥ ecosystem median, public telemetry, auto-abstain registration, open-source contributions or operator-first tooling. Selection ratified by DRep vote.
2. **48M ADA delegated** across the curated network. Principal remains in administrator-controlled multisig at all times.
3. **Strategic reserve administrator** holding ~12% of the deployed amount (~6M ADA equivalent) in a structured BTC + USDCx position. USDCx is Circle's USDC-backed stablecoin issued via xReserve on Cardano (live February 27, 2026), with cross-chain interoperability via CCTP. Use of a Tier 1 audited stablecoin — not an experimental synthetic — is a deliberate de-risking choice. Reserve sized to back ~18 months of operating costs.
4. **Public dashboard** at a stable URL exposing: delegation allocations per epoch, pool performance, monthly yield returned to treasury, reserve composition, and full transaction history. Live USD valuation of all assets via Pyth Network feeds (live on Cardano since late 2025, sub-100ms institutional-grade pricing). All data on-chain and independently verifiable.
5. **Monthly on-chain reporting** with quarterly community calls.

## Milestones

| Quarter | Milestone | Verification |
|---|---|---|
| Q3 2026 | Administrator entity stood up; pool selection criteria published; DRep ratification of initial pool list | On-chain governance action with the ratified list |
| Q4 2026 | First 24M ADA delegated; dashboard v1 live; first yield return to treasury | Stake distribution certificate + dashboard URL + on-chain return tx |
| Q1 2027 | Full 48M ADA deployed; strategic reserve established; first quarterly report | Stake delegation complete + reserve composition published |
| Q2 2027 | Mid-pilot review: yield performance, dashboard adoption, community feedback | Public report + DRep continuation vote |
| Q4 2027 | Pilot completion: full return of principal to treasury, final report, framework recommendation for Phase 2 | Return tx + framework adoption proposal |

## Sustainability path

This is the central design feature. The pilot is structured to be **net-positive to the treasury at completion.**

| Flow | Amount | Direction |
|---|---|---|
| Initial withdrawal | 50M ADA | Treasury → Administrator |
| Principal returned at completion | 48M ADA | Administrator → Treasury |
| Operational budget consumed | 2M ADA | Administrator (over 18 months) |
| Expected staking yield (~4% × 48M × 1.5yr) | ~2.9M ADA | Administrator → Treasury monthly |
| **Net change to treasury** | **+0.9M ADA** | **Positive** |

The pilot is functionally a 2M ADA grant for dashboard + operations, plus a 48M ADA repayable structure that generates ~2.9M ADA of yield returns. The treasury ends the pilot with more ADA than it started with, and with a proven yield-generating infrastructure to scale.

## Budget breakdown

| Line item | ADA | Purpose |
|---|---|---|
| Operations (admin entity, multisig, audits) | 1.0M | 18 months of governance + custody + quarterly audit |
| Dashboard development + hosting | 0.6M | Open-source build, hosting, on-chain indexing |
| Reserve administrator costs | 0.3M | Custody multisig + monthly rebalancing operations |
| Contingency | 0.1M | Reserved for documented unforeseen costs only |
| **Total operational** | **2.0M** | |
| Delegated principal (returned at completion) | 48.0M | |
| **Total ask** | **50.0M** | |

## Reporting commitments

- Monthly on-chain transaction publishing yield returns
- Monthly dashboard data refresh
- Quarterly written report to DRep voters with delegation, yield, reserve, and dashboard usage metrics
- Mid-pilot (Q2 2027) and end-pilot (Q4 2027) community calls
- Full open-source release of dashboard code under MIT or Apache 2.0
- Administrator entity board governance via Constitutional Committee oversight, in line with existing Snek Foundation precedent

## Team

To be assembled through open call following ratification. Required composition: at least one independent SPO with multi-year operational track record, one independent treasury/audit professional, one community-elected representative, with Constitutional Committee oversight. No founding entity (IOG, Emurgo, Cardano Foundation) holds a controlling seat — preserves perceived neutrality.

## Why this passes when other proposals are failing

This week's votes show the community will fund work with clear deliverables (Leios passed at 84%) and reject opaque ongoing commitments (Maintenance Initiative at 46%, Vision 2026 at 13%). This proposal:

- Has measurable deliverables (delegated principal, yield returned, dashboard live)
- Has a defined completion date and full principal return
- Is net-positive to the treasury at exit
- Carries no recurring obligation
- Routes around the "founding entities funding themselves" objection by excluding their controlling participation
- Costs the treasury 2M ADA on a 1.621B ADA base — well below the threshold that triggers community resistance

## Ask

**50 million ADA**, single tranche, 18-month duration, structured as 48M ADA repayable delegation principal + 2M ADA operational budget. Net expected change to treasury: **+0.9M ADA**.

---

*This proposal is a template draft. Final submission requires: ratified administrator entity, finalized pool selection criteria, dashboard technical specification, and Constitutional Committee oversight mechanism — all of which would be developed in the 30 days preceding submission.*
