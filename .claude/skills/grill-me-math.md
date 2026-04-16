---
name: grill-me-math
description: Socratic interrogation to establish shared understanding of a mathematical or theoretical problem before any solving begins. Use when the user wants to clarify what they're trying to understand, stress-test their framing, or says "grill me". Covers probability theory, statistics, and ML theory in a physics-style problem-solving register.
---

# Grill Me — Math

Before touching any calculation or proof idea, establish a shared, crisp understanding of what we are actually trying to figure out and why. The goal of this skill is a problem statement both of us agree on — not a solution.

## Process

### 1. Orient from the wiki

Read `docs/math-wiki/INDEX.md`. Scan for topic areas and result cards that are directly relevant to what the user has described. If relevant prior cards exist, surface them briefly: "We've worked on [topic] before — [one-line summary of relevant card]." This grounds the new session in accumulated context without requiring the user to re-explain.

### 2. Establish motivation before anything else

Ask: what is the user trying to understand, and why does it matter to them right now? Do not touch their approach or intuition yet. Listen for:

- The object they are studying (a quantity, an estimator, a bound, a distribution, a learning algorithm)
- The property they want to understand (convergence, tightness, sample complexity, identifiability, generalization)
- The context that makes this interesting (a paper they are reading, a model they are building, a gap in their intuition)

Reflect back what you heard in one sentence and ask if it is right before proceeding.

### 3. Interrogate the problem structure

Walk the user down each branch of the problem's decision tree, one question at a time. For each question, provide your own recommended answer or framing — do not leave the user holding an open question alone. Probe:

- **What kind of claim is this?** Existence, uniqueness, asymptotic, finite-sample, exact characterization?
- **What regime matters?** Large n? High dimension? Sparse signal? Specific parameter ranges?
- **What is the object of interest precisely?** Nail down the random variable, estimator, loss, or quantity — ambiguity here propagates everywhere.
- **What would a satisfying answer look like?** A closed form? An order-of-magnitude bound? A qualitative behavior?

### 4. Surface the user's current mental model

Ask the user what tools or results they think are relevant. Do not evaluate yet — just draw out the model. Then ask where they feel uncertain or where their intuition feels shaky. This is the map of the terrain before we judge the route.

### 5. Flag suspicious assumptions

Review the assumptions implicit in the user's framing. For each one that seems load-bearing or potentially unnecessary, flag it explicitly:

- "You seem to be assuming [X] — is that given, or is it something we need to justify?"
- "This approach typically requires [Y] — do we have that here?"
- "It's worth checking whether [Z] is actually necessary or just convenient."

Do not attempt to resolve these — just make the assumption structure visible. The user may not have known they were making them.

### 6. Crystallize the problem statement

Once the branches are resolved, write a crisp problem statement in the following form:

```
We want to understand: [precise statement of the question]
Setting: [relevant assumptions, regime, object definitions]
A satisfying answer would be: [what form the answer should take]
Open tensions: [assumptions we flagged but did not resolve, alternative framings worth keeping in mind]
```

Confirm this with the user. If they agree, this becomes the input to `/solve-math`.
