# ATT_63 — Finite Overlap and Convolution: A Finite Symbolic Mechanics Treatment

**Essay ID:** ATT_63  
**Title:** Finite Overlap and Convolution: A Finite Symbolic Mechanics Treatment  
**College:** College of Attralucian Studies  
**Series:** FSM series — companion to ATT_51 (Non-Commutativity), ATT_52 (FPU), ATT_53 (Bayesian Unfolding), ATT_54 (Quaternions)  
**Lesson:** ATT_63  
**Pillars (primary → secondary):** P3, P4 (primary); P1, P2, P5 (secondary)  
**Status:** Stable  
**Last updated:** 2026-05-10

---

## Architectural Note

ATT_63 is the most technically concise essay in the collection — a tightly focused mathematical treatment with a two-part structure. The main body stays "within the classical basin," making finiteness explicit without invoking FSM language. The **Afterword** then lifts the lid: the finite overlap operator is the *primary* FSM object; the classical integral is its admissible endogenous extension. The relationship is not approximation but **unfolding** — the classical form compresses a process; the finite operator makes that process explicit.

The essay introduces the **generonic sphere** — the finest measurement distinguishable at a given epoch — as the natural boundary of the index set K. This connects directly to ATT_62's measurement apparatus $\tilde{\mathcal{M}}$ with resolution bound $\rho(\tilde{\mathcal{M}}) > 0$.

**LaTeX note:** the document has a severe structural error — `\begin{document}` appears at line 153, after two `\maketitle` calls. This results in three `\maketitle` calls and a nested document environment. The `\begin{document}` should appear before the first `\maketitle`.

---

## Overview

Convolution, cross-correlation, and autocorrelation are typically presented as algebraic or integral operations over functions or sequences. These formulations compress an underlying sequential process involving displacement, interaction, and accumulation.

ATT_63 makes that implicit process explicit. It defines a **finite overlap operator** $\mathcal{O}(f, g; \delta)$ that captures the essential structure: a bounded index set, a displacement parameter, a local interaction function, and accumulation over ordered steps. Classical convolution and its relatives are recovered as special cases. The aim is to supplement classical formulations with a process-level description useful for computational interpretation, resource estimation, generalisation to non-multiplicative interactions, and analysis of symbolic overlap in high-dimensional systems such as language models.

**Central claim:** *The symbolic form is not primary. It is the compressed trace of a finite ordered process.*

---

## Classical Formulations (as Idealisations)

**Continuous convolution:**
$$(f * g)(t) = \int_{-\infty}^{\infty} f(\tau)\, g(t - \tau)\, d\tau$$

**Discrete convolution** (idealised form):
$$(f * g)(n) = \sum_{k \in \mathbb{Z}} f(k)\, g(n - k)$$

**Cross-correlation:**
$$(f \star g)(n) = \sum_{k \in \mathbb{Z}} f(k)\, g(k + n)$$

**Autocorrelation:**
$$R_f(n) = \sum_{k \in \mathbb{Z}} f(k)\, f(k + n)$$

These are static expressions that conceal a **hidden sequential structure**:
1. Domain is discretised or sampled
2. One function is displaced relative to the other
3. Local interactions are computed at each displacement
4. Interactions are accumulated to produce an output value

Any actual computation must instantiate these steps explicitly — storing intermediate values, traversing indices in order, evaluating pairwise interactions repeatedly.

---

## The Finite Overlap Operator

$$\mathcal{O}(f, g; \delta) = \sum_{k \in K} I\big(f(k),\, g(k - \delta)\big)$$

| Component | Role |
|-----------|------|
| $f, g$ | Finite sequences or sampled functions |
| $\delta \in \mathbb{Z}$ | Displacement between sequences |
| $K \subset \mathbb{Z}$ | **Finite** index set — bounded domain of summation |
| $I : \mathbb{R} \times \mathbb{R} \to \mathbb{R}$ | Local interaction function — not necessarily multiplication |
| $\sum$ | Accumulation over ordered steps |

The finiteness of $K$ is essential: any realisable computation operates over a bounded set of indices. The summation over $\mathbb{Z}$ in classical forms is an idealisation. The finite overlap operator makes the bounded domain explicit through its parameter $K$.

### Recovery of Classical Cases

Let $\tilde{g}(k) = g(-k)$ (time reversal). Then:

| Operation | Finite overlap form | Interaction |
|-----------|---------------------|-------------|
| Convolution $(f * g)(n)$ | $\mathcal{O}(f, \tilde{g}; n)$ | $I(x,y) = x \cdot y$ |
| Cross-correlation $(f \star g)(n)$ | $\mathcal{O}(f, g; -n)$ | $I(x,y) = x \cdot y$ |
| Autocorrelation $R_f(n)$ | $\mathcal{O}(f, f; -n)$ | $I(x,y) = x \cdot y$ |

Classical convolution is a *special case* of $\mathcal{O}$ — restricted to multiplicative interaction and extended (by idealisation) to infinite index sets.

---

## Beyond Multiplication: Generalised Interaction

The operator allows $I$ to be any measurable interaction:

| $I(x,y)$ | Interpretation |
|-----------|---------------|
| $x \cdot y$ | Classical linear convolution |
| $\max(0, x + y)$ | Thresholded additive overlap |
| $\mathbf{1}[x = y]$ | Symbolic equality / set intersection |
| $\exp(-\|x - y\|^2)$ | Similarity kernel |
| $\|x - y\|^2$ | Squared distance / displacement cost |

This generality extends the operator beyond signal processing — to comparing symbolic sequences, measuring structural overlap in representational spaces, and any domain where pairwise interaction between positioned elements is meaningful.

---

## Temporal Unfolding Interpretation

Define $C(n) = \mathcal{O}(f, g; n)$. Then $C(n)$ is not merely a value — it is the result of a finite sequence of operations indexed by $n$.

The sequence $\{C(n)\}_{n \in \mathbb{Z}}$ is a **trajectory of interaction states**. Each step in $n$ corresponds to a new configuration of overlap between $f$ and $g$. Total operation count: $|K| \cdot |N|$ pairwise interactions, where $N$ is the set of output indices.

**Connection to ATT_52 (FPU):** the temporal unfolding of $\{C(n)\}$ is Finite Process Unfolding applied to convolution — each displacement $n$ is one step of the unfolding, generating a new measured interaction state.

This reframes convolution as a **process evolving over discrete states**, rather than a static functional mapping.

---

## Multi-Basin Interaction

Let $\{T_i\}_{i=1}^m$ be a finite family of templates, and $X$ an input sequence:

$$Y(n) = \sum_{i=1}^m w_i \sum_{k \in K} I\big(T_i(k),\, X(n - k)\big)$$

Each $T_i$ acts as an interaction template with weight $w_i$. The result $Y(n)$ reflects combined interaction across multiple structures — a **finite superposition of overlap processes** analogous to multi-template matching or attention-like pooling.

---

## Application: Symbolic Overlap in LLMs

For texts $A$ and $B$ mapped into vector representations $V_A, V_B \subset \mathbb{R}^d$ (e.g., activation vectors across layers):

**Projected overlap:**
$$R(A, B) = \Pi\left(V_A \cap V_B\right)$$

where $V_A \cap V_B$ represents overlap in representation space and $\Pi$ projects into a measurable low-dimensional subspace.

**Conjecture of Resonance** — the resonance volume across layers $\ell$, positions $k$, and displacement $\delta$:

$$\mathrm{Res}(A, B) = \sum_{\ell=1}^L \sum_{k \in K_\ell} I\left(h_\ell^{(A)}(k),\; h_\ell^{(B)}(k - \delta)\right)$$

Predictions:
- High resonance implies high structural overlap in the model's internal representations
- Resonance profiles are **invariant** under meaning-preserving paraphrases (empirical prediction)
- Resonance profiles change under permutations or structural perturbations

This yields a **testable hypothesis for LLM interpretability**: symbolic overlap can be measured without reconstructing semantics.

**Connection to ATT_60:** the layerwise sum in $\mathrm{Res}(A,B)$ is structurally identical to the layerwise generalization cascade $G^{\mathbb{M}}(x) = \frac{1}{K}\sum_\ell G_\ell^{\mathbb{M}}(x)$ — the same multi-scale accumulation pattern applied to structural overlap rather than prediction stability.

---

## Afterword: Boundary Conditions and FSM

The Afterword explicitly lifts the essay into the FSM frame, introducing concepts not deployed in the main text.

### The Generonic Sphere

In FSM, every symbolic operation occurs within a **bounded container**. The boundary corresponds to the **generonic sphere** — the finest measurement distinguishable at a given epoch. Within this sphere, symbols are produced directly by *exogenous* generonic events (measurements at the boundary). Beyond it, structure is *inferred* via *endogenous* generonic events (modelling within the symbolic space).

**Connection to ATT_62:** the generonic sphere is the operational realisation of $\rho(\tilde{\mathcal{M}}) > 0$ — the resolution bound of the measurement apparatus. The finite index set $K$ bounded by the generonic sphere is the $\Sigma$ (admissible symbol space) of ATT_62 applied to signal processing.

### Exogenous vs Endogenous Operators

The finite overlap operator $\mathcal{O}$ with finite $K$ bounded by the generonic sphere is an **exogenous** operator — it operates within directly measurable reach. The classical convolution integral is an **endogenous projection** — an inference that extrapolates from measured finite overlaps to an idealised continuum.

This resolves a longstanding tension: how can a finite symbolic system represent infinite or continuous structures? The answer: it does not measure them directly. It **models them endogenously** from boundary measurements. The classical integral is not primary; it is a stable compression of a finite procedure followed by an admissible inference.

### The Primary Object

> *The finite overlap operator $\mathcal{O}$ is not merely a computational approximation to an idealised convolution. It is, within the FSM frame, the primary object. The classical integral is its admissible endogenous extension. The relationship between them is not one of approximation but of unfolding: the classical form compresses a process; the finite operator makes that process explicit.*

---

## Re-style Checklist (LaTeX)

- [ ] **PRIORITY: `\begin{document}` at wrong position** — appears at line 153 after two `\maketitle` calls; move `\begin{document}` to before the first `\maketitle`; this creates a nested document environment and three `\maketitle` calls (lines 93, 150, 155)
- [ ] **`\textbf\textbf{}`** on secondary title page — nested bold; correct to `\textbf{}`
- [ ] **`{\textit\textbf{First Edition}}`** — fix to `{\textit{\textbf{First Edition}}}`

---

## Cross-References

| Essay / Lesson | Connection |
|---|---|
| ATT_52 | Finite Process Unfolding: temporal unfolding of $\{C(n)\}_{n}$ is FPU applied to convolution — each displacement $n$ is a step of the unfolding generating a new interaction state; the process-level description of O is FPU instantiated |
| ATT_51 | Non-Commutativity / Temporal Trace Theorem: classical convolution with $I(x,y) = x \cdot y$ is commutative; cross-correlation (without reversal) is not — the ordering of $f$ vs $\tilde{g}$ matters; ATT_51's non-commutativity analysis applies to choices of $I$ and displacement direction |
| ATT_54 | FSM Quaternions: same FSM series; both reframe classical mathematical objects (quaternion multiplication, convolution integral) as finite processes with explicit step structure |
| ATT_53 | Bayesian Unfolding: the sequential traversal over $k \in K$ in $\mathcal{O}$ is the same ordered-cost structure as ATT_53's pipe operator — each pairwise interaction carries a resource cost |
| ATT_62 | Measurement Constraint Thesis: generonic sphere (Afterword) is the operational realisation of $\rho(\tilde{\mathcal{M}}) > 0$; exogenous/endogenous distinction maps onto ATT_62's measurement-admissible vs formally-admissible distinction; finite $K$ bounded by generonic sphere corresponds to admissible $\Sigma$ |
| ATT_60 | Geofinite Learning: resonance volume $\mathrm{Res}(A,B) = \sum_\ell \sum_{k \in K_\ell} I(h_\ell^{(A)}, h_\ell^{(B)})$ is the same layerwise accumulation pattern as the generalization cascade $G^{\mathbb{M}} = \frac{1}{K}\sum_\ell G_\ell^{\mathbb{M}}$ |
| ATT_08 | Geofinitism — Measurement-First: "equations represent compressed traces of transformations" (Discussion) is M = (v, ε, P) applied to symbolic expressions; the classical integral is the v; the finite procedure is the trace; provenance records which procedure |

---

*Kevin R. Haylett — School of Geofinitism*  
*Simul Pariter.*
