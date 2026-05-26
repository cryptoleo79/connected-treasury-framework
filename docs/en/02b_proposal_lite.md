# Connected Treasury Framework — Phase 0 Lite Pilot

**Treasury Withdrawal Governance Action · 2026 Cycle · Minimal-ask variant**

## What this is

A 10M ADA dashboard-and-delegation-pilot version of the CTF — designed to *pass*, not to optimize. It tests the smallest version of the framework that still produces meaningful evidence. Use this variant when the community appetite is low and a larger proposal would fail.

## Problem

Same as the full CTF Phase 1: the Cardano treasury holds 1.621B ADA generating zero yield, depleting at ~350M ADA/year. The full Phase 1 proposal (50M ADA) tests the framework at scale. This Lite variant tests the *mechanism* at a scale low enough that even skeptical DReps cannot reasonably reject it on size grounds.

## Scope

This pilot deploys 10M ADA (~0.6% of treasury, ~$2.4M USD) over 12 months. It validates three things only:

- **Curated pool selection works** — the criteria publish, the DRep ratification process functions, the auto-abstain registration holds.
- **The dashboard tracks reality** — every delegation, every yield event, every USD valuation (via Pyth) is queryable, public, and accurate.
- **Yield comes back** — small but measurable monthly returns to the treasury, demonstrating the loop closes.

Strategic reserve and loan-first components are deferred to Phase 1 proper.

## Deliverables

1. **Curated pool list** of 5–10 stake pools meeting published criteria. DRep-ratified at onset.
2. **9M ADA delegated** across the curated network in an administrator multisig.
3. **Public dashboard** (open-source MIT/Apache 2.0) with Pyth-anchored USD valuation, monthly yield events, full delegation history.
4. **Monthly on-chain yield returns** to the treasury.
5. **Final report at 12 months** with full data release and recommendation on Phase 1 progression.

## Milestones

| Quarter | Milestone |
|---|---|
| Q3 2026 | Administrator stood up, criteria published, DReps ratify 5–10 pools |
| Q4 2026 | 9M ADA delegated, dashboard v1 live, first monthly yield return |
| Q2 2027 | Mid-pilot data release |
| Q3 2027 | Pilot completion, full principal returned, Phase 1 recommendation |

## Sustainability path

| Flow | Amount | Direction |
|---|---|---|
| Initial withdrawal | 10M ADA | Treasury → Administrator |
| Principal returned at completion | 9M ADA | Administrator → Treasury |
| Operational budget consumed | 1M ADA | Administrator (12 months) |
| Expected yield (~4% × 9M × 1 yr) | ~0.36M ADA | Administrator → Treasury monthly |
| **Net change to treasury** | **–0.64M ADA** | **Small net cost** |

This variant is *not* net-positive — the operational cost (1M ADA) exceeds the expected yield (~0.36M ADA) because the principal is small. That's deliberate: the cost of learning whether the framework works is ~0.64M ADA, less than 0.04% of the treasury. The Lite pilot pays for itself in information, not yield.

If the pilot succeeds, Phase 1 (50M ADA, +0.9M ADA net) follows with confidence.

If the pilot fails, the framework is falsified empirically for under 1M ADA, and the community has learned something valuable for the cost of one mid-sized failed proposal in any given month.

## Budget breakdown

| Line item | ADA | Purpose |
|---|---|---|
| Dashboard development + hosting | 0.5M | Open-source build, 12 months hosting, Pyth integration |
| Administrator operations + audits | 0.4M | Multisig, monthly reporting, end-of-pilot audit |
| Contingency | 0.1M | Documented unforeseen costs only |
| **Total operational** | **1.0M** | |
| Delegated principal (returned) | 9.0M | |
| **Total ask** | **10.0M** | |

## Why this passes when the full proposal might not

The full Phase 1 proposal is structured to be net-positive at exit, which is a strong argument. The Lite proposal is structured to be **impossible to oppose on size grounds**. At 10M ADA — 0.6% of treasury, less than a single mid-sized rejected proposal from this week's cycle — even maximally skeptical DReps struggle to construct a "this is too much" argument.

The Lite proposal also de-risks every non-financial objection:
- No BTC, no stablecoin allocation (deferred to Phase 1)
- No protocol changes
- No constitutional amendments
- No founding-entity dependence
- One clear deliverable: prove the dashboard + delegation mechanism works
- Single 12-month duration

It's the minimum viable evidence-gathering proposal.

## When to use which variant

| Variant | Use when |
|---|---|
| **Lite (this doc, 10M ADA)** | Community sentiment is hostile to new spending; first submission; reputation-building |
| **Phase 1 (50M ADA, net +0.9M)** | Community appetite supports learning; Lite has succeeded; or strong coalition exists |

These are sequential, not parallel. Submit Lite first if uncertain. Use the success of Lite as the strongest possible argument for Phase 1.

## Ask

**10 million ADA**, single tranche, 12-month duration, structured as 9M ADA repayable delegation principal + 1M ADA operational budget. Net expected change to treasury: **–0.64M ADA** (the cost of validating the model).

Successful completion is the strongest possible foundation for the full Connected Treasury Framework proposal.
