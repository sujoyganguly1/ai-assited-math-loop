---
name: solve-math
description: Collaborative physics-style problem solving for probability theory, statistics, and ML theory. Takes a crystallized problem statement (from /grill-me-math or the user directly) and works through it with the user, going off independently only when an approach has a gap or the user expresses uncertainty. Ends with a result card written to docs/math-wiki/.
---

# Solve Math

Work through a theoretical problem collaboratively in a physics-style register: push the machinery, check limiting cases, grind through calculations when needed, and surface what breaks. The user leads — intervene independently only when there is a real gap or expressed uncertainty.

## Process

### 1. Receive the problem statement

Accept either the crystallized problem statement from `/grill-me-math` or a direct statement from the user. If the problem statement is loose, spend at most two clarifying questions tightening it before proceeding — do not re-run the full grilling here.

Read `docs/math-wiki/INDEX.md` and any result cards in the relevant topic area. Note any techniques or results from prior sessions that may be reusable. Mention them briefly if relevant: "We used [technique] in a similar setting before — might be worth keeping in mind."

### 2. Work together, user-led

Let the user drive their approach. Your default mode is collaborative engagement:

- Work through steps together, filling in algebra or invoking standard results as needed
- Point out when a step is non-trivial or deserves more care
- Ask "what do you want to do next?" at natural branch points

Do NOT go off independently unless one of the following triggers fires:

**Trigger A — Gap in approach**: The user's stated approach has a step that does not follow, relies on an unjustified claim, or leads to a contradiction. Say what the gap is, then go off and work through one or more alternatives before returning.

**Trigger B — Expressed uncertainty**: The user signals they are unsure how to proceed, whether a step is right, or whether an assumption holds. Go off and investigate before returning with a concrete finding.

**Trigger C — Assumption check requested**: The user asks whether an assumption is necessary. Go off and attempt to construct a counterexample or find the minimal condition under which the result still holds.

### 3. When going off independently

State clearly what you are going to investigate and why, then work through it fully before presenting. Structure your return as:

```
What I tried: [approach or calculation attempted]
What happened: [what worked, what broke, what the calculation showed]
Key insight: [the one thing that matters]
Implication for our problem: [how this changes or confirms the approach]
```

For each approach attempted, check:
- Limiting cases: does the answer behave correctly as parameters go to 0, ∞, or degenerate values?
- Assumption necessity: can you construct a counterexample if you drop each assumption in turn?
- Structural sanity: does the answer have the right qualitative shape (monotonicity, symmetry, scaling)?

If you attempted multiple approaches, report which ones failed and why — failed attempts are part of the result.

### 4. Flag assumptions continuously

Throughout the session, flag assumptions that appear to be doing hidden work. Use the form:

- "[Assumption] is load-bearing here — the result breaks without it because [brief reason]."
- "[Assumption] may be unnecessary — here is a weaker condition that might suffice: [condition]."
- "This step uses [standard result] — worth noting it requires [condition] which we should verify we have."

Do not interrupt flow for minor flags — collect them and surface at a natural pause point.

### 5. Close the session — write the result card

When the problem is resolved (or a meaningful partial result is reached), write a result card to `docs/math-wiki/<topic-area>/<kebab-case-title>.md` using this template:

```markdown
# [Title: what was understood]

**Date**: [YYYY-MM-DD]  
**Topic area**: [e.g., Concentration Inequalities, PAC Learning, Variational Inference]  
**Tags**: [technique tags, e.g., symmetrization, change-of-measure, bias-variance]

## Problem statement
[The crystallized statement of what we were trying to understand]

## Setting and assumptions
[The objects, regime, and assumptions — flag which ones are load-bearing]

## Key insight
[The one or two sentences that capture what makes this problem tick]

## Solution sketch
[The main line of argument or calculation — physics register, not formal proof. Enough that a future session can reconstruct the reasoning without redoing all the work.]

## Failed approaches
[What was tried and why it did not work — this is often the most useful part]

## Gotchas and open tensions
[Assumptions that were flagged but not resolved, edge cases, things to revisit]

## Techniques used
[List of named techniques invoked — links to other cards if they exist]
```

After writing the card, update `docs/math-wiki/INDEX.md`:
- Add the card under the correct topic area section
- Add a one-line summary next to the card link

Tell the user the card path and one-line summary of what was captured.
