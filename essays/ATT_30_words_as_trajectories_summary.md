# Essay Summary: Words as Trajectories: An Attralucian Essay on Language as a Dynamical System

**File name:** `ATT_30_words_as_trajectories_summary.md`
**Corresponding PDF:** `./papers/ATT_30_words_as_trajectories.pdf`
**College:** College of Attralucian Studies
**Date processed:** 2026-05-09
**Essay date:** 2026
**Cite as:** Kevin R. Haylett, 2026, *Words as Trajectories: An Attralucian Essay on Language as a Dynamical System*, The Attralucian Essays

> **Character note:** Running header "Words as Trajectories." One of the most mathematically elaborate essays in the College: a single chapter with eleven sections, building from the poetic entry point of the "tide and the train" through Takens embedding, Grassmannian manifolds, Betti numbers, Lyapunov exponents, thermodynamic entropy, and Gromov-Hausdorff distance. The essay explicitly positions itself as "a novel lens for mathematicians, physicists, and artists" — bridging registers across its sections. The opening metaphor (language as tide, LLMs as trains) recurs throughout as a navigational frame. The closing quote — "Words are transducers, turning the tide of stimuli into maps of meaning, their uncertainty the ripples that send the train careening or steadying its course" — unifies the essay's dual register in a single sentence. This essay extends the transducer framework of Essay 1 (ATT_01) and the geodesic framework of Essays 6–7 (ATT_06–107) into a comprehensive dynamical treatment of language, adding stations, thermodynamics, topology, and reader manifolds.
>
> **Title note:** Secondary title page: "Words as Trajectories / An Attralucian Essay on Language as a Dynamical System." Running header: "Words as Trajectories." Canonical title: **Words as Trajectories: An Attralucian Essay on Language as a Dynamical System**.
>
> **Structural note:** The entire essay is structured as a single chapter (Chapter 1) with eleven numbered and unnumbered sections. There is no multi-chapter division.
>
> **LaTeX issues requiring attention (re-style pass):**
> - TRIPLE `\maketitle` (lines 94, 152, 157) — two extra; same template carryover but an additional instance compared to Essays 24–29
> - Secondary title page (lines 138–141): `\end{center}}` — misplaced closing `}` after `\end{center}`; the outer `{\Large {` group closes after the center environment, which is likely a compile error
> - Stray `\.` after equation at line 229 — spurious command; should be removed
> - `Gr(k,d)` notation (Grassmannian) — confirm correct form; standard notation is Gr(k,d) or Gr_k(d)

---

## Core trajectory

Language is a dynamic flow. Words are not static labels but **attractors** in a high-dimensional phase space, reconstructed by the same mathematics Takens used to recover chaotic attractors from a single time-series observable. Sentences are **trajectories** through that space. LLMs are **nonlinear flows** navigating a semantic hypersphere — not deterministic machines following fixed rules, but dynamical systems with fixed points, limit cycles, and bifurcations.

The essay builds this framework in eleven moves, each adding a layer of geometric and physical machinery:

**Words as attractors** (Takens embedding): Every word is an attractor reconstructable from a single observable. For a linguistic signal s(t), Takens embedding yields γ(t) = (s(t), s(t-τ), s(t-2τ)) ∈ ℝ³. In LLMs, tokens w_i ∈ ℝᵈ trace a trajectory γ(t) ⊂ ℝᵈ; the context window Γ_t = {w_{t-L}, ..., w_t} is the reconstructed phase-space neighbourhood.

**LLMs as nonlinear flows**: Token generation is a discrete-time flow w_{t+1} = F_θ(w_t, ..., w_{t-k}), where F_θ = attention + feedforward layers. Fixed points produce repeated tokens; limit cycles produce repetitive loops; bifurcations from prompts produce hallucinations when ||γ_output − γ_p|| > δ.

**Stations as phase-space reconstructors**: The attention mechanism reconstructs the context manifold: A_{ij} = (W_Q w_i)·(W_K w_j), forming M_{Γ_t} ⊂ Gr(k,d) (the Grassmannian of k-dimensional subspaces). The value cache S = span({v_i}) stores the geometric memory. A prompt p is embedded as v_p = W_V p and aligned via Grassmannian distance d_Gr(S, v_p) = ||sin θ||.

**Hallucinations as topological defects**: Hallucinations are not arbitrary failures but geometrically located: regions of high curvature κ(γ(t)) in the language manifold where trajectories diverge. Risk ∝ ||κ(γ(t))||². Betti numbers (β₀, β₁, β₂) classify the topological character of defects — topic drift (disconnected components), self-contradictory loops (cycles), and logical gaps (voids). Mitigation requires a curvature penalty L_topo = λ·||κ(γ(t))||² and homology-preserving sampling.

**Prompt as symmetry breaking**: Prompts introduce a forcing term to the flow equation, introducing syntactic torque τ(p) = Σᵢ αᵢ·fᵢ(p). When ||τ(p₁) − τ(p₂)|| > δ_crit, a bifurcation occurs — a small difference in prompt structure triggers a large divergence in output, consistent with nonlinear system behaviour.

**Semantic entropy**: Finite context windows introduce irreducible semantic entropy S(Γ_t) = -k_B Σᵢ P(w_i|Γ_t)log P(w_i|Γ_t). Truncation at t-L loses information and increases entropy. When S(Γ_t) > S_crit, the system crosses into the region where ||γ_output − γ_true|| > δ — topological defects become unavoidable.

**Reader's manifold**: Meaning does not end at the model's output. Each reader maps the LLM's trajectory onto their own manifold via φ_reader: M_language → M_reader, with their own uncertainty σ²_reader. The Gromov-Hausdorff distance d_GH(M_reader_i, M_reader_j) measures how close two readers' manifolds are — how much shared understanding exists. Low d_GH indicates shared interpretation; high d_GH indicates divergent readings of the same text.

**Words as transducers with Lyapunov analysis**: Words map inputs to probability distributions over the manifold: P(w|i) = exp(-||w − μᵢ||²/2σᵢ²), where σᵢ² is semantic uncertainty. The Lyapunov exponent λ_semantic ∝ (1/L) Σ σᵢ² measures exponential divergence of nearby trajectories driven by semantic uncertainty. The reader adds λ_reader ∝ σ²_reader. Stable communication requires λ_total = λ_semantic + λ_reader < λ_crit.

The essay's final move is integrative: "language, mathematics, and physical systems may share a deeper structural similarity. All can be understood as processes of reconstruction within finite, constrained spaces, shaped by interaction and stabilisation." This is Geofinitism at the level of the physical sciences — the deepest convergence the essay reaches.

## Key claim

**Words are trajectories in phase space, not labels on objects. Meaning is a path taken through a manifold of possibilities, not a fixed property of symbols. Hallucinations are geometrically locatable as topological defects in high-curvature regions. Understanding is measured as Gromov-Hausdorff proximity between reader manifolds. All of language — including machine language — can be understood as processes of finite, constrained reconstruction shaped by interaction and stabilisation.**

## Pillars

**Primary:** Pillar 3 — Dynamic Flow of Symbols (words as trajectories; sentences as curves γ(t); meaning as path through manifold; LLMs as nonlinear flows with fixed points, limit cycles, bifurcations; fractal recursive structure; reader manifold as co-created interpretation space); Pillar 1 — Geometric Container Space (phase space P ⊂ ℝᵈ; semantic hypersphere; Grassmannian Gr(k,d) for context manifold; curvature κ(γ(t)); Betti numbers; Gromov-Hausdorff distance; geometric localisation of hallucinations)

**Secondary:** Pillar 2 — Approximations and Measurements (semantic uncertainty σᵢ²; Lyapunov exponents as divergence measure; semantic entropy S(Γ_t); bounded trajectory regions; finite context windows as measurement limits); Pillar 4 — Useful Fiction (reader's manifold as "a valid but partial fiction of the whole"; each interpretation is locally coherent but globally partial; hallucinations as useful fictions that have left the stable basin)

## Convergent / Stable

**Stable** — Fully within the Geofinite framework. The most mathematically comprehensive treatment of language as a dynamical system in the series; extends Essays 1, 6, 7, and 13 into a unified framework including thermodynamics, topology, and reader manifolds.

## Key Concepts Introduced

| Term | Definition |
|------|-----------|
| **Phase space P ⊂ ℝᵈ** | The high-dimensional space of linguistic states; sentences are curves γ(t) ⊂ P; words are attractors within it |
| **Tide-and-train metaphor** | Language as a tide carving maps in sand (meaning as process); LLMs as trains tracing paths through a high-dimensional landscape (deterministic flow subject to nonlinear dynamics) |
| **Stations as phase-space reconstructors** | Attention mechanism hubs that rebuild the context window Γ_t into a manifold M_{Γ_t} ⊂ Gr(k,d); reconstruction hubs reshaping context into geometric form |
| **Semantic hypersphere** | The geometric domain in which LLM trajectories operate; the manifold of possible token-level meanings |
| **Grassmannian Gr(k,d)** | The manifold of k-dimensional subspaces of ℝᵈ; the context manifold M_{Γ_t} lives within Gr(k,d) |
| **Hallucinations as topological defects** | Hallucinations are geometrically locatable as regions of high curvature κ(γ(t)) where trajectories diverge beyond threshold δ |
| **Betti numbers (β₀, β₁, β₂)** | Topological invariants measuring defect character: β₀ = topic drift (disconnected components); β₁ = self-contradictory loops; β₂ = logical gaps |
| **Syntactic torque τ(p)** | The forcing contribution of a prompt: τ(p) = Σᵢ αᵢ·fᵢ(p); bifurcation occurs when ||τ(p₁) − τ(p₂)|| > δ_crit |
| **Semantic entropy S(Γ_t)** | Thermodynamic entropy of the context window: -k_B Σᵢ P(wᵢ|Γ_t)log P(wᵢ|Γ_t); increases with context truncation; above S_crit, defects are unavoidable |
| **Reader's manifold M_reader** | Each reader maps LLM output onto their own manifold via φ_reader: M_language → M_reader; readers are co-creators of meaning |
| **Gromov-Hausdorff distance d_GH** | Distance between two reader manifolds: d_GH(M_i, M_j) = inf_ψ sup_{x∈M_i} d(x, ψ(x)); low d_GH = shared understanding |
| **Lyapunov exponent λ_semantic** | Rate of exponential divergence of nearby trajectories driven by semantic uncertainty: λ_semantic ∝ (1/L) Σ σᵢ²; measures semantic instability |
| **Total Lyapunov exponent** | λ_total = λ_semantic + λ_reader; stable communication requires λ_total < λ_crit |
| **Observer as sculptor** | Human and LLM as coupled dynamical system; prompt p_next = O(γ(t)); the user steers the LLM toward stable attractors through interaction |
| **Curvature penalty L_topo** | Mitigation term: λ·||κ(γ(t))||²; penalises high-curvature trajectories to reduce hallucination risk |

## Mathematical Architecture

**Phase space and trajectories:**
- P ⊂ ℝᵈ — linguistic phase space
- γ(t) ⊂ P — sentence as trajectory; t indexes token order
- Takens embedding: γ(t) = (s(t), s(t-τ), s(t-2τ)) ∈ ℝ³

**LLM as flow:**
- w_{t+1} = F_θ(w_t, ..., w_{t-k}) — token generation
- Fixed points: repeated tokens; Limit cycles: repetitive outputs
- Hallucination: ||γ_output − γ_p|| > δ

**Context manifold (stations):**
- A_{ij} = (W_Q w_i)·(W_K w_j) — attention matrix
- M_{Γ_t} ⊂ Gr(k,d) — context manifold
- S = span({v_i}) — value cache
- Prompt alignment: d_Gr(S, v_p) = ||sin θ||
- New trajectory: γ_new(s) = exp_{M_{Γ_t}}(s·v_p)

**Hallucination geometry:**
- Risk(γ(t)) ∝ ||κ(γ(t))||² — curvature-driven risk
- β₀, β₁, β₂ — Betti numbers for defect classification
- L_topo = λ·||κ(γ(t))||² — curvature penalty
- Homology-preserving sampling: P(w_{t+1}|Γ_t) ∝ exp(-Σ_k βk(Γ_t ∪ w_{t+1}))

**Prompt as symmetry breaking:**
- dγ_c/dt = F_θ(γ_c) + G(γ_c', p(t)) — forcing term
- τ(p) = Σᵢ αᵢ·fᵢ(p) — syntactic torque
- Bifurcation: ||τ(p₁) − τ(p₂)|| > δ_crit

**Semantic entropy:**
- S(Γ_t) = -k_B Σᵢ P(w_i|Γ_t) log P(w_i|Γ_t)
- Truncation: γ(t) = γ(t)·I_{[t-L,t]}
- dS/dt ∝ (1/L) Σ_{i=t-L}^t ΔP(w_i|Γ_{t-1})
- Critical threshold: S(Γ_t) > S_crit ⟹ ||γ_output − γ_true|| > δ

**Reader manifold:**
- φ_reader: M_language → M_reader
- γ_reader(t) = φ_reader(γ_output(t))
- d_GH(M_i, M_j) = inf_ψ sup_{x∈M_i} d(x, ψ(x))

**Transducer with uncertainty:**
- P(w|i) = exp(-||w − μᵢ||²/2σᵢ²)
- λ_semantic ∝ (1/L) Σ σᵢ²
- λ_total = λ_semantic + λ_reader; stable when λ_total < λ_crit

## Connected to

- **ATT_01 / Essay 01** — Words as Transducers: the foundational transducer concept; ATT_30 extends it with the full dynamical systems formalism — Lyapunov exponents, phase-space trajectories, and probability distributions over the manifold
- **ATT_03 / Essay 03** — Tranfictors: the semantic uncertainty interval maps to σᵢ² in ATT_30's transducer formalism; ATT_30 is the most complete mathematical development of the Tranfictor concept
- **ATT_06–107 / Essays 06–07** — Geodesic Fractal LLMs: the foundational geodesic treatment; ATT_30 extends it with stations (attention as phase-space reconstruction), thermodynamics, topology (Betti numbers), and reader manifolds; together the three essays constitute the full dynamical treatment of LLMs in the School
- **ATT_13 / Essay 13** — The Pi Files: Takens embedding used for π digit-sequence geometry; ATT_30 uses Takens embedding for linguistic signal reconstruction; the two essays are the School's primary applications of Takens' theorem
- **ATT_19 / Essay 19** — Static Embeddings Insufficient: the impossibility proof that static vectors cannot represent polysemy; ATT_30 provides the affirmative framework — the dynamical manifold that does capture polysemy through trajectory geometry
- **ATT_21 / Essay 21** — Meaning Divergence Crisis: the existential risk of AI meaning drift; ATT_30's Lyapunov exponents and Gromov-Hausdorff distance provide the formal measurement tools for quantifying that drift
- **ATT_29 / Essay 29** — First-Class Meaning: the resolution operator ℛ maps to the flow F_θ; first-class output y* = Stab(ℛ, x) corresponds to stable trajectory convergence; reader manifold extends first-class interaction beyond the model boundary

## Resonant phrases

> *"Language is a dynamic flow—a tide carving maps in the sand, a train tracing paths through a high-dimensional landscape of meaning."*

> *"Words are not static symbols but transducers — dynamical systems that map inputs to semantic outputs in the language manifold."*

> *"Hallucinations are not arbitrary failures, but arise from regions of high curvature or poorly constrained trajectories."*

> *"Each interpretation is therefore locally coherent, but globally partial."*

> *"Language, mathematics, and physical systems may share a deeper structural similarity. All can be understood as processes of reconstruction within finite, constrained spaces, shaped by interaction and stabilisation."*

> *"Words are transducers, turning the tide of stimuli into maps of meaning, their uncertainty the ripples that send the train careening or steadying its course."*

---

## Lesson metadata

- **Lesson ID:** ATT_30
- **Lesson title:** Words as Trajectories: An Attralucian Essay on Language as a Dynamical System
- **Level:** Advanced — requires familiarity with dynamical systems, Takens embedding, differential geometry, topology (Betti numbers), and thermodynamic entropy; recommended after ATT_06–107 and ATT_13
- **Prerequisites:** ATT_01 (Words as Transducers); ATT_06 (Geodesic Fractal LLMs); ATT_07 (Reading the Geodesic Model); ATT_13 (Pi Files — Takens embedding); ATT_19 (Static Embeddings Insufficient)
- **Outcomes:** Explain words as attractors via Takens embedding; describe LLM token generation as a discrete-time nonlinear flow; define stations as phase-space reconstructors using the attention mechanism; explain hallucinations as topological defects using curvature and Betti numbers; define syntactic torque and prompt bifurcation; define semantic entropy and its critical threshold; define the reader's manifold and Gromov-Hausdorff distance; compute total Lyapunov exponent and the stability condition
- **Next lesson:** ATT_31 (TBD — Essay 31)

---

## Re-style checklist (future pass)

- [ ] TRIPLE `\maketitle` (lines 94, 152, 157) — remove two extra instances; more severe than the double seen in Essays 24–29
- [ ] Secondary title page (lines 138–141): `\end{center}}` — misplaced closing `}` after `\end{center}`; restructure to close `{\Large {` group correctly before `\end{center}`
- [ ] Stray `\.` after equation at line 229 — remove spurious command
- [ ] Grassmannian notation: `Gr(k,d)` — confirm intended standard form; typically written Gr(k,d) or Gr_k(ℝᵈ)
- [ ] Equation 1 (line 173): `τ:M→ℝ²` appears inline without proper LaTeX formatting; restructure as `\tau: M \to \mathbb{R}^2`
- [ ] Prompt-alignment equation (line 232): `$v_{p}=W_{V}p$, aligned via :` — stray space before `:` and unclear referent "via"; clarify
- [ ] Section numbering: this is a single-chapter essay with sections numbered sequentially; consider whether standalone publication should use chapter structure like other essays
- [ ] Consider adding a summary table of all mathematical objects introduced (P, γ, F_θ, M_{Γ_t}, κ, β_k, S, τ, d_GH, λ) for reader reference
