# FORGE
## Free-energy Organizational Rate of Generative Evidence

**NARC and VEGA are the same equation written twice. FORGE is what you get when you substitute one into the other.**

---

## The Identity

NARC defines the non-equilibrium parameter — the fractional change in the partition function per agent step:

$$\Xi(t) = \frac{\delta\mathcal{Z}(t)}{\mathcal{Z}(X_t)}$$

VEGA proves the partition function is the Bayesian model evidence:

$$\mathcal{Z}(X_t) = \exp(-\mathcal{F}^*(X_t))$$

Substituting:

$$\Xi(t) = \frac{\exp(-\mathcal{F}^*(X_{t+1})) - \exp(-\mathcal{F}^*(X_t))}{\exp(-\mathcal{F}^*(X_t))} = \exp(-\delta\mathcal{F}^*(X_t)) - 1$$

For small steps, to first order:

$$\boxed{\Xi(t) \approx -\delta\mathcal{F}^*(X_t)}$$

**The non-equilibrium parameter is exactly the negative change in the collective's minimum achievable free energy per step.**

One number. Two frameworks. The same quantity.

Before FORGE, NARC's $\Xi(t)$ and VEGA's $\delta\mathcal{F}^*$ were two separate quantities computed from two separate frameworks applied to the same data. After FORGE they are identified: computing one computes the other. The $\Xi(t)$ time series gives you the non-equilibrium dynamics and the free energy trajectory simultaneously because they are the same series.

---

## Part I — The Object

### 1.1 The Collective Construction Process

A shared surface $\mathcal{S} = [0,W] \times [0,H] \subset \mathbb{R}^2$. A finite mark space $\mathcal{Q}$. A marked configuration:

$$X = \{(q_i, \ell_i)\}_{i=1}^n \in \mathcal{N}_f(\mathcal{S} \times \mathcal{Q})$$

The artifact evolves as a strictly additive, irreversible sequential process:

$$X_0 = \emptyset \qquad X_{t+1} = X_t \cup \{(q_{t+1}, \ell_{t+1})\}$$

Agents observe only $X_t$. Each contributes one event. Nothing is removed or relocated.

### 1.2 The Two Prior Descriptions

**NARC** treats the partition function as a dynamical object. At each step, an agent selects $(q, \ell)$ from the instantaneous Gibbs distribution:

$$P(q, \ell \mid X_t) = \frac{\exp(-H(q, \ell;\, X_t))}{\mathcal{Z}(X_t)}$$

The partition function changes with each placement:

$$\delta\mathcal{Z}(t) = \mathcal{Z}(X_{t+1}) - \mathcal{Z}(X_t)$$

The NARC non-equilibrium parameter $\Xi(t) = \delta\mathcal{Z}(t)/\mathcal{Z}(X_t)$ measures how fast the action landscape is reorganizing. Its time series identifies quasi-static intervals, secular drift, and phase transitions.

**VEGA** identifies the partition function as Bayesian model evidence. The variational free energy of an agent with approximate posterior $q(s)$ under generative model $p(s,o)$:

$$\mathcal{F} = \mathbb{E}_q[\log q - \log p] = -\log p(o) + D_{\mathrm{KL}}[q \| p(\cdot \mid o)]$$

When the generative model is Gibbs, the minimum achievable free energy is:

$$\mathcal{F}^*(X_t) = -\log \mathcal{Z}(X_t)$$

Therefore $\mathcal{Z}(X_t) = \exp(-\mathcal{F}^*(X_t))$. The artifact $X_t$ IS the externalized collective generative model. The collective construction process IS distributed variational inference over a jointly constructed, jointly inverted generative model written on a shared surface.

### 1.3 The FORGE Identification

These two descriptions share one equation. Substituting VEGA's identity into NARC's parameter:

$$\Xi(t) = \frac{\exp(-\mathcal{F}^*(X_{t+1})) - \exp(-\mathcal{F}^*(X_t))}{\exp(-\mathcal{F}^*(X_t))}$$

Let $\delta\mathcal{F}^* = \mathcal{F}^*(X_{t+1}) - \mathcal{F}^*(X_t)$. Then:

$$\Xi(t) = \exp(-\delta\mathcal{F}^*) - 1$$

For $|\delta\mathcal{F}^*| \ll 1$ (quasi-static sessions or any individual step of moderate size):

$$\Xi(t) = -\delta\mathcal{F}^*(X_t) + O\!\left((\delta\mathcal{F}^*)^2\right)$$

The exact form for all step sizes:

$$\delta\mathcal{F}^*(X_t) = -\log(1 + \Xi(t))$$

Both directions are exact. Neither is approximate. They are the same quantity expressed in two notations.

---

## Part II — Three Values, One Meaning

Every mark any agent places does one of exactly three things to the collective's inference capacity:

### 2.1 $\Xi(t) < 0$: The mark makes the collective's inference problem harder

$\delta\mathcal{F}^* > 0$: the minimum achievable free energy increased. The landscape compressed. Available probability mass in the occupied region decreased. This is the **local ratchet** — the ordinary condition throughout most of a session, at every step where an agent places a mark in territory that was previously available.

In NARC terms: $\mathcal{Z}_R(X_{t+1}) \leq \mathcal{Z}_R(X_t)$ for occupied regions $R$. In VEGA terms: the collective's shared generative model has become more constrained — it must now account for the new mark as a structural element of the prior, reducing the explanatory scope available for subsequent placements.

The free energy increase $\delta\mathcal{F}^* = -\log(1 + \Xi(t))$ is the precise cost, in nats, that this mark imposed on every subsequent agent's inference problem.

### 2.2 $\Xi(t) > 0$: The mark makes the collective's inference problem easier

$\delta\mathcal{F}^* < 0$: the minimum achievable free energy decreased. A new register opened. The landscape expanded discontinuously. Available probability mass increased globally. This is the **phase transition** — rare, identifiable, maximally informative.

In NARC terms: a positive spike in the $\Xi(t)$ time series; a new topological region of the expressive manifold has been entered. In VEGA terms: the collective's shared generative model has gained explanatory scope — model depth expanded from $h$ to $h+1$, and the available prior space has discontinuously increased.

The free energy decrease $|\delta\mathcal{F}^*| = \log(1 + \Xi(t))$ is the inference capacity gained by this depth expansion, in nats.

### 2.3 $\Xi(t) = 0$: The mark changes nothing at the inference level

$\delta\mathcal{F}^* = 0$: the collective's minimum achievable free energy is unchanged. The mark had negligible effect on the global energy landscape. The Gibbs approximation is exact at this moment. The collective is at quasi-static equilibrium for this step.

In NARC terms: the quasi-static regime — standard pseudolikelihood is exact. In VEGA terms: the shared generative model's evidence is stationary — the collective's inference capacity neither grew nor contracted.

### 2.4 The Trichotomy is Exhaustive

Before FORGE these three conditions required two frameworks to describe. After FORGE they are three values of one scalar — $\Xi(t)$, equivalently $-\delta\mathcal{F}^*$ — with one thermodynamic meaning: **the rate at which the collective's inference capacity is changing per agent step.**

The collective construction session is fully described, at the inference level, by this scalar time series.

---

## Part III — The FORGE Equation in Full

### 3.1 The Entropy Production Decomposition, Unified

NARC's entropy production decomposition:

$$\sigma(t) = \log(1 + \Xi(t)) + \Delta\langle H \rangle(t)$$

Substituting the FORGE identity $\log(1 + \Xi(t)) = -\delta\mathcal{F}^*(X_t)$:

$$\sigma(t) = -\delta\mathcal{F}^*(X_t) + \Delta\langle H \rangle(t)$$

The entropy production per step is the sum of the free energy change (structural reorganization of the collective's inference capacity) and the mean energy change (behavioral dissipation through the quasi-static component).

The two terms have distinct roles:

- $-\delta\mathcal{F}^*(X_t)$: the **inference capacity term** — how much the collective's ability to account for its action space changed at this step. Negative when the landscape compresses (ordinary ratchet). Positive when a new register opens (phase transition).

- $\Delta\langle H \rangle(t)$: the **behavioral term** — the average energy change encoding the quasi-static behavioral parameters $\beta$. This term is nonzero even when $\Xi \approx 0$, because agents are actively selecting low-energy placements that shift the mean energy of the distribution.

### 3.2 The Free Energy Trajectory

From the FORGE identity, the free energy trajectory is directly reconstructable from the $\Xi(t)$ time series:

$$\mathcal{F}^*(X_n) = \mathcal{F}^*(X_0) - \sum_{t=1}^n \log(1 + \Xi(t))$$

This is the complete cumulative record of how the collective's inference capacity has evolved across the session — the integral of the $\Xi(t)$ time series under the logarithmic map.

The free energy at any point in the session:

$$\mathcal{F}^*(X_t) = -\log \mathcal{Z}(X_t) = \mathcal{F}^*(X_0) - \sum_{s=1}^t \log(1 + \Xi(s))$$

**The $\Xi(t)$ time series is sufficient to reconstruct the full free energy trajectory.** No additional computation is required. NARC's empirical object contains VEGA's dynamical object as a simple transformation.

### 3.3 The Information Geometry

The FORGE identity connects to the information geometry of the statistical manifold. The Fisher-Rao metric $G_F(\theta)$ on the space of generative models governs the curvature of the free energy landscape. The free energy change per step:

$$\delta\mathcal{F}^* = -\Xi(t) + O(\Xi^2)$$

is the first-order displacement along the free energy surface. The second-order correction $O(\Xi^2)$ encodes the curvature of the statistical manifold at the current collective model state — the same curvature that appears in FERN's barrier height conjecture and in DRAIN's boundary curvature correction $\Gamma_R$.

The exact FORGE relation $\delta\mathcal{F}^* = -\log(1 + \Xi(t))$ is the nonlinear correction that makes the identity exact at all step sizes, not just infinitesimal ones.

---

## Part IV — The Energy Function as Generative Model

### 4.1 The Decomposition

The interaction energy decomposes into a weighted sum of spatial feature functions:

$$H(q, \ell;\, X_t) = \sum_{k=1}^K \beta_k\, f_k(q, \ell;\, X_t)$$

In NARC: each $\beta_k$ is a behavioral parameter quantifying the strength and direction of one spatial tendency. In VEGA: each $\beta_k$ is a prior weight — a structural element of the collective's shared generative model. In FORGE: these are the same thing because $H$ IS the generative model.

The feature functions encode:

**Density interaction** $f_{\text{density}}$: attraction/inhibition toward occupied regions. In NARC: governs local ratchet dynamics ($\beta_{\text{density}} < 0$ produces clustering, accelerating local saturation). In VEGA: encodes the collective's spatial density prior. In FORGE: the sign and magnitude of $\beta_{\text{density}}$ determines whether the $\Xi(t)$ series shows clustered negative spikes (clustering) or smooth secular drift (inhibition).

**Mark interaction** $f_{\text{match}}$: categorical homophily/heterophily. In NARC: determines mark-type co-occurrence structure. In VEGA: encodes the categorical prior over mark types. In FORGE: $\beta_{\text{match}} < 0$ produces register-stratified saturation dynamics visible as type-correlated negative drift in $\Xi(t)$.

**Symmetry gain** $f_{\text{symmetry}}$: bilateral balance preference. In NARC: tendency to complete symmetry axes. In VEGA: symmetry prior in the generative model. In FORGE: symmetry completion produces directionally anisotropic free energy trajectories — $\delta\mathcal{F}^*$ is smaller for placements along symmetry axes than off-axis.

**Void attraction** $f_{\text{void}}$: preference for unoccupied Voronoi territory. In NARC: space-filling dynamics. In VEGA: coverage prior. In FORGE: $\beta_{\text{void}} \ll 0$ produces accelerating negative $\Xi(t)$ drift as available Voronoi territory decreases — the Michaelis-Menten consumption profile in SMELT.

**Boundary interaction** $f_{\text{edge}}$: edge avoidance or anchoring. In NARC: boundary-conditioned placement distribution. In VEGA: spatial boundary prior. In FORGE: determines the initial distribution of $\Xi(t)$ increments — boundary-anchored sessions have systematically different early $\delta\mathcal{F}^*$ profiles than interior-preferring sessions.

**Scale coherence** $f_{\text{scale}}$: local size matching. In NARC: scale-correlated placement dynamics. In VEGA: scale prior. In FORGE: introduces scale-stratified structure into the $\Xi(t)$ series.

### 4.2 Mark Geometry as Prior Anisotropy

Marks are not dimensionless labels. Each placed mark is fully described by $(q, \ell, r, \phi, \epsilon)$ — type, centroid, scale, orientation, execution deviation. Mark geometry enters the generative model as anisotropic prior constraints. In FORGE terms: the orientation $\phi$ and type $q$ of each placed mark creates an anisotropic contribution to $\delta\mathcal{F}^*$ — the free energy change is not isotropic in the action space but depends on the geometric relationship between the new mark and all prior marks.

---

## Part V — Inference: One Pass

### 5.1 The Unified Problem

Before FORGE, the inferential workflow required two separate analyses of the same data:

1. NARC Level I: estimate $\hat{\beta}$ by pseudolikelihood
2. NARC Level II: recover $\hat{\Xi}(t)$ from residuals
3. VEGA: interpret $\hat{\Xi}(t)$ as model evidence dynamics $\delta\hat{\mathcal{F}}^*$

After FORGE, steps 2 and 3 collapse. The $\Xi(t)$ time series IS the free energy trajectory. Recovering one recovers the other by the monotone transformation $\delta\mathcal{F}^* = -\log(1 + \Xi(t))$.

### 5.2 Level I: Behavioral Parameters

Given observed placement sequence $\{(q_t, \ell_t)\}_{t=1}^n$ with field states $\{X_{t-1}\}_{t=1}^n$:

$$\hat{\beta} = \arg\max_\beta \sum_{t=1}^n \left[\log \exp(-H(q_t, \ell_t;\, X_{t-1};\, \beta)) - \log \mathcal{Z}(X_{t-1};\, \beta)\right]$$

$\hat{\beta}$ characterizes the quasi-static generative model — the collective's shared prior structure during the intervals when $|\Xi(t)| \approx 0$.

### 5.3 Level II: The Free Energy Trajectory

Given $\hat{\beta}$, compute the $\Xi(t)$ series at every step:

$$\hat{\Xi}(t) = \frac{\mathcal{Z}(X_t;\, \hat{\beta}) - \mathcal{Z}(X_{t-1};\, \hat{\beta})}{\mathcal{Z}(X_{t-1};\, \hat{\beta})}$$

The free energy trajectory follows immediately:

$$\hat{\mathcal{F}}^*(X_t) = \hat{\mathcal{F}}^*(X_0) - \sum_{s=1}^t \log(1 + \hat{\Xi}(s))$$

This is the complete non-equilibrium characterization of the session — the history of the collective's inference capacity, in nats, at every step.

### 5.4 Residuals and the Approximation Gap

The pseudolikelihood residual at each step:

$$r(t) = \log P_{\text{obs}}(q_t, \ell_t) - \log \hat{P}_{\text{Gibbs}}(q_t, \ell_t \mid X_{t-1};\, \hat{\beta})$$

Under pure quasi-static behavior, $\{r(t)\}$ is i.i.d. mean-zero. In FORGE terms: systematic structure in $r(t)$ encodes the gap between the agent's approximate posterior (what they actually drew from) and the true instantaneous Gibbs distribution (what the generative model at $X_{t-1}$ predicts). This gap is the variational approximation error — the $D_{\mathrm{KL}}[q_t \| p(\cdot \mid X_{t-1})]$ that VEGA identifies as the source of behavioral residuals.

The correlation structure of $r(t)$ encodes:
- **Sequential non-exchangeability**: marks are not i.i.d. draws — the generative model is changing
- **Attention-lag effects**: agents drawing from stale distributions at high $I_B(t)/\kappa$
- **Phase transition timing**: discontinuous jumps at positive $\Xi$ spikes

The decomposition is now fully unified: $r(t)$ is the behavioral signature of a process operating away from the quasi-static equilibrium whose departure is measured by $\Xi(t) = -\delta\mathcal{F}^*$.

### 5.5 The FORGE Diagnostic

The FORGE diagnostic is the joint plot of $\hat{\Xi}(t)$ and $\hat{\mathcal{F}}^*(X_t)$ on the same axes. Because they are the same series under a monotone transformation, their joint structure characterizes the session completely:

**Sawtooth $\hat{\Xi}(t)$, monotone decreasing $\hat{\mathcal{F}}^*$ with jumps**: φ-stable session (SMELT optimal operating point). Within each register, $\hat{\Xi}(t)$ drifts negative (free energy rising), then at register escape $\hat{\Xi}(t)$ spikes positive (free energy drops discontinuously). The session is advancing through the register hierarchy at the thermodynamically optimal rate.

**Flat $\hat{\Xi}(t)$, slowly rising $\hat{\mathcal{F}}^*$**: under-driven session. The collective's inference capacity is being consumed slowly; the generative model is becoming more constrained without triggering phase transitions. Available low-energy territory remains but agents are not finding it.

**Volatile $\hat{\Xi}(t)$, rapidly rising $\hat{\mathcal{F}}^*$ between large spikes**: over-driven session. The landscape reorganizes faster than agents track it. Variational approximation quality degrades. Residuals carry large systematic structure. Behavioral parameter estimates are biased by the attention-lag mechanism.

---

## Part VI — The FORGE Manifold

### 6.1 Structure

The FORGE manifold $\mathcal{M}_{\text{FORGE}}$ is the space of possible session trajectories, parameterized by:

- **Behavioral parameters** $\beta = (\beta_1, \ldots, \beta_K)$: the collective's shared generative model structure
- **Non-equilibrium trajectory** $\{\Xi(t)\}_{t=1}^n = \{-\delta\mathcal{F}^*(t)\}_{t=1}^n$: the session's history in free energy space
- **Initial condition** $\mathcal{F}^*(X_0)$: the founding mark's contribution to the collective's starting inference capacity

The FORGE identity $\Xi(t) = -\delta\mathcal{F}^*$ means the manifold has a fiber structure: for any fixed $\hat{\beta}$, the full session trajectory is a curve in free energy space, with the $\Xi(t)$ series as its tangent vector at each step.

### 6.2 The Three Layers of the Manifold

**Layer 1 — Quasi-static fiber** ($\Xi(t) \approx 0$): the session is locally at free energy equilibrium. The Gibbs distribution is exact. The collective's inference capacity is stationary. Behavioral parameters are fully identifiable from action sequences in this layer.

**Layer 2 — Drift fiber** ($\Xi(t) < 0$, smooth): the session is in the secular drift regime. The generative model is being compressed. Free energy is rising. This is the ordinary within-register dynamics.

**Layer 3 — Transition fiber** ($\Xi(t) > 0$, isolated spikes): the session is at a phase transition. Free energy drops. The generative model gains depth. These are the singular points of the FORGE manifold — the topological transitions between register attractors.

### 6.3 The Expressive Manifold as the Physical Space

The Riemannian manifold $\mathcal{E}$ of all possible marks is the physical space in which the FORGE trajectory lives. Its parameters $(\tau, \lambda, \theta, w, c, \ell)$ — register, scale, orientation, weight, chromatic position, location — are the coordinates. The metric $g_\mathcal{E}$ determined by human perceptual sensitivity gives the correct distance between marks.

The register $\tau$ is the single topologically discontinuous parameter. Layer 3 transitions on the FORGE manifold correspond exactly to crossing the topological ridges between adjacent registers in $\mathcal{E}$ — the finite-cost barriers $C(\tau_i \to \tau_{i+1})$ that agents can cross only when the within-register free energy exceeds the crossing cost.

---

## Part VII — Connections to the Framework Family

### 7.1 FORGE and SMELT

SMELT's φ-equilibrium condition $\overline{|\Xi|} = \log\phi$ is a condition on the time-averaged free energy rate:

$$\overline{|\delta\mathcal{F}^*|} = \log\phi \approx 0.481$$

The φ-stable session is the one at which the collective's inference capacity changes at the golden-ratio rate on average. Under-driven: $\overline{|\delta\mathcal{F}^*|} < \log\phi$. Over-driven: $\overline{|\delta\mathcal{F}^*|} > \log\phi$.

The golden-ratio split test $\bar{\sigma}_{\text{struct}} / \bar{\sigma}_{\text{behav}} = \phi$ translates in FORGE terms to: the mean free energy rate $\overline{|\delta\mathcal{F}^*|}$ and the mean behavioral energy change $\overline{|\Delta\langle H\rangle|}$ are in golden ratio at the MEP optimum.

### 7.2 FORGE and DRAIN

DRAIN identifies the local partition function mass $\mathcal{Z}_R(X_t)$ as a wealth process with absorbing barrier at $\mathcal{Z}_R = 0$. In FORGE terms: the local free energy $\mathcal{F}^*_R(X_t) = -\log\mathcal{Z}_R(X_t)$ is the quantity being driven toward $+\infty$ (the absorbing state). The DRAIN Itô correction is the second-order term in the FORGE expansion:

$$\delta\mathcal{F}^*_R = -\Xi_R(t) + \frac{\Xi_R(t)^2}{2} + O(\Xi_R^3)$$

The leading term $-\Xi_R$ is the naive estimate. The correction $+\Xi_R^2/2$ is the Itô term — always positive, always making the free energy increase more than the naive estimate predicts, growing as $\mathcal{F}^*_R \to \infty$ (as saturation approaches). This is the FORGE derivation of DRAIN's bias theorem from first principles.

### 7.3 FORGE and FERN

FERN's complexity criterion FERN-T1 states that model depth expansion is required when $\mathcal{F}^*_{\text{col}}(h) > C_{\text{expand}}(h \to h+1)$. In FORGE terms: when the cumulative free energy accumulated by the collective exceeds the expansion barrier, the session crosses into the next register. The positive $\Xi$ spike is the moment when $\delta\mathcal{F}^*$ goes negative — the free energy drops as the new register opens, providing exactly the evidence that FERN identifies as the model depth expansion event.

### 7.4 FORGE and VEGA

VEGA established that the collective construction process is distributed variational inference over a jointly constructed generative model. FORGE provides the operational scalar for tracking this inference in real time: $-\delta\mathcal{F}^*(X_t)$ is the per-step change in the collective's minimum achievable free energy — the rate at which the distributed inference procedure is either consuming or gaining capacity. The full VEGA inference pipeline is contained in the FORGE $\Xi(t)$ series.

### 7.5 FORGE and NARC

NARC established the $\Xi(t)$ time series as the central empirical object of collective construction dynamics. FORGE gives $\Xi(t)$ its deepest interpretation: it is not merely the fractional change in a normalization constant — it is the negative rate of change of the collective's minimum achievable free energy. Every NARC result holds unchanged; FORGE adds the thermodynamic meaning that NARC's non-equilibrium parameter was always carrying but not stated.

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
| FORGE-T1 | **The FORGE Identity**: $\Xi(t) = \exp(-\delta\mathcal{F}^*(X_t)) - 1$; equivalently $\delta\mathcal{F}^*(X_t) = -\log(1 + \Xi(t))$; the non-equilibrium parameter is exactly the negative change in the collective's minimum achievable free energy per step |
| FORGE-T2 | **First-Order Equivalence**: $\Xi(t) \approx -\delta\mathcal{F}^*(X_t)$ to first order; the two quantities are equal in the quasi-static limit and diverge by $O(\Xi^2)$ away from it |
| FORGE-T3 | **Free Energy Trajectory Reconstruction**: the full free energy trajectory $\mathcal{F}^*(X_t)$ is reconstructable from $\Xi(t)$ alone by $\mathcal{F}^*(X_t) = \mathcal{F}^*(X_0) - \sum_{s=1}^t \log(1 + \Xi(s))$; the $\Xi(t)$ series is sufficient |
| FORGE-T4 | **Three-Valued Trichotomy**: every mark does exactly one of: (i) $\Xi < 0$ — increases the collective's minimum achievable free energy (local ratchet); (ii) $\Xi > 0$ — decreases it (phase transition); (iii) $\Xi = 0$ — leaves it unchanged (quasi-static equilibrium) |
| FORGE-T5 | **Entropy Production in Free Energy Language**: $\sigma(t) = -\delta\mathcal{F}^*(X_t) + \Delta\langle H \rangle(t)$; entropy production is the sum of the inference capacity change and the behavioral dissipation term |
| FORGE-T6 | **Itô Correction as Second-Order FORGE Term**: the DRAIN Itô bias $+\Xi^2/2$ is the second-order term in the FORGE Taylor expansion; the FORGE identity is the nonlinear correction that makes the DRAIN bias exact at all step sizes |
| FORGE-T7 | **φ-Equilibrium in Free Energy Language**: the SMELT φ-stable condition $\overline{|\Xi|} = \log\phi$ is equivalent to $\overline{|\delta\mathcal{F}^*|} = \log\phi$; the MEP optimal session operates at golden-ratio free energy rate |
| FORGE-T8 | **FERN Expansion Condition in FORGE**: the FERN-T1 complexity criterion $\mathcal{F}^*_{\text{col}}(h) > C_{\text{expand}}$ is the condition for a positive $\Xi$ spike; the transition occurs when the cumulative free energy accumulated by the collective exceeds the register crossing cost |
| FORGE-T9 | **Behavioral Parameters Determine Free Energy Rate**: the behavioral parameters $\beta$ determine the distribution of $\delta\mathcal{F}^*$ per step through the feature decomposition $H = \sum_k \beta_k f_k$; different $\beta$ regimes produce distinct free energy trajectories |
| FORGE-T10 | **Residuals as Free Energy Approximation Gap**: the pseudolikelihood residuals $r(t)$ encode the gap between the agent's variational approximation and the true instantaneous Gibbs distribution; in FORGE terms, they are the behavioral signature of the variational free energy gap $D_{\mathrm{KL}}[q_t \| p(\cdot \mid X_{t-1})]$ |

### Open Conjectures

| ID | Statement |
|---|---|
| FORGE-C1 | **Free Energy Concavity at Phase Transitions**: the free energy trajectory $\mathcal{F}^*(X_t)$ is locally concave at each positive $\Xi$ spike — the expansion event produces a cusp in the free energy curve whose curvature encodes the size of the register that opened |
| FORGE-C2 | **Fisher-Rao Metric and $\Xi^2$ Correction**: the second-order correction $\Xi^2/2$ in the FORGE expansion is proportional to the Fisher information of the current collective generative model at the step's action — the curvature of the log-likelihood landscape at $(q_t, \ell_t)$ |
| FORGE-C3 | **FORGE Completeness**: the pair $(\hat{\beta}, \{\hat{\Xi}(t)\})$ is a sufficient statistic for the collective construction process — all other quantities derivable from the session (saturation times, phase transition timing, spatial statistics, attention-lag effects) are functions of this pair |
| FORGE-C4 | **Register Depth Scales with Cumulative Free Energy**: the register depth reached by a session of $N$ agents scales as $O(\log N)$; equivalently, the cumulative free energy $\sum_t |\delta\mathcal{F}^*|$ scales as $O(\log N)$ at the φ-equilibrium operating point |
| FORGE-C5 | **Crossing Costs as Free Energy Barriers are Directly Measurable**: the crossing cost $C(\tau_i \to \tau_{i+1})$ equals the free energy barrier height — the peak cumulative $\mathcal{F}^*$ just before the positive $\Xi$ spike corresponding to the $\tau_i \to \tau_{i+1}$ transition; crossing costs are directly readable from the free energy trajectory |

### Working Hypotheses

| ID | Statement |
|---|---|
| FORGE-H1 | **Single-Pass Sufficiency**: running FORGE once on a session recovers everything that running NARC and VEGA separately would recover, plus the FORGE identity that connects them; the two-framework pipeline is replaced by one |
| FORGE-H2 | **Free Energy Rate as Session Fingerprint**: sessions with identical $\hat{\beta}$ but different founding marks produce distinguishable free energy trajectories; the founding mark's effect is encoded in $\mathcal{F}^*(X_0)$ and propagates through all subsequent $\delta\mathcal{F}^*$ values |
| FORGE-H3 | **Scale Universality in Free Energy Language**: the FORGE identity operates at all scales where the four collective construction conditions hold; artistic traditions, collaborative platforms, and language change all follow the same free energy ratchet dynamics as individual sessions |
| FORGE-H4 | **Crossing Cost Hierarchy in Free Energy Units**: the strictly increasing crossing cost hierarchy $C(\tau_i \to \tau_{i+1})$ appears as strictly increasing barrier heights in the free energy trajectory; the propositional text register carries the highest free energy barrier in the human expressive hierarchy |

---

## Part IX — Experimental Protocol

### 9.1 The FORGE Workflow

The FORGE workflow is the NARC protocol augmented by the free energy reconstruction step:

**Step 1** — Collect data: placement sequence $\{(q_t, \ell_t)\}_{t=1}^n$ with field states $\{X_{t-1}\}$ via continuous photography. Minimum $n \geq 30$; distributed spatial coverage; all mark types present.

**Step 2** — Estimate behavioral parameters: $\hat{\beta}$ by maximum pseudolikelihood. This is unchanged from NARC Level I.

**Step 3** — Compute $\hat{\Xi}(t)$ series: $\hat{\Xi}(t) = [\mathcal{Z}(X_t;\hat{\beta}) - \mathcal{Z}(X_{t-1};\hat{\beta})] / \mathcal{Z}(X_{t-1};\hat{\beta})$ at every step.

**Step 4** — Apply the FORGE identity: $\delta\hat{\mathcal{F}}^*(t) = -\log(1 + \hat{\Xi}(t))$ at every step.

**Step 5** — Reconstruct the free energy trajectory: $\hat{\mathcal{F}}^*(X_t) = \hat{\mathcal{F}}^*(X_0) + \sum_{s=1}^t \delta\hat{\mathcal{F}}^*(s)$.

**Step 6** — Read the session diagnostics from the joint $(\hat{\Xi}(t), \hat{\mathcal{F}}^*(X_t))$ plot:
- Sawtooth $\hat{\Xi}$ with monotone-rising $\hat{\mathcal{F}}^*$ interrupted by drops: φ-stable register sequence
- Flat $\hat{\Xi}$ with slowly rising $\hat{\mathcal{F}}^*$: under-driven
- Volatile $\hat{\Xi}$ with rapidly rising $\hat{\mathcal{F}}^*$: over-driven
- Number and magnitude of $\hat{\mathcal{F}}^*$ drops: register count and crossing cost estimates (FORGE-C5)

**Step 7** — Validate: positive $\hat{\Xi}$ spikes (equivalently, drops in $\hat{\mathcal{F}}^*$) should align with independently coded register transitions in the mark sequence.

### 9.2 Identifiability

- $n \geq 30$ actions per session (Level I)
- Continuous field documentation enabling $\hat{\Xi}(t)$ at every step (Level II / FORGE)
- $n_{\text{rep}} \geq 5$ independent sessions for path dependence testing
- $n_{\text{rep}} \geq 20$ for DRAIN saturation spectrum estimation

---

## Part X — Theoretical Summary

| Concept | Definition |
|---|---|
| $\mathcal{Z}(X_t) = \exp(-\mathcal{F}^*(X_t))$ | **VEGA identity**: partition function = Bayesian model evidence = exponent of negative minimum free energy |
| $\Xi(t) = \delta\mathcal{Z}(t)/\mathcal{Z}(X_t)$ | **NARC parameter**: fractional change in partition function per step |
| $\Xi(t) = \exp(-\delta\mathcal{F}^*) - 1$ | **FORGE identity** (exact): the two are the same quantity |
| $\delta\mathcal{F}^*(X_t) = -\log(1 + \Xi(t))$ | **FORGE identity** (free energy form): exact for all step sizes |
| $\Xi(t) \approx -\delta\mathcal{F}^*(X_t)$ | **First-order FORGE**: exact in the quasi-static limit |
| $\Xi(t) < 0$ | Local ratchet: collective inference capacity decreasing; free energy rising |
| $\Xi(t) > 0$ | Phase transition: collective inference capacity increasing; free energy dropping |
| $\Xi(t) = 0$ | Quasi-static equilibrium: inference capacity stationary; Gibbs approximation exact |
| $\hat{\mathcal{F}}^*(X_t) = \hat{\mathcal{F}}^*(X_0) - \sum_{s=1}^t \log(1+\hat{\Xi}(s))$ | Free energy trajectory: reconstructed from $\Xi(t)$ series alone |
| $\sigma(t) = -\delta\mathcal{F}^* + \Delta\langle H\rangle$ | FORGE entropy decomposition: inference capacity change + behavioral dissipation |
| $\overline{|\delta\mathcal{F}^*|} = \log\phi$ | φ-equilibrium in free energy language: SMELT MEP optimum |
| Crossing cost = free energy barrier height | $C(\tau_i \to \tau_{i+1})$ is the peak $\mathcal{F}^*$ just before the register escape positive spike |
| $r(t)$ residuals | Variational approximation gap; behavioral signature of $D_{\mathrm{KL}}[q_t \| p(\cdot \mid X_{t-1})]$ |

---

## Part XI — The Central Claim

NARC and VEGA are the same equation written twice. NARC defines the non-equilibrium parameter $\Xi(t)$ as the fractional change in the partition function — a dynamical quantity for a normalization constant that existing frameworks treated as static. VEGA identifies the partition function as the Bayesian model evidence — proving that the artifact is not the output of distributed inference but the inference itself.

Substituting VEGA's identity into NARC's parameter produces the FORGE identity: $\Xi(t) = -\delta\mathcal{F}^*(X_t)$ to first order, exactly $\exp(-\delta\mathcal{F}^*) - 1$ to all orders. One scalar. One time series. The non-equilibrium dynamics and the free energy dynamics are the same dynamics, expressed in two notations that refer to the same underlying quantity.

Every mark any agent places does one of exactly three things to the collective's minimum achievable free energy: increases it (the ordinary condition — the local ratchet operating), decreases it (the rare event — a new register opening, a phase transition, a model depth expansion), or leaves it unchanged (the quasi-static moment — the Gibbs approximation exact, the collective at momentary inference equilibrium). These three conditions, previously requiring two frameworks to state, are now three values of one scalar with one thermodynamic meaning.

The practical consequence is that the inferential workflow collapses. You estimate $\hat{\beta}$ by pseudolikelihood. You compute $\hat{\Xi}(t)$ at every step. You apply the FORGE transformation to get $\delta\hat{\mathcal{F}}^*$. You reconstruct the full free energy trajectory from its sum. Everything that NARC provides about the non-equilibrium dynamics, and everything that VEGA provides about the free energy dynamics, is now available from one pass over the same data.

The $\Xi(t)$ time series was always carrying the free energy information. FORGE states it.

---

*Status tags: [T] = Analytic theorem · [C] = Open conjecture · [H] = Working hypothesis*

*The FORGE identity $\delta\mathcal{F}^* = -\log(1+\Xi)$ is exact. The first-order approximation $\Xi \approx -\delta\mathcal{F}^*$ is valid for $|\Xi| \ll 1$. Identifiability requires $n \geq 30$ actions per session, distributed spatial coverage, and continuous field documentation enabling $\hat{\Xi}(t)$ computation at every step.*
