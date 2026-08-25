# Proposed Optimal Draft Strategy

**Date:** 2026-08-24

## Pick 1.03

Only two players can be selected before me. Use this order:

1. **Jahmyr Gibbs**
2. **Puka Nacua**
3. **Bijan Robinson**
4. **Ja'Marr Chase**
5. **Jaxon Smith-Njigba**
6. **Josh Allen**, if the elite RB/WR tier is gone or OP/FLEX rules make QB materially more valuable.

Default pick: **Gibbs**. Main alternative: **Puka**.

## Why

- The league starts 3 RB, 3 WR, 2 TE, 3 FLEX, and 1 OP.
- There is only 1 required QB slot.
- Gibbs benefits from RB scarcity and strong custom-league projections.
- Puka has the highest current projected total in the ESPN payload.
- ESPN Superflex rank helps predict opponents; it does not override our custom value calculation.

## Later rounds

- Build RB/WR depth before chasing quarterback value.
- Move Trey McBride and Brock Bowers up because the league starts two TEs.
- Take a QB when the projection gap justifies it, not merely because ESPN ranks him highly.
- Delay K, P, and HC.
- Verify `1pt Safety = 1000` before optimizing defensive players.

## Simulator model

Opponent pick:

```text
ESPN rank + roster fit + positional need + small random noise
```

My pick:

```text
custom projected points + positional replacement value - risk penalty
```

First target: determine which players are likely to be gone before 1.03.

## Network investigation

The Network tab can show rankings, projections, roster limits, draft state, and any request sent when an autopick occurs. The actual choice logic may instead run in ESPN's downloaded `draft.js` bundle, so we should inspect the code that consumes `draftRanksByRankType`, roster availability, and `CUSTOM_MOCK` state.
