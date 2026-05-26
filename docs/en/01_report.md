# Cardano Treasury: Erosion, Risk, and the Connected Treasury Framework

**A deep-dive on what the treasury holds, what it lost, what this week's governance data says about it, and a self-sustaining model for what comes next.**

*Version 2 · May 26, 2026*

---

## 1. Executive Summary

- **Treasury today:** ~1.621 billion ADA, valued at roughly **$389M USD** at $0.24/ADA (epoch 627, April 2026).
- **Treasury all-time high (ADA terms):** 1.822 billion ADA at epoch 574 (mid-2025).
- **Treasury all-time high (USD terms):** approximately **$2.0 billion** notional in late 2024 when ADA traded near $1.10.
- **Net "shrinkage":**
  - ADA balance: **–201 million ADA** (–11%) — withdrawn faster than the protocol could replenish.
  - USD purchasing power: **~$1.6 billion erased** (~80% drawdown) — driven mostly by ADA's price decline.
- **The 2025 Net Change Limit of 350M ADA was ~99.5% consumed** — the community spent almost the entire annual cap.
- **Projection:** at the current ~320–350M ADA/year burn, the treasury runs out around **Q3 2033**. Lowering withdrawals to 220M ADA/year extends runway to ~2038. Adding a yield component on the full balance extends runway indefinitely if paired with the reduced cap.
- **The hard truth:** the loss wasn't really "lost" — most of it was *value destruction from a single-asset (ADA-only) treasury holding a depreciating asset while spending obligations stayed roughly USD-denominated.*
- **This report proposes the Connected Treasury Framework (CTF):** a five-component model that turns the treasury from a passive ADA reservoir into a yield-generating, transparently-reported, fiscally-disciplined endowment.
- **The framework is now executable in a way it wasn't 6 months ago.** Pyth Network (live on Cardano via the Pentad's Critical Integrations program, late 2025) provides institutional-grade real-time price feeds for every treasury operation. USDCx (Circle, live February 27, 2026) provides a Tier 1 USDC-backed stablecoin natively on Cardano. The two pieces of infrastructure that made the framework theoretical six months ago are now both production-ready.

---

## 2. How the Treasury Actually Works

Two flows fund the on-chain treasury every epoch (~5 days):

| Source | Mechanism |
|---|---|
| **Monetary expansion (ρ)** | 0.3% of the remaining ADA reserves enters a virtual reward pot each epoch |
| **Transaction fees** | 100% of fees from blocks produced in the epoch enter that same pot |
| **Treasury tax (τ)** | 20% of the combined pot is sent to the treasury; 80% is distributed to stake pools and delegators |

Source: Cardano Docs, monetary policy specification.

Three structural problems with this:

1. **Reserves are exponentially decaying.** As the unissued reserve shrinks, monetary expansion shrinks with it. Treasury inflow from this source falls every year.
2. **Transaction fees are tiny.** Cardano typically generates well under 1M ADA per epoch in fees. At ~$0.17 per transaction and modest throughput, this is not yet a meaningful counterweight.
3. **The treasury is a passive ADA balance.** Under current protocol design, the on-chain treasury cannot itself be staked, delegated, or earn rewards. It is dead weight, in financial terms.

This is the root problem: the treasury earns nothing on what it holds. Inflows are decelerating, outflows (governance withdrawals) are accelerating, and the asset itself has lost ~92% of its USD value from peak.

---

## 3. The Erosion Story: How Much Was Lost

### 3A. Headline numbers

| Metric | Value |
|---|---|
| ADA all-time high price | $3.10 (Sept 2, 2021) |
| ADA price today (May 2026) | ~$0.24 |
| Drawdown from ATH | ~–92% |
| Treasury ATH (ADA) | 1.822B ADA (epoch 574) |
| Treasury today (ADA) | 1.621B ADA (epoch 627) |
| Net ADA balance change | –201M ADA (–11%) |
| Treasury USD value Nov 2024 (~peak) | ~$2.0B |
| Treasury USD value today | ~$389M |
| Notional USD destruction | ~$1.6B (~80%) |

### 3B. What was withdrawn vs. what was destroyed by price

The community sometimes conflates these. They are different.

- **Spent / withdrawn from the treasury (2025 cycle):** ~348–349M ADA, against a 350M ADA Net Change Limit (NCL). Roughly 99.4–99.7% of the cap was used or allocated. (Source: Intersect Budget Committee minutes, January 5, 2026.)
- **Destroyed by ADA price decline:** the ~80% USD value drop is *almost entirely* a price effect on the ADA the treasury still holds, not money spent.

In other words: **the community withdrew roughly 19% of peak ADA balance**, but the *USD purchasing power* shrank ~80% — meaning **most of the loss had nothing to do with governance decisions**. It was caused by holding a single volatile asset whose value collapsed against the USD-denominated costs the treasury was meant to fund.

### 3C. Was any money returned?

Yes, partially, but tiny relative to outflows:

- **Refundable governance deposits.** Each governance action requires a 100,000 ADA deposit, returned if the action is enacted or expires. Small amounts.
- **Snek Foundation 5M ADA structured as a *loan*, not a grant** — explicit repayment to the treasury. Precedent-setting.
- **Cardano Foundation's proposed $50M (50M ADA) liquidity fund** would return 15% of generated revenue as ADA back to the treasury monthly, with 85% compounding in DeFi protocols. Estimated ~4% annual yield. Not yet enacted.
- **Cardano x Draper Dragon Fund (DDC)** is explicitly designed to "deliver a return multiple back to the Treasury" via VC-style equity exits. No realized returns yet.

There is no on-chain mechanism today for the treasury to automatically earn yield. Every "return" path is a downstream consequence of a withdrawal that has to be voted on, executed, and managed externally.

---

## 4. This Week in Governance (May 18–26, 2026)

This week's vote results tell us exactly what the community will and will not fund.

**The IOG nine-proposal cycle (deadline May 24):**

| Proposal | Ask | Outcome | DRep Approval |
|---|---|---|---|
| Leios scaling (Consensus Initiative) | 27.7M ADA | **Passed** | ~84% |
| Babel Fees | 13.1M ADA | Borderline | ~60% |
| Cardano Maintenance Initiative | 62.1M ADA | Failing | 46.58% |
| Layer 2 scaling | 10.4M ADA | **Rejected** | 16.08% |
| Pogun (BTC DeFi) | included in bundle | **Rejected** | 32.4% |
| Blockfrost | included | **Rejected** | — |
| IO Developer Experience | 3.6M ADA | Failing | Cardanians (17.82M ADA DRep) NO |
| Vision 2026 Research (separate, June 8) | 33M ADA | Failing | 13% |
| Revised Summit 2026 Singapore (May 29) | 7.8M ADA | Trending abstain | Cardano Foundation abstained |

**The pattern is unmistakable.** Six of nine IOG proposals passed — so the community isn't anti-IOG. But the rejections cluster on a specific failure mode: large ongoing-maintenance commitments, unclear cost breakdowns, and infrastructure work that doesn't show a self-sustainability path.

**The single most telling event:** DRep Dave flipped from YES to NO on the 62M ADA Plutus/Maintenance proposal, citing lack of line-by-line budget and weakened trust in leadership. That's ~67M ADA of voting power swinging on transparency alone.

**Leios passed at 84%** — clear deliverable (800K → 27M tx/month), defined timeline, measurable outcome. Proposals with sharp scope and ecosystem-wide benefit still sail through.

### 4A. What this means for treasury management

The community is now actively pricing in operational discipline. The proposals being rejected this week are precisely the ones the Connected Treasury Framework is designed to make unnecessary:

| What DReps rejected this week | What the framework does instead |
|---|---|
| Opaque cost structures | Public reporting on every flow |
| Open-ended maintenance commitments | Hard annual spending cap |
| Grants with no return path | Loan-first by default |
| Single-asset price exposure | Small structured diversified reserve |
| Passive ADA bleeding USD value | Treasury earns its own yield via delegation |

---

## 5. Diversification Context: What Has Already Been Tried

### 5A. The Hoskinson $100M proposal (June 2025)

Charles Hoskinson proposed converting approximately $100M of treasury ADA into a blend of native Cardano stablecoins (USDM, USDA, iUSD synthetics) plus Bitcoin, explicitly modeled on sovereign-wealth-fund design (Norway, Abu Dhabi). The thesis: Cardano's stablecoin-to-TVL ratio sits below 10% (vs. Ethereum 190%, Solana 110%), the proposal would target 33–40%, and yield generated would be non-inflationary revenue that could buy back ADA over time.

ADA fell 4–6% on the day of the proposal. The Cardano Foundation CEO downplayed TVL as a metric, surfacing a philosophical split. The proposal has not been submitted as a formal on-chain governance action. Given this week's community mood, passage would be difficult without a tighter, smaller, more transparent structure.

### 5B. The Cardano Foundation already did this — with its own treasury

This is critical and often overlooked. The Cardano Foundation (a separate Swiss-based entity, distinct from the on-chain treasury) has already restructured its balance sheet:

- 2024: ADA was over 75% of Foundation reserves.
- 2025/2026: ADA dropped to **51.6%**, Bitcoin grew to **25.5%**, cash + other financial assets reached **22.9%**.
- Foundation's total reported assets fell to ~$361M in 2025, down ~45% YoY, largely due to ADA's decline.
- Over the comparable period: ADA fell ~63%, BTC fell ~25%. **BTC measurably outperformed ADA as a treasury asset.**

The Foundation is, in practice, the proof-of-concept for the diversification thesis. The on-chain treasury simply hasn't done it yet.

### 5C. Counterfactual math

Imagine the on-chain treasury had executed a 50/50 ADA/BTC split at the November 2024 peak (~$2.0B notional):

- ADA half ($1.0B notional) → today: ~$1.0B × (0.24/1.10) = ~$218M
- BTC half ($1.0B notional) → today: ~$1.0B × (1 – 0.25) = ~$750M
- Total: ~$968M
- Actual today: ~$389M
- Hypothetical retained value: **~$580M**

A 25% BTC / 25% stablecoin / 50% ADA split would have done even better on the downside, with ~25% of the treasury holding par-value USD throughout.

### 5D. Other live proposals worth noting

- **Cardano Foundation $50M Liquidity Fund** — 50M ADA into Cardano DeFi, estimated ~4% annual return, 15% of revenue returns to treasury as ADA monthly. The most operationally concrete yield proposal currently on the table.
- **Cardano x Draper Dragon Ecosystem Fund (DDC)** — up to 175M ADA across 3 tranches over 6 years, VC-style returns target.
- **Snek Foundation 5M ADA loan** — Constitutional Committee approved 85.71%. Precedent for repayable structures.

---

## 6. The Connected Treasury Framework (CTF)

**A self-sustaining model for the Cardano on-chain treasury.**

Core principle: the treasury earns through connection to the network's own infrastructure, holds a small diversified reserve for USD-denominated obligations, lends rather than grants where revenue exists, caps its own spending, and reports everything publicly.

### 6.1 Yield loop
The treasury delegates a portion of its ADA holdings to a curated network of community-vetted stake pools. Pool inclusion criteria:
- Independent infrastructure (no shared cloud monoculture, geographic diversity)
- Public operator telemetry (uptime, block production history, fee structure)
- Pledge-to-stake ratio above ecosystem median
- Auto-abstain on all governance votes (mandatory, enforced at registration)
- Open-source contributions or operator-first observability tooling

Yield flows back to the treasury monthly as ADA. At ~4% APY on the deployed portion, this generates ~65M ADA/year on the current balance — roughly 18% of current annual burn.

### 6.2 Strategic reserve
A small allocation (10–15% of the deployed amount, ~$45–65M USD equivalent) into Bitcoin and Cardano-native stablecoins. The launch of **USDCx** (Circle's USDC-backed stablecoin, live on Cardano via xReserve as of February 27, 2026) fundamentally changes this component: the reserve now uses a Tier 1, audited, fully-backed stablecoin issued by Circle, with cross-chain interoperability via CCTP burn-and-mint — not an experimental synthetic. USDM and USDA remain available as native-issued options for diversification within the stablecoin allocation.

The reserve is sized to cover ~18 months of forecast USD-denominated operational costs. Real-time price feeds for the BTC portion and de-peg detection for stablecoins are sourced from **Pyth Network** (live on Cardano late 2025, sub-100ms institutional feeds from 125+ publishers), giving the administrator transparent, verifiable benchmarks for every rebalancing decision.

This mirrors the Cardano Foundation's existing balance sheet structure, which materially outperformed an ADA-only portfolio over the past 12 months. Critically, this reserve is structured to support USD obligations (audits, infrastructure, salaries for funded teams), not to speculate on BTC appreciation.

### 6.3 Loan-first capital
Treasury withdrawals to entities that generate revenue default to repayable loan structure. The Snek Foundation 5M ADA loan (approved 85.71% by the Constitutional Committee in November 2025) is the working precedent. Grants reserved for pure public goods: research, audits, education, security disclosures.

Single largest behavioral change: converting half of current grant-style outflows into loans extends runway by years and creates a virtuous-cycle of revenue-generating ecosystem teams.

### 6.4 Spending cap
Hard annual ceiling at the lower of:
- (a) 220M ADA, or
- (b) 80% of prior-year (yield + baseline replenishment from monetary expansion + fees)

This forces convergence toward self-sustainability. If yields rise, spending capacity rises. If yields fall, spending automatically tightens. The cap is enforced through the existing Net Change Limit mechanism via Info Action governance.

### 6.5 Open reporting
A public dashboard tracks every treasury delegation, pool performance, monthly yield return, reserve composition, and loan repayment status. All data on-chain, queryable, and visualized at a stable URL. Operator-first observability principles: the treasury "explains its own health" rather than requiring trust.

The dashboard uses **Pyth Network** feeds for live USD valuation of all reserve components (ADA, BTC, USDCx, USDM, USDA), giving the community independent, institutional-grade price benchmarking. Every reserve rebalancing event publishes the Pyth-anchored price at execution time, on-chain, immutably.

This directly answers DRep Dave's transparency objection that swung 67M ADA of voting power this week.

---

## 7. Strategy Comparison Matrix

| Strategy | Estimated Annual Return | Implementation Difficulty | Political Risk | Status |
|---|---|---|---|---|
| Status quo (passive ADA) | 0% (price-dependent) | None | None | Current state |
| CF $50M Liquidity Fund | ~4% on deployed capital | Low — governance vote | Moderate | Proposed |
| Draper Dragon Ecosystem Fund | Multi-year IRR, unknown | Moderate | Moderate | Proposed (up to 175M ADA) |
| Hoskinson $100M BTC + stablecoin | Depends on BTC; ~4–6% via stablecoin DeFi | Moderate | High (community split) | Public proposal, no formal action |
| **Connected Treasury Framework (CTF)** | **~4% via staking on deployed portion + ~6% on stablecoin portion** | **Phase 1 low (governance vote). Phase 2 protocol change.** | **Low — designed around current rejection patterns** | **Not yet submitted** |
| CIP-XX: Protocol-level treasury staking | ~4% on full treasury = ~65M ADA/yr | Very high — hard fork + constitution | High | Heavy-lift moonshot (see CIP outline) |

---

## 8. Implementation Path

The CTF is intentionally modular. Components can be enacted in any order, each through standard governance channels.

**Phase 1 — Pilot (governance vote only, no protocol change required):**
1. Submit a Treasury Withdrawal action for a small administrator entity to deploy 50–100M ADA into a curated stake pool delegation pilot.
2. Submit a Treasury Withdrawal action for a Strategic Reserve administrator to convert 20–30M ADA to a structured BTC + stablecoin position.
3. Submit an Info Action proposing the loan-first principle as default structure for all future revenue-capable withdrawals.
4. Submit an Info Action setting the 2027 Net Change Limit at 220M ADA.
5. Fund a public dashboard via a small Treasury Withdrawal (likely 1–3M ADA over 18 months).

**Phase 2 — Protocol enablement (requires CIP + hard fork):**
6. Enable on-chain treasury staking at the ledger level, with mandatory auto-abstain voting (see attached CIP outline).
7. Migrate Phase 1 delegation infrastructure to the native protocol mechanism.

Phase 1 alone is implementable within a single 2026 governance cycle. Phase 2 likely 2027–2028.

---

## 9. Risks and Counter-Arguments

**Against diversification:**
- Selling pressure on ADA from any large conversion. Mitigated by sizing (10–15%, not 50%) and gradual execution (multi-week treasury auctions).
- "Cardano holding non-Cardano-native assets" undermines the self-sufficiency narrative. Counter: the Foundation already does this, and "self-sufficiency" requires USD-denominated obligations to be backed by USD-denominated assets.
- Custody risk for BTC + stablecoins. Mitigated by multisig + transparent administrator entity + regular auditing.
- Stablecoin de-peg risk, particularly for algorithmic ones. Mitigated by allocation limits per asset and prioritizing fiat-backed options.

**Against protocol-level staking:**
- 1.6B ADA of treasury voting weight would be a centralization vector. Mitigated by mandatory auto-abstain enforced at the ledger level (not just by convention).
- Pool selection becomes a governance problem. Mitigated by published criteria + periodic DRep ratification of the approved list.
- May reduce average rewards for individual delegators by inflating staked supply. Marginal impact at current staking saturation levels.

**Against doing nothing:**
- At 320–350M ADA/year burn, treasury exhausted by ~2033.
- The community's growing rejection of proposals signals governance straining under treasury pressure.
- USD funding capacity shrinks faster than ADA balance due to price exposure.

---

## 10. Bottom Line

The Cardano treasury didn't shrink in any meaningful protocol sense — it lost ~11% of its ADA balance to withdrawals while gaining roughly the same from monetary expansion + fees. The ~$1.6B in USD value destruction is overwhelmingly a function of holding 100% of reserves in a single asset that fell 92% from its high.

The fix is not technical. It's portfolio management — something every serious treasury in finance has known for centuries and something Cardano's own Foundation has already begun doing with its off-chain assets. The on-chain treasury is the last large holdout.

The Connected Treasury Framework is not a single proposal — it's a coherent model assembled from elements that already have community support (Leios-style transparency, Snek-style loans, Foundation-style diversification, community-staking culture). Its Phase 1 is fully implementable through the existing governance system without requiring any protocol change.

The choice is no longer between "spend less" and "let the treasury melt." The choice is between an active, yield-generating, transparent endowment and a passive ice cube.

---

## Annex A — Supporting Data

### Treasury balance and USD value over time

| Period | Treasury (M ADA) | ADA Price (approx) | USD Value (M) |
|---|---|---|---|
| 2021 Q4 | 300 | $1.30 | $390 |
| 2022 Q2 | 500 | $0.45 | $220 |
| 2022 Q4 | 750 | $0.25 | $175 |
| 2023 Q2 | 950 | $0.34 | $320 |
| 2023 Q4 | 1,200 | $0.55 | $660 |
| 2024 Q2 | 1,500 | $0.45 | $675 |
| 2024 Q4 | 1,650 | $1.00 | $1,650 |
| 2025 Q2 | 1,822 | $0.65 | $1,184 |
| 2025 Q4 | 1,750 | $0.45 | $788 |
| 2026 Q2 | 1,621 | $0.24 | $389 |

### Runway scenarios (years to depletion from May 2026)

| Scenario | Annual outflow | Annual inflow | Depletion year |
|---|---|---|---|
| Status quo | 350M ADA | ~40M ADA (baseline) | 2033 |
| Reduced burn only | 220M ADA | ~40M ADA | 2038 |
| Status quo + 4% staking yield | 350M ADA | ~105M ADA | 2040 |
| Reduced burn + 4% staking yield | 220M ADA | ~105M ADA | Indefinite (positive trajectory) |

### Annual yield revenue scenarios on current treasury (1.621B ADA)

| Strategy | Effective APY | Annual revenue (M ADA) | Annual revenue (USD at $0.24) |
|---|---|---|---|
| Status quo (no yield) | 0% | 0 | $0 |
| Treasury-controlled SPO (external delegation only) | ~1% effective | 16 | $4M |
| Phase 1 CTF pilot (partial delegation) | ~2% blended | ~32 | $8M |
| Full protocol-level treasury staking | ~4% | ~65 | $15M |
| Stablecoin DeFi yield (Foundation-style) | ~6% | ~97 | $23M |

---

## Sources

- TapTools, "Should Cardano Treasury Spending Be Reduced?" (April 28, 2026).
- Cardano Foundation Financial Report 2025 (via BitcoinKE coverage, April 2026).
- Cardano Docs — Monetary Policy specification.
- Cardano Developer Portal — Governance Actions, Constitution Article IV §5.
- Cryptobriefing, ZyCrypto, CCN — Hoskinson $100M diversification proposal coverage (June 2025).
- Intersect Budget Committee meeting minutes, January 5, 2026.
- Crypto.news — "The civil war inside Cardano: Hoskinson vs the foundation" (May 25, 2026).
- Cryptonomist — "Cardano governance review: Hoskinson audits 11,000 DAOs" (May 25, 2026).
- Cryptotimes — "Cardano Pushes Ahead With Leios After Strong Governance Vote" (May 25, 2026).
- CryptoSlate — IOG Vision 2026 / 33M ADA research vote coverage (May 22, 2026).
- LiveBitcoinNews — Cardano Foundation Summit 2026 abstention coverage (May 2026).
- CoinDesk — "Input Output seeks $46.8M to bring Bitcoin DeFi scaling upgrade to Cardano" (April 23, 2026).
- Cexplorer — Treasury projection tool.

---

## Acknowledgements

This framework draws on the operator-first observability and self-sustainability principles that have emerged in independent Cardano infrastructure work — including projects that have proven the model at the SPO scale by funding their development through pool delegation rather than treasury grants. The intellectual lineage of "connection as generative force" comes from Japanese cultural-philosophical traditions (繋ぎ / 結び) that frame relationships as productive in themselves, not transactional. Translating that principle from operator-scale to protocol-scale is the wager of this framework.

*This report is for informational purposes only and is not financial advice.*
