# Predictive vs Prognostic Biomarker Score — Problem Statement

**Status:** Problem statement crystallized. Ready for solve phase.

---

## We want to understand

How to construct a score $R(\phi)$ over biomarker chains $\phi$ (compositions of hard-partition filters on a non-uniform bag of patients) that distinguishes treatment-specific predictive signal from treatment-agnostic prognostic signal, using real-world clinical data where the counterfactual treatment arm is structurally absent.

The score is used **comparatively** — to rank chain A vs chain B on the predictive-vs-prognostic spectrum. We do not seek globally optimal chains; relatively optimal is valid. The practical target is clinical deployment: standards of care, diagnostic biomarker panels.

---

## Setting

- **Patients are non-uniform bags of data.** Different patients have different fields measured. No fixed schema. The ensemble has broad measurement coverage even though each individual has sparse coverage.

- **A biomarker $B$ is a filter:** takes a bag of patients in, returns a sub-bag out. Hard partition at deployment (patients missing the queried field are rejected). Soft superposition at optimization (patients with missing fields contribute fractionally to both B+ and B- sub-bags).

- **A chain $\phi = B_1 \circ B_2 \circ \cdots \circ B_k$** is a composition of filters.

- **Outcome $Y$ is survival-like.** Overall survival with right-censoring (last known follow-up dates available). Sparse, partial progression-free survival data (progression events often missing due to data limitations).

- **The counterfactual arm is structurally absent.** In the motivating example (EGFR+ NSCLC), essentially all patients receive osimertinib. There is no principled comparison arm within the target disease-treatment context.

- **Cross-context specificity as counterfactual proxy.** Adjacent contexts (same drug in other diseases, same disease on other treatments, related conditions) serve as proxies for the missing counterfactual. A biomarker that lights up only in the target context is evidence of predictive interaction; one that lights up everywhere is prognostic. This is analogous to a difference-in-differences interaction across a (disease x treatment) grid, though the formal structure need not be rigidly tabular.

- **KL divergence between B+ and B- outcome distributions** is a candidate scoring object that may do double duty: (1) scoring biomarker informativeness via sign-flipping sensitivity, and (2) quantifying the cost of unresolved superposition for missing-data patients. The connection between these two roles needs careful development.

---

## A satisfying answer would be

A formula or algorithm for $R(\phi)$. Not a proof of identification. Not a working prototype.

---

## Open tensions

1. **Selection-induced confounding.** Chains can look predictive by selecting easy patients (younger, better performance status). The score must adjust for this internally, not rely on external correction.

2. **Score-sample-size coupling.** Deeper chains shrink the sub-bag. The score must penalize or account for the uncertainty this creates. A regularized or lower-confidence-bound style objective is likely needed.

3. **Transportability.** Cross-context specificity only separates predictive from prognostic if, in the absence of a true interaction, the marker's effect would be similar across contexts. This assumption is load-bearing. A marker can be prognostic within one disease but biologically inactive in the negative-control disease, which would falsely appear as specificity.

4. **Superposition structure for missing data.** How the soft weights for missing-data patients are computed during optimization is unspecified. Imputation from other measured fields is a default; ideally this is learned. The connection to sign-flipping / KL (missing-data patients naturally sit in the "flipped" position) needs careful development in the solve phase.

5. **Censoring as a first-class concern.** The score must handle right-censored OS and sparse PFS natively. Beyond handling it, the score should quantify how censoring degrades confidence bounds, to motivate acquisition of better data with less censoring.

6. **Why KL?** KL is the candidate divergence but has not been justified over alternatives (Wasserstein, hazard ratios, rank-based statistics). Censored data complicates KL computation specifically — may need to go through hazard estimates or Kaplan-Meier. This is a solve-phase choice.

7. **Comparative, not absolute.** Since the score ranks chains rather than estimating absolute effect sizes, some biases (censoring, transportability wobble) may be tolerable as long as they affect all candidate chains roughly equally. This relaxation should be examined explicitly.
