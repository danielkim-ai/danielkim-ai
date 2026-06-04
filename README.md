<p align="center">
  <img src="https://raw.githubusercontent.com/danielkim-ai/portfolio-2026/main/public/assets/symbolic-diagram.svg" width="350" alt="Stats-CS-RL Symbolic Diagram" />
</p>

<h1 align="center">ARCHITECTING RELIABLE INTELLIGENCE THROUGH BAYESIAN FOUNDATIONS</h1>
<h3 align="center">Navigating the nexus of sequential decision-making and statistical rigour</h3>
<p align="center"><strong>Yonsei University | CS &amp; Applied Statistics</strong></p>

<p align="center">
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" alt="PyTorch" />
  <img src="https://img.shields.io/badge/R_Language-276DC3?style=flat-square&logo=r&logoColor=white" alt="R" />
  <img src="https://img.shields.io/badge/SQLD-4A4A4A?style=flat-square" alt="SQLD" />
  <img src="https://img.shields.io/badge/ADsP-4A4A4A?style=flat-square" alt="ADsP" />
</p>

---

## Academic Honours &amp; Leadership

**Yonsei Artificial Intelligence (YAI) Club**
* **Best Academic Group Award (Mar 2026):** Spearheaded collective research as a Tutor, orchestrating multidisciplinary collaboration that elevated the team's rigorous theoretical investigations to top-tier recognition.
* **Best Academic Member (Jan 2023):** Recognised for individual excellence and outstanding contributions to deep learning seminars and rigorous academic presentations.
* *[YAI Official Notion](https://y-ai.notion.site/)*

**Samsung AI Challenge:** Recognised as an Award Nominee, demonstrating robust capabilities in applied machine learning algorithms.

---

## Core Research Interests

My academic trajectory is anchored in interrogating the structural guarantees of intelligent systems at the intersection of **Statistics (Theory)**, **Reinforcement Learning (Domain)**, and **Computer Science (Systems)**.

```
          Stats (Theory)
             /       \
            /         \
           /           \
   RL (Domain)   CS (Systems)
```

### Bayesian Reinforcement Learning
**Sample efficiency via uncertainty estimation &amp; Variational inference.**

Interrogating the convergence of Bayesian statistics and reinforcement learning to maximise sample efficiency within high-dimensional state spaces. By transitioning beyond conventional point estimation, I am investigating the structural guarantees of uncertainty estimation. This entails leveraging variational inference for robust posterior approximation and quantifying epistemic uncertainty within a Variational Actor-Critic framework.

### Privacy-Preserving Offline RL
**Differential privacy guarantees &amp; Machine unlearning in sequential decision-making.**

Establishing the structural guarantees of $(\epsilon, \delta)$-Differential Privacy within offline reinforcement learning, particularly concerning sensitive medical and financial logs. Rather than relying on naive noise injection, this work implements utility-optimised mechanisms that negotiate the privacy-utility trade-off via precise optimisation under constraints, including machine unlearning for efficient policy updates and robust policy evaluation under stringent privacy boundaries.

---

## Global Hub

- [Portfolio](https://github.com/danielkim-ai/portfolio-2026): website, research profile, and public technical materials.
- [Projects](https://github.com/danielkim-ai/projects): implementation archive for reinforcement learning and trustworthy ML experiments.
- [Coursework](https://danielkim-ai.vercel.app/coursework): study notes and mathematical foundations across statistics and reinforcement learning.

---

## ?뱥 Research Project Log

### ??Stability of Bayesian-SAC under Non-Stationary Reward Scaling

> **Status:** Completed | **Repo:** [`projects/policy-learning-stability`](https://github.com/danielkim-ai/projects/tree/main/policy-learning-stability)

Studies whether entropy-regularised continuous-control policies remain stable when reward magnitudes drift over time. Uses a Gymnasium reward wrapper to induce sinusoidal and abrupt-collapse scaling regimes, coupled with Bayesian temperature adaptation guided by a Gaussian Process surrogate.

**Core Contributions:**
- Formalises reward scaling as a non-stationary process $\tilde{r}_t = \alpha_t r_t$ and tracks how changing reward magnitude can miscalibrate static entropy schedules.
- Implements Bayesian entropy-temperature adaptation so the policy retains uncertainty-aware exploration when reward evidence becomes sparse or compressed.
- Provides MuJoCo/Ray-oriented experiment scaffolding, automated visualisation, and diagnostics for collapse variance under sinusoidal drift and abrupt reward collapse.

---

### ??Bayesian RL Meets MCMC (Phase 1?? Complete)

> **Status:** All phases complete | **Repo:** [`projects/bayesian-rl-meets-mcmc`](https://github.com/danielkim-ai/projects/tree/main/bayesian-rl-meets-mcmc)

A completed four-phase programme for posterior-aware reinforcement learning under data scarcity, validated on HalfCheetah-v4, Ant-v4, Hopper-v4, and Humanoid-v4.

**Phase Breakdown:**
- **Phase 1 ??Foundations:** Low-data diagnostic infrastructure, Variational Actor-Critic baselines, SGLD building blocks, and report-facing calibration, regret, effective sample size, and PAC-Bayes metrics.
- **Phase 2 ??MuJoCo Validation:** Stability analysis for continuous-control benchmarks, including regret-oriented comparison against brittle point-estimated exploration. Demonstrated sub-linear Bayesian regret $\tilde{O}(\sqrt{dT})$ vs. frequentist $O(T)$.
- **Phase 3 ??MCMC Posterior Analysis:** SGLD posterior traces over policy and selected RL hyperparameters across all four MuJoCo environments. Hyperparameter posterior estimation and comprehensive calibration analysis.
- **Phase 4 ??Differential Privacy Integration:** Clipped/noisy training hooks, epsilon sensitivity studies, privacy-budget plots, and final posterior/performance artefacts. Completes the full privacy-preserving Bayesian RL pipeline.

---

### Trustworthy Offline RL via DP &amp; Machine Unlearning (Completed)

> **Status:** Completed | **Repo:** [`projects/trustworthy-offline-rl-via-dp`](https://github.com/danielkim-ai/projects/tree/main/trustworthy-offline-rl-via-dp)

This completed project establishes a multi-domain framework integrating trajectory-level Differential Privacy $(\varepsilon \approx 2.74)$ and Implicit Q-Learning (IQL) to guarantee secure sequence optimisation without the out-of-distribution value-collapse typical of CQL under heavy gradient noise.

The implementation demonstrates deterministic seed-based execution and high-fidelity domain proxies for MIMIC-III sepsis treatment and FinRL trading. This architecture audits privacy leakage risk and decision-making loss transparently, separating the effect of DP noise from uncontrolled database access or irreproducible sampling.

**Core Contributions:**
- Implements trajectory-level DP-SGD with episode-wise clipping and RDP-compatible privacy accounting.
- Implements LiSSA influence-function unlearning and SISA shard identification for deletion requests.
- Introduces `PrivacyAwareIQL`, reducing DP-induced gradient variance by relying on in-sample expectile regression rather than OOD action sampling.
- Supports MIMIC-III-style ICU trajectories and FinRL-style trading trajectories through a shared `EpisodeBatch` abstraction.

**Featured Cross-Domain Plots:**

| Medical Domain (MIMIC-III Sepsis Proxy) | Financial Domain (FinRL Trading Proxy) |
| --- | --- |
| ![Medical MIA Margin](https://raw.githubusercontent.com/danielkim-ai/projects/main/trustworthy-offline-rl-via-dp/results/plots/plot_unlearning_margin_medical_iql.png) | ![Financial Utility Trade-off](https://raw.githubusercontent.com/danielkim-ai/projects/main/trustworthy-offline-rl-via-dp/results/plots/plot_utility_tradeoff_financial_iql.png) |
| MIA distribution collapse indicating strong membership indistinguishability $(\varepsilon \approx 2.74)$. | In-sample expectile regression showing tight utility-gap containment $(\Delta J \approx 0.98)$ under private perturbations. |

---

### ?럳 Capstone Project ??Optimising Contextual Sentence Prediction Models for AI-Assisted Authoring Tools ([Episod](https://episod.ink/))

> **Status:** Completed | **Role:** Evaluation Model Team Member (2 of 4) | **Repo:** Private industrial repository; code not publicly available due to intellectual property constraints.

A university capstone initiative conducted in collaboration with [Episod](https://episod.ink/), a live AI-assisted creative-writing platform. The project was centred on optimising contextual sentence prediction models and constructing a rigorous evaluation framework to assess the quality of AI-generated outputs within the production environment.

**Key Contributions:**
- Designed and refined evaluation rubrics integrating **Contextual Coherence**, **Creativity**, and **Fluency** criteria, establishing a structured and reproducible scoring methodology across diverse narrative registers.
- Engineered and optimised **LLM-as-judge evaluation prompts** for Gemini 2.5 models, implementing rigorous calibration procedures using benchmark datasets to ensure scoring consistency and sensitivity.
- Generated and analysed **110 empirical test cases** (20 per book across 11 books) to validate model consistency, identify scoring sensitivity thresholds, and surface systematic failure modes.
- Collaborated on improving **prompt efficiency** and developing structured feedback extraction mechanisms to support continuous refinement of the deployed prediction system.

> ?뵏 **Intellectual Property Notice:** The source code, internal evaluation benchmarks, and proprietary datasets associated with this engagement are not publicly available. All implementation details remain within a private industrial repository in accordance with intellectual property constraints.

---

## ?렞 Current Focus

Rather than mere implementation, my current focus is directed towards interrogating fundamental academic questions:

* **Uncertainty Quantification:** How can we construct tight bounds on epistemic uncertainty to prevent catastrophic degradation in out-of-distribution state spaces?
* **Utility-Optimised Privacy:** To what extent can we integrate $(\epsilon, \delta)$-Differential Privacy into offline policy evaluation without compromising the convergence properties of the target policy?
* **Algorithmic Unlearning:** What are the theoretical prerequisites for provable machine unlearning in sequential decision-making paradigms, ensuring minimal computational overhead whilst maintaining model integrity and predictable behaviour?

---

## ?벉 Contact Information

I welcome discourse with fellow researchers and practitioners regarding potential collaborations or theoretical discussions.

* **Email**: [coderpoirot@gmail.com](mailto:coderpoirot@gmail.com) / [daniel1kim@yonsei.ac.kr](mailto:daniel1kim@yonsei.ac.kr)
* **LinkedIn**: [danielkim-ai](https://www.linkedin.com/in/danielkim-ai/)
* **Portfolio**: [danielkim-ai.vercel.app](https://danielkim-ai.vercel.app)

<br/>

<p align="center">
  <small><em>"The ultimate prerogative of choice must remain anchored in human agency, ensuring accountability within the algorithmic framework."</em></small>
</p>

