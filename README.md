# Connected Treasury Framework — Document Packet

**A proposal to turn the Cardano on-chain treasury from a passive ADA reservoir into a yield-generating, transparently-reported, fiscally-disciplined endowment.**

*Last updated: May 26, 2026*

---

## What is this packet?

Six documents that together make the case for the Connected Treasury Framework (CTF), provide a submission-ready governance proposal, sketch the long-term protocol upgrade, and let anyone interrogate the numbers themselves.

The CTF is not a single proposal. It's a coherent model assembled from elements that already have community support (Leios-style transparency, Snek-style loans, Foundation-style diversification) and from production-ready Cardano infrastructure that didn't exist six months ago (Pyth oracle feeds, USDCx Tier 1 stablecoin).

---

## Read in this order

The packet is designed to be read sequentially. Each document builds on the previous and answers questions the previous one raises.

### 1. `01_report.md` — The foundation document
Read this first. It establishes the problem (treasury erosion), the data (this week's governance votes, historical balance/USD value, runway projections), and the framework (five components, comparison to active proposals, implementation phases). 3,300 words. ~12 minutes.

**Use case:** Cardano Forum long-post, briefing document for DReps, source material for any further communication.

### 2. `02_proposal.md` — The submission-ready governance action
A one-page Phase 1 pilot in the Leios template that's currently winning votes. Structured to be **net-positive to the treasury at exit** (+0.9M ADA). The actual ask is 50M ADA: 48M repayable delegation principal + 2M operational. ~1,000 words. ~4 minutes.

**Use case:** What gets submitted to gov.tools. Adapt the proposer/team section, then post.

### 3. `03_cip.md` — The long-game protocol upgrade
A CIP outline for protocol-level treasury staking with mandatory voting-power neutralization at the ledger level. This is the heavy structural change that unlocks ~65M ADA/year on the full treasury. Hard fork required. 18–30 month path to mainnet. 1,700 words. ~7 minutes.

**Use case:** Submission to the CIP repository, technical conversations with ledger implementers, signal that Phase 1 has a Phase 2.

### 4. `index.html` — The interactive tool
A standalone web page with four sliders (yield, spending cap, loan return, reserve %) that shows real-time runway projections versus the do-nothing baseline. No backend, no dependencies beyond Chart.js. Drop on any web host or open in a browser.

**Use case:** Forum embed, Twitter share, the thing you point skeptics to when they want to argue with the numbers. The simulator goes last because by the time someone wants to dial parameters, you've already won the argument that there's a problem worth solving.

### 5. `05_objections.md` — The hostile-review defense
Pre-emptive responses to every likely objection: market impact, centralization concerns, yield assumption skepticism, "we already have this," Hoskinson framing, constitutional questions, process objections, and the "I just don't trust this" position. Used as backup when a debate gets unfair or vague. 3,000 words. ~12 minutes.

**Use case:** Reference document during DRep Q&A, forum reply backup, mid-debate de-escalation.

### 0. `00_README.md` — This file
You're reading it.

---

## What's new since the framework was first sketched

Two critical pieces of Cardano infrastructure went live in the last six months. The framework was theoretical before them; it's executable now.

**Pyth Network (live late 2025)** — Sub-100ms pull-based oracle feeds from 125+ institutional publishers, covering crypto, equities, FX, commodities, and ETFs. The first Pentad Critical Integration. Provides real-time, verifiable price benchmarks for every treasury operation, every reserve rebalancing, every yield-to-USD calculation. Already integrated by Indigo and being considered for Djed.

**USDCx (live February 27, 2026)** — Circle's first Tier 1 stablecoin on Cardano, backed 1:1 by USDC via the xReserve infrastructure. Cross-chain via Circle's CCTP (burn-and-mint, no wrapped-bridge risk). Over 15M USDCx minted at launch. Delivered through the same Critical Integrations program that funded Pyth.

**Why this matters for the CTF:** The Strategic Reserve (component 6.2 of the framework) was the riskiest piece because it depended on either experimental synthetics (iUSD) or off-chain custody. USDCx replaces that with a Circle-issued, audited, fully-backed stablecoin native to Cardano. The de-peg detection problem is solved by Pyth's institutional-grade oracle feeds. The two components people pushed back on hardest got production-grade infrastructure to back them — in the same governance program that this proposal flows through.

---

## TL;DR for those who won't read

- The Cardano treasury holds 1.621B ADA generating zero yield.
- USD value has fallen ~80% from late-2024 peak ($2.0B → $389M) due to single-asset exposure.
- At current ~350M ADA/year burn, the treasury depletes around 2033.
- The Cardano Foundation already diversified its own treasury to 51.6% ADA / 25.5% BTC / 22.9% cash — and outperformed an ADA-only portfolio.
- The Connected Treasury Framework proposes: stake the treasury, hold a small structured USDCx + BTC reserve, default to loans not grants, cap annual spending, report everything publicly via Pyth-anchored on-chain data.
- Phase 1 pilot: 50M ADA over 18 months, +0.9M ADA net at exit. Phase 2: protocol upgrade for full treasury staking via hard fork.
- This is not Hoskinson's $100M proposal. It is not the Foundation's $50M Liquidity Fund. It is complementary to both and structurally tighter than either.

---

## Quick links

| File | Purpose | Length |
|---|---|---|
| `00_README.md` | You're here | 2 min |
| `01_report.md` | Foundation document | 12 min |
| `02_proposal.md` | Submission-ready proposal | 4 min |
| `03_cip.md` | Protocol-level CIP outline | 7 min |
| `index.html` | Interactive parameter tool | hands-on |
| `05_objections.md` | Hostile-review defense | 12 min |

Total reading time start-to-finish: ~37 minutes.

---

## Naming

This packet uses "Connected Treasury Framework (CTF)" throughout, deliberately chosen to be:

- Descriptive rather than philosophical
- Not associated with any single project, operator, or founding entity
- Compatible with Cardano's convention of clear, function-anchored names

The intellectual lineage of the "connection as generative force" principle (the framework's core philosophical claim — that the treasury earns by connecting to the network's own infrastructure rather than by sitting passively) traces to Japanese cultural concepts that have animated operator-first independent infrastructure work on Cardano. That lineage is credited in `01_report.md` acknowledgments but is not embedded in the framework name itself, to keep the proposal ecosystem-neutral.

If the community prefers a different name, the framework's mechanics are unchanged. The name is the lightest commitment in the entire packet.

---

## How to use this

**If you're an SPO or community member who wants to push this forward:**
1. Read everything in order.
2. Fork or adapt `02_proposal.md` with your team and submit to gov.tools as a Treasury Withdrawal Governance Action.
3. Host `index.html` somewhere stable and link to it from the proposal.
4. Use `05_objections.md` as backup material during DRep Q&A and forum debate.

**If you're a DRep evaluating the proposal:**
1. Read `01_report.md` for context.
2. Read `02_proposal.md` for the specific ask.
3. Test your assumptions in `index.html`.
4. Review `05_objections.md` if you find yourself with a concern — chances are it's addressed.

**If you're a developer or researcher:**
1. `03_cip.md` is the technical document. Comments, critique, and reference-implementation work welcomed.
2. `index.html` is fully open-source HTML/JS/Chart.js. Fork, extend, fact-check.

**If you're a skeptic:**
1. Start with `05_objections.md`. If your objection isn't on the list, raise it on the forum — additions are welcomed.
2. Then read `01_report.md` to check the data.
3. Then `index.html` to see how your alternative numbers play out.

---

## What this packet doesn't claim

- It doesn't claim to solve all treasury problems. It addresses earning, diversification, lending discipline, and spending discipline. It doesn't address proposal-by-proposal quality control, DRep voter participation, or governance attack vectors broader than treasury voting weight.
- It doesn't claim 4% yield is guaranteed. It claims 4% is achievable under current Cardano staking conditions and that the simulator lets anyone test lower assumptions.
- It doesn't claim the framework is the only solution. The Cardano Foundation's $50M Liquidity Fund and the Draper Dragon Ecosystem Fund are complementary; they target different surface area.
- It doesn't claim the proposal will pass. It claims the proposal is structured to address every reason proposals failed this week and to be net-positive to the treasury at exit.

---

*This packet is for informational purposes only and is not financial advice. All claims are sourced in `01_report.md`. Errors should be reported and will be corrected.*
