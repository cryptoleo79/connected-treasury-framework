# Hostile Review of the CTF Proposal

*Written from the perspective of a skeptical DRep who has read the full packet and intends to vote NO on the Phase 1 proposal as currently drafted. This is what the strongest opposition forum post would look like. If the proposal cannot survive this critique, it should not be submitted.*

---

## "I've read the packet. Here's why I'm voting no."

Posted to the Cardano Forum, May 2026.

I've spent the weekend going through the Connected Treasury Framework packet in full. It's the most thoroughly-prepared treasury proposal I've seen in this governance cycle, and I want to engage with it on its own terms before voting. After careful review, I'll be voting NO on Phase 1 as currently drafted. Here's why, and what I'd need to see to change my vote.

### 1. The framing is more compelling than the math

The packet does an excellent job describing the *problem*. The treasury is bleeding USD value. The single-asset exposure is real. Status quo runway ends in 2033. None of this is in dispute. What I want to flag is that the *problem framing is doing too much rhetorical work*, and the actual proposal — a 50M ADA pilot — doesn't move those numbers in any way that matters.

50M ADA at 4% yield = 2M ADA/year. Against a treasury bleeding 310M ADA/year net, this is rounding error. The proposer knows this; that's why the report frames the pilot as "proof-of-concept" rather than "solution." But proof-of-concept of what? We already know staking yields exist. We already know dashboards can be built. We already know multisigs work. None of these need a 50M ADA test.

What's actually being validated by the pilot? Trust in the administrator entity. That's the real ask. The 50M ADA isn't testing the framework's mechanics — it's testing whether the community will accept an administrator entity controlling 50M ADA of treasury funds. That is a much harder question than the proposal acknowledges.

### 2. The "net-positive at exit" framing is technically true and structurally misleading

The proposal claims net +0.9M ADA at exit. This is correct under the stated assumptions. But the assumptions paper over real risks:

- **Administrator failure risk.** The 48M ADA principal is in administrator multisig for 18 months. Multisig keys get lost, members leave, signing protocols break. The proposal mentions "CC oversight" but oversight is not recovery — if the administrator cannot return the principal, the CC has no mechanism to force it.
- **Yield realization risk.** 4% pre-fee staking yield is real. 4% *net* yield after pool fees, after administrator operational drag, after slashing for missed blocks, after time-value-of-money on monthly distributions — is optimistic.
- **Opportunity cost.** The 48M ADA could be staked directly by the protocol if the CIP passes. The pilot's principal is *less productively deployed* than under the eventual Phase 2 — meaning the pilot is structurally inferior to its stated successor.

I'd vote yes on a pilot that addressed these three risks explicitly. The current draft acknowledges only the first.

### 3. The Lite variant is the proposal that should have been submitted first

The packet includes a 10M ADA Lite variant. Reading it, I want to vote yes on *that one*. It's structured to learn one thing (does the mechanism work) at a cost the treasury can absorb without debate. The fact that the Lite variant exists in the same packet as the Phase 1 proposal suggests the proposer knows it's the easier vote. So why are we voting on Phase 1?

If the answer is "to move faster," the proposer should accept that moving faster has costs in legitimacy. If the answer is "Phase 1 generates more meaningful data," the proposer should defend that against the Lite variant's cost-of-evidence argument explicitly. The packet doesn't do this.

I'd be much more receptive to a phased proposal that explicitly sequenced Lite → Phase 1 with measurable success criteria gating the transition.

### 4. The administrator entity is the actual decision being asked

Reading between the lines: the proposer is asking the community to ratify a new administrator entity that will control increasing portions of treasury funds, with the Phase 1 pilot as the first commitment. This is a much larger ask than "stake some ADA."

Who governs the administrator? "Composition determined post-ratification" is not an answer to that question — it defers it. The Snek Foundation precedent the proposal leans on had a *known entity* with a track record submitting the proposal. This proposal asks the community to trust an entity that doesn't yet exist.

Real-world treasury administration requires institutional trust. The proposal asks for institutional trust without specifying the institution. That's the central asymmetry I object to.

### 5. The USDCx and Pyth integration arguments are stronger than the framework needs

The packet leans heavily on USDCx and Pyth being live as evidence the framework is "now executable." This is true but oversold. USDCx launched three months ago. Pyth launched six months ago. The framework would benefit from these integrations *seasoning* — observing how they perform under stress, watching for de-peg events, seeing the oracle feeds tested in real adversarial conditions on Cardano specifically.

USDCx is a Circle product, and Circle has had its own custody questions (USDC briefly depegged in March 2023 during the SVB collapse). Tier 1 doesn't mean immune to systemic risk. The framework would be more credible if it acknowledged this and proposed a longer observation period before deploying treasury funds into the new infrastructure.

### 6. The objections document is excellent and also revealing

The packet includes a thorough objections-and-responses document. I want to praise this — it's better than 90% of treasury proposal submissions and demonstrates genuine engagement with critique. It also reveals the proposer's anxieties.

When the objections doc says "the framework will not accept the position that doing nothing is safer than doing something," that's the proposer's frustration showing. Doing nothing is in fact one valid option. It is the option the community has effectively chosen for eight years. The argument for action is strong but not so strong that it dismisses doing-nothing as illegitimate. When advocacy frames its own conclusion as the only reasonable position, voters notice.

### 7. What would change my vote

I would vote yes on a revised proposal that:

1. Starts with the Lite variant (10M ADA) and explicitly defers Phase 1 to post-Lite-completion governance action.
2. Names the administrator entity at submission time, with full board composition, conflict-of-interest disclosures, and track record.
3. Adds an explicit "principal recovery procedure" defining what happens if the administrator fails to return funds — including the role of the CC and any backstop mechanisms.
4. Acknowledges that USDCx and Pyth, while live, are recently deployed and proposes a 6-month observation period before any reserve deployment to either.
5. Replaces the "net-positive at exit" framing with a more honest "expected outcome distribution" — best case, base case, worst case — with explicit probabilities the proposer is willing to defend.
6. Reframes the report's conclusion to acknowledge that doing nothing is a legitimate position that thoughtful DReps may hold for reasons other than naivety.

The framework's core insight — that the treasury should earn through connection rather than sit passively — is correct and important. I want to vote yes on this concept eventually. I am voting no on the current draft because the implementation has not yet earned the trust that the conceptual elegance assumes.

I look forward to the proposer's response. I'll engage with any substantive revision in good faith.

---

## What the proposer should take from this

This review is the *sympathetic* version of the no vote. The unsympathetic versions will be shorter, less informed, and more reflexive — but they'll still cluster around these themes:

1. **The administrator entity question is the central issue, not the framework mechanics.** The proposal needs to either name the administrator at submission or explain why deferring composition is acceptable.
2. **Phase 1 vs Lite is a real choice that benefits from being made explicit.** The current packet hedges by including both; the actual submission needs to pick one and defend it.
3. **Risk asymmetries deserve explicit treatment.** Best case / base case / worst case framing is more credible than single-point projections, even when the proposer is right about the central estimate.
4. **The packet's confidence sometimes reads as dismissiveness.** Tone matters. The objections document's closing paragraph is the strongest example — phrases like "the framework will not accept" make the proposer sound impatient with disagreement, which is exactly the wrong signal during a governance vote.
5. **New infrastructure (USDCx, Pyth) is leveraged in the argument but not stress-tested. The proposal would be stronger with explicit acknowledgment that these are recent and that an observation period might be warranted.**

If the proposer revises along these lines — especially items 1, 2, and 5 — the proposal becomes substantially harder to vote against. The hostile review above is the kind of post that wins arguments in the Cardano Forum, and the response to it would be the proposal's most-read defensive document. Writing it out in advance is how you control that conversation.

The packet is strong. The submission can be stronger.
