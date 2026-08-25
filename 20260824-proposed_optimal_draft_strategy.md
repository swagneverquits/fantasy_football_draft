# Proposed Optimal Draft Strategy

**Date:** 2026-08-24

<details open>
<summary><big><big><big><strong>Motivation</strong></big></big></big></summary>

This strategy is designed for an eight-team ESPN league where the roster and scoring settings create much more demand for RB, WR, and TE production than a normal one-QB league.

<div style="margin-left: 1.25rem; padding-left: 1rem; border-left: 3px solid #777;">

<details>
<summary><strong>Value - use the league's actual scoring.</strong></summary>

- Rank players by projected points under this league's scoring, not ESPN's editorial rank.
- Adjust for positional replacement value across 3 RB, 3 WR, 2 TE, 3 FLEX, and 1 OP slot.
- Treat ESPN Standard, PPR, and Superflex ranks as behavioral inputs for opponents.

</details>

<details>
<summary><strong>Robustness - build a roster that survives bad luck.</strong></summary>

- Prefer high-volume players with multiple paths to points.
- Use tiers and fallback groups instead of one-player draft plans.
- Penalize injury uncertainty and fragile touchdown dependence.

</details>

<details>
<summary><strong>Exploitation - let ESPN's rank-driven teams overpay for quarterbacks.</strong></summary>

- The league has one required QB slot, while ESPN's visible board is Superflex-oriented.
- If opponents chase quarterback rank, collect scarce elite RB/WR/TE production.
- Take a quarterback when the marginal value and downside protection justify it, not simply because he is rank 1.

</details>

</div>

**The through-line is to maximize points above replacement while using the observed ESPN behavior to anticipate, rather than imitate, the autodrafters.**

</details>

<hr style="height: 3px; background: rgba(160, 160, 160, 0.35); border: 0; margin: 0.25rem 0;">
<details open>
<summary><big><big><big><strong>Recommended Decision Rules</strong></big></big></big></summary>

### Pick 1.03

Use this order as the initial manual shortlist:

1. Jahmyr Gibbs when the replacement-value model confirms the RB edge.
2. Puka Nacua when healthy and available; he has the highest current projected total in the ESPN payload.
3. Ja'Marr Chase or Jaxon Smith-Njigba as elite WR fallbacks.
4. Bijan Robinson as the RB fallback.
5. Josh Allen only when the QB scarcity penalty becomes large enough or the elite skill-player tier is gone.

Do not select Jayden Daniels, Drake Maye, or Jalen Hurts at 1.03 solely because their Superflex rank is high.

### Picks 2.06 and 3.03

- Pair the first pick with the best remaining player from a different high-value tier when possible.
- Prioritize a second elite RB/WR before taking a merely good quarterback.
- Move Trey McBride or Brock Bowers up materially because the league starts two TEs and has three FLEX slots.
- Take a quarterback in this range if Allen, Lamar Jackson, or a top projected QB falls well below the expected cost of waiting.

### Picks 4.06 and 5.03

- Secure a starting quarterback if one has not been drafted.
- Continue adding RB/WR volume and prioritize players with FLEX eligibility.
- Use the optimizer's replacement-value gap rather than a fixed positional quota.

### Later rounds

- Add depth before selecting kicker, punter, or head coach.
- Treat defensive players as a separate value pool because sacks, interceptions, forced fumbles, and tackles are unusually valuable here.
- Delay K, P, and HC until the model shows a clear replacement-value edge.

</details>

<hr style="height: 3px; background: rgba(160, 160, 160, 0.35); border: 0; margin: 0.25rem 0;">
<details>
<summary><big><big><big><strong>Opponent Autodraft Model</strong></big></big></big></summary>

The initial ESPN opponent model should use a league-wide weighted selection rather than hard-coded manager personalities.

For each available player, calculate a score such as:

```text
selection_score =
    rank_value
  + projected_value
  + positional_scarcity
  + roster_fit
  + round_strategy_bonus
  + random_noise
```

Recommended initial behavior:

- Use ESPN Superflex rank as the primary opponent rank signal because the observed drafts consistently begin with elite quarterbacks.
- Blend in PPR/Standard rank and ESPN projected FPTS instead of using one rank column exclusively.
- Apply roster legality, position limits, and open-slot fit.
- Add a softmax-style random choice among the highest-scoring candidates rather than selecting the exact maximum every time.
- Recalculate roster fit after every pick.
- Fit the rank/value/noise weights against the observed autodraft fixtures.

The five observations for my pick at 1.03 currently include Daniels, Allen, Lamar, Puka, and Bijan. That is evidence for a weighted elite candidate pool, not enough evidence for exact probabilities yet.

</details>

<hr style="height: 3px; background: rgba(160, 160, 160, 0.35); border: 0; margin: 0.25rem 0;">
<details>
<summary><big><big><big><strong>Risk Objective</strong></big></big></big></summary>

The simulator should optimize more than mean projected points. For each candidate strategy, report:

- Expected roster points.
- 10th, 25th, 50th, and 90th percentile outcomes.
- Injury-adjusted downside.
- Probability of missing a required starting position.
- Probability of finishing in the bottom tier of simulated rosters.

Initial risk preference:

- Prefer a slightly lower mean if it materially improves the 10th-percentile roster.
- Avoid taking multiple fragile players from the same team or position tier.
- Preserve fallback paths at every pick.

</details>

<hr style="height: 3px; background: rgba(160, 160, 160, 0.35); border: 0; margin: 0.25rem 0;">
<details>
<summary><big><big><big><strong>Open Questions</strong></big></big></big></summary>

- Is `1pt Safety = 1000` intentional? This must be confirmed before optimizing defensive players.
- Does OP allow quarterbacks, and does FLEX allow quarterbacks and tight ends?
- Are the first-column values in the draft room ESPN projections, auction values, or another ranking metric?
- Which four managers are expected to use ESPN autodraft?
- Are the observed mock drafts generated from a completely fresh state or through undo/reset?
- Should the objective prioritize expected points, championship probability, or avoiding the bottom finish?

</details>
