# CIP-XXXX: Protocol-Level Treasury Staking with Mandatory Voting Neutralization

**Status:** Draft outline
**Type:** Standards Track
**Authors:** *to be assembled*
**Created:** May 2026

---

## Abstract

This CIP proposes a hard-fork change to the Cardano ledger that enables the on-chain treasury to participate in stake pool delegation and earn staking rewards, while neutralizing the voting power associated with that delegated stake at the protocol level. Rewards accrue directly to the treasury balance. This converts the treasury from a passive ADA reservoir into a yield-generating endowment, projected to add ~65M ADA per year at current treasury size and ~4% APY — sufficient to materially extend or eliminate the treasury's depletion trajectory.

## Motivation

The on-chain treasury holds ~1.621B ADA as of May 2026, generating zero yield. At current ~350M ADA/year burn the treasury depletes by ~Q3 2033. Every other actor holding ADA at scale — the Cardano Foundation, individual whales, exchanges holding customer deposits — stakes and earns rewards. The treasury is the largest single non-staking ADA holder in the network. This is not a deliberate design choice for the current era; the original treasury specification predates the maturation of Cardano's delegation infrastructure and was written when "treasury participates in consensus" was not yet a tractable design problem.

Two non-protocol workarounds exist:

1. Withdraw treasury ADA to administrator entities that stake externally (architecturally feasible today, but politically fraught — see Cardano Foundation precedent and the Snek Foundation loan precedent).
2. Run treasury-controlled stake pools that collect delegation from others (bounded by external delegation volume, marginal revenue).

Neither addresses the core inefficiency. The treasury itself, the largest ADA balance on-chain, sits idle. This CIP fixes that at the protocol level.

## Specification

### 1. Ledger state changes

The current ledger state attribute `AccountState.treasury` is a single `Coin` value. This is extended to a structured type:

```
TreasuryAccount = {
  liquid_balance: Coin,           -- not currently delegated
  staked_balance: Coin,            -- delegated to one or more pools
  pending_rewards: Coin,           -- earned but not yet credited
  pool_delegations: Map<PoolID, Coin>  -- per-pool stake allocation
}
```

The sum `liquid_balance + staked_balance + pending_rewards` MUST equal what was previously a single `treasury` value. No ADA is created or destroyed in the migration.

### 2. Delegation authority

Delegation of treasury stake to pools is authorized exclusively through governance actions. A new governance action type is introduced:

```
TreasuryDelegationAction = {
  pool_allocations: Map<PoolID, Coin>,
  expires_at_epoch: EpochNo,
  rationale_url: URL
}
```

This action requires the same approval threshold as a Treasury Withdrawal (DRep + Constitutional Committee). Pool allocations are checked against the active "approved pool registry" (see §4).

The action does not move ADA off-chain; it changes the delegation map within `TreasuryAccount`.

### 3. Mandatory voting neutralization

Stake delegated by the treasury MUST contribute to pool consensus weight (Sybil resistance, decentralization metrics) but MUST NOT contribute to any governance voting weight. Specifically:

- For DRep votes: the treasury's delegated stake is excluded from the active stake denominator and from any DRep's voting power calculation, regardless of which pool it is delegated to.
- For SPO governance votes: pools cannot exercise voting power derived from treasury delegation. The pool's effective voting stake = total delegated stake − treasury-delegated stake.
- For pledge-influence calculations (`a₀`): treasury stake does not count toward pool pledge or pledge-influence.

This is enforced at the ledger level. No "auto-abstain by convention" — voting weight is structurally zero.

### 4. Approved pool registry

A new on-chain registry tracks pools eligible to receive treasury delegation. Inclusion criteria are defined in a separate governance action of type `TreasuryPoolCriteriaAction` and require DRep + CC ratification. Suggested initial criteria (to be ratified by the community at activation):

- Operator pledge above the ecosystem median for at least 12 months
- Public telemetry endpoint with verifiable uptime
- No relationship to founding entities (IOG, Emurgo, Cardano Foundation) above a defined threshold
- Geographic and infrastructure diversity (no two delegated pools may share the same hosting provider for more than 10% of treasury delegation)
- Audit-passing operator identity attestation

Pools may apply to join the registry through an `ApplyToPoolRegistry` transaction. Inclusion is decided by DRep vote on rolling cycles (suggested: quarterly).

### 5. Reward routing

Rewards earned by treasury-delegated stake are computed identically to ordinary delegator rewards (Ouroboros reward formula, pool margins applied). The reward flow differs:

- Pool operator fees: routed to pool operator's reward account as today.
- Delegator share of rewards: routed to `TreasuryAccount.pending_rewards`.
- At each epoch boundary, `pending_rewards` is added to `liquid_balance`.

No reward account or stake credential is created for the treasury — the treasury's "stake address" is a system-level construct, not a UTxO address.

### 6. Liquidity guarantees

Governance Treasury Withdrawals (existing mechanism) must be satisfiable on any epoch boundary. To guarantee liquidity:

- A minimum `liquid_balance` ratio is enforced: at least 20% of total treasury MUST remain in `liquid_balance` at all times.
- If a TreasuryDelegationAction would drop the liquid ratio below 20%, it is rejected at validation.
- If a Treasury Withdrawal exceeds available `liquid_balance`, the ledger automatically un-delegates the shortfall proportionally across pools (acts at the next epoch boundary).

## Rationale

### Why protocol-level, not administrative

An administrator-controlled approach (a withdrawal to an entity that stakes externally) is faster to implement but introduces:

- Custody risk on a multi-hundred-million-ADA scale
- Governance attack surface (controller-entity capture, key compromise)
- Voting weight contamination (the administrator's stake retains voting power unless they manually auto-abstain — a convention, not a guarantee)
- Centralization of decision-making

A protocol-level mechanism eliminates these by making the constraints structural.

### Why mandatory voting neutralization

Without neutralization, treasury delegation concentrates ~65M+ ADA of voting power (at any single pool) or ~1.6B ADA distributed across an approved pool list. Either creates a governance attack vector. Neutralization at the ledger level — not by convention — is the only design that makes treasury staking safe at the scale envisioned.

### Why DRep + CC ratification of pool list

Treasury delegation is functionally a directed economic subsidy. The pool selection mechanism must therefore be subject to the same democratic legitimacy as Treasury Withdrawals. Algorithmic-only selection (e.g., "delegate proportionally to top-N pools by performance") is tempting but creates predictable centralization toward larger pools and removes accountability for the choice.

### Why a liquidity floor

The treasury must be able to fund approved withdrawals without delay or market disruption. A 20% liquid floor balances yield-generating capacity (80% deployable) with operational responsiveness.

## Backward compatibility

This is a hard fork. Protocol Version must bump. Affected components:

- **Cardano node** — ledger state representation, governance action handling, reward calculation pipeline. Estimated effort: significant (multi-month implementation + testing).
- **DB-sync** — schema additions for the new account structure. Estimated effort: moderate.
- **Wallets** — no impact for end-users; treasury structure is invisible to user wallets.
- **Explorers and dashboards** — must surface the new treasury structure. Estimated effort: minor per explorer.
- **Stake pool operators** — no operational changes. Pools see treasury delegation as ordinary stake (with voting weight excluded).
- **DRep tooling** — must exclude treasury-delegated stake from voting power calculations.

Migration: on hard fork activation, the current `treasury` value is initialized as `TreasuryAccount.liquid_balance = treasury_value`, with all other fields zero. The treasury continues to receive monetary expansion + fee inflows into `liquid_balance` as today.

## Constitutional compatibility

Cardano Constitution Article IV §5 currently requires that "Funds held by administrators must be delegated to the 'auto abstain' voting option and shall not be delegated to SPOs." This applies to administrators of withdrawn treasury funds, not to the on-chain treasury itself. However, the spirit of the article — that treasury-origin stake should not amplify any political faction — is honored more strongly by this CIP than by the current rule, since neutralization is structural rather than behavioral.

A clarifying constitutional amendment is recommended in parallel with CIP activation, explicitly recognizing protocol-level treasury staking as constitutionally compatible. This is a separate governance action and not a prerequisite for CIP ratification.

## Path to active

| Stage | Action |
|---|---|
| 1 | Draft expansion (this outline → full CIP text, including precise pseudocode and CDDL spec changes) |
| 2 | Community review on Cardano Forum and CIP repo |
| 3 | Technical review by IOG ledger team, Cardano Foundation, independent ledger implementers |
| 4 | Reference implementation in a node fork; testnet activation |
| 5 | Public testnet deployment with simulated treasury staking |
| 6 | CIP "Last Call" status with public review window |
| 7 | Governance: Hard Fork Initiation action (DRep + SPO + CC approval required) |
| 8 | Mainnet activation |

Estimated total timeline: 18–30 months from CIP submission to mainnet, consistent with prior major hard forks (Chang, Plomin).

## Implementation considerations

- The approved pool registry could be bootstrapped from the Phase 1 pilot's curated pool list, allowing operational learnings to inform the on-chain criteria.
- Reward calculation for treasury stake should be implemented as a thin wrapper around the existing delegator reward function to minimize new code paths.
- Liquidity floor enforcement may interact with multi-epoch withdrawal commitments (e.g., the Draper Dragon Fund's tranched structure). The CIP should specify whether committed-but-not-yet-withdrawn amounts count against the floor.
- Treasury delegation should be visible in standard pool explorers (Pool.pm, Cexplorer) with appropriate labeling so delegators can see the share of pool stake that comes from the treasury.

## Open questions

1. Should pool selection criteria include a maximum percentage of treasury delegation per pool? (Recommended: yes, no pool above 5% of treasury-delegated total)
2. Should there be a "cooling-off period" between approved-pool list changes to prevent rapid reallocation in response to short-term events? (Recommended: 30 epochs minimum between list changes)
3. Should the treasury receive a discount on pool margin? (Recommended: no — treasury pays standard margin, same as any delegator, to preserve operator incentives)
4. How should treasury delegation interact with future possible features (Mithril certificates, partner chains, Hydra)? (Out of scope for this CIP, but should be considered in the full text)
5. Should the 20% liquidity floor be a hardcoded parameter or a governance-mutable protocol parameter? (Recommended: governance-mutable, with the initial value set by the CIP)
6. Should this CIP specify use of Pyth Network feeds for on-chain price validation of the strategic reserve, or remain oracle-agnostic? (Recommended: oracle-agnostic in the CIP text, with Pyth as the recommended reference implementation given its 2025 mainnet deployment on Cardano.)
7. Should treasury-side stablecoin holdings be restricted to a defined list (e.g., USDCx via Circle xReserve, USDM, USDA), or governance-mutable? (Recommended: governance-mutable with conservative initial allow-list anchored on USDCx as the only Tier 1 option currently available.)

## Copyright

This CIP is licensed under CC-BY-4.0.

---

*This is a structural outline. A full CIP submission requires expansion into precise specification language (CDDL schemas, formal semantics, reference implementation links) and may take 4–8 weeks of focused drafting in collaboration with ledger implementers.*
