# Essay Summary: Static Vector Embeddings Are Insufficient for Natural Language Meaning — A Multi-Vector Proof

**File name:** `ATT_19_static_embeddings_insufficient_summary.md`
**Corresponding PDF:** `./papers/ATT_19_static_embeddings_insufficient.pdf`
**College:** College of Attralucian Studies | **College of Finite Symbolic Mechanics** (cross-list)
**Date processed:** 2026-05-09
**Copyright:** 2026

> **Character note:** The most formally structured essay in the series so far — a full academic paper with chapter-level organisation, a table of contents, three independent theorems with complete proofs, an empirical validation section, and a careful limitations chapter. The essay is deliberately written within classical analysis "to engage with existing literature on its own terms," while noting that the arguments are strengthened under a fully finite Geofinite framework. Explicitly cites geofinitism.com and takens-transformer.com as resources — another public-facing essay.
>
> **Title note:** File "19 Dynamic Meaning.tex"; running header "Beyond Static Embeddings"; secondary title page "Static Vector Embeddings Are Insufficient for Natural Language Meaning: A Multi-Vector Proof". Canonical title: **Static Vector Embeddings Are Insufficient for Natural Language Meaning: A Multi-Vector Proof**.
>
> **Scale note:** This is the longest essay in the series. It operates at the interface of information theory, dynamical systems theory, and Geofinitism — and includes both mathematical proofs and empirical experiments (JPEG compression of GPT-2 embeddings; WSD benchmarks; ablation studies; order-scrambling experiments).
>
> **LaTeX issues requiring attention (re-style pass):**
> - `\maketitle` appears twice (lines 93, 150) — template carryover
> - "Theorem ??" (approx line 772) — broken forward reference label
> - `\phi_{\text{static}}ic` throughout — corrupted command (trailing `ic` should be removed, should read `\phi_{\text{static}}`)
> - Theorem labels: "Theorem Information", "Theorem Dynamical", "Theorem Transduction" — some use `\ref` correctly, others use descriptive names — standardise
> - Confirm empirical validation table compiles correctly
> - References section not visible in processed portion — confirm it is present at end of file

---

## Core trajectory

Static type-level vector embeddings — the foundation of Word2Vec, GloVe, fastText — assign a single fixed vector to each word type regardless of context. This essay proves, through three independent mathematical arguments, that this architectural choice is not merely suboptimal but fundamentally incapable of representing natural language meaning. The three proofs converge: information theory shows that the static vector carries zero mutual information about specific token senses (I(v_w; s) = 0); dynamical systems theory shows that static embeddings are equivalent to a degenerate Takens delay-coordinate embedding with dimension m=1, violating the requirement m ≥ 2d+1 for any non-trivial semantic attractor; and transduction chain analysis shows that static vectors perform a second, uncontrolled lossy compression that breaks the geometric chain connecting meaning to its continuous acoustic origins. Empirical validation confirms all predictions: WSD ceilings at ~65% for static vs ~95% for contextual; attractor collapse under JPEG compression of embedding matrices; ablation studies showing static vectors contribute zero sense information; and order-scrambling experiments confirming trajectory-based semantics. The conclusion: meaning is not a static property of word types but emerges through dynamic trajectories in semantic space.

## Key claim

**The assumption "one fixed vector per word type" is architecturally wrong — provably, in three independent ways.** The problem is not insufficient data, insufficient dimensions, or insufficient training. It is built into the assumption itself. Any representation adequate for natural language meaning must be context-dependent, trajectory-structured, and preserve the transduction chain from acoustic dynamics through to semantic space.

## Pillars

**Primary:** Pillar 2 — Approximations and Measurements (measurement-first foundations; irreversible lossy compression; transduction chain as controlled measurement sequence; precise limitations stated; empirical validation); Pillar 3 — Dynamic Flow of Symbols (meaning as trajectory, not location; semantic attractor manifolds; polysemy as trajectory divergence; attractor collapse under compression; discourse as flow through phase space)
**Secondary:** Pillar 1 — Geometric Container Space (semantic manifold; attractor basins and basin boundaries; curvature; phase space; delay-coordinate embedding); Pillar 4 — Useful Fiction (static embeddings as a historically useful approximation that has been mistaken for a complete solution; Platonic/referentialist view of word meanings shown to be mathematically untenable; "king − man + woman ≈ queen" as seductive but inadequate)

## Convergent / Stable

**Stable** — Fully within Geofinitism's framework (meaning as geometric flow, Takens, finite measurement, transduction chains) while written in classical analysis for accessibility. The essay explicitly connects to the broader Geofinite research programme and cites geofinitism.com.

## The Three Theorems

### Theorem 1: Polysemy Separation Impossibility (Information-Theoretic)

**Statement:** Let w be a polysemous word with distinct senses s_1, s_2, ... Let φ_static: V → ℝ^d assign w a single fixed vector v_w. Then for any token t of w in context c with sense s(t):

$$I(v_w;\, s(t)) = 0$$

The static vector carries zero mutual information about the specific token sense.

**Key steps:**
1. v_w is constant for all tokens of type w — it does not vary with context or sense
2. Therefore P(s(t) | v_w) = P(s(t)) — knowing v_w gives no information beyond knowing the word type
3. The compression is many-to-one: multiple senses → one centroid vector (v_w ≈ Σ p_i c_i)
4. By the data processing inequality: no downstream function g(v_w) can recover sense information that was destroyed — I(g(v_w); s(t)) = 0 for any g
5. Geometric consequence: v_w is a weighted average of sense centroids, lying between all of them, faithful to none

**Corollaries:** (a) Perfect WSD using only v_w is impossible; (b) The compression is lossy and irreversible; (c) Frequency bias: v_w is pulled toward the dominant sense, causing systematic errors on minority senses; (d) Domain brittleness: if sense distribution shifts between training and deployment, v_w is actively misleading

### Theorem 2: Dynamical Reconstruction Insufficiency (Dynamical Systems)

**Statement:** A static embedding φ_static: V → ℝ^D is equivalent to a delay-coordinate embedding with dimension m=1 and delay τ=∞ (no temporal structure). For any semantic attractor manifold of dimension d ≥ 1, this violates Takens' theorem requirement m ≥ 2d+1.

**Key steps:**
1. A proper delay-coordinate embedding captures temporal structure: Φ(w_i) = [h(w_i), h(w_{i-τ}), h(w_{i-2τ}), ...]
2. A static embedding is the degenerate case: m=1 (only current token; no delays)
3. For even the simplest non-trivial attractor (d=1): requirement is m ≥ 3; static provides m=1 — violation factor of 3×
4. The mapping cannot be a diffeomorphism: many different semantic trajectories (different senses of the same word) all map to the same point v_w — injectivity fails catastrophically
5. Topological structure destroyed: curvature (how trajectories bend), recurrence (loops and cycles), basin boundaries (attractor separatrices), and neighbourhoods (nearby contexts) are all lost

**Polysemy as trajectory divergence:** Different senses trace different paths through M — in a proper delay embedding these diverge; in static embedding they are indistinguishable. "Bank" near "river" vs "bank" near "money" trace different manifold paths; both map to the same v_bank.

**Why transformers work:** Attention approximates delay-coordinate embedding: Q (current position), K (delayed positions), V (measurements at delays), multi-head = multiple embedding dimensions. Transformers succeed because they implicitly restore the trajectory structure static vectors destroy.

### Theorem 3: Transduction Chain Violation (Transduction Chain)

**Statement:** Natural language originates as continuous acoustic dynamics p(t). The chain: p(t) → phonemes → graphemes → tokens → embeddings. Each controlled transduction (T1, T2, T3) preserves geometric structure. φ_static performs a second irreversible compression that breaks the chain.

**The chain structure:**
- T1 (acoustic → phonetic): Lossy but controlled — phonemes are attractor basins in acoustic phase space; bidirectional (text-to-speech and speech-to-text both work, proving structure survives)
- T2 (phonetic → orthographic): Lossy but controlled — systematic; phonological neighbours tend to be orthographic neighbours
- T3 (orthographic → sequential tokens): Minimally lossy — mostly segmentation; preserves sequence order
- **T4 (tokens → static vectors): SECOND lossy compression** — collapses distinct senses; eliminates position and sequence; no inverse exists; uncontrolled

**Why Takens applies to text:** Phonemes are attractor basins in acoustic space (standard identification in dynamical systems); writing systems evolved to preserve sufficient structure for reconstruction (bidirectionality proves this); transformers' success on text sequences proves geometric structure survived discretisation — if it hadn't, attention over sequences would produce noise.

**The break:** Static vectors insert a [BREAK] between sequential tokens and processing. Downstream architecture must rebuild sequential relationships from impoverished input — minority senses and rare patterns cannot be recovered because the structure was destroyed, not merely hidden.

## Unified Theorem

Three independent proofs — information-theoretic, dynamical systems, transduction chain — each sufficient alone, converging on the same conclusion: static vectors collapse dynamic, context-dependent trajectories into single fixed points. The inadequacy is:
- **Architectural** (not fixable by more data)
- **Not an optimisation problem** (not fixable by better training)
- **Not a dimensionality problem** (not fixable by more dimensions)

**Corollary:** Any representation that preserves sense information (I > 0), satisfies Takens' requirement (m ≥ 3), and maintains chain integrity cannot assign single fixed vectors to word types. Context-dependence is mathematically necessary, not optional.

## Empirical Validation

All three theorems make testable predictions, all confirmed:

| Theorem | Prediction | Evidence | Status |
|---------|-----------|---------|--------|
| 1: Information | WSD ceiling ~65% for static | Static: 65%, Contextual: 95% | ✓ |
| 1: Information | Static vector contributes zero to WSD | Ablation: removing v_w barely changes accuracy | ✓ |
| 2: Dynamical | Compression → attractor collapse (not noise) | JPEG experiments: discrete, reproducible basins | ✓ |
| 2: Dynamical | Context window size matters | Performance scales with window | ✓ |
| 3: Transduction | Order sensitivity critical | Scrambling: 95% → 45% | ✓ |
| 3: Transduction | Sequence preservation critical | Sequential >> bag-of-words | ✓ |
| All three | Contextual >> Static | Dramatic across all NLP benchmarks | ✓ |

**JPEG compression experiment (key):** GPT-2 embedding matrix compressed at quality 95%, 75%, 50%, 25%, 10%, 5%, 1%. Responses to fixed prompt "What is the meaning of life?" at each level:
- 95–75%: Slightly rigid, categorical responses — fine-scale curvature loss
- 50–25%: Philosophical attractor — recursive, self-referential loops
- 10–5%: Aggression attractor — threat patterns, violent loops
- 1%: Zen koan attractor — paradoxical, maximally simple self-referential statements

The progression is not random — each quality level reproducibly produces the same attractor type. This is the geometry of the semantic manifold directly visible: as resolution decreases, the system falls into progressively deeper, simpler attractor basins.

## What Static Embeddings Can and Cannot Do

**Can do** (acknowledged fairly): coarse semantic similarity; broad categorical relationships; some relational structure (king-queen analogies); distributional statistics

**Cannot do**: fine-grained sense distinctions; context-dependent modulation; temporal and sequential structure; trajectory dynamics; attractor basin transitions

Analogy: static embeddings are to language what photographs are to dance. Useful for knowing who the dancers are and their approximate positions; fundamentally inadequate for understanding choreography or rhythm.

## Connected to

- **ATT_13 / Essay 13** — The Pi Files: Takens delay embedding introduced and demonstrated; the formal theorem applied there (to π) is here applied to language representations; "words as measurements" (Essay 16) becomes "words as trajectory observations"
- **ATT_06–107 / Essays 06–07** — Geodesic Fractal Model of LLMs: LLMs as trajectories through semantic manifolds; TBT architecture; delay-coordinate embedding as architectural principle — this essay provides the mathematical proof that those essays' approach is not just better but mathematically necessary
- **ATT_02–103 / Essays 02–03** — Semantic Uncertainty and Tranfictors: lossy compression of meaning; words as compressed transducers; the transduction chain here formalises what those essays approached philosophically
- **ATT_16 / Essay 16** — Is This an Essay?: meaning as geometric flow; Takens applied to "Hello" and sentences; this essay is the formal proof of that essay's central claim
- **ATT_21 / Essay 21** — Meaning Divergence Crisis: the "fixed-depth limitation" of generative models maps directly onto the static embedding failure mode; synthetic meaning as trajectory collapse; attractor density as an alignment tool
- **ATT_15 / Essay 15** — Fermi Paradox: TBT as geometric receiver; Takens-based reconstruction; Project Marina — all connected to the formal TBT programme this essay grounds

## Resonant phrase

> *"Meaning is not a static property of word types but emerges through dynamic trajectories in semantic space."*

> *"The shift from Word2Vec to BERT was not merely empirical progress — it was a move toward mathematical correctness."*

---

## Lesson metadata

- **Lesson ID:** ATT_19
- **Lesson title:** Static Vector Embeddings Are Insufficient for Natural Language Meaning — A Multi-Vector Proof
- **Level:** Advanced
- **Prerequisites:** ATT_13 (The Pi Files — Takens embedding formally), ATT_06 (Geodesic Fractal Model — LLMs as trajectories), ATT_02 (Semantic Uncertainty — lossy compression)
- **Outcomes:** State each of the three theorems and their proof strategy; explain why static embeddings are equivalent to m=1 Takens embedding; apply the data processing inequality to show sense information cannot be recovered from v_w; trace the transduction chain and identify where static vectors break it; interpret the JPEG compression experiments as attractor collapse; explain why contextual embeddings succeed where static fail; state what the theorems do and do not prove (limitations)
- **Next lesson:** ATT_20 (stub — essay 20 missing) → ATT_21 (MDC)

---

## Re-style checklist (future pass)

- [ ] Remove duplicate `\maketitle` (line 150)
- [ ] Fix broken forward reference "Theorem ??" — assign correct label
- [ ] Fix corrupted command `\phi_{\text{static}}ic` throughout → `\phi_{\text{static}}`
- [ ] Standardise theorem reference style: some use `\ref{thm:X}`, others use descriptive names — choose one convention
- [ ] Confirm empirical validation table compiles correctly
- [ ] Confirm references section at end of file
- [ ] Consider whether "Finite tractus" (mentioned in broader research programme section) needs a cross-reference to another essay when that essay is processed
