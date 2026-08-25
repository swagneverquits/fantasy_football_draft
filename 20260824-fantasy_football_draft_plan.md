# Fantasy Football Draft Simulator Plan

**Date:** 2026-08-24

<details open>
<summary><big><big><big><strong>Motivation</strong></big></big></big></summary>

This plan turns a customized ESPN fantasy football league into a repeatable draft-simulation workflow.

<div style="margin-left: 1.25rem; padding-left: 1rem; border-left: 3px solid #777;">

<details>
<summary><strong>League Model - make the unusual rules explicit.</strong></summary>

- Capture custom scoring, roster constraints, draft order, and player data.
- Represent my roster needs and the behavior of every manager.
- Model the four managers expected to follow ESPN's autodraft behavior.

</details>

<details>
<summary><strong>Simulation Engine - make draft outcomes observable.</strong></summary>

- Simulate legal snake drafts with configurable manager strategies.
- Preserve randomness while supporting reproducible seeded runs.
- Record complete draft traces so surprising outcomes can be explained.

</details>

<details>
<summary><strong>Decision Support - reduce the chance of another last-place season.</strong></summary>

- Estimate the probability that each player reaches each of my picks.
- Compare draft strategies, roster outcomes, and downside percentiles.
- Produce fallback options instead of relying on one ideal draft path.

</details>

</div>

**The through-line is to replace draft-day guesswork with a transparent model of what this league is likely to do.**

</details>

<hr style="height: 3px; background: rgba(160, 160, 160, 0.35); border: 0; margin: 0.25rem 0;">
<details open>
<summary><big><big><big><strong>Work Items</strong></big></big></big></summary>

**Status:** 🟿 Not Started | 🛠️ In Progress | ✅ Done | ⏸️ Paused | ⛔ Blocked

<div style="margin-left: 1.25rem; padding-left: 1rem; border-left: 3px solid #777;">

<details open>
<summary><big><strong>1. 🟿 Capture League Inputs</strong></big></summary>

<table style="width: 100%; table-layout: fixed;">
  <colgroup><col style="width: 2%; white-space: nowrap;"><col style="width: 20%;"><col style="width: 10%; white-space: nowrap;"><col style="width: 10%; white-space: nowrap;"><col style="width: 10%; white-space: nowrap;"><col style="width: 48%;"></colgroup>
  <thead><tr><th>#</th><th>Subtask</th><th>Status</th><th>PR</th><th>Date Completed</th><th>Notes</th></tr></thead>
  <tbody>
    <tr><td style="white-space: nowrap;">a</td><td>Record league size, draft order, rounds, and draft format</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Support the league's actual ESPN configuration.</td></tr>
    <tr><td style="white-space: nowrap;">b</td><td>Record roster slots, bench size, and position limits</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Include unusual eligibility and lineup rules.</td></tr>
    <tr><td style="white-space: nowrap;">c</td><td>Record scoring bonuses, penalties, and reception settings</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Scoring is the source of player value.</td></tr>
    <tr><td style="white-space: nowrap;">d</td><td>Define player projections, ADP, tiers, injuries, and status inputs</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Start with one documented import shape.</td></tr>
    <tr><td style="white-space: nowrap;">e</td><td>Document manager behavior and my draft strategy</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Include the four ESPN autodrafters and my risk tolerance.</td></tr>
  </tbody>
</table>

> <details>
> <summary><strong>Design Notes</strong></summary>
>
> Keep league rules and manager assumptions in data files so scenarios can change without changing simulation code.
>
> </details>

</details>
<hr style="height: 1px; background: rgba(160, 160, 160, 0.25); border: 0; margin: 0.25rem 0;">
<details>
<summary><big><strong>2. 🟿 Build Draft Model</strong></big></summary>

<table style="width: 100%; table-layout: fixed;">
  <colgroup><col style="width: 2%; white-space: nowrap;"><col style="width: 20%;"><col style="width: 10%; white-space: nowrap;"><col style="width: 10%; white-space: nowrap;"><col style="width: 10%; white-space: nowrap;"><col style="width: 48%;"></colgroup>
  <thead><tr><th>#</th><th>Subtask</th><th>Status</th><th>PR</th><th>Date Completed</th><th>Notes</th></tr></thead>
  <tbody>
    <tr><td style="white-space: nowrap;">a</td><td>Create validated league, player, roster, and manager schemas</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Validation should fail with useful errors.</td></tr>
    <tr><td style="white-space: nowrap;">b</td><td>Implement snake-draft sequencing</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Make pick order independently testable.</td></tr>
    <tr><td style="white-space: nowrap;">c</td><td>Enforce roster eligibility and draft legality</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Prevent impossible rosters and duplicate picks.</td></tr>
    <tr><td style="white-space: nowrap;">d</td><td>Track rosters, remaining players, and complete pick history</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Pick traces will make model behavior explainable.</td></tr>
  </tbody>
</table>

> <details>
> <summary><strong>Design Notes</strong></summary>
>
> Keep the core draft engine independent from data import, reporting, and any future ESPN integration.
>
> </details>

</details>
<hr style="height: 1px; background: rgba(160, 160, 160, 0.25); border: 0; margin: 0.25rem 0;">
<details>
<summary><big><strong>3. 🟿 Implement Manager Strategies</strong></big></summary>

<table style="width: 100%; table-layout: fixed;">
  <colgroup><col style="width: 2%; white-space: nowrap;"><col style="width: 20%;"><col style="width: 10%; white-space: nowrap;"><col style="width: 10%; white-space: nowrap;"><col style="width: 10%; white-space: nowrap;"><col style="width: 48%;"></colgroup>
  <thead><tr><th>#</th><th>Subtask</th><th>Status</th><th>PR</th><th>Date Completed</th><th>Notes</th></tr></thead>
  <tbody>
    <tr><td style="white-space: nowrap;">a</td><td>Implement ESPN-autodraft behavior</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Use rankings/value subject to roster constraints.</td></tr>
    <tr><td style="white-space: nowrap;">b</td><td>Implement ADP-following behavior with configurable randomness</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Represent uncertainty among the four autodrafters.</td></tr>
    <tr><td style="white-space: nowrap;">c</td><td>Implement positional, tier/value, and custom profiles</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Profiles should be configurable, not hard-coded.</td></tr>
    <tr><td style="white-space: nowrap;">d</td><td>Implement my strategy profile</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Support targets, fades, tiers, needs, and risk tolerance.</td></tr>
  </tbody>
</table>

> <details>
> <summary><strong>Design Notes</strong></summary>
>
> Every agent should produce a legal and explainable pick, with behavior parameters exposed for scenario testing.
>
> </details>

</details>
<hr style="height: 1px; background: rgba(160, 160, 160, 0.25); border: 0; margin: 0.25rem 0;">
<details>
<summary><big><strong>4. 🟿 Run Simulations And Analyze Outcomes</strong></big></summary>

<table style="width: 100%; table-layout: fixed;">
  <colgroup><col style="width: 2%; white-space: nowrap;"><col style="width: 20%;"><col style="width: 10%; white-space: nowrap;"><col style="width: 10%; white-space: nowrap;"><col style="width: 10%; white-space: nowrap;"><col style="width: 48%;"></colgroup>
  <thead><tr><th>#</th><th>Subtask</th><th>Status</th><th>PR</th><th>Date Completed</th><th>Notes</th></tr></thead>
  <tbody>
    <tr><td style="white-space: nowrap;">a</td><td>Run seeded and unseeded Monte Carlo drafts</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Seeded runs must be repeatable.</td></tr>
    <tr><td style="white-space: nowrap;">b</td><td>Calculate player availability at each of my picks</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Show probabilities rather than one deterministic answer.</td></tr>
    <tr><td style="white-space: nowrap;">c</td><td>Calculate positional runs, scarcity, and roster outcomes</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Include downside percentiles to address last-place risk.</td></tr>
    <tr><td style="white-space: nowrap;">d</td><td>Compare alternate strategies and draft positions</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Make tradeoffs visible before draft day.</td></tr>
  </tbody>
</table>

> <details>
> <summary><strong>Design Notes</strong></summary>
>
> Treat manager behavior as a distribution of plausible decisions, not as a claim that any one manager will draft exactly as modeled.
>
> </details>

</details>
<hr style="height: 1px; background: rgba(160, 160, 160, 0.25); border: 0; margin: 0.25rem 0;">
<details>
<summary><big><strong>5. 🟿 Produce Draft Reports And Verify Behavior</strong></big></summary>

<table style="width: 100%; table-layout: fixed;">
  <colgroup><col style="width: 2%; white-space: nowrap;"><col style="width: 20%;"><col style="width: 10%; white-space: nowrap;"><col style="width: 10%; white-space: nowrap;"><col style="width: 10%; white-space: nowrap;"><col style="width: 48%;"></colgroup>
  <thead><tr><th>#</th><th>Subtask</th><th>Status</th><th>PR</th><th>Date Completed</th><th>Notes</th></tr></thead>
  <tbody>
    <tr><td style="white-space: nowrap;">a</td><td>Export CSV and readable Markdown/HTML reports</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Inputs should be updateable without code changes.</td></tr>
    <tr><td style="white-space: nowrap;">b</td><td>Report players most likely to fall to each pick</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Include fallback options by round.</td></tr>
    <tr><td style="white-space: nowrap;">c</td><td>Add tests for scoring, rosters, sequencing, and agent selection</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Focus on shared behavior and high-risk logic.</td></tr>
    <tr><td style="white-space: nowrap;">d</td><td>Validate against small hand-constructed drafts and ADP behavior</td><td style="white-space: nowrap;">🟿 Not Started</td><td style="white-space: nowrap;">-</td><td style="white-space: nowrap;">-</td><td>Do not trust recommendations until model behavior is inspectable.</td></tr>
  </tbody>
</table>

> <details>
> <summary><strong>Design Notes</strong></summary>
>
> Keep verification proportional to risk, expanding coverage when shared logic or user-facing outputs change.
>
> </details>

</details>

</div>

</details>

<hr style="height: 3px; background: rgba(160, 160, 160, 0.35); border: 0; margin: 0.25rem 0;">
<details>
<summary><big><big><big><strong>Open Questions</strong></big></big></big></summary>

- What are the exact scoring and roster settings?
- How many teams, rounds, and what draft position do I have?
- Are there keepers, traded picks, or special position limits?
- Which projection, ranking, and ADP source should we use?
- How does each manager draft beyond the four ESPN autodrafters?
- How should “avoid last place” risk be defined and optimized?

</details>
