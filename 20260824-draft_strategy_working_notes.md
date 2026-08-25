# Fantasy Football Draft Strategy — Working Notes

**Date:** 2026-08-24  
**League:** Practice Draft for STOGA PIONEERS  
**Draft position:** 1.03  
**Teams:** 8  
**Draft type:** Snake

## Core conclusion

This is not a normal one-QB league.

The roster has:

- 1 QB slot
- 1 OP slot, which accepts any offensive player, including quarterbacks
- 3 RB
- 3 WR
- 2 TE
- 3 FLEX

ESPN’s player eligibility data confirms that Josh Allen is eligible for `QB + OP`, while quarterbacks are not FLEX-eligible. Therefore each team can start up to two quarterbacks, although OP may be more valuable when used on an elite non-QB.

Across eight teams, there are up to 16 QB-capable starting slots. This makes quarterback scarcity materially different from a standard one-QB league.

## Current ESPN projection snapshot

| Player | Position | Projected points |
|---|---|---:|
| Puka Nacua | WR | 431.0 |
| Josh Allen | QB | 422.2 |
| Ja’Marr Chase | WR | 409.7 |
| Jaxon Smith-Njigba | WR | 399.0 |
| Jahmyr Gibbs | RB | 395.6 |
| Bijan Robinson | RB | 389.8 |
| Christian McCaffrey | RB | 380.9 |
| Lamar Jackson | QB | 375.0 |
| Drake Maye | QB | 373.4 |
| Joe Burrow | QB | 370.8 |
| Jalen Hurts | QB | 367.3 |
| Jayden Daniels | QB | 363.1 |
| Trey McBride | TE | 349.6 |
| Brock Bowers | TE | 342.0 |

Raw projected points are not enough. The simulator needs to compare each player against the realistic replacement value for the slot he fills.

## Pick 1.03 strategy

Only two players can be selected before me, so there should not be a rigid opening-round script.

### Round 1 priority

1. Josh Allen, if available.
2. Puka Nacua, Ja’Marr Chase, Jahmyr Gibbs, or Bijan Robinson, depending on availability and replacement value.
3. Lamar Jackson or Jayden Daniels if the QB run is accelerating or the elite skill tier has been depleted.

The key correction is that quarterbacks should not be pushed down merely because there is only one QB-labelled slot. OP makes a second QB strategically viable.

My current lean:

- Allen: clear first-round target.
- Lamar: very strong first-round consideration.
- Daniels: a real first-round option, but not automatically ahead of Puka or Gibbs based only on current projected points.

## Preferred opening construction

If the board cooperates:

- **Round 1:** elite QB or elite RB/WR
- **Round 2:** Trey McBride or Brock Bowers
- **Round 3:** the other elite TE, if available; otherwise QB2 or elite RB/WR
- **Round 4–5:** QB2 if not already taken
- **Rounds 5–8:** aggressively fill RB/WR starters and flex depth

### Should I draft two TEs in Rounds 2–3?

Yes, if McBride and Bowers are available at both picks.

The league starts two TEs, and the current projections show a major gap between the top two and the next tier:

- McBride: approximately 350
- Bowers: approximately 342
- Several next-tier TEs: approximately 250–270

That gap could create a large weekly positional advantage.

Do not force a mediocre TE in Round 3 if both elite TEs are gone. Take QB2 or the best remaining RB/WR instead, then target TE later.

## Example ideal draft

Assuming the board cooperates:

| Round | Target |
|---:|---|
| 1 | Josh Allen or elite RB/WR |
| 2 | Trey McBride |
| 3 | Brock Bowers, or QB2 |
| 4 | QB2 if still needed |
| 5 | Best available RB |
| 6 | Best available WR |
| 7 | Second RB |
| 8 | Second WR |
| 9 | Third RB |
| 10 | Third WR |
| 11 | TE3 or flex-quality RB/WR |
| 12 | Flex-quality RB/WR |
| 13+ | IDP, K, P, HC, and upside bench players |

## Round-by-round blueprint from pick 1.03

| Round | Pick | Default objective |
|---:|---:|---|
| 1 | 1.03 | Elite QB or elite RB/WR |
| 2 | 2.06 | TE1 or second elite skill player |
| 3 | 3.03 | TE2, QB2, or elite skill player |
| 4 | 4.06 | QB2 if still needed |
| 5 | 5.03 | RB/WR starter |
| 6 | 6.06 | RB/WR starter |
| 7 | 7.03 | RB/WR depth |
| 8 | 8.06 | RB/WR depth or TE3 |
| 9–12 | — | Finish RB/WR/TE/flex depth; begin IDP selectively |
| 13+ | — | IDP, K, P, HC, bench, and upside players |

## QB plan

Aim to have QB2 by Round 4 or 5.

QB2 is not merely a backup. It can fill OP and become one of the team’s actual starters. However, OP is flexible, so a QB should only occupy it when the QB advantage exceeds the value of using OP on a skill player.

If a major QB run begins, move earlier. If the QB pool remains deep and elite RB/WR value is falling, delay QB2 slightly—but do not treat the league as one-QB.

## RB/WR plan

The league starts 3 RB, 3 WR, and 3 FLEX, so the roster needs substantial skill-position depth.

After securing the high-value QB/TE structure, prioritize players who can start at RB, WR, or FLEX. Avoid drafting too many low-ceiling specialists simply to fill a nominal position.

## Other positions

- TE is unusually important because two TEs start and TE receptions score 1.5 points.
- IDP should be modeled separately; defensive scoring is unusually aggressive, especially sacks, interceptions, forced fumbles, and passes defended.
- K, P, and HC can probably wait unless projections reveal a large replacement-value gap.
- The `1pt Safety = 1000` setting must be confirmed as intentional. If real, it could radically change defensive strategy.

## What ESPN autodraft appears to be doing

The observed all-auto drafts frequently select Allen, Lamar, Daniels, Maye, and Hurts in the first two rounds alongside elite RBs and WRs.

This is broadly sensible under the actual roster because OP creates additional QB demand. ESPN does not appear to be behaving like a standard one-QB autodraft.

However, ESPN is not proven to be optimizing this exact custom ruleset. Its behavior may combine:

```text
ESPN displayed rank
+ position and OP roster fit
+ tier scarcity
+ availability
+ hidden randomness
```

The observed drafts suggest a league-wide best-available calculation with stochastic variation. Jayden Daniels sometimes being selected ahead of higher-projected skill players may reflect ESPN’s rank signal or hidden roster-fit weighting rather than strict custom projected-point optimization.

## Simulator model to build

### User strategy

```text
custom projected points
+ slot-aware replacement value
+ roster construction value
+ TE-premium adjustment
- injury and uncertainty penalty
```

### Opponent strategy hypothesis

```text
ESPN rank signal
+ position/OP roster fit
+ positional scarcity
+ current roster needs
+ small stochastic component
```

The simulator should replay many drafts, fit opponent behavior to the observed all-auto fixtures, and report:

- probability each player is available at 1.03
- probability of getting each player at every later pick
- expected roster under each opening strategy
- expected starter points
- downside cases where the team gets stuck at QB, TE, RB, or WR

## Questions to refine next

1. Is the `1pt Safety = 1000` setting intentional?
2. Are the three FLEX slots definitely restricted to non-QBs in ESPN’s eligibility data?
3. What defensive-player projections does ESPN provide for this league?
4. Do the observed drafts change when only one team is manually controlled?
5. Can we estimate ESPN’s hidden pick weights from the six recorded all-auto drafts?

## Bottom line

The current preferred plan is:

> Take an elite QB or elite RB/WR in Round 1; target McBride/Bowers aggressively in Rounds 2–3; secure QB2 by Round 4–5; then build heavy RB/WR/flex depth.

The exact Round 1 pick should be determined by slot-aware replacement value, not raw ESPN rank alone.
