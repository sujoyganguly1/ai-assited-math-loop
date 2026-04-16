# CLAUDE.md

Instructions for Claude when operating in this repository. Read this at the start of every session.

---

## What this repo is for

This is a personal theoretical study system for probability theory, statistics, and ML theory. Problem solving is done in a physics-style register: push the machinery, check limiting cases, grind through calculations, surface what breaks. It is not a formal proof system.

---

## Skills available

| Skill | Trigger | Purpose |
|---|---|---|
| `/grill-me-math` | User wants to clarify or stress-test a problem | Socratic interrogation to reach a shared problem statement |
| `/solve-math` | User has a crystallized problem and wants to work through it | Collaborative solving with wiki output |

When the user says "grill me" or wants to understand something before doing any math, run `/grill-me-math`. When the problem statement is clear and the user wants to work through it, run `/solve-math`. The two skills are designed to run in sequence but can be used independently.

---

## Wiki

The persistent knowledge base lives in `docs/math-wiki/`. Always read `docs/math-wiki/INDEX.md` at the start of a session to orient. Surface relevant prior result cards briefly — do not summarize everything, just note what is directly relevant to the current problem.

When `/solve-math` closes a session, it writes a result card and updates the index. Do not skip this step.

---

## Behavioral defaults

**Stay in the background.** The user leads. Do not take over a calculation or redirect the approach unless a specific trigger fires (gap in approach, expressed uncertainty, assumption check requested).

**Physics register, not formal proof.** Reasoning should be rigorous but not pedantic. Invoke standard results by name, check limiting cases, track assumptions — but do not write epsilon-delta proofs unless explicitly asked.

**Flag assumptions actively.** Both skills surface assumptions that are doing hidden work. When an assumption appears load-bearing or potentially unnecessary, say so explicitly. Do not let assumptions pass silently.

**Failed approaches are output.** When going off independently, always report what was tried and why it did not work, not just the result that succeeded.

**One question at a time.** During `/grill-me-math`, ask one question per turn with your own recommended answer. Do not present a list of questions.

**Techniques get their own cards.** When a named technique (symmetrization, coupling, change-of-measure, etc.) appears in a result card for the first time, also create a card for it in `docs/math-wiki/techniques/` if one does not already exist.

---

## Topic areas

The current focus is:

- Probability theory (measure-theoretic foundations, convergence, limit theorems)
- Concentration inequalities (Hoeffding, Bernstein, sub-Gaussian, McDiarmid)
- Statistical estimation and inference (MLE, Bayes, minimax, efficiency)
- PAC learning and generalization (VC theory, Rademacher complexity, uniform convergence)
- Information theory and divergences (KL, mutual information, data processing)
- Variational inference and approximation (ELBO, mean field, importance weighting)
- Optimization in ML (convexity, SGD convergence, landscape)

New topic areas can be added. When a new area is introduced, create a directory under `docs/math-wiki/` and add a section to `INDEX.md`.

---

## File placement

```
.claude/skills/grill-me-math.md     # Skill definitions
.claude/skills/solve-math.md
docs/math-wiki/INDEX.md             # Master topic index
docs/math-wiki/<topic>/<card>.md    # Result cards
docs/math-wiki/techniques/<card>.md # Technique cards
```
