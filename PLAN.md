# Fantasy Football Draft Simulator — Plan

## Objective

Build a draft simulator for a highly customized ESPN fantasy football league. The simulator should estimate which players are likely to be available at each of my picks, conditional on the known draft habits and strategies of the other managers.

## Phase 1: Capture league rules and inputs

- Record league size, draft type, draft order, roster slots, bench size, and rounds.
- Capture scoring settings, including bonuses, penalties, receptions, passing, positional premiums, and any unusual ESPN settings.
- Import or manually define the player pool, positions, teams, injury/status flags, projections, and average draft position (ADP).
- Represent my draft picks and roster needs.
- Represent each manager’s drafting behavior, including the four managers likely to follow ESPN’s autodrafter.

## Phase 2: Create drafting agents

Implement configurable manager profiles, such as:

- ESPN autodraft: rank/value based, subject to roster constraints.
- ADP follower: selects near consensus ADP with configurable randomness.
- Position-focused drafter: prioritizes selected positions or roster construction.
- Tier/value drafter: waits for positional scarcity and targets falling players.
- Custom manager: user-defined preferences, keepers, fades, and player exposure limits.
- My strategy: configurable player rankings, tiers, positional targets, and risk tolerance.

Every agent should expose parameters so behavior can be tested rather than hard-coded.

## Phase 3: Build the draft engine

- Support snake drafts and configurable pick orders.
- Enforce roster eligibility, roster limits, and draftability.
- Apply player rankings, projections, ADP, tiers, scarcity, and manager preferences.
- Add controlled randomness so simulations produce distributions instead of one deterministic result.
- Save complete draft traces for debugging and review.

## Phase 4: Monte Carlo simulation

- Run hundreds or thousands of simulated drafts.
- Vary uncertain manager behavior and pick randomness within explicit ranges.
- Track the players available at each of my picks.
- Track the probability of each player reaching each pick.
- Track expected roster outcomes, positional distributions, and replacement-value results.
- Compare alternate draft strategies and draft positions.

## Phase 5: Analysis and recommendations

Produce reports showing:

- Player availability probabilities at each of my picks.
- Players most likely to fall to me.
- Players I should not expect to reach me.
- Positional runs and scarcity by round.
- Draft-plan decision points and fallback options.
- The effect of each manager profile, especially the ESPN autodrafters.
- Worst-case and percentile outcomes, so avoiding last place is based on more than average projections.

## Phase 6: Interface and usability

- Start with a command-line workflow and CSV/JSON inputs.
- Add reproducible random seeds for comparing scenarios.
- Add a simple scenario configuration file.
- Export results to CSV and readable Markdown/HTML reports.
- Optionally add a local browser dashboard after the simulation model is trustworthy.

## Validation and testing

- Unit-test roster rules, snake-draft order, player eligibility, and agent selection.
- Test that autodraft profiles respect rankings and roster constraints.
- Run deterministic simulations with fixed seeds.
- Validate results against manually constructed small drafts.
- Add regression fixtures for the league’s custom settings.

## Initial deliverables

1. Project structure and documentation.
2. League configuration schema.
3. Player-data import format.
4. Draft engine with snake-draft support.
5. Configurable autodrafter and custom manager agents.
6. Simulation runner with reproducible seeds.
7. Pick-availability report for my draft slots.

## Decisions needed from the league data

- Exact scoring and roster settings.
- Number of teams and draft order.
- Whether there are keepers, traded picks, or position limits.
- My draft position and preferred strategy.
- Player projections/rankings source.
- How each manager tends to draft, beyond the four ESPN autodrafters.
