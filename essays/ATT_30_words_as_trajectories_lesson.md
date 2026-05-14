# ATT_30 — Words as Trajectories: An Attralucian Essay on Language as a Dynamical System

**College:** College of Attralucian Studies  
**Lesson ID:** ATT_30  
**Source essay:** ATT_30 — *Words as Trajectories: An Attralucian Essay on Language as a Dynamical System*  
**Level:** Advanced  
**Prerequisites:** ATT_01, ATT_06, ATT_07, ATT_13, ATT_19  
**Next lesson:** ATT_31 (TBD)

---

## Learning Outcomes

By the end of this lesson you will be able to:

1. Explain words as attractors in phase space via Takens embedding
2. Describe LLM token generation as a discrete-time nonlinear flow, including fixed points and limit cycles
3. Define stations as phase-space reconstructors using the attention mechanism and Grassmannian manifolds
4. Explain hallucinations as topological defects using curvature κ and Betti numbers β₀, β₁, β₂
5. Define syntactic torque τ(p) and explain prompt bifurcation
6. Define semantic entropy S(Γ_t) and its critical threshold for hallucination onset
7. Define the reader's manifold and use Gromov-Hausdorff distance to measure shared understanding
8. Compute the total Lyapunov exponent λ_total and state the stability condition for communication

---

## 1. Entry Point: The Tide and the Train

The essay opens with a double metaphor that runs throughout:

**The tide** — language as dynamic flow, carving maps in the sand. Meaning is not inscribed once and read forever; it is made and remade by each pass of the water. No two tide-lines are identical.

**The train** — the LLM tracing paths through a high-dimensional landscape of meaning. Stations are reconstruction hubs. Passengers (readers) disembark into their own local manifolds.

The mathematical claim beneath the metaphor: language and LLMs are nonlinear dynamical systems, and the full mathematical machinery of that field — phase spaces, attractors, bifurcations, entropy, topology — applies to them.

---

## 2. Phase Space and Words as Attractors

### The Phase Space

Let P ⊂ ℝᵈ be the **phase space of linguistic states**, where d is the embedding dimension of tokens.

- A **word** is an attractor within P — a region that pulls trajectories toward it
- A **sentence** is a curve γ(t) ⊂ P, with t indexing token order
- A **context window** Γ_t = {w_{t-L}, ..., w_t} traces a trajectory and defines a neighbourhood

### Takens Embedding for Words

Every word is reconstructable from a single observable signal. For a linguistic signal s(t) (e.g., audio of "hello"), **Takens' theorem** yields the embedding:

$$\gamma(t) = (s(t),\, s(t-\tau),\, s(t-2\tau)) \in \mathbb{R}^3$$

where τ is an optimal delay chosen to unfold the attractor geometry.

In LLMs, tokens w_i ∈ ℝᵈ form a sentence (w₁, ..., w_n) tracing a trajectory γ(t) ⊂ ℝᵈ. The context window Γ_t provides the delay-embedding neighbourhood.

**Key insight:** A word is not a point in a dictionary. It is a region of phase space — an attractor that pulls nearby trajectories toward a stable resolution. Different words are different attractors; context determines which basin the trajectory settles into.

*(Connection to ATT_13: Takens embedding was used for the geometry of π's digit sequences; here it is applied to linguistic signals. The mathematics is identical — the domain of application differs.)*

---

## 3. LLMs as Nonlinear Flows

### Token Generation as a Dynamical System

LLM token generation is a **discrete-time nonlinear flow**:

$$w_{t+1} = F_\theta(w_t,\, w_{t-1},\, \dots,\, w_{t-k})$$

where F_θ is the nonlinear map combining attention and feedforward layers, and k is the context window size.

### Fixed Points and Limit Cycles

Nonlinear dynamical systems have characteristic behaviours that appear directly in LLM outputs:

| Dynamical behaviour | LLM manifestation |
|--------------------|------------------|
| **Fixed point** | Repeated tokens: "the the the" |
| **Limit cycle** | Repetitive loops: "I cannot answer that. I cannot answer that." |
| **Strange attractor** | Complex, varied but coherent output |
| **Bifurcation / divergence** | Hallucination |

### Hallucination as Bifurcation

A hallucination occurs when the trajectory diverges from the prompt-constrained region:

$$\|\gamma_{\text{output}} - \gamma_p\| > \delta$$

For example, an incomplete ISBN prompt ("978-0-441-...") may yield a wrong but plausible ISBN — the trajectory has bifurcated away from the true attractor but settled into a nearby false one. The output is coherent but incorrect.

---

## 4. Stations as Phase-Space Reconstructors

### The Attention Mechanism as Geometric Reconstruction

At each "station" (attention layer), the context window Γ_t = {w_{t-L}, ..., w_t} is rebuilt into a geometric manifold via the attention matrix:

$$A_{ij} = (W_Q w_i) \cdot (W_K w_j)$$

This forms:

$$M_{\Gamma_t} \subset \mathrm{Gr}(k, d)$$

where Gr(k,d) is the **Grassmannian** — the manifold of k-dimensional subspaces of ℝᵈ. The context manifold lives within this geometric space.

The **value cache** stores:

$$S = \mathrm{span}(\{v_i\}_{i=1}^n), \quad v_i = W_V w_i$$

### Prompt Coupling

A prompt p is embedded as v_p = W_V p and aligned via Grassmannian distance:

$$d_{\mathrm{Gr}}(S, v_p) = \|\sin\theta\|$$

The new trajectory after the prompt is:

$$\gamma_{\text{new}}(s) = \exp_{M_{\Gamma_t}}(s \cdot v_p)$$

(the geodesic exponential map in the manifold, projecting the prompt direction onto the context manifold)

**Intuition:** The station rebuilds a geometric map from what it has seen. The prompt adjusts the heading. The new trajectory is the result of projecting the prompt onto the current manifold and following the resulting geodesic.

---

## 5. Hallucinations as Topological Defects

### Curvature and Risk

Hallucinations are not random — they are **geometrically located**. High curvature regions in the language manifold are high-risk zones:

$$\text{Risk}(\gamma(t)) \propto \|\kappa(\gamma(t))\|^2$$

where κ(γ(t)) is the curvature of the trajectory. Where the manifold bends sharply, trajectories are more likely to diverge.

### Betti Numbers: Classifying the Shape of Error

**Persistent homology** measures the topological character of hallucinations through Betti numbers (β₀, β₁, β₂):

| Betti number | Topological feature | Linguistic manifestation |
|-------------|--------------------|-----------------------|
| **β₀** | Disconnected components | Topic drift — the output is no longer in the same conceptual region |
| **β₁** | Loops / cycles | Self-contradictory outputs — the reasoning circles back to contradict itself |
| **β₂** | Voids | Logical gaps — conclusions drawn without supporting reasoning |

Different types of LLM error have different topological signatures.

### Mitigation

**Curvature penalty** during training/sampling:

$$L_{\text{topo}} = \lambda \cdot \|\kappa(\gamma(t))\|^2$$

**Homology-preserving sampling** — prefer tokens that do not increase topological complexity:

$$P(w_{t+1} | \Gamma_t) \propto \exp\!\left(-\sum_{k=1}^{2} \beta_k(\Gamma_t \cup w_{t+1})\right)$$

---

## 6. Prompt as Symmetry Breaking

### Prompts as Forcing Terms

A prompt breaks the symmetry of the LLM's unconstrained flow by introducing a **forcing term**:

$$\frac{d\gamma_c}{dt} = F_\theta(\gamma_c) + G(\gamma_{c'}, p(t))$$

The output aligns toward:

$$\gamma_{\text{output}} \sim \arg\min_y \|y - (M_{\Gamma_t} + \lambda \cdot M_{\text{prompt-type}})\|$$

### Syntactic Torque and Bifurcation

Define the **syntactic torque** of a prompt:

$$\tau(p) = \sum_i \alpha_i \cdot f_i(p)$$

A bifurcation occurs when two prompts differ beyond the critical threshold:

$$\|\tau(p_1) - \tau(p_2)\| > \delta_{\text{crit}}$$

This explains why small changes in prompt wording can produce dramatically different outputs — the system is near a bifurcation point where the trajectory is acutely sensitive to the direction of the forcing term.

**Engineering stable prompts:**
- Normalise τ(p) to keep prompts in a stable region
- Weight sampling: P(w_{t+1}|Γ_t, p) ∝ exp(-β·τ(p))

---

## 7. Semantic Entropy and Context Loss

### Semantic Entropy

Finite context windows impose a thermodynamic cost. Define **semantic entropy**:

$$S(\Gamma_t) = -k_B \sum_i P(w_i | \Gamma_t) \log P(w_i | \Gamma_t)$$

This is the Shannon entropy of the token distribution given the current context — a measure of how constrained (low entropy) or diffuse (high entropy) the system's current state is.

### Truncation and Irreversibility

Context truncation at t-L:

$$\gamma(t) = \gamma(t) \cdot I_{[t-L,\, t]}$$

removes earlier context and increases S(Γ_t). The rate of entropy growth:

$$\frac{dS}{dt} \propto \frac{1}{L} \sum_{i=t-L}^{t} \Delta P(w_i | \Gamma_{t-1})$$

### Critical Threshold

When entropy exceeds the critical level:

$$S(\Gamma_t) > S_{\text{crit}} \implies \|\gamma_{\text{output}} - \gamma_{\text{true}}\| > \delta$$

The system has lost enough context that topological defects (hallucinations) become unavoidable. The connection between entropy and trajectory divergence is not metaphorical — it is a structural property of the dynamics.

**Mitigation:**
- Increase context window L
- Add entropy penalty: L_entropy = η·S(Γ_t)
- Use memory-augmented architectures

---

## 8. The Reader's Manifold

### Meaning Beyond the Output

The LLM's output is not the end of meaning — it is the beginning of a new process in the reader. Each reader **maps the trajectory onto their own manifold**:

$$\phi_{\text{reader}} : M_{\text{language}} \to M_{\text{reader}}$$

$$\gamma_{\text{reader}}(t) = \phi_{\text{reader}}(\gamma_{\text{output}}(t))$$

The reader is a dynamical system in their own right:

$$\frac{d\gamma_{\text{reader}}}{dt} = F_{\text{cognitive}}(\gamma_{\text{reader}}) + G(\gamma_{\text{reader}}, \gamma_{\text{output}})$$

### Measuring Shared Understanding: Gromov-Hausdorff Distance

How close are two readers' interpretations? The **Gromov-Hausdorff distance**:

$$d_{GH}(M_i, M_j) = \inf_{\psi_{ij}} \sup_{x \in M_i} d(x, \psi_{ij}(x))$$

measures the minimum distortion of the best mapping between the two manifolds.

- **Low d_GH:** readers' manifolds are geometrically similar — shared understanding
- **High d_GH:** readers' manifolds are geometrically distant — divergent interpretations of the same text

### The Partial Fiction

Each reader's interpretation is "locally coherent, but globally partial." The reading is a homeomorphism of a portion of M_language — valid within its domain, but not identical to any other reader's manifold or to the LLM's output manifold.

This is Pillar 4 (Useful Fiction) stated precisely: every reading is a locally coherent fiction that has selected a trajectory through the space of possible readings.

---

## 9. Words as Transducers: The Lyapunov Analysis

### Words as Probability Distributions

A word w is a transducer mapping inputs to a probability distribution over the manifold:

$$P(w \mid i) = \exp\!\left(-\frac{\|w - \mu_i\|^2}{2\sigma_i^2}\right)$$

where μᵢ ∈ M_language is the mean semantic embedding for input i, and σᵢ² is **semantic uncertainty**.

**Example:** "red" maps a range of wavelengths (620–750 nm) to a cluster in M_language. Variations ("crimson" vs "scarlet") or context ("red wine" vs "red light") broaden σᵢ², increasing trajectory variability.

### Lyapunov Exponent for Semantic Instability

The **Lyapunov exponent** measures the rate of exponential divergence of nearby trajectories:

$$\lambda = \lim_{t \to \infty} \frac{1}{t} \ln\!\left(\frac{\|\delta\gamma(t)\|}{\|\delta\gamma(0)\|}\right)$$

Semantic uncertainty contributes:

$$\lambda_{\text{semantic}} \propto \frac{1}{L} \sum_{i=t-L}^{t} \sigma_i^2$$

The reader adds their own contribution:

$$\lambda_{\text{total}} = \lambda_{\text{semantic}} + \lambda_{\text{reader}}, \quad \lambda_{\text{reader}} \propto \sigma_{\text{reader}}^2$$

### The Stability Condition

Communication is **stable** when:

$$\lambda_{\text{total}} < \lambda_{\text{crit}}$$

When either semantic uncertainty (poorly constrained word distributions) or reader uncertainty (divergent cognitive manifold) pushes λ_total above the critical threshold, the communication trajectory diverges — meaning fails to stabilise between sender and receiver.

---

## 10. The Observer as Sculptor

Human and LLM form a **coupled dynamical system**:

$$p_{\text{next}} = O(\gamma(t))$$

The user's next prompt is a function of the LLM's current trajectory. Context limits introduce entropy, but prompts steer the system toward stable attractors. The human observer is not passive — they are continually reshaping the geometric landscape through which the LLM trajectory flows.

Like a sculptor removing marble to reveal a form: the observer guides the system toward certain structures by selectively applying forcing terms (prompts) that break symmetry and select among possible trajectories.

---

## 11. The Unifying Claim

The Discussion section states what all of this adds up to:

> *Language, mathematics, and physical systems may share a deeper structural similarity. All can be understood as processes of reconstruction within finite, constrained spaces, shaped by interaction and stabilisation.*

This is Geofinitism applied to the structure of cognition itself. Every domain — language, mathematics, physics — is a process of finite, constrained reconstruction. The specific machinery (tokens, proofs, measurements) differs; the underlying dynamic is the same.

---

## Summary: The Full Mathematical Map

| Object | Symbol | Meaning |
|--------|--------|---------|
| Phase space | P ⊂ ℝᵈ | Space of linguistic states |
| Trajectory | γ(t) | Sentence as a curve in P |
| Context window | Γ_t | {w_{t-L}, ..., w_t} |
| LLM flow | F_θ | Nonlinear attention + feedforward map |
| Context manifold | M_{Γ_t} ⊂ Gr(k,d) | Reconstructed context geometry |
| Curvature | κ(γ(t)) | Local bending of trajectory; drives hallucination risk |
| Betti numbers | β₀, β₁, β₂ | Topological defect classification |
| Syntactic torque | τ(p) | Forcing contribution of prompt |
| Semantic entropy | S(Γ_t) | Information loss from context truncation |
| Reader manifold | M_reader | Individual reader's interpretation space |
| GH distance | d_GH | Geometric distance between reader manifolds |
| Semantic uncertainty | σᵢ² | Width of word's probability distribution |
| Lyapunov exponent | λ_semantic | Rate of divergence driven by uncertainty |
| Stability condition | λ_total < λ_crit | Condition for coherent communication |

---

## Connections to Other Lessons

| Lesson | Connection |
|--------|-----------|
| ATT_01 | Words as Transducers: foundational concept extended here with full dynamical formalism |
| ATT_03 | Tranfictors: σᵢ² corresponds to the Tranfictor's semantic uncertainty interval |
| ATT_06–107 | Geodesic Fractal LLMs: foundational geodesic treatment; ATT_30 adds stations, thermodynamics, topology |
| ATT_13 | Pi Files: Takens embedding used for π; same mathematics applied here to linguistic signals |
| ATT_19 | Static Embeddings Insufficient: impossibility proof; ATT_30 provides the affirmative dynamical alternative |
| ATT_21 | Meaning Divergence Crisis: λ_total and d_GH provide formal measurement tools for meaning divergence |
| ATT_29 | First-Class Meaning: ℛ maps to F_θ; stability condition y* = Stab(ℛ,x) maps to λ_total < λ_crit |

---

*Kevin R. Haylett — School of Geofinitism*  
*Simul Pariter.*
