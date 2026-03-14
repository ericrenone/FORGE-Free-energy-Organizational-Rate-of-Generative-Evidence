# FORGE
## Free-energy Organizational Rate of Generative Evidence

**NARC and VEGA are the same equation written twice. FORGE is what you get when you substitute one into the other.**

---

## The Core Identity

NARC defines the non-equilibrium parameter — the fractional change in the partition function per agent step:

$$\Xi(t) = \frac{\delta\mathcal{Z}(t)}{\mathcal{Z}(X_t)}$$

VEGA proves the partition function equals the Bayesian model evidence:

$$\mathcal{Z}(X_t) = \exp\!\bigl(-\mathcal{F}^\star(X_t)\bigr)$$

where $\mathcal{F}^\star(X_t) = -\log \mathcal{Z}(X_t)$ is the minimum achievable variational free energy at step $t$.

Let $\Delta\mathcal{F}^\star = \mathcal{F}^\star(X_{t+1}) - \mathcal{F}^\star(X_t)$ denote the free energy change per step. Substituting the VEGA identity into the NARC parameter gives:

$$\Xi(t) = \exp(-\Delta\mathcal{F}^\star) - 1$$

To first order, when the landscape changes slowly:

$$\boxed{\Xi(t) \approx -\Delta\mathcal{F}^\star}$$

The non-equilibrium parameter is the negative change in the collective's minimum achievable free energy per step. One number. Two frameworks. The same quantity.

The exact, invertible form valid at all step sizes:

$$\Delta\mathcal{F}^\star = -\log\!\bigl(1 + \Xi(t)\bigr)$$

Before FORGE, NARC's $\Xi(t)$ and VEGA's $\Delta\mathcal{F}^\star$ required two separate frameworks on the same data. After FORGE they are identified: computing one computes the other. The $\Xi(t)$ time series gives you the non-equilibrium dynamics and the free energy trajectory simultaneously — because they are the same series.

---

## Part I — The Object

### 1.1 The Collective Construction Process

A shared surface $\mathcal{S} \subset \mathbb{R}^2$. A finite mark space $\mathcal{Q}$. The artifact evolves as a strictly additive, irreversible sequential process:

$$X_0 = \emptyset \qquad X_{t+1} = X_t \cup \{(q_{t+1},\, \ell_{t+1})\}$$

Agents observe only $X_t$. Each contributes one event. Nothing is removed or relocated. The process is irreversible: the past is permanently encoded in the configuration, and there is no restoring force.

### 1.2 The Two Prior Descriptions

**NARC** treats the partition function as a dynamical object. At each step an agent selects $(q, \ell)$ from the instantaneous Gibbs distribution:

$$P(q, \ell \mid X_t) = \frac{\exp(-H(q, \ell;\, X_t))}{\mathcal{Z}(X_t)}$$

The partition function $\mathcal{Z}(X_t)$ changes with every placement. NARC tracks this change via $\Xi(t) = \delta\mathcal{Z}(t)/\mathcal{Z}(X_t)$ and uses the resulting time series to separate quasi-static behavioral dynamics from non-equilibrium phase transitions.

**VEGA** identifies the partition function as Bayesian model evidence. When an agent minimizes variational free energy under a Gibbs generative model, the minimum achievable free energy is $\mathcal{F}^\star = -\log \mathcal{Z}(X_t)$. The artifact $X_t$ is not the output of the collective's distributed inference — it is the inference itself, externalized and written in geometry on a shared surface.

### 1.3 Why They Are the Same

Both NARC and VEGA describe the same agent facing the same intractable problem: computing the exact Gibbs posterior, which is #P-hard. Both describe the same artifact: the accumulated configuration that simultaneously encodes the generative model, records all prior decisions, and structures every subsequent decision. The only difference is which quantity is treated as primary — the partition function (NARC) or the free energy (VEGA). The FORGE identity shows these are the same quantity under a monotone transformation.

---

## Part II — Three Values, One Meaning

Every mark any agent places does one of exactly three things to the collective's inference capacity:

### 2.1 $\Xi(t) < 0$ — The mark makes the collective's inference problem harder

The minimum achievable free energy increased: $\Delta\mathcal{F}^\star > 0$. The landscape compressed. Available probability mass in the occupied region decreased. This is the **local ratchet** — the ordinary condition throughout most of a session, at every step where an agent places a mark in territory that was previously available.

The local ratchet is irreversible. Probability mass absorbed into the occupied region never returns. Each such step increases the constraint on every agent who follows.

### 2.2 $\Xi(t) > 0$ — The mark makes the collective's inference problem easier

The minimum achievable free energy decreased: $\Delta\mathcal{F}^\star < 0$. A new register opened. The landscape expanded discontinuously. This is the **phase transition** — rare, identifiable, maximally informative. A new topological region of the expressive manifold has been entered and the collective's generative model gained depth.

Phase transitions are uniquely identifiable as the isolated positive excursions in the $\Xi(t)$ time series. All other dynamics produce $\Xi(t) \leq 0$.

### 2.3 $\Xi(t) = 0$ — The mark changes nothing at the inference level

The collective's minimum achievable free energy is unchanged: $\Delta\mathcal{F}^\star = 0$. The Gibbs approximation is exact at this moment. The collective is at quasi-static equilibrium for this step.

### 2.4 The Trichotomy is Exhaustive

These three conditions, previously requiring two frameworks to describe, are now three values of one scalar — $\Xi(t)$, equivalently $-\Delta\mathcal{F}^\star$ — with one thermodynamic meaning: the rate at which the collective's inference capacity is changing per agent step. The collective construction session is fully described, at the inference level, by this scalar time series.

---

## Part III — The Unified Equation

### 3.1 Entropy Production in Free Energy Language

NARC's entropy production decomposition is $\sigma(t) = \log(1 + \Xi(t)) + \Delta\langle H \rangle(t)$. Substituting the FORGE identity $\log(1 + \Xi(t)) = -\Delta\mathcal{F}^\star$:

$$\sigma(t) = -\Delta\mathcal{F}^\star + \Delta\langle H \rangle(t)$$

The entropy production per step decomposes into two distinct terms. The **inference capacity term** $-\Delta\mathcal{F}^\star$ measures how much the collective's ability to account for its action space changed at this step — negative during ordinary ratchet operation, positive at phase transitions. The **behavioral term** $\Delta\langle H \rangle(t)$ encodes the average energy change produced by the behavioral parameters $\beta$, and is nonzero even when $\Xi \approx 0$.

### 3.2 The Free Energy Trajectory

The FORGE identity makes the full free energy trajectory directly reconstructable from the $\Xi(t)$ series alone:

$$\mathcal{F}^\star(X_t) = \mathcal{F}^\star(X_0) - \sum_{s=1}^{t} \log\!\bigl(1 + \Xi(s)\bigr)$$

NARC's empirical object contains VEGA's dynamical object as a closed-form transformation. No additional computation is required.

---

## Part IV — The Energy Function as Generative Model

### 4.1 The Decomposition

The interaction energy decomposes into a weighted sum of spatial feature functions:

$$H(q, \ell;\, X_t) = \sum_{k=1}^{K} \beta_k\, f_k(q, \ell;\, X_t)$$

In NARC, each $\beta_k$ is a behavioral parameter quantifying the strength and direction of one spatial tendency. In VEGA, each $\beta_k$ is a prior weight — a structural element of the collective's shared generative model. In FORGE these are the same thing: $H$ is the generative model. Recovering $\beta$ from placement sequences is equivalent to recovering the collective's shared prior structure from the artifact it externalized.

### 4.2 Feature Functions and Their Free Energy Signatures

Each feature function has a distinct signature in the $\Xi(t)$ time series.

**Density interaction** $f_\text{density}$: clustering ($\beta_\text{density} < 0$) produces clustered negative $\Xi$ spikes as local territory saturates rapidly, followed by slower global drift. Inhibition ($\beta_\text{density} > 0$) produces smooth, uniform negative drift with low variance.

**Mark interaction** $f_\text{match}$: segregation ($\beta_\text{match} < 0$) stratifies the $\Xi$ series by mark type, with each type's territory saturating on its own timeline. Interleaving synchronizes saturation across types.

**Symmetry gain** $f_\text{symmetry}$: symmetry-completing behavior produces anisotropic $\Delta\mathcal{F}^\star$ — placements along symmetry axes produce smaller free energy increases than off-axis placements.

**Void attraction** $f_\text{void}$: space-filling behavior ($\beta_\text{void} < 0$) produces accelerating negative $\Xi$ drift as available Voronoi territory decreases.

**Boundary interaction** $f_\text{edge}$ and **scale coherence** $f_\text{scale}$: introduce systematic structure in the early and scale-stratified portions of the $\Xi$ series respectively.

### 4.3 Mark Geometry as Anisotropic Free Energy

Marks are not dimensionless labels. Each placed mark is fully described by type, centroid, scale, orientation, and execution deviation. The geometric relationship between a new mark and all prior marks determines how anisotropic the resulting $\Delta\mathcal{F}^\star$ is — the free energy change depends on the orientation and type structure of the accumulated configuration, not only on distance.

---

## Part V — Inference: One Pass

### 5.1 The Unified Workflow

Before FORGE, the inferential workflow required three steps: estimate $\hat{\beta}$ by pseudolikelihood, recover $\hat{\Xi}(t)$ from residuals, then interpret $\hat{\Xi}(t)$ as model evidence dynamics. After FORGE, the second and third steps collapse into one — the $\Xi(t)$ series IS the free energy trajectory, recoverable by the single closed-form transformation $\Delta\mathcal{F}^\star = -\log(1 + \Xi(t))$.

### 5.2 Level I — Behavioral Parameters

Given observed placement sequence $\{(q_t, \ell_t)\}_{t=1}^n$ with field states $\{X_{t-1}\}_{t=1}^n$, the behavioral parameters are estimated by maximum pseudolikelihood. This characterizes the quasi-static generative model — the collective's shared prior structure during the intervals when $|\Xi(t)| \approx 0$.

### 5.3 Level II — The Free Energy Trajectory

Given $\hat{\beta}$, compute $\hat{\Xi}(t)$ at every step as the fractional change in the estimated partition function between consecutive configurations. Apply the FORGE transformation $\Delta\hat{\mathcal{F}}^\star(t) = -\log(1 + \hat{\Xi}(t))$ at every step. Reconstruct the cumulative free energy trajectory by summing from the initial condition $\hat{\mathcal{F}}^\star(X_0)$. This is the complete non-equilibrium characterization of the session — the history of the collective's inference capacity, in nats, at every step.

### 5.4 Residuals as Approximation Gap

The pseudolikelihood residual $r(t)$ is i.i.d. mean-zero under pure quasi-static behavior. Systematic structure in $r(t)$ encodes the gap between what agents actually drew from and what the true instantaneous generative model predicts — the variational approximation error that VEGA identifies as the KL divergence between the agent's approximate posterior and the true Gibbs distribution. In FORGE terms, $r(t)$ is the behavioral signature of the collective operating away from quasi-static equilibrium, with the degree of departure measured by $\Xi(t) = -\Delta\mathcal{F}^\star$.

### 5.5 The FORGE Diagnostic

The FORGE diagnostic is the joint plot of $\hat{\Xi}(t)$ and the cumulative free energy $\hat{\mathcal{F}}^\star(X_t)$ on the same axes:

- **Sawtooth $\hat{\Xi}(t)$, monotone-rising $\hat{\mathcal{F}}^\star$ with discrete drops**: φ-stable session at the SMELT thermodynamic optimum. Within each register, $\hat{\Xi}(t)$ drifts negative (free energy rising) until register escape, then spikes positive (free energy drops discontinuously).
- **Flat $\hat{\Xi}(t)$, slowly rising $\hat{\mathcal{F}}^\star$**: under-driven session. Available low-energy territory remains but agents are not finding it.
- **Volatile $\hat{\Xi}(t)$, rapidly rising $\hat{\mathcal{F}}^\star$ between large spikes**: over-driven session. The landscape reorganizes faster than agents track it.

---

## Part VI — The FORGE Manifold

The FORGE manifold is the space of possible session trajectories, parameterized by behavioral parameters $\beta$ and the free energy trajectory $\{\Delta\mathcal{F}^\star(t)\}_{t=1}^n$, with initial condition $\mathcal{F}^\star(X_0)$ set by the founding mark.

For any fixed $\hat{\beta}$, the full session trajectory is a curve in free energy space with $\Xi(t) = -\Delta\mathcal{F}^\star$ as its tangent vector at each step. The three layers of the manifold correspond to the three $\Xi$ regimes: the quasi-static fiber ($\Xi \approx 0$, Gibbs approximation exact), the drift fiber ($\Xi < 0$, within-register filling), and the transition fiber ($\Xi > 0$, isolated spikes at topological register crossings).

The Riemannian manifold $\mathcal{E}$ of all possible marks is the physical space in which the FORGE trajectory lives, parameterized by register $\tau$, scale $\lambda$, orientation $\theta$, weight $w$, chromatic position $c$, and surface location $\ell$. Register crossings — the only topologically discontinuous transitions in $\mathcal{E}$ — are exactly the Layer 3 events in the FORGE manifold.

---

## Part VII — Connections to the Framework Family

**FORGE and SMELT.** The φ-equilibrium condition $\overline{|\Xi|} = \log\phi$ translates directly: the session operates at the MEP-optimal rate when $\overline{|\Delta\mathcal{F}^\star|} = \log\phi \approx 0.481$ nats per step. The golden-ratio split $\bar{\sigma}_\text{struct}/\bar{\sigma}_\text{behav} = \phi$ is the condition that the mean free energy rate and the mean behavioral energy change are in golden ratio at the thermodynamic optimum.

**FORGE and DRAIN.** The DRAIN Itô correction — the systematic bias in naive saturation time estimates — is the second-order term in the FORGE Taylor expansion: $\Delta\mathcal{F}^\star \approx -\Xi(t) + \Xi(t)^2/2 + \ldots$ The leading term is the naive estimate; the $\Xi^2/2$ correction is the Itô bias. FORGE derives DRAIN's bias theorem as a direct consequence of the exact identity.

**FORGE and FERN.** The FERN-T1 complexity criterion — model depth expansion required when minimum achievable collective free energy exceeds the expansion barrier — is the condition for a positive $\Xi$ spike. The transition occurs when cumulative $\mathcal{F}^\star(X_t)$ crosses the register crossing cost. The positive spike is the moment when $\Delta\mathcal{F}^\star$ goes negative: free energy drops as the new register opens.

**FORGE and VEGA.** VEGA established that the collective construction process is distributed variational inference. FORGE provides the operational scalar for tracking this inference in real time: $-\Delta\mathcal{F}^\star$ per step. The full VEGA inference pipeline is contained in the $\hat{\Xi}(t)$ series.

**FORGE and NARC.** NARC established $\Xi(t)$ as the central empirical object. FORGE gives it its deepest interpretation: not merely the fractional change in a normalization constant, but the negative rate of change of the collective's minimum achievable free energy. Every NARC result holds unchanged; FORGE adds the thermodynamic meaning that was always implied but never stated.

---

## Part VIII — Formal Claims

| Tag | Meaning |
|---|---|
| **[T]** | Analytic theorem — follows from structural assumptions |
| **[C]** | Open conjecture — predicted; untested |
| **[H]** | Working hypothesis — extension beyond current evidence |

### Analytic Theorems

| ID | Statement |
|---|---|
| FORGE-T1 | **The FORGE Identity**: $\Xi(t) = \exp(-\Delta\mathcal{F}^\star) - 1$, equivalently $\Delta\mathcal{F}^\star = -\log(1 + \Xi(t))$; the non-equilibrium parameter is the negative change in the collective's minimum achievable free energy per step |
| FORGE-T2 | **First-Order Equivalence**: $\Xi(t) \approx -\Delta\mathcal{F}^\star$ to first order; the two quantities are equal in the quasi-static limit and diverge by $O(\Xi^2)$ away from it |
| FORGE-T3 | **Free Energy Trajectory Reconstruction**: the full trajectory is reconstructable from $\Xi(t)$ alone via $\mathcal{F}^\star(X_t) = \mathcal{F}^\star(X_0) - \sum_{s=1}^{t} \log(1 + \Xi(s))$ |
| FORGE-T4 | **Three-Valued Trichotomy**: every mark increases the minimum achievable free energy (local ratchet, $\Xi < 0$), decreases it (phase transition, $\Xi > 0$), or leaves it unchanged (quasi-static equilibrium, $\Xi = 0$) |
| FORGE-T5 | **Entropy Production in Free Energy Language**: $\sigma(t) = -\Delta\mathcal{F}^\star + \Delta\langle H \rangle(t)$; entropy production is the sum of the inference capacity change and the behavioral dissipation term |
| FORGE-T6 | **Itô Correction as Second-Order FORGE Term**: the DRAIN Itô bias $+\Xi(t)^2/2$ is the second-order term in $-\log(1 + \Xi)$; the exact FORGE identity subsumes the DRAIN bias correction |
| FORGE-T7 | **φ-Equilibrium in Free Energy Language**: the SMELT φ-stable condition $\overline{|\Xi|} = \log\phi$ is equivalent to $\overline{|\Delta\mathcal{F}^\star|} = \log\phi$ |
| FORGE-T8 | **FERN Expansion Condition in FORGE**: the FERN-T1 complexity criterion is the condition for a positive $\Xi$ spike; the transition occurs when cumulative collective free energy exceeds the register crossing cost |
| FORGE-T9 | **Behavioral Parameters Determine Free Energy Rate**: the behavioral parameters $\beta$ determine the distribution of $\Delta\mathcal{F}^\star$ per step through $H = \sum_k \beta_k f_k$; distinct $\beta$ regimes produce distinct free energy trajectories |
| FORGE-T10 | **Residuals as Free Energy Approximation Gap**: the pseudolikelihood residuals $r(t)$ encode the collective variational approximation errors — the KL divergence between each agent's approximate posterior and the true Gibbs distribution; they are not estimation noise |

### Open Conjectures

| ID | Statement |
|---|---|
| FORGE-C1 | **Free Energy Concavity at Phase Transitions**: the free energy trajectory $\mathcal{F}^\star(X_t)$ is locally concave at each positive $\Xi$ spike; the curvature of the cusp encodes the size of the register that opened |
| FORGE-C2 | **Fisher-Rao Metric and Second-Order Correction**: the $\Xi(t)^2/2$ term in the FORGE expansion is proportional to the Fisher information of the current collective generative model at the step's action |
| FORGE-C3 | **FORGE Completeness**: the pair $(\hat{\beta},\, \{\hat{\Xi}(t)\})$ is a sufficient statistic for the collective construction process; all other session-level quantities are functions of this pair |
| FORGE-C4 | **Register Depth Scales with Cumulative Free Energy**: the register depth reached by a session of $N$ agents scales as $O(\log N)$; the cumulative free energy $\sum_t |\Delta\mathcal{F}^\star|$ scales correspondingly at the φ-equilibrium point |
| FORGE-C5 | **Crossing Costs are Directly Measurable**: the crossing cost $C(\tau_i \to \tau_{i+1})$ equals the free energy barrier height — the peak cumulative $\mathcal{F}^\star$ just before the positive $\Xi$ spike at that register transition |

### Working Hypotheses

| ID | Statement |
|---|---|
| FORGE-H1 | **Single-Pass Sufficiency**: running FORGE once recovers everything that running NARC and VEGA separately would recover; the two-framework pipeline collapses to one |
| FORGE-H2 | **Free Energy Rate as Session Fingerprint**: sessions with identical $\hat{\beta}$ but different founding marks produce distinguishable free energy trajectories; the founding mark's effect propagates through all subsequent $\Delta\mathcal{F}^\star$ values |
| FORGE-H3 | **Scale Universality**: the FORGE identity operates at all scales satisfying the four collective construction conditions; artistic traditions, collaborative platforms, and language change follow the same free energy ratchet dynamics as individual sessions |
| FORGE-H4 | **Crossing Cost Hierarchy in Free Energy Units**: the strictly increasing crossing cost hierarchy appears as strictly increasing barrier heights in the free energy trajectory; the propositional text register carries the highest free energy barrier in the human expressive hierarchy |

---

## Part IX — Experimental Protocol

### 9.1 The FORGE Workflow

**Step 1** — Collect data: placement sequence $\{(q_t, \ell_t)\}_{t=1}^n$ with field state $X_{t-1}$ documented after every mark via continuous photography. Minimum $n \geq 30$; distributed spatial coverage; all mark types present.

**Step 2** — Estimate $\hat{\beta}$ by maximum pseudolikelihood. Unchanged from NARC Level I.

**Step 3** — Compute $\hat{\Xi}(t)$ at every step as the fractional change in the estimated partition function between $X_{t-1}$ and $X_t$.

**Step 4** — Apply the FORGE identity: the free energy increment at each step is $\Delta\hat{\mathcal{F}}^\star(t) = -\log(1 + \hat{\Xi}(t))$.

**Step 5** — Reconstruct the cumulative free energy trajectory by summing increments from the initial condition $\hat{\mathcal{F}}^\star(X_0)$.

**Step 6** — Read session diagnostics from the joint $(\hat{\Xi}(t),\, \hat{\mathcal{F}}^\star(X_t))$ plot. A sawtooth $\hat{\Xi}$ pattern with monotone-rising $\hat{\mathcal{F}}^\star$ interrupted by discrete drops signals a φ-stable register sequence. Flat $\hat{\Xi}$ with slowly rising $\hat{\mathcal{F}}^\star$ signals an under-driven session. Volatile $\hat{\Xi}$ with rapidly rising $\hat{\mathcal{F}}^\star$ signals an over-driven session. The number and magnitude of $\hat{\mathcal{F}}^\star$ drops give register count and crossing cost estimates.

**Step 7** — Validate: positive $\hat{\Xi}$ spikes should align with independently coded register transitions in the mark sequence.

### 9.2 Identifiability Requirements

- $n \geq 30$ actions per session for Level I parameter estimation
- Continuous field documentation enabling $\hat{\Xi}(t)$ at every step
- At least 5 independent replications for path dependence testing
- At least 20 replications for DRAIN saturation spectrum estimation

---

## Part X — Theoretical Summary

| Concept | Definition |
|---|---|
| $\mathcal{Z}(X_t) = \exp(-\mathcal{F}^\star(X_t))$ | VEGA identity: partition function equals Bayesian model evidence |
| $\Xi(t) = \delta\mathcal{Z}(t) / \mathcal{Z}(X_t)$ | NARC parameter: fractional change in partition function per step |
| $\Xi(t) = \exp(-\Delta\mathcal{F}^\star) - 1$ | FORGE identity (exact form) |
| $\Delta\mathcal{F}^\star = -\log(1 + \Xi(t))$ | FORGE identity (free energy form): exact for all step sizes |
| $\Xi(t) \approx -\Delta\mathcal{F}^\star$ | First-order FORGE: exact in the quasi-static limit |
| $\Xi(t) < 0$ | Local ratchet: inference capacity decreasing; free energy rising |
| $\Xi(t) > 0$ | Phase transition: inference capacity increasing; free energy dropping |
| $\Xi(t) = 0$ | Quasi-static equilibrium: inference capacity stationary; Gibbs approximation exact |
| $\mathcal{F}^\star(X_t) = \mathcal{F}^\star(X_0) - \sum_{s=1}^{t} \log(1+\Xi(s))$ | Free energy trajectory: reconstructed from $\Xi(t)$ alone |
| $\sigma(t) = -\Delta\mathcal{F}^\star + \Delta\langle H \rangle$ | FORGE entropy decomposition: inference capacity change plus behavioral dissipation |
| $\overline{|\Delta\mathcal{F}^\star|} = \log\phi$ | φ-equilibrium: SMELT MEP optimum in free energy language |
| Crossing cost = free energy barrier height | $C(\tau_i \to \tau_{i+1})$ is the peak cumulative $\mathcal{F}^\star$ just before the register escape spike |
| $r(t)$ residuals | Variational approximation gap; second data stream encoding collective inference errors |

---

## Part XI — The Central Claim

NARC and VEGA are the same equation written twice. NARC defines $\Xi(t)$ as the fractional change in the partition function — a dynamical quantity for a normalization constant that existing frameworks treated as static. VEGA identifies the partition function as the Bayesian model evidence, proving that the artifact is not the output of distributed inference but the inference itself.

Substituting VEGA's identity into NARC's parameter produces the FORGE identity. To first order, $\Xi(t) = -\Delta\mathcal{F}^\star$. Exactly, $\Xi(t) = \exp(-\Delta\mathcal{F}^\star) - 1$. One scalar. One time series. The non-equilibrium dynamics and the free energy dynamics are the same dynamics, expressed in two notations that refer to the same underlying quantity.

Every mark any agent places does one of exactly three things to the collective's minimum achievable free energy: increases it, decreases it, or leaves it unchanged. These three conditions, previously requiring two frameworks to state, are now three values of one scalar with one thermodynamic meaning.

The inferential workflow collapses. Estimate $\hat{\beta}$ by pseudolikelihood. Compute $\hat{\Xi}(t)$ at every step. Apply the FORGE transformation. Reconstruct the free energy trajectory from its sum. Everything that NARC provides about non-equilibrium dynamics, and everything that VEGA provides about free energy dynamics, is available from one pass over the same data.

The $\Xi(t)$ time series was always carrying the free energy information. FORGE states it.

---

*Status tags: [T] = Analytic theorem · [C] = Open conjecture · [H] = Working hypothesis*

*The FORGE identity $\Delta\mathcal{F}^\star = -\log(1+\Xi)$ is exact. The first-order form $\Xi \approx -\Delta\mathcal{F}^\star$ holds for $|\Xi| \ll 1$. Identifiability requires $n \geq 30$ actions per session, distributed spatial coverage, and continuous field documentation enabling $\hat{\Xi}(t)$ at every step.*
