# ATT_53 — Bayesian Inference: A Finite Process Unfolding

**College:** College of Attralucian Studies  
**Lesson ID:** ATT_53  
**Source essay:** ATT_53 — *Bayesian Inference: A Finite Process Unfolding*  
**Level:** Advanced  
**Prerequisites:** ATT_08; ATT_28; ATT_52 (strongly recommended — ATT_53 applies FPU as established in ATT_52); background in probability theory and Bayesian inference  
**Next lesson:** ATT_54 (TBD)

---

## Learning Outcomes

By the end of this lesson you will be able to:

1. Explain why the standard Bayes equation is a symbolic compression and what it compresses
2. State the FPU reinterpretation of the pipe symbol `|` as a temporal arrow with a memory cost
3. Apply all seven FPU steps to the Bayes equation $P(H \mid D) = P(D \mid H) P(H) / P(D)$
4. Describe the two sequential experiments and the memory commitment that the equation compresses
5. Compute the process cost lower bound $\text{Cost} \geq (2n+2) \cdot \Delta M$ for $n = |\mathcal{H}|$
6. State the admissibility condition for Bayesian inference and explain why improper priors violate it
7. Describe the geometric picture: hypothesis manifold, prior as diffuse state, posterior as contracted state
8. Explain sequential Bayesian updating as manifold traversal and convergence as basin attraction
9. Explain the difference between the synchronic and diachronic readings of $P(A \mid B)$
10. Connect the Bayesian FPU analysis to all five Pillars

---

## 1. The Compression Problem in Bayesian Statistics

The standard Bayes equation is one of the most compactly expressed — and most pedagogically problematic — results in quantitative reasoning:

$$P(H \mid D) = \frac{P(D \mid H) \cdot P(H)}{P(D)}$$

For students trained in frequentist methods, this equation is routinely misread: the posterior is interpreted as a frequency; the prior is treated as arbitrary or subjective; the conditionality is read synchronically ("the probability of H given that D is also the case") rather than sequentially ("the probability of H after D was observed, recorded, and stored").

The essay's diagnostic claim: these errors are not failures of intelligence. They are **failures induced by notation**. The Bayes equation compresses a sequential experimental procedure into a static relation — and what is lost in that compression is precisely what makes Bayesian reasoning difficult to grasp.

### What the Equation Hides

The expression $P(H \mid D)$ conceals:
1. A first finite experiment that bounds and measures a hypothesis space
2. A mandatory memory commitment — the output of the first experiment must be stored
3. A second finite experiment that inherits the stored state and generates data
4. A geometric contraction of the hypothesis manifold

None of these appear in the symbolic form. FPU recovers all of them.

---

## 2. The Symbolic Frame and the Admissibility Condition

### The Symbolic Frame

Following ATT_52's FPU convention, the entire analysis operates within the **symbolic frame**: no appeal to entities beyond the boundary at which symbols are formed. Each probability value is treated as the outcome of a finite measurement act — a generonic event.

### The Admissibility Precondition

Before any Bayesian reasoning can proceed, an **admissibility condition** must be satisfied:

> The hypothesis space $\mathcal{H} = \{H_1, H_2, \ldots, H_n\}$ must be **finite, enumerable, and bounded** before the first experiment begins.

This is not a technical convenience. It is a container requirement: without a finite, closed $\mathcal{H}$, the first measurement act has no definite output, and the second experiment has no defined state to inherit.

**Pillar I connection:** $\mathcal{H}$ is the geometric container within which all subsequent measurement acts take place. The container must be established before it can be measured.

---

## 3. The Seven FPU Steps Applied

### Step 1: Compression Boundary

The symbolic object:
$$S = P(H \mid D) = \frac{P(D \mid H) \cdot P(H)}{P(D)}$$

This is the compression boundary. The task: reconstruct the admissible generating procedure $\mathcal{P}(S)$ — the finite sequential process that produced this compressed trace.

### Step 2: Compression Type

$S$ is a **sequential composition** compressed into a static ratio. The pipe symbol `|` appears twice with different meanings:
- In $P(D \mid H)$: conditioning on a *stored result* from Experiment 1
- In $P(H \mid D)$: a *temporal sequencing marker* — after $D$ was produced

The essay's key claim: both uses of `|` are suppressed by the notation.

### Step 3: The Sequential Procedure

**Experiment 1 — Prior Measurement Act:**

| Sub-step | Action | Cost |
|----------|--------|------|
| 1a | Bound and enumerate $\mathcal{H} = \{H_1, \ldots, H_n\}$ | $n \cdot \Delta M$ |
| 1b | Assign prior probabilities $P(H_i)$ via finite, completable procedure | $\geq \Delta M$ |
| 1c | Store result as intermediate state $\sigma_1 = \{P(H_i)\}_{i=1}^{n}$ | storage cost |

**Memory Commitment:**
$\sigma_1$ must persist between experiments. This is not passive — it imposes a minimum storage cost proportional to $|\mathcal{H}|$ and the precision of each $P(H_i)$. Without this storage, Experiment 2 cannot proceed.

**Experiment 2 — Likelihood Measurement Act:**

| Sub-step | Action | Cost |
|----------|--------|------|
| 2a | Retrieve stored $\sigma_1$ | — |
| 2b | Generate data $D$; evaluate $P(D \mid H_i)$ for each $H_i$ (tethered to $\sigma_1$) | $n \cdot \Delta M$ |
| 2c | Compute marginal: $P(D) = \sum_i P(D \mid H_i) P(H_i)$ | $\Delta M$ |
| 2d | Apply Bayes' rule; output $\sigma_2 = \{P(H_i \mid D)\}_{i=1}^n$ | — |

**Critical constraint:** the hypothesis space cannot be revised during Experiment 2. It was fixed in Experiment 1. Revising $\mathcal{H}$ mid-procedure is a re-initialisation of the manifold, not a Bayesian operation.

### Step 4: State Requirements

| State | Content | When required |
|-------|---------|---------------|
| $\mathcal{H}$ | Hypothesis enumeration | Before Experiment 1; inherited by Experiment 2 |
| $\sigma_1$ | Prior distribution | Between experiments |
| $P(D \mid H_i)$ | Intermediate likelihood values | During Experiment 2 |
| $P(D)$ | Marginal normalisation constant | At end of Experiment 2 |

None of these appear in $S$.

### Step 5: Process Cost

$$\text{Cost}(\mathcal{P}(S)) \geq (2n + 2) \cdot \Delta M$$

where $n = |\mathcal{H}|$. The four terms:
- Bounding $\mathcal{H}$: $n$ distinctions
- Completing Experiment 1: 1 act
- Evaluating likelihoods: $n$ acts
- Computing the marginal: 1 act

**Consequence:** cost scales **linearly** with hypothesis space size. A Bayesian inference over a 1,000-hypothesis space has a minimum process cost of $2{,}002 \cdot \Delta M$. The static expression $S$ is silent on this.

### Step 6: Admissibility Test

**Admissible when:**
- $\mathcal{H}$ is finite and enumerable before Experiment 1
- At least one $P(H_i) > 0$ (non-vacuous container)
- Storage of $\sigma_1$ is feasible within the available symbolic container
- Experiment 2 is independent of Experiment 1 except through inherited $\mathcal{H}$ and $\sigma_1$

**Inadmissible case — Improper Priors:**

An improper prior is a prior distribution over an **unbounded** hypothesis space (e.g., uniform over all real numbers). Under FSM, this is not a technical inconvenience — it is a **container violation**:

> The first experiment has no finite boundary and therefore no admissible output. The intermediate state $\sigma_1$ cannot be formed. Experiment 2 cannot proceed.

Improper priors are the Bayesian analogue of the Banach-Tarski decomposition (ATT_46) — a procedure that appears to work algebraically but violates the admissibility conditions of a finite measurement system.

### Step 7: Restated Expression

> $P(H \mid D)$ is a compressed trace of the following: a finite hypothesis container was established and measured (Experiment 1); the result was stored as an intermediate state (memory commitment); a second independent experiment was conducted within the same container, tethered to the stored state (Experiment 2); the hypothesis manifold was contracted by the joint evidence of both experiments (posterior).

> **The pipe $\mid$ in $P(H \mid D)$ does not mean "given D simultaneously." It means: after D was produced and the intermediate state was consulted. It is a temporal arrow. It is a "then", not a "given".**

---

## 4. The Geometric Picture

The FPU analysis suggests a geometric interpretation the algebraic notation suppresses entirely.

### The Hypothesis Manifold

Let the hypothesis space $\mathcal{H}$ define a finite manifold $\mathcal{M}$, where each point corresponds to a hypothesis and position is weighted by probability mass.

**Prior state $\sigma_1$:** diffuse support across $\mathcal{M}$ — broad uncertainty, many hypotheses plausible.

**Experiment 2 — Geometric Contraction:** the likelihood function $P(D \mid H)$ selects against regions of $\mathcal{M}$ inconsistent with $D$. The manifold is deformed: regions with high likelihood gain mass, regions with low likelihood lose it.

**Posterior state $\sigma_2$:** contracted support within $\mathcal{M}$ — evidence has narrowed the hypothesis space.

### What the Geometry Reveals

The two experiments are **not interchangeable**: swapping their order produces a different $\sigma_1$ and therefore a different posterior. Sequential structure is constitutive — this is the Temporal Trace Theorem (ATT_51) applied to probability.

The posterior is **not a rescaled prior**: it is a geometrically contracted state of the same manifold, produced by a genuinely distinct finite act.

Improper priors correspond to **unbounded manifolds**: the contraction operation of Experiment 2 has no admissible domain to act upon.

---

## 5. Sequential Updating as Manifold Traversal

For sequential Bayesian updating, each posterior $\sigma_k$ becomes the prior for the next experiment:

$$\sigma_k(H) \propto P(D_k \mid H) \cdot \sigma_{k-1}(H)$$

### FPU Reading of Sequential Updating

This is not a sequence of algebraic rescalings. It is a **trajectory** in the space of probability distributions over $\mathcal{H}$:

$$\sigma_0 \xrightarrow{D_1} \sigma_1 \xrightarrow{D_2} \sigma_2 \xrightarrow{D_3} \sigma_3 \xrightarrow{\cdots} \sigma_\infty$$

### Key Properties (Invisible in Algebraic Notation)

**Ordering matters:** the trajectory is path-dependent when experiments interact. Intermediate states are not computational artifacts — they are the actual history of the process.

**Convergence is basin attraction:** under mild conditions, the trajectory converges to a stable region of $\mathcal{M}$ regardless of initial prior $\sigma_0$. Bayesian consistency, viewed geometrically, is a basin structure:
- The **attractor** = the region of $\mathcal{H}$ supported by the accumulated data
- The **prior** = the initial position in the basin, not the destination

**Memory is structural:** each $\sigma_k$ is a compression of the full experimental history $\{D_1, \ldots, D_k\}$. This compression is only admissible if $\mathcal{H}$ was established at the outset and held fixed throughout the trajectory.

**Connection to ATT_06 (Geodesic Fractal Model):** the trajectory $\sigma_0 \to \sigma_1 \to \cdots$ is a geodesic in the hypothesis manifold; the attractor region is a basin in ATT_06's sense. FPU provides the procedural grounding for this geometric picture.

---

## 6. The Pipe Symbol: Synchronic vs. Diachronic

### Standard (Synchronic) Definition

$$P(A \mid B) = \frac{P(A \cap B)}{P(B)}$$

This is a ratio between two probabilities both defined on the same static space. There is no time. Both $A$ and $B$ coexist simultaneously.

### FPU (Diachronic) Reading

In the Bayesian inference context, the synchronic reading is a **notational fiction**:

| Quantity | Synchronic reading | FPU reading |
|----------|-------------------|-------------|
| $P(H)$ | A probability value in a static space | Output of a first finite experiment |
| $P(D \mid H)$ | Conditional probability in a static space | Second experiment tethered to stored $\sigma_1$ |
| $P(H \mid D)$ | Conditional probability in a static space | Final contracted state after both experiments |
| The pipe $\mid$ | Conditioning operator | Tethering symbol — temporal sequencing marker |

The pipe marks the point at which a second experiment is tethered to the stored output of a first.

**Pedagogical implication:** Bayesian inference should be taught with the diachronic reading as primary. The synchronic ratio definition is a legitimate compression — admissible in certain contexts — but it suppresses the sequential structure that makes Bayesian reasoning hard to grasp.

---

## 7. All Five Pillars Applied

### Pillar I — Geometric Container Space

The hypothesis manifold $\mathcal{M}$ is the FSM geometric container. Prior and posterior are positions within this container — distributions over its points. The container must be established (Experiment 1) before it can be measured (Experiment 2). Contraction through updating is Dynamic Flow within a finite container.

### Pillar II — Approximations and Measurements (primary)

Each probability value is a finite measurement outcome with bounded precision, not an ideal real number. $P(H_i)$ carries the uncertainty of the estimation procedure that produced it. The Bayesian formalism typically suppresses this — FPU makes it explicit. The prior is not a belief; it is a measured quantity with provenance.

### Pillar III — Dynamic Flow (primary)

The Bayesian procedure is irreducibly sequential: Experiment 1 → memory commitment → Experiment 2. This temporal ordering is constitutive, not incidental. The pipe `|` is a dynamic flow marker — the process flows from prior measurement to posterior contraction. Sequential Bayesian updating is a trajectory through the manifold; convergence is the terminal state of that trajectory.

### Pillar IV — Useful Fiction / Contextual Validity

The synchronic definition $P(A \mid B) = P(A \cap B) / P(B)$ is a useful fiction: a compression of the diachronic experimental structure into a static ratio. This compression is valid (admissible) when the experimental procedure underlying it is admissible and when the fiction produces stable, reproducible predictions. It becomes inadmissible when the process structure it suppresses is what is at issue — as in pedagogy, in the design of updating procedures, or in the assessment of improper priors.

### Pillar V — Finite Reality

Bayesian inference, properly construed, is a finite process with a finite cost, operating within a bounded container. Its extension to continuous hypothesis spaces, improper priors, and limiting distributions should be treated as approximations to this finite reality — not as the fundamental case. The prior is not a distribution over all real numbers; it is a compression of a finite estimation procedure. The posterior is not an ideal contraction; it is a bounded measurement act with cost $\geq (2n+2) \cdot \Delta M$.

---

## 8. Summary

| Concept | Classical Bayesian | FPU / FSM |
|---------|-------------------|-----------|
| Bayes equation | Static relation between four probability values | Compressed trace of two sequential experiments + memory |
| Prior $P(H)$ | Pre-existing belief or frequency | Output of a first finite measurement act |
| Pipe $\mid$ | Conditioning operator (synchronic) | Temporal arrow with memory cost (diachronic) |
| Posterior $P(H \mid D)$ | Updated belief | Contracted state of hypothesis manifold |
| Sequential updating | Algebraic rescaling | Trajectory in hypothesis manifold |
| Convergence | Bayesian consistency theorem | Basin attraction in geometric manifold |
| Improper priors | Technical inconvenience | Container violation — inadmissible |
| Process cost | Not asked | $\geq (2n+2) \cdot \Delta M$ |

---

## Connections to Other Lessons

| Lesson | Connection |
|--------|-----------|
| ATT_52 | Finite Process Unfolding: ATT_53 is the first application of the FPU method; all seven steps are applied directly; ATT_52 should precede this lesson |
| ATT_51 | Non-Commutativity: the two Bayesian experiments are non-interchangeable (swapping order yields a different posterior) — this is an instance of the Temporal Trace Theorem; sequential structure is constitutive |
| ATT_28 | Commitment, Consensus, Admissibility: the hypothesis container $\mathcal{H}$ must be committed before Experiment 1; improper priors violate the admissibility condition; the Bayesian procedure is admissible iff its container conditions are met |
| ATT_08 | Geofinitism — Measurement-First: the prior is a measurement outcome, not a belief; every probability carries provenance; the pipe is a measurement sequencing marker |
| ATT_46 | Banach-Tarski: improper priors are the Bayesian analogue of Banach-Tarski decomposition — algebraically coherent but violating finite container admissibility |
| ATT_06 | Geodesic Fractal Model of LLMs: sequential updating as manifold traversal; convergence as basin attraction; FPU provides the procedural grounding for ATT_06's attractor framework |

---

*Kevin R. Haylett — School of Geofinitism*  
*Simul Pariter.*
