# ATT_53 — Bayesian Inference: A Finite Process Unfolding

**Essay ID:** ATT_53  
**Title:** Bayesian Inference: A Finite Process Unfolding  
**College:** College of Attralucian Studies  
**Series:** Finite Symbolic Mechanics (FSM) — first application essay of the FPU method (ATT_52)  
**Lesson:** ATT_53  
**Pillars (primary → secondary):** P3, P2 (primary); P1, P5, P4 (secondary)  
**Status:** Stable  
**Last updated:** 2026-05-09

---

## Overview

This essay applies the method of **Finite Process Unfolding (FPU)** — established in ATT_52 — to Bayesian inference. FPU is taken as the established instrument; Bayesian inference is its specimen. The central argument: the standard Bayes equation

$$P(H \mid D) = \frac{P(D \mid H) \cdot P(H)}{P(D)}$$

appears as a static relation between four probability values but is in fact a compressed trace of two distinct finite experiments, a mandatory memory commitment between them, and a geometric contraction of a bounded hypothesis manifold. The pipe symbol `|`, conventionally read as "given", is reinterpreted as a **temporal arrow with a memory cost** — not a synchronic conditioning operator, but a diachronic tethering marker: not "given D" but "after D was produced and the intermediate state was consulted."

The broader claim: properly unfolded, Bayesian inference is a **trajectory in a finite hypothesis manifold**. Each updating step is a geometric contraction. Convergence is basin attraction. The notation hides this. FPU recovers it.

---

## Why Bayes Is Hard to Understand

The essay opens with a diagnostic observation: the pedagogical difficulty of Bayesian statistics is not a failure of intelligence. It is a **failure induced by notation**. The standard presentation offers the Bayes equation as a relation between probabilities that appear to coexist simultaneously. The word "conditional" is introduced as a modifier ("the probability of H, *given* D") without indicating that "given" encodes a temporal commitment: D must have been *produced, recorded, and stored* before the conditioned quantity is defined.

This is a failure of symbolic compression. The equation compresses two sequential experiments and the memory operation between them into a single static expression. FPU is the diagnostic instrument for reversing this compression.

---

## The Symbolic Frame

Following FPU convention, all analysis operates within the **symbolic frame**: no appeal to entities beyond the boundary at which symbols are formed. Each probability value is the outcome of a finite measurement act — a generonic event — embedded within a bounded hypothesis container.

**Admissibility condition:** the hypothesis space $\mathcal{H} = \{H_1, H_2, \ldots, H_n\}$ must be enumerated and bounded **before** the first experiment. Without a finite, closed container, the first measurement act has no definite output, and the second experiment has no defined state to inherit.

---

## FPU Applied: The Seven Steps

### Step 1 — Compression Boundary

The symbolic object under analysis:

$$S = P(H \mid D) = \frac{P(D \mid H) \cdot P(H)}{P(D)}$$

Behind this expression lie two experiments, a storage operation, and a normalisation procedure. $S$ is treated as a compressed trace; the task is to reconstruct the admissible generating procedure $\mathcal{P}(S)$.

### Step 2 — Compression Type

$S$ is a **sequential composition** compressed into a static ratio. Its components:
- $P(H)$: output of Experiment 1 (prior measurement)
- $P(D \mid H)$: output of Experiment 2, conditioned on stored intermediate state
- $P(D)$: marginalisation over all admissible hypotheses
- $P(H \mid D)$: final contracted state

The pipe `|` appears twice in $S$ with **different meanings** both suppressed by the notation: once as conditioning on a stored result (in $P(D \mid H)$), and once as a temporal sequencing marker (in $P(H \mid D)$).

### Step 3 — Sequential Procedure

**Experiment 1 — Prior Measurement Act:**
1. Bound and enumerate $\mathcal{H} = \{H_1, \ldots, H_n\}$. Cost: $n$ distinction operations at $\Delta M$ each.
2. Assign prior probabilities $P(H_i)$ through a finite, completable procedure.
3. Store the result as intermediate state $\sigma_1 = \{P(H_i)\}_{i=1}^{n}$.

**Memory Commitment — Storage of $\sigma_1$:**
The prior distribution must persist between experiments. This is not passive: it imposes a minimum storage cost proportional to $|\mathcal{H}|$ and the precision of each $P(H_i)$.

**Experiment 2 — Likelihood Measurement Act:**
1. Retrieve stored state $\sigma_1$.
2. Generate data $D$; evaluate $P(D \mid H_i)$ for each $H_i$ — tethered to $\sigma_1$; hypothesis space cannot be revised here.
3. Compute marginal: $P(D) = \sum_i P(D \mid H_i) P(H_i)$ — normalisation over the bounded container from Experiment 1.
4. Apply Bayes' rule: $P(H_i \mid D) = P(D \mid H_i) P(H_i) / P(D)$.
5. Output posterior distribution $\sigma_2 = \{P(H_i \mid D)\}_{i=1}^{n}$.

### Step 4 — State Requirements

The procedure requires retention of: $\mathcal{H}$ (hypothesis enumeration); $\sigma_1$ (prior distribution); intermediate likelihood values $P(D \mid H_i)$; and marginal $P(D)$. **None of these appear in the compressed expression $S$.**

### Step 5 — Process Cost

$$\text{Cost}(\mathcal{P}(S)) \geq (2n + 2) \cdot \Delta M$$

where $n = |\mathcal{H}|$. The four terms correspond to: bounding $\mathcal{H}$ ($n$ distinctions), completing Experiment 1 (1 act), evaluating likelihoods ($n$ acts), computing the marginal (1 act). **Cost scales linearly with hypothesis space size — invisible in $S$.**

### Step 6 — Admissibility

Admissible when: $\mathcal{H}$ is finite and enumerable before Experiment 1; $P(H_i) > 0$ for at least one $H_i$; storage of $\sigma_1$ is feasible; Experiment 2 is independent of Experiment 1 except through inherited $\mathcal{H}$ and $\sigma_1$.

**Key inadmissibility condition — improper priors:** a prior over an unbounded hypothesis space (e.g. uniform over all real numbers) is not a technical inconvenience — it is a **container violation**: the first experiment has no finite boundary and therefore no admissible output. Experiment 2 cannot proceed.

### Step 7 — Restated Expression

> $P(H \mid D)$ is a compressed trace of: a finite hypothesis container was established and measured (Experiment 1); the result was stored as an intermediate state (memory commitment); a second independent experiment was conducted within the same container, tethered to the stored state (Experiment 2); the hypothesis manifold was contracted by the joint evidence of both experiments (posterior).

> **The pipe $\mid$ in $P(H \mid D)$ does not mean "given D simultaneously." It means: after D was produced and the intermediate state was consulted. It is a temporal arrow.**

---

## The Geometric Picture

The hypothesis space $\mathcal{H}$ defines a finite manifold $\mathcal{M}$. The prior $\sigma_1$ occupies this manifold with diffuse support. Experiment 2 applies a **geometric contraction**: the likelihood function selects against regions of $\mathcal{M}$ inconsistent with $D$. The posterior $\sigma_2$ is a contracted state of the same manifold.

The geometric picture reveals what the algebraic notation conceals:
- **The two experiments are not interchangeable** — swapping their order yields a different posterior because the container and stored state would be different. Sequential structure is constitutive, not incidental.
- **The posterior is not merely a rescaled prior** — it is a geometrically contracted state of the same manifold, produced by a genuinely distinct finite act.
- **Improper priors correspond to unbounded manifolds** — the contraction of Experiment 2 has no admissible domain to act upon.

---

## Sequential Updating as Manifold Traversal

For sequential Bayesian updating, where each posterior becomes the prior for the next experiment:

$$\sigma_k(H) \propto P(D_k \mid H) \cdot \sigma_{k-1}(H)$$

Under FPU this is a **trajectory** in the space of probability distributions over $\mathcal{H}$. Properties invisible in the algebraic notation:

**Ordering matters.** The trajectory $\sigma_0 \to \sigma_1 \to \sigma_2 \to \cdots$ is path-dependent when experiments interact. Intermediate states are the actual history of the process.

**Convergence is basin attraction.** Under mild conditions the trajectory converges to a stable region of $\mathcal{M}$ regardless of the initial prior $\sigma_0$. Bayesian consistency, geometrically viewed, is a basin structure: the attractor is the region of $\mathcal{H}$ supported by the data; the prior determines only the initial position in the basin, not the destination.

**Memory is structural.** Each $\sigma_k$ is a compression of the full experimental history $\{D_1, \ldots, D_k\}$. This compression is only admissible if $\mathcal{H}$ was established at the outset and held fixed throughout the trajectory. Revising $\mathcal{H}$ mid-trajectory is not a Bayesian operation — it is a re-initialisation of the manifold.

---

## The Pipe Symbol Reconsidered

Standard probability theory defines $P(A \mid B) = P(A \cap B) / P(B)$ — a synchronic definition: both $A$ and $B$ are events in the same probability space, no time involved. FPU reveals this synchronic reading as a **notational fiction** in the Bayesian context. $P(H)$ and $P(D \mid H)$ are not co-present values in a static space; they are outputs of distinct finite experimental acts, separated by a memory commitment, with a determinate temporal ordering.

The pipe symbol therefore carries different meanings depending on whether it is read synchronically (as in the ratio definition) or diachronically (as in the experimental procedure). FPU insists on the **diachronic reading as primary**: the pipe is a **tethering symbol** marking the point at which a second experiment is tethered to the stored output of a first. The synchronic definition is a legitimate but process-suppressing compression.

---

## Connection to FSM

**Admissibility prior to logic:** $\mathcal{H}$ must be admissible before any probabilistic reasoning over it can proceed — not as a consequence of Bayes' theorem but as a precondition for its application. FSM places admissibility before logic; the Bayesian case illustrates this priority.

**Geometric Container Space (P1):** The hypothesis manifold $\mathcal{M}$ is an FSM geometric container — a bounded space within which distinctions are made and measurements stored. Contraction through updating is Dynamic Flow within a finite container.

**Approximations and Measurements (P2):** Each probability value is a finite measurement outcome, not an ideal real number. Precision is bounded by the measurement process that produced it.

**Finite Reality (P5):** Extension to continuous hypothesis spaces, improper priors, and limiting distributions should be treated as approximations to the finite reality, not as the fundamental case.

---

## Summary Table (Appendix A)

| FPU Step | Bayesian Interpretation |
|----------|------------------------|
| Compression boundary | $P(H \mid D) = P(D \mid H) P(H) / P(D)$ |
| Compression type | Sequential composition of two experiments |
| Sequential procedure | Exp. 1 (prior) → memory → Exp. 2 (likelihood) → posterior |
| State requirements | $\mathcal{H}$, $\sigma_1$, $P(D \mid H_i)$, $P(D)$ |
| Process cost | $\geq (2n+2) \cdot \Delta M$ where $n = |\mathcal{H}|$ |
| Admissibility condition | $\mathcal{H}$ finite; $\sigma_1$ stored; Exp. 2 tethered to $\sigma_1$ |
| Restated expression | Compressed trace of two sequential contractions of $\mathcal{M}$ |
| Geometric picture | Trajectory in hypothesis manifold; posterior as attractor |

---

## Conclusion

> *The symbolic form is not primary. It is a compression of process. And the pipe $\mid$ is not a given. It is a* **then.**

---

## Re-style Checklist (LaTeX)

- [ ] **PRIORITY: Running header "Finite Process Unfolding"** — carries over ATT_52's header; should be updated to reflect ATT_53 content (e.g. "Bayesian Unfolding" or "Bayesian Inference: An FPU Analysis")
- [ ] **PRIORITY: Secondary title page** — shows ATT_52's full title "Finite Process Unfolding / A Method for Recovering Temporal Structure from Static Symbolic Forms"; should be ATT_53's own title
- [ ] **`\usepackage{tikz}` missing from preamble** — two TikZ diagrams (hypothesis manifold contraction; sequential updating trajectory) will fail to compile without it; add `\usepackage{tikz}` and `\usetikzlibrary{decorations.pathreplacing,arrows.meta}` to preamble
- [ ] **Double `\maketitle`** — second call redundant; remove
- [ ] **`\textbf\textbf{}`** on secondary title page — nested bold; correct to `\textbf{}`
- [ ] **No axiomline / tcolorbox Formal Core** — consistent with FSM essay style (ATT_51, ATT_52); intentional

---

## Cross-References

| Essay / Lesson | Connection |
|---|---|
| ATT_52 | Finite Process Unfolding: ATT_53 is the first application essay of the FPU method; ATT_52 established the 7-step methodology; ATT_53 applies all seven steps to the Bayesian equation |
| ATT_51 | Non-Commutativity: ATT_53's claim that the two Bayesian experiments are non-interchangeable (swapping order yields different posterior) is an instance of the Temporal Trace Theorem — the sequential structure is constitutive |
| ATT_28 | Commitment, Consensus, Admissibility: improper priors are inadmissible under FSM — container violation; $\mathcal{H}$ must be committed before Experiment 1 |
| ATT_08 | Geofinitism — Measurement-First: prior P(H) is the output of a first finite measurement act, not a pre-existing belief; measurement-first stance applied to probability |
| ATT_06 | Geodesic Fractal Model of LLMs: sequential Bayesian updating as manifold traversal, convergence as basin attraction — directly invokes ATT_06's attractor/basin framework |
| ATT_23 | The Generon: each probability assignment is a generonic event; the full Bayesian procedure is a Generon sequence whose output is the posterior |

---

*Kevin R. Haylett — School of Geofinitism*  
*Simul Pariter.*
