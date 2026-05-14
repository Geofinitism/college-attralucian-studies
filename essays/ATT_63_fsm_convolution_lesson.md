# ATT_63 — Finite Overlap and Convolution: A Finite Symbolic Mechanics Treatment

**College:** College of Attralucian Studies  
**Lesson ID:** ATT_63  
**Source essay:** ATT_63 — *Finite Overlap and Convolution: A Finite Symbolic Mechanics Treatment*  
**Level:** Advanced / Technical  
**Prerequisites:** ATT_52 (FPU — essential); ATT_51 (Non-Commutativity — recommended); ATT_54 (FSM Quaternions — recommended); ATT_62 (Measurement Constraints — for Afterword material); background in discrete mathematics and signal processing  
**Next lesson:** ATT_64 (TBD)

---

## Learning Outcomes

By the end of this lesson you will be able to:

1. State the classical definitions of discrete convolution, cross-correlation, and autocorrelation
2. Identify the hidden sequential structure underlying each classical formulation
3. Define the finite overlap operator $\mathcal{O}(f, g; \delta)$ and explain the role of each component
4. Show how convolution, cross-correlation, and autocorrelation are recovered as special cases of $\mathcal{O}$
5. Give at least three examples of non-multiplicative interaction functions $I$ and explain what each measures
6. Explain the temporal unfolding interpretation: why $\{C(n)\}$ is a trajectory of interaction states rather than a static mapping
7. Compute the total operation count for a finite overlap computation
8. Define the multi-basin interaction operator and explain how it generalises to weighted template superposition
9. Define the resonance volume $\mathrm{Res}(A, B)$ and state the three resonance predictions for LLM interpretability
10. Explain the generonic sphere and why it is the natural bound for the index set $K$
11. Distinguish exogenous from endogenous operators in the FSM frame and explain why the finite overlap operator is primary
12. State the central claim of the essay in one sentence and explain what "compressed trace" means
13. Apply all five Pillars to the FSM reframing of convolution

---

## 1. Classical Convolution and Its Hidden Structure

### The Definitions

For sequences $f, g : \mathbb{Z} \to \mathbb{R}$:

**Discrete convolution (idealised):**
$$(f * g)(n) = \sum_{k \in \mathbb{Z}} f(k)\, g(n - k)$$

**Cross-correlation:**
$$(f \star g)(n) = \sum_{k \in \mathbb{Z}} f(k)\, g(k + n)$$

**Autocorrelation:**
$$R_f(n) = \sum_{k \in \mathbb{Z}} f(k)\, f(k + n)$$

These are *static expressions*. They compress what is, in any actual computation, a sequential process.

### The Hidden Steps

Any realisation of these operations requires:

1. **Sampling** — the domain is discretised at finite resolution
2. **Displacement** — one function is shifted relative to the other by parameter $n$
3. **Local interaction** — at each position $k$, values $f(k)$ and $g(n-k)$ are combined
4. **Accumulation** — these interactions are summed to produce the output at $n$

Each output index $n$ therefore corresponds to a **finite process** involving:
- Storage of intermediate values
- Ordered traversal of indices $k$
- Repeated evaluation of pairwise interactions

The summation over $\mathbb{Z}$ is an idealisation. Real computation operates over a finite, practically sufficient bound.

**Connection to ATT_52 (FPU):** this is the core observation of Finite Process Unfolding — equations compress finite ordered procedures; the process is primary.

---

## 2. The Finite Overlap Operator

### Definition

$$\mathcal{O}(f, g; \delta) = \sum_{k \in K} I\big(f(k),\; g(k - \delta)\big)$$

| Component | Role |
|-----------|------|
| $f, g$ | Finite sequences or sampled functions |
| $\delta \in \mathbb{Z}$ | Displacement between sequences |
| $K \subset \mathbb{Z}$ | **Finite** index set — the bounded domain of summation |
| $I : \mathbb{R} \times \mathbb{R} \to \mathbb{R}$ | Local interaction function |
| $\sum_{k \in K}$ | Accumulation over ordered steps |

**The finiteness of $K$ is essential.** It is not a computational convenience — it is the honest description of any realisable operation. No physical computation sums over an infinite index set.

### Four Explicit Commitments

By writing $\mathcal{O}$ rather than the classical integral, the operator makes four commitments explicit that the classical form leaves implicit:

| Commitment | Classical form | $\mathcal{O}$ |
|-----------|----------------|----------------|
| Domain of summation | $\mathbb{Z}$ (infinite, idealised) | $K \subset \mathbb{Z}$ (finite, declared) |
| Interaction | Multiplication (implicit) | $I$ (explicit, arbitrary) |
| Displacement | Built into index shift | $\delta$ (named parameter) |
| Sequential structure | Compressed into $\sum$ | Made explicit through ordered traversal |

---

## 3. Recovery of Classical Cases

Let $\tilde{g}(k) = g(-k)$ denote the time-reversed sequence. Classical operations are special cases of $\mathcal{O}$ with $I(x, y) = x \cdot y$:

$$\text{Convolution: } (f * g)(n) = \mathcal{O}(f,\, \tilde{g};\, n)$$
$$\text{Cross-correlation: } (f \star g)(n) = \mathcal{O}(f,\, g;\, -n)$$
$$\text{Autocorrelation: } R_f(n) = \mathcal{O}(f,\, f;\, -n)$$

**The key insight:** convolution requires time-reversal of $g$ because the index shift $g(n-k)$ reverses the function before sliding it. Cross-correlation does not reverse — it slides $g$ directly. This is why convolution is commutative ($f * g = g * f$) while cross-correlation is not ($f \star g \neq g \star f$ in general).

**Connection to ATT_51 (Non-Commutativity):** the reversal step in convolution is an instance of the ordering sensitivity that ATT_51 analyses through the Temporal Trace Theorem. The presence or absence of time-reversal changes the operation's algebraic properties.

---

## 4. Beyond Multiplication: Generalised Interactions

Classical convolution fixes $I(x, y) = x \cdot y$. The finite overlap operator permits any measurable interaction:

| $I(x, y)$ | Interpretation | Use case |
|-----------|---------------|----------|
| $x \cdot y$ | Multiplicative linear interaction | Signal convolution, filtering |
| $\max(0, x + y)$ | Thresholded additive overlap | Relu-like interaction |
| $\mathbf{1}[x = y]$ | Symbolic equality | Set intersection, pattern matching |
| $\exp(-\|x - y\|^2)$ | Gaussian similarity kernel | Kernel methods, smoothing |
| $\|x - y\|^2$ | Squared displacement cost | Distance-based overlap |

The choice of $I$ determines what "overlap" means in each domain. Convolution defines overlap as scaled contribution; equality indicator defines overlap as exact match; similarity kernel defines overlap as proximity.

**Geofinite reading:** the choice of $I$ is a **committed parameter** (ATT_28) — declared before computation, not inferred post hoc. Different choices of $I$ yield different but equally admissible overlap measures.

---

## 5. Temporal Unfolding: $\{C(n)\}$ as a Trajectory

Define $C(n) = \mathcal{O}(f, g; n)$. The sequence $\{C(n)\}_{n \in N}$ is a **trajectory of interaction states** — not a static function evaluated at points, but a sequence generated by a finite process.

### What Changes with Each $n$

At each output index $n$, a fresh traversal of $k \in K$ is required:
- The displacement $\delta = n$ changes
- The pairing $(f(k), g(k - n))$ changes for every $k$
- The accumulation produces a new value $C(n)$

**Total resource cost:** $|K| \cdot |N|$ pairwise evaluations of $I$, where $N$ is the set of output indices. This is the explicit finite cost of convolution — invisible in the classical summation notation.

**Connection to ATT_52 (FPU):** the unfolding of $C(n)$ as $n$ varies is FPU instantiated. Each displacement step is one stage of the process, generating a new measured overlap state. The trajectory $\{C(n)\}$ is the complete finite unfolding.

**Connection to ATT_53 (Bayesian Unfolding):** the sequential traversal over $k \in K$ at each $n$ is the same ordered-cost structure as ATT_53's pipe operator — each step has a resource cost, and the accumulation carries memory of prior steps.

---

## 6. Multi-Basin Interaction

Let $\{T_i\}_{i=1}^m$ be a finite family of templates and $X$ an input sequence. The **weighted superposition** of overlap processes:

$$Y(n) = \sum_{i=1}^m w_i \sum_{k \in K} I\big(T_i(k),\; X(n - k)\big)$$

**Interpretation:**
- Each $T_i$ is an interaction template — a pattern being searched for in $X$
- $w_i$ controls the contribution of template $i$ to the output
- $Y(n)$ reflects **combined interaction across multiple structures** simultaneously

This is a finite superposition of overlap processes — analogous to multi-head attention in transformers, or multi-filter convolution in CNNs, expressed at the level of the finite overlap operator.

**Connection to ATT_60 (Learning):** $Y(n)$ as a weighted sum over templates is the same architecture as the Geofinite learning objective $\mathcal{J}^{\mathbb{M}}$ — multiple components combined with weights toward a measured output.

---

## 7. Application: Symbolic Overlap in LLMs

### Projected Overlap

For texts $A$ and $B$ with vector representations $V_A, V_B \subset \mathbb{R}^d$:

$$R(A, B) = \Pi\left(V_A \cap V_B\right)$$

where $\Pi$ projects shared representational directions into a measurable low-dimensional subspace. This provides a **measurable estimate of structural interaction** under a given model — without claiming to reconstruct meaning.

### Resonance Volume

$$\mathrm{Res}(A, B) = \sum_{\ell=1}^L \sum_{k \in K_\ell} I\left(h_\ell^{(A)}(k),\; h_\ell^{(B)}(k - \delta)\right)$$

Summing over layers $\ell$ and positions $k$, with layer-specific index sets $K_\ell$, using interaction $I$ (e.g., cosine similarity).

**Three testable predictions:**

| Prediction | Status |
|-----------|--------|
| High resonance ↔ high structural overlap in internal representations | Operational definition |
| Resonance profile invariant under meaning-preserving paraphrases | Empirical prediction |
| Resonance profile changes under permutation or structural perturbation | Empirical prediction |

The resonance conjecture yields a **testable hypothesis for LLM interpretability**: structural overlap between texts can be measured geometrically, without reconstructing semantics from internal activations.

**Connection to ATT_60:** $\mathrm{Res}(A,B) = \sum_\ell \sum_k I(h_\ell^{(A)}, h_\ell^{(B)})$ is structurally identical to the layerwise generalization cascade $G^{\mathbb{M}}(x) = \frac{1}{K}\sum_\ell G_\ell^{\mathbb{M}}(x)$ — the same multi-scale accumulation pattern applied to overlap rather than stability.

---

## 8. The Afterword: FSM Frame and Generonic Sphere

The Afterword lifts the essay from the "classical basin" into the full FSM frame. The main essay deliberately stays within conventional mathematical language; the Afterword reveals the deeper structure.

### The Generonic Sphere

In Finite Symbolic Mechanics, every symbolic operation occurs within a bounded container. The natural boundary of the index set $K$ is the **generonic sphere** — the finest measurement distinguishable at a given epoch.

- **Within the generonic sphere:** symbols are produced by *exogenous* generonic events — direct measurements at the boundary
- **Beyond the generonic sphere:** structure is *inferred* via *endogenous* generonic events — modelling within the already-established symbol space

**Connection to ATT_62:** the generonic sphere is the operational realisation of $\rho(\tilde{\mathcal{M}}) > 0$ — the resolution bound of the measurement apparatus. The finite $K$ bounded by the generonic sphere is the admissible symbol space $\Sigma$ applied to signal indices.

### Exogenous vs Endogenous Operators

| Operator type | Description | Example |
|--------------|-------------|---------|
| Exogenous | $K$ bounded by generonic sphere; operates within direct measurement reach | $\mathcal{O}(f, g; \delta)$ with finite $K$ |
| Endogenous | Extrapolates from measured finite overlaps to idealised continuum | Classical convolution integral over $\mathbb{R}$ |

The distinction resolves the apparent paradox: how can a finite system represent infinite structures? It does not *measure* them — it *models* them endogenously from boundary measurements. The classical integral is a stable compression of a finite procedure followed by an admissible inference.

### The Primary Relationship

The finite overlap operator is **not** an approximation to the classical integral. The classical integral is the admissible endogenous extension of the finite operator.

> *The relationship between them is not one of approximation but of unfolding: the classical form compresses a process; the finite operator makes that process explicit.*

This is the same move as ATT_59 ($K^{\mathbb{M}}$ is primary; classical $K(x)$ is the useful fiction toward which it tends), ATT_56 (HALT/NO_HALT is primary; classical undecidability is the forward collapse), and ATT_57 ($\mathsf{CTT}_{\mathbb{M}}$ is primary; classical CTT is the forward collapse).

---

## 9. The Central Claim

> **The symbolic form is not primary. It is the compressed trace of a finite ordered process.**

This applies to:
- The summation $\sum_{k \in \mathbb{Z}}$ — compressed trace of bounded sequential accumulation
- The integral $\int_{-\infty}^{\infty}$ — compressed trace of finite sampling and summation plus endogenous extension
- The equation $(f * g)(n) = \sum_k f(k) g(n-k)$ — compressed trace of a displacement-interaction-accumulation procedure

**Connection to ATT_08:** "equations represent compressed traces of transformations" — the Discussion section of ATT_63 echoes this exactly. M = (v, ε, P) applied to equations: v is the symbolic form; ε is the uncertainty from finite sampling and truncation; P is the provenance of the computation procedure.

---

## 10. All Five Pillars Applied

### Pillar I — Finite Index Set as Geometric Container (secondary)

$K \subset \mathbb{Z}$ is the geometric container within which the overlap computation occurs. The displacement parameter $\delta$ moves $g$ through this container. The generonic sphere (Afterword) defines the natural boundary of $K$ — the container edge determined by measurement resolution. The output set $N$ is a second container: the space of overlap values indexed by displacement.

### Pillar II — Interaction as Measurement (secondary)

Each evaluation of $I(f(k), g(k-\delta))$ is a pairwise measurement — the interaction between the value of $f$ at position $k$ and the value of $g$ at position $k - \delta$. The choice of $I$ determines what is being measured. The resonance volume $\mathrm{Res}(A,B)$ is a measurable quantity: a finite sum of layer-position interactions carrying provenance from the model and similarity function used.

### Pillar III — Convolution as Temporal Trajectory (primary)

The sequence $\{C(n)\}_{n \in N}$ is Dynamic Flow — a trajectory of interaction states generated by unfolding the displacement $n$ step by step. This is the core Pillar III move of the essay: reframing a static functional form as an ordered process evolving through states. FPU (ATT_52) is the method; the finite overlap operator is the object.

### Pillar IV — Classical Integral as Useful Fiction (primary)

The classical convolution integral — summation over $\mathbb{Z}$, integration over $\mathbb{R}$ — is a useful fiction: a stable, powerful idealisation that extends finite finite finite processes to infinite domains. It is not wrong; it is the endogenous extension of the finite operator. The finite overlap operator $\mathcal{O}$ is primary; the classical integral is its forward collapse in the limit of infinite $K$ and vanishing discretisation step. This is Pillar IV applied to mathematical analysis.

### Pillar V — Finite Index Set and Finite Operation Count (secondary)

$|K|$ is the fundamental finite quantum of the computation. Total operations: $|K| \cdot |N|$ — a finite count made explicit by the operator's structure. No realisable computation exceeds this bound. The "practically sufficient bound" mentioned in the classical discussion is always finite; $\mathcal{O}$ makes this explicit rather than hiding it in idealised summation notation.

---

## 11. Summary

| Concept | Classical formulation | Geofinite / FSM (ATT_63) |
|---------|----------------------|--------------------------|
| Convolution | $\sum_{k \in \mathbb{Z}} f(k)g(n-k)$ | $\mathcal{O}(f, \tilde{g}; n)$ with finite $K$, $I(x,y) = x \cdot y$ |
| Domain | $\mathbb{Z}$ or $\mathbb{R}$ (infinite, ideal) | $K \subset \mathbb{Z}$ (finite, declared) |
| Interaction | Multiplication (implicit) | $I$ (explicit, arbitrary) |
| Structure | Static functional mapping | Temporal trajectory $\{C(n)\}_{n \in N}$ |
| Resource cost | Hidden | $|K| \cdot |N|$ pairwise interactions (explicit) |
| Classical integral | Primary object | Endogenous extension / useful fiction |
| $\mathcal{O}$ | Approximation | Primary object; classical form is its compression |
| Generonic sphere | Not present | Natural boundary of $K$; connects to $\rho(\tilde{\mathcal{M}}) > 0$ |
| Exogenous/endogenous | Not distinguished | Key distinction in FSM frame |
| LLM application | Not addressed | Resonance volume — testable interpretability hypothesis |

---

## Connections to Other Lessons

| Lesson | Connection |
|--------|-----------|
| ATT_52 | Finite Process Unfolding: $\{C(n)\}$ unfolding is FPU applied to convolution — each displacement step is one stage; temporal unfolding makes the sequential structure of summation explicit |
| ATT_51 | Non-Commutativity: time-reversal in convolution vs direct shift in cross-correlation is the ordering sensitivity analysed in ATT_51; $I(x,y)$ commutativity determines whether $\mathcal{O}(f,g;\delta) = \mathcal{O}(g,f;\delta)$ |
| ATT_54 | FSM Quaternions: same FSM series — both reframe classical mathematical objects (quaternion multiplication, convolution) as finite processes; the derivation-from-axioms method is parallel |
| ATT_62 | Measurement Constraints: generonic sphere (Afterword) is the operational realisation of $\rho(\tilde{\mathcal{M}}) > 0$; exogenous $\mathcal{O}$ maps to measurement-admissible; endogenous classical integral maps to formally-admissible |
| ATT_60 | Geofinite Learning: resonance volume $\mathrm{Res}(A,B)$ is the same layerwise accumulation as the generalization cascade; both are multi-scale sums over representation layers |
| ATT_08 | Measurement-First: "equations represent compressed traces of transformations" — the symbolic form $(f * g)(n)$ is the compressed trace; $\mathcal{O}$ is the explicit procedure; M = (v, ε, P) applies to symbolic expressions as well as measurements |

---

*Kevin R. Haylett — School of Geofinitism*  
*Simul Pariter.*
