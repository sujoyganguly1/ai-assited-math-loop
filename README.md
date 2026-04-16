# ai-assited-math-loop
## Math Wiki & Problem-Solving Skills

A personal knowledge system for theoretical problem solving in probability theory, statistics, and ML theory — in a physics-style register. It pairs two Claude skills with a persistent wiki so understanding accumulates across sessions.

---

## Structure

```
.claude/
  skills/
    grill-me-math.md      # Skill: establish shared understanding before solving
    solve-math.md         # Skill: collaborative problem solving with wiki output

docs/
  math-wiki/
    INDEX.md              # Master index — all result cards organized by topic
    probability-theory/   # Topic directories, created as cards are written
    concentration-inequalities/
    statistical-estimation/
    pac-learning/
    information-theory/
    variational-inference/
    optimization/
    techniques/           # Cross-cutting technique cards
```

---

## How to Use

### Starting a new problem

Always start with `/grill-me-math`. This skill orients from the wiki, establishes what you are trying to understand and why, and walks the problem structure before any math is attempted. It closes with a crisp problem statement both you and Claude agree on.

Then run `/solve-math`. This takes the crystallized problem statement and works through it collaboratively. Claude stays in the background unless your approach has a gap, you express uncertainty, or you want an assumption checked — then it goes off, works through alternatives fully, and returns with a structured report.

### Returning to a prior topic

Both skills read `docs/math-wiki/INDEX.md` at the start of a session and surface relevant prior cards. You do not need to re-explain prior work — the wiki carries it forward.

### When a session ends

`/solve-math` writes a result card to the appropriate topic directory and updates the index. The card captures: problem statement, setting and assumptions, key insight, solution sketch, failed approaches, and gotchas.

---

## The Two Skills

| Skill | Purpose | Ends with |
|---|---|---|
| `/grill-me-math` | Establish shared understanding | Agreed problem statement |
| `/solve-math` | Work through the problem | Result card written to wiki |

---

## The Wiki

`docs/math-wiki/` is a flat two-layer structure: topic areas at the top level, result cards within each topic. A **Techniques Library** section captures reusable techniques (symmetrization, change-of-measure, coupling arguments, etc.) independent of specific problems.

Cards are listed chronologically within each topic so the arc of understanding is visible across sessions.

---

## Design Principles

- **Understanding before solving.** `/grill-me-math` exists because the hardest part of theoretical work is often knowing precisely what you are trying to show and why.
- **User-led by default.** `/solve-math` does not take over. It intervenes only when there is a real gap, expressed uncertainty, or an assumption to check.
- **Failed approaches are first-class.** Result cards explicitly capture what was tried and why it did not work. This is often the most useful part of a record.
- **Assumptions are made visible.** Both skills flag assumptions that are doing hidden work — load-bearing, potentially unnecessary, or unverified.
- **Techniques accumulate separately.** When a named technique appears in a problem, it gets its own card in the Techniques Library so it is findable independently of the problem that first used it.
