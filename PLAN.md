# Plan: Fantasy Football Draft Simulator

## Objective

Build a simulator for this customized ESPN fantasy football league that estimates which players are available at my picks, conditional on how every manager drafts, including me.

## Current state

- Repository: https://github.com/swagneverquits/fantasy_football_draft
- Status: planning only; no application code yet.

## Plan

### 1. Capture league inputs

- [ ] Record team count, draft order, rounds, draft format, roster slots, bench size, and position limits.
- [ ] Record custom ESPN scoring, bonuses, penalties, and lineup rules.
- [ ] Define player inputs: projections, ADP, positions, tiers, injuries, and status.
- [ ] Define my rankings, roster needs, targets, fades, and risk tolerance.
- [ ] Document behavior assumptions for every manager, including the four ESPN autodrafters.

### 2. Build the draft model

- [ ] Create validated league, player, roster, and manager schemas.
- [ ] Implement snake-draft sequencing and legal roster construction.
- [ ] Track drafted players, rosters, remaining players, and pick history.
- [ ] Support deterministic runs with explicit random seeds.

### 3. Implement manager strategies

- [ ] ESPN-autodraft agent based on rankings/value and roster constraints.
- [ ] ADP-following agent with configurable randomness.
- [ ] Positional, tier/value, and custom manager agents.
- [ ] My strategy agent with rankings, tiers, targets, fades, and roster objectives.
- [ ] Keep behavior parameters configurable rather than hard-coded.

### 4. Simulate and analyze

- [ ] Run hundreds or thousands of drafts.
- [ ] Vary uncertain manager behavior within explicit ranges.
- [ ] Calculate player-availability probability at every one of my picks.
- [ ] Calculate positional runs, scarcity, roster outcomes, and downside percentiles.
- [ ] Compare alternate strategies and draft positions.

### 5. Produce reports

- [ ] Export CSV and readable Markdown/HTML reports.
- [ ] Show players most likely to fall to each pick.
- [ ] Show players I should not expect to reach me.
- [ ] Show decision points and fallback options by round.
- [ ] Allow input updates without changing application code.

## Acceptance criteria

- A fresh checkout runs a minimal example draft and the test suite.
- Invalid league settings produce clear validation errors.
- A hand-checkable draft produces the expected pick order and legal rosters.
- Each manager agent makes legal, explainable picks.
- Seeded simulations are repeatable; unseeded simulations produce distributions.
- Reports identify player availability at my picks and quantify downside outcomes.

## Verification

- [ ] Unit-test scoring, roster rules, pick sequencing, and agent selection.
- [ ] Use fixed seeds for regression tests.
- [ ] Validate against manually constructed small drafts.
- [ ] Add fixtures for unusual ESPN settings.
- [ ] Compare simulated behavior with known ADP behavior.

## Open questions

- [ ] Exact scoring and roster settings.
- [ ] Number of teams, rounds, and my draft position.
- [ ] Keepers, traded picks, or special position limits.
- [ ] Projection/ranking and ADP source.
- [ ] Manager behavior beyond the four ESPN autodrafters.
- [ ] How to define and optimize “avoid last place” risk.
