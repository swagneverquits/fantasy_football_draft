# Proposed Optimal Draft Strategy

**Date:** 2026-08-24

## Corrected league model

This is not a normal one-quarterback league.

| Slot | Starters per team | Important eligibility |
|---|---:|---|
| QB | 1 | Quarterbacks only |
| OP | 1 | Any offensive player, including quarterbacks |
| RB | 3 | Running backs |
| WR | 3 | Wide receivers |
| TE | 2 | Tight ends |
| FLEX | 3 | Skill-position flex; ESPN data shows quarterbacks are not FLEX-eligible |

The remaining slots are DP 2, K 1, P 1, HC 1, plus 9 bench and 2 IR spots.

Therefore every team must start one QB, and each team has a second offensive slot that can be used on a QB. Across eight teams, there are up to 16 QB-capable starting slots. The OP slot is the key reason quarterbacks can be drafted aggressively.

## Pick 1.03

Do not use a fixed “avoid QB” rule. At 1.03, only two players are gone, so evaluate the best remaining player using slot-aware value:

```text
player value = projected points - the best realistic replacement value
                 for the starting slot that player fills
```

For a quarterback, compare both possibilities: filling the mandatory QB slot and filling OP. For a non-quarterback, compare RB/WR/TE/FLEX/OP usage. The best pick is the player who creates the largest lineup advantage, not necessarily the player with the highest raw projection.

Practical 1.03 rule:

1. If Josh Allen, Lamar Jackson, or another elite QB remains, compare that QB’s QB/OP advantage against Gibbs, Puka, Bijan, Chase, and the best remaining skill player.
2. If the top QB advantage is not clearly larger, take the best elite skill player by the same calculation.
3. Do not rank quarterbacks below skill players merely because there is only one QB-labelled slot; OP makes that assumption false.

The current ESPN projections make this a genuine comparison rather than an automatic answer: Puka Nacua is projected for 431.0 points, Josh Allen 422.2, Ja’Marr Chase 409.7, Jaxon Smith-Njigba 399.0, and Jahmyr Gibbs 395.6. Those raw totals are not enough by themselves; QB scarcity and the OP slot determine the replacement adjustment.

## Draft priorities

- Secure at least one high-end QB early. A second QB is attractive when the remaining QB pool is falling faster than the skill pool, or when the player can profitably occupy OP.
- Treat the QB pool as a 16-slot-capable market, with the caveat that OP is flexible and may be better used on a skill player.
- Value TE highly because two TEs start and the scoring gives each TE reception 1.5 points.
- Value RB and WR depth heavily because the league starts 3 RB, 3 WR, and 3 FLEX.
- Delay K, P, HC, and most defensive players unless the unusual scoring produces a clearly large, verified advantage.
- Keep the `1pt Safety = 1000` setting flagged for confirmation; if intentional, it can dominate defensive-player strategy.

## What ESPN’s observed autodraft suggests

The six observed all-auto openings are broadly consistent with a league-wide best-available process that understands quarterback scarcity: Allen, Lamar, Daniels, Maye, and Hurts frequently appear in the first two rounds alongside the elite RB/WR tier.

That means ESPN is making roughly sensible macro-level moves under this roster—not behaving like a standard one-QB autodraft. However, the exact order is not demonstrably optimal for this custom league. ESPN’s displayed rank and its hidden roster-fit/randomness rules can disagree with a strict custom projected-points-plus-replacement calculation. Daniels, for example, can be selected early because of ESPN’s ranking model even when his current projected total trails several elite skill players.

Our working hypothesis for an opponent pick is:

```text
ESPN rank signal
+ position/OP roster fit
+ availability and tier scarcity
+ small stochastic component
```

Our strategy should instead use:

```text
custom projected points
+ slot-aware replacement value
+ TE-premium adjustment
+ roster construction value
- injury/uncertainty penalty
```

The simulator should fit the opponent weights and randomness to the observed draft fixtures, then compare the user’s expected roster outcomes against this corrected strategy.

## Bottom line

Yes: once OP is interpreted correctly, ESPN’s early QB selections look broadly rational and often approximately optimal at the strategic level. No: that does not prove ESPN is optimizing this exact ruleset. The simulator should test whether ESPN’s rank/fit/randomness model leaves repeatable value—especially when ESPN selects a lower-projected QB ahead of a high-projected RB/WR/TE.
