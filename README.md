
# Probabilistic Drake Equation

**A probabilistic computational framework for estimating the number of carbon-based technological civilizations that have emerged in the Milky Way.**

**Author:** Izzudin Priyambodo  
**Field:** Computational Physics / Mathematical Modeling / Astrobiology  
**Project Type:** Independent Computational Project  
**Status:** In Development

---

## 1. Project Overview

The Drake Equation, introduced by Frank Drake in 1961, provides a framework for estimating the number of technologically capable civilizations in the Milky Way.

Traditionally, the equation is expressed as:

$$
N = R_* \times f_p \times n_e \times f_l \times f_i \times f_c \times L
$$

Although several astronomical parameters have become increasingly constrained through modern observations, biological parameters remain highly uncertain. In particular, the probabilities of abiogenesis, biological evolution, the emergence of intelligence, and the development of technological civilizations are still poorly understood.

This project explores a probabilistic reformulation of the Drake Equation by combining observational astronomical data with statistical and evolutionary models adopted from existing scientific literature.

Rather than assigning a single fixed value to each uncertain parameter, the project represents uncertain quantities using probability distributions and stochastic models. Monte Carlo simulation is then used to propagate these uncertainties and estimate the resulting distribution of technological civilizations.

The primary focus of this project is mathematical modeling, probabilistic analysis, and computational simulation rather than developing new biological or astrobiological theories.

The model focuses on carbon-based life and Earth-like planetary environments as a practical reference case, using the only known example of life and technological civilization: Earth.

---

## 2. Project Objectives

The main objectives of this project are:

- To construct a probabilistic reformulation of the Drake Equation.
- To estimate the population of potentially habitable Earth-like planets using astronomical observations and published occurrence-rate studies.
- To distinguish between different stellar populations, including F, G, K, and M-type main-sequence stars.
- To adopt existing statistical and evolutionary models for major biological transitions.
- To incorporate evolutionary timing into the probability of reaching technological civilization.
- To integrate astronomical and biological uncertainties into a unified mathematical framework.
- To perform Monte Carlo simulations to evaluate uncertainty in the estimated number of technological civilizations.
- To identify the most influential parameters through sensitivity analysis.

---

## 3. Scientific Scope

### 3.1 Carbon-Based Life

This project focuses on carbon-based life using water as its primary solvent.

The choice is based on the fact that all currently known life forms on Earth rely on carbon-based biochemistry. Carbon can form a wide variety of stable chemical bonds, allowing the formation of complex organic molecules such as proteins, DNA, and RNA.

This chemical flexibility provides an empirical foundation for studying the emergence of complex biological systems.

The restriction does not imply that non-carbon-based life is impossible. It is introduced to establish a more clearly defined research scope and reduce the number of assumptions required by the mathematical model.

### 3.2 Earth-Like Planets

The model considers potentially habitable terrestrial planets with characteristics resembling Earth.

The initial selection criteria include:

- Rocky or terrestrial planetary composition.
- Location within the circumstellar habitable zone.
- Orbit around a main-sequence star.
- Planetary radius and, where available, mass within predefined Earth-like ranges.

The habitable zone is defined as the region around a star where surface liquid water may be possible under suitable atmospheric conditions.

These criteria are used as screening conditions rather than proof that a planet is actually habitable or inhabited.

Planetary radius alone does not establish rocky composition, and habitable-zone location does not guarantee the presence of liquid water.

The operational selection criteria will be finalized based on published occurrence-rate studies to maintain consistency between the astronomical data and the statistical model.

**References:**

- [Kopparapu et al. (2013) — Habitable Zones Around Main-Sequence Stars](https://doi.org/10.1088/0004-637X/765/2/131)
- [Schulze-Makuch et al. (2011) — A Two-Tiered Approach to Assessing the Habitability of Exoplanets](https://doi.org/10.1089/ast.2010.0592)

---

## 4. Mathematical Framework

The model separates the problem into two major components:

1. Estimating the population of eligible Earth-like planets.
2. Estimating the probability that biological evolution reaches technological capability within the available planetary time window.

### 4.1 Astronomical Population

The astronomical component estimates the expected number of eligible planets in the Milky Way.

The initial formulation is:

$$
N_E = \sum_{s \in \{F,G,K,M\}}
N_{\star,s}\eta_{E,s}
$$

Where:

| Parameter | Description |
|---|---|
| $N_E$ | Expected number of eligible Earth-like planets |
| $N_{\star,s}$ | Number of main-sequence stars in stellar class $s$ in the Milky Way |
| $\eta_{E,s}$ | Average number of eligible planets per star in stellar class $s$ |
| $s$ | Stellar spectral class: F, G, K, or M |

The occurrence rate $\eta_{E,s}$ represents the average number of planets per star satisfying the adopted planetary criteria. It is not necessarily the probability that a star hosts at least one eligible planet.

The stellar population and occurrence rates will be obtained from separate astronomical studies.

Published occurrence-rate estimates will be treated as uncertain quantities rather than exact constants.

### 4.2 Biological Evolutionary Pathway

The biological component considers a simplified evolutionary pathway based on the known history of life on Earth:

**Earth-like Planet → Abiogenesis → Eukaryotic Life → Multicellularity → Intelligence → Technological Civilization**

The corresponding conditional probabilities are:

| Parameter | Description |
|---|---|
| $P_A$ | Probability of abiogenesis |
| $P_{EU}$ | Probability of evolving eukaryotic life, conditional on abiogenesis |
| $P_M$ | Probability of multicellular evolution, conditional on eukaryotic life |
| $P_I$ | Probability of developing intelligence, conditional on multicellular evolution |
| $P_C$ | Probability of developing technological civilization, conditional on intelligence |

The probability of completing the evolutionary pathway can be represented using the chain rule:

$$
P_{\mathrm{success}} =
P_A P_{EU|A} P_{M|EU} P_{I|M} P_{C|I}
$$

These probabilities are conditional on the preceding evolutionary stages and the assumed planetary environment.

This pathway is a working simplification based on Earth's evolutionary history. It is not a claim that every possible carbon-based intelligent organism must follow exactly the same evolutionary sequence.

### 4.3 Evolutionary Timing

In addition to the probability of evolutionary transitions, the time required for these transitions is important.

A planet has a finite period during which its environment may remain suitable for the development of complex life.

Therefore, this project also considers evolutionary transitions as stochastic waiting-time processes.

For transition $i$, the waiting time is represented by:

$$
\tau_i \sim f_i(t|\theta_i)
$$

Where:

- $\tau_i$ is the waiting time associated with evolutionary transition $i$.
- $f_i$ is the probability distribution of the waiting time.
- $\theta_i$ represents the parameters of the selected statistical model.

The total time required to reach technological capability is:

$$
T_{\mathrm{tech}} =
\tau_A+\tau_{EU}+\tau_M+\tau_I+\tau_C
$$

The probability of completing the evolutionary pathway within the available habitability window is:

$$
P(T_{\mathrm{tech}}\leq T_H)
$$

Where $T_H$ represents the available evolutionary time window of the planet.

The initial approach will investigate hard-step evolutionary models and stochastic waiting-time distributions based on existing literature.

The exponential distribution may be considered as a baseline model:

$$
\tau_i|\lambda_i \sim \operatorname{Exponential}(\lambda_i)
$$

However, the choice of distribution, transition rates, and dependence between evolutionary stages must be justified using scientific literature.

The conditional probability and waiting-time formulations must also be combined carefully. If a transition's probability of occurring is already represented by its waiting-time model, the same probability must not be multiplied again.

### 4.4 Final Model

The expected number of planets that have reached technological civilization within the available evolutionary time window is:

$$
\boxed{
\mathbb{E}[N_{\mathrm{tech}}]
=
N_E P_{\mathrm{tech}}(T_H)
}
$$

Here, $P_{\mathrm{tech}}(T_H)$ represents the probability that the complete evolutionary pathway succeeds and reaches technological capability within the available time window.

The model aims to produce a probability distribution rather than a single deterministic estimate.

**Note on the lifetime parameter:** The classical Drake Equation includes $L$, the average lifetime of a communicating civilization. This project intentionally omits $L$ because its objective is to estimate the number of planets that have reached technological capability during their evolutionary time windows, rather than the number of civilizations communicating at a particular moment.

Estimating currently active civilizations would require an additional civilization-lifetime model.

---

## 5. Astronomical Data and Literature

### 5.1 NASA Exoplanet Archive

The primary astronomical data source is the [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/).

The initial dataset uses the **Planetary Systems Composite Parameters (PSCompPars)** table, which provides planetary and stellar parameters for confirmed exoplanets.

Relevant parameters include:

- Planetary radius and mass.
- Orbital period and semi-major axis.
- Stellar mass and radius.
- Stellar effective temperature.
- Stellar luminosity.
- Planetary equilibrium temperature.

The data will be processed to identify exoplanets satisfying the predefined Earth-like selection criteria.

Additional documentation:

- [PSCompPars Table Documentation](https://exoplanetarchive.ipac.caltech.edu/docs/pscp_about.html)
- [Data Column Definitions](https://exoplanetarchive.ipac.caltech.edu/docs/API_TD_columns.html)
- [NASA Exoplanet Archive TAP Documentation](https://exoplanetarchive.ipac.caltech.edu/docs/TAP/usingTAP.html)
- [NASA Habitable Zone](https://science.nasa.gov/exoplanets/habitable-zone/)

**Important methodological consideration:** The catalog of confirmed exoplanets is not a complete census of the Milky Way. Detection biases and survey completeness must be considered before extrapolating the observed sample to the total galactic population.

Therefore, the confirmed-planet catalog will primarily be used for data exploration and planetary characterization, while occurrence-rate studies will provide estimates of the underlying planet population.

### 5.2 Planet Occurrence Rates

To estimate the population of Earth-like planets, this project adopts occurrence-rate estimates from published studies.

The initial literature includes:

**Hsu, Ford & Terrien (2020)**

*Occurrence Rates of Planets Orbiting M Stars: Applying ABC to Kepler DR25, Gaia DR2, and 2MASS Data.*

This study estimates the occurrence rate of planets around M-type stars using Approximate Bayesian Computation (ABC).

For planets with radii of $0.75$–$1.5\,R_\oplus$, the authors report:

$$
\eta_{M,HZ}=0.33^{+0.10}_{-0.12}
$$

using their baseline Dirichlet prior.

Reference: [arXiv:2002.02573](https://arxiv.org/abs/2002.02573)

**Kunimoto & Matthews (2020)**

*Searching the Entirety of Kepler Data. II. Occurrence Rate Estimates for FGK Stars.*

This study estimates planet occurrence rates around F, G, and K-type stars using Kepler data and Approximate Bayesian Computation.

For G-type stars and planets with radii of $0.75$–$1.5\,R_\oplus$ in the conservative habitable zone, the reliability-corrected estimate is:

$$
\eta_{G,HZ}=0.11^{+0.07}_{-0.05}
$$

The estimate involves extrapolation into orbital periods where Kepler completeness is limited.

Reference: [arXiv:2004.05296](https://arxiv.org/abs/2004.05296)

**Bryson et al. (2020)**

*The Occurrence of Rocky Habitable Zone Planets Around Solar-Like Stars from Kepler Data.*

This study estimates the occurrence of rocky habitable-zone planets using Kepler DR25 and updated stellar properties.

It provides separate estimates for G- and K-type stellar populations and investigates the effects of different completeness assumptions.

The main analysis considers planets with radii of $0.5$–$1.5\,R_\oplus$.

Reference: [arXiv:2010.14812](https://arxiv.org/abs/2010.14812)

**Methodological consideration:**

The results of these studies cannot be combined directly because they use different planetary-radius ranges, stellar samples, completeness assumptions, and statistical methods.

The occurrence-rate parameters must first be harmonized before being used in the final astronomical model.

Detailed extraction and comparison are documented in [`docs/literature_review.md`](docs/literature_review.md).

---

## 6. Biological Models and Scientific Literature

The biological parameters will be based on previously published statistical and evolutionary models.

### 6.1 Abiogenesis — Bayesian Inference

**Spiegel & Turner (2012)**

*Bayesian Analysis of the Astrobiological Implications of Life's Early Emergence on Earth.*

This study applies Bayesian inference to examine the implications of the relatively early emergence of life on Earth.

The authors demonstrate that the estimated probability of abiogenesis depends strongly on the choice of prior distribution and the limited observational evidence available.

This framework provides a starting point for modeling:

$$
P_A =
P(\text{Abiogenesis}|\text{Earth-like conditions})
$$

Reference: [DOI: 10.1073/pnas.1111694108](https://doi.org/10.1073/pnas.1111694108)

### 6.2 Evolutionary Transitions — Hard-Step Model

**Carter (1983)**

*The Anthropic Principle and its Implications for Biological Evolution.*

The hard-step model proposes that certain evolutionary transitions may be intrinsically unlikely relative to the available time for biological evolution.

These transitions are treated as stochastic events that must occur within a finite planetary habitability window.

The model provides a theoretical basis for investigating the timing of major evolutionary transitions.

Reference: [Carter (1983), Philosophical Transactions of the Royal Society A](https://sseh.uchicago.edu/doc/Carter_Phil_Trans_1983.pdf)

### 6.3 Bayesian Hard-Step Model

**Snyder-Beattie et al. (2021)**

*The Timing of Evolutionary Transitions Suggests Intelligent Life is Rare.*

This research develops a Bayesian approach to evolutionary timing and examines the implications of major evolutionary transitions for the probability of intelligent life.

It provides a more quantitative framework for studying evolutionary transitions under the hard-step hypothesis.

Reference: [DOI: 10.1089/ast.2019.2149](https://doi.org/10.1089/ast.2019.2149)

### 6.4 Alternative Evolutionary Model

**Mills et al. (2025)**

*A Reassessment of the "Hard-Steps" Model for the Evolution of Intelligent Life.*

This study critically examines the assumptions of the classical hard-step model.

The authors propose that the timing of evolutionary transitions may be influenced by the gradual development of suitable planetary environmental conditions rather than solely by intrinsically improbable biological events.

This provides an alternative theoretical scenario for comparison with the hard-step framework.

Reference: [DOI: 10.1126/sciadv.ads5698](https://doi.org/10.1126/sciadv.ads5698)

### 6.5 Technological Civilization

The probability of intelligence developing into technological civilization is a particularly uncertain parameter.

Unlike abiogenesis and several major evolutionary transitions, there is currently no well-established empirical probability distribution for this process.

This parameter will therefore require additional literature review and explicit prior assumptions.

Alternative probability scenarios may be examined through sensitivity analysis.

---

## 7. Computational Methodology

The project will use a combination of probabilistic modeling and numerical simulation.

### Step 1 — Astronomical Data Collection

Retrieve exoplanet and stellar parameters from the NASA Exoplanet Archive.

Review published occurrence-rate studies and determine consistent planetary selection criteria.

Identify estimates of the Milky Way stellar population by spectral class.

### Step 2 — Astronomical Population Estimation

Estimate the expected number of eligible planets using:

$$
N_E =
\sum_{s\in\{F,G,K,M\}}
N_{\star,s}\eta_{E,s}
$$

The uncertainties in stellar population estimates and occurrence rates will be documented and incorporated where suitable statistical information is available.

### Step 3 — Biological Model Construction

Adopt statistical and evolutionary models from existing literature for the major biological transitions.

Construct probability distributions or Bayesian posteriors for the biological parameters.

Investigate evolutionary waiting-time models and their relationship to the available planetary time window.

### Step 4 — Monte Carlo Simulation

Monte Carlo simulation will be used to propagate uncertainty through the mathematical model.

For each iteration:

1. Sample astronomical parameters from their selected probability distributions.
2. Sample biological parameters or evolutionary transition times.
3. Calculate the probability of reaching technological capability within the planetary time window.
4. Combine the biological and astronomical components.
5. Repeat the process over a sufficiently large number of iterations.
6. Analyze the resulting distribution.

The initial simulation target is approximately $10^5$ to $10^6$ iterations, subject to convergence testing.

### Step 5 — Sensitivity Analysis

Sensitivity analysis will be performed to determine which parameters contribute most strongly to uncertainty in the final estimate.

The initial method under consideration is **Sobol sensitivity analysis**, with appropriate treatment of parameter dependence where necessary.

---

## 8. Expected Results

The expected outputs of this project include:

- A probabilistic reformulation of the Drake Equation.
- An astronomical dataset with documented planetary selection criteria.
- An estimated population of eligible Earth-like planets.
- Probability distributions for major biological transitions.
- A stochastic model of evolutionary timing.
- Monte Carlo simulation results.
- Statistical summaries of the estimated number of technological civilizations.
- Sensitivity analysis identifying the most influential parameters.

The primary output will be a probability distribution rather than a single deterministic estimate.

The results will be interpreted as model-dependent estimates under explicitly stated assumptions, rather than definitive predictions about extraterrestrial life.

---

## 9. Project Structure

The repository is planned to follow this structure:

```text
probabilistic-drake-equation/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── docs/
│   ├── literature_review.md
│   └── mathematical_framework.md
│
├── notebooks/
│   ├── 01_exoplanet_data.ipynb
│   ├── 02_planetary_selection.ipynb
│   ├── 03_occurrence_rates.ipynb
│   ├── 04_stellar_population.ipynb
│   ├── 05_biological_models.ipynb
│   ├── 06_monte_carlo.ipynb
│   └── 07_sensitivity_analysis.ipynb
│
├── src/
│   ├── data_processing.py
│   ├── astronomical_model.py
│   ├── probability_models.py
│   ├── monte_carlo.py
│   └── sensitivity.py
│
├── results/
│   └── figures/
│
├── references.bib
├── requirements.txt
└── README.md
```

---

## 10. Current Development Status

- [x] Initial project concept and objectives.
- [x] Define the initial carbon-based and Earth-like planetary scope.
- [x] Identify initial biological literature.
- [x] Identify initial astronomical occurrence-rate literature.
- [x] Download NASA PSCompPars dataset.
- [x] Create initial literature extraction for occurrence-rate studies.
- [ ] Finalize Earth-like planetary selection criteria.
- [ ] Harmonize F-, G-, K-, and M-star occurrence-rate estimates.
- [ ] Estimate the Milky Way stellar population by spectral class.
- [ ] Calculate the expected population of eligible planets.
- [ ] Finalize the biological transition and waiting-time framework.
- [ ] Determine probability distributions and prior assumptions.
- [ ] Implement the probabilistic model in Python.
- [ ] Perform Monte Carlo simulations.
- [ ] Perform sensitivity analysis.
- [ ] Evaluate model assumptions and limitations.

**This repository is an independent computational project in development.** The mathematical formulation, parameter distributions, and computational implementation may be revised as the literature review and analysis progress.

---

## References

1. Drake, F. D. (1961). The origins of the search for extraterrestrial intelligence.
2. Carter, B. (1983). The Anthropic Principle and its Implications for Biological Evolution.
3. Spiegel, D. S., & Turner, E. L. (2012). Bayesian analysis of the astrobiological implications of life's early emergence on Earth. *PNAS*. [DOI](https://doi.org/10.1073/pnas.1111694108)
4. Snyder-Beattie, A., et al. (2021). The Timing of Evolutionary Transitions Suggests Intelligent Life is Rare. *Astrobiology*. [DOI](https://doi.org/10.1089/ast.2019.2149)
5. Mills, D. B., et al. (2025). A Reassessment of the "Hard-Steps" Model for the Evolution of Intelligent Life. *Science Advances*. [DOI](https://doi.org/10.1126/sciadv.ads5698)
6. Kopparapu, R. K., et al. (2013). Habitable Zones Around Main-Sequence Stars: New Estimates. *The Astrophysical Journal*. [DOI](https://doi.org/10.1088/0004-637X/765/2/131)
7. Schulze-Makuch, D., et al. (2011). A Two-Tiered Approach to Assessing the Habitability of Exoplanets. *Astrobiology*. [DOI](https://doi.org/10.1089/ast.2010.0592)
8. Hsu, D. C., Ford, E. B., & Terrien, R. (2020). Occurrence Rates of Planets Orbiting M Stars. [arXiv](https://arxiv.org/abs/2002.02573)
9. Kunimoto, M., & Matthews, J. M. (2020). Searching the Entirety of Kepler Data. II. Occurrence Rate Estimates for FGK Stars. [arXiv](https://arxiv.org/abs/2004.05296)
10. Bryson, S., et al. (2020). The Occurrence of Rocky Habitable Zone Planets Around Solar-Like Stars from Kepler Data. [arXiv](https://arxiv.org/abs/2010.14812)

**Astronomical Data Source:** [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/)

**Project Principle:** Make assumptions explicit, preserve uncertainty, and keep every result traceable to its data and scientific source.
