# Probabilistic Drake Equation

A computational project exploring a probabilistic, time-dependent formulation of the Drake Equation, combining exoplanet occurrence-rate literature with stochastic models of evolutionary transitions.

**Author:** Izzudin Priyambodo  
**Language:** Python  
**Project type:** Computational astrophysics / probability / scientific computing  
**Status:** In development

---

## 1. Overview

The classical Drake Equation, introduced by Frank Drake in 1961, provides a framework for discussing the number of technologically capable civilizations in the Milky Way:

$$
N = R_* f_p n_e f_l f_i f_c L
$$

Several terms are uncertain, especially those concerning the emergence and evolution of life. This project explores how these uncertainties can be represented using probability distributions and stochastic waiting-time models.

The project has two main components:

1. **Astronomical component:** estimate the expected population of planets that meet an explicitly defined Earth-like / habitable-zone working criterion.
2. **Biological component:** model the time required for a planet to pass through a sequence of evolutionary transitions leading to technological capability.

The aim is not to claim a definitive number of extraterrestrial civilizations. It is to build a transparent, reproducible computational model and examine how its assumptions affect the result.

## 2. Current mathematical framework

### 2.1 Astronomical population

The initial astronomical model is organized by stellar spectral class:

$$
N_E = \sum_{s\in\{F,G,K,M\}} N_{\star,s}\,\eta_{\mathrm{HZ},s}
$$

where:

| Symbol | Meaning |
|---|---|
| $N_{\star,s}$ | Estimated number of Milky Way stars in spectral class $s$ |
| $\eta_{\mathrm{HZ},s}$ | Average number of planets per star meeting the adopted radius and habitable-zone criteria for class $s$ |
| $N_E$ | Expected number of eligible planets in the Milky Way |

Here, $\eta_{\mathrm{HZ},s}$ is an **occurrence rate (average planets per star)**. It is not automatically the probability that a star hosts at least one eligible planet; a system can contain multiple planets.

The occurrence-rate literature does not by itself provide the Milky Way star counts $N_{\star,s}$. Those counts require a separate stellar-population source.

### 2.2 Stochastic evolutionary waiting times

Rather than multiplying a sequence of fixed biological probabilities, the current working approach represents the duration of evolutionary transitions as random waiting times.

For transition $i$, a provisional model is:

$$
\tau_i\mid\lambda_i \sim \operatorname{Exponential}(\lambda_i)
$$

The total time to technological capability is represented as:

$$
T_{\mathrm{tech}} = \sum_{i=1}^{k}\tau_i
$$

where $k$ is the number of transitions defined by the biological framework. The rates $\lambda_i$, their probability distributions, the number of stages, and any dependence between stages still require explicit justification and calibration from the biological literature.

This is a **working model**, not an established conclusion that evolutionary transitions are independent exponential processes.

### 2.3 Expected number reaching technological capability

For a specified available evolutionary time window $T_H$, the working output is:

$$
\mathbb{E}[N_{\mathrm{tech}}] =
N_E\,P(T_{\mathrm{tech}}\leq T_H)
$$

This estimates the expected number of eligible planets on which technological capability has emerged within the chosen time window under the model assumptions.

**The result is not the number of civilizations currently active or communicating.** The classical lifetime parameter $L$ is intentionally excluded from this initial scope. A present-day active-civilization estimate would require a model for civilization duration and temporal overlap.

## 3. Astronomical literature and data

The initial literature review focuses on Kepler-based estimates of rocky or small-planet occurrence in habitable zones.

| Study | Population / scope | Relevant result |
|---|---|---|
| Hsu, Ford & Terrien (2020) | M dwarfs; $0.75$–$1.5\,R_\oplus$ | $0.33^{+0.10}_{-0.12}$ planets per star using the authors' baseline Dirichlet prior |
| Kunimoto & Matthews (2020) | G dwarfs; $0.75$–$1.5\,R_\oplus$, conservative HZ | $0.11^{+0.07}_{-0.05}$ planets per star with catalogue-reliability correction |
| Bryson et al. (2020) | Separate G- and K-dwarf samples; $0.5$–$1.5\,R_\oplus$, conservative HZ | Estimates depend on stellar-temperature group and completeness extrapolation |

These values are **not yet a harmonized parameter set**. Their planet-radius ranges, target samples, inference methods, and completeness assumptions differ. They must not be averaged as though they were measurements under identical conditions.

See [docs/literature_review.md](docs/literature_review.md) for the detailed extraction, assumptions, limitations, and open questions.

### Initial data source

The [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/) is an initial source for confirmed exoplanet and host-star properties.

Potentially useful fields include:

- Planet radius and mass.
- Orbital period and semi-major axis.
- Stellar mass and radius.
- Stellar effective temperature and luminosity.
- Planetary equilibrium temperature, where available.

**Important observational limitation:** the confirmed-planet catalogue is an incomplete, detection-biased sample. Counting confirmed planets in a catalogue does not directly measure the total occurrence rate of planets in the Galaxy. Occurrence-rate studies attempt to correct for survey completeness, reliability, and selection effects. The project will use the catalogue for data exploration and explicitly distinguish that task from estimating the underlying planet population.

## 4. Working scope and definitions

The project focuses on carbon-based, water-associated life as a tractable reference case because Earth is the only known example of life. This is a modeling scope, not a claim that alternative biochemistries are impossible.

The working astronomical comparison range in the initial literature synthesis is $0.75$–$1.5\,R_\oplus$, because it is reported by both Hsu et al. (2020) and Kunimoto & Matthews (2020). It is **not yet a final definition** of an Earth-like planet.

A habitable-zone orbit does not establish that a planet is inhabited or actually habitable. Atmospheric composition, water inventory, geological activity, stellar activity, and other conditions matter. Planet radius alone also does not prove rocky composition.

## 5. Computational approach

Python will be used for:

- Retrieving, cleaning, and exploring astronomical data.
- Documenting selection criteria and parameter provenance.
- Sampling uncertain astronomical occurrence rates.
- Implementing stochastic waiting-time models.
- Running Monte Carlo simulations.
- Quantifying uncertainty and conducting sensitivity analysis.
- Producing reproducible figures and summary statistics.

The precise distributions and inference methods will be selected only after their assumptions have been reviewed and documented.

## 6. Repository structure

The repository will grow as the analysis is implemented. The intended structure is:

    probabilistic-drake-equation/
    ├── docs/
    │   ├── literature_review.md
    │   └── mathematical_framework.md
    ├── data/
    │   ├── raw/
    │   └── processed/
    ├── notebooks/
    │   ├── 01_exoplanet_data.ipynb
    │   ├── 02_occurrence_rates.ipynb
    │   ├── 03_stellar_population.ipynb
    │   ├── 04_waiting_time_model.ipynb
    │   ├── 05_monte_carlo.ipynb
    │   └── 06_sensitivity_analysis.ipynb
    ├── src/
    │   ├── data_processing.py
    │   ├── astronomical_model.py
    │   ├── waiting_time_model.py
    │   ├── monte_carlo.py
    │   └── sensitivity.py
    ├── results/
    │   └── figures/
    ├── references.bib
    ├── requirements.txt
    └── README.md

This is a planned structure; files should be added when their corresponding work begins. Large raw datasets should not be committed blindly. Record their source, retrieval date, query, and any relevant licence or redistribution restrictions.

## 7. Development roadmap

- [x] Define the initial project scope.
- [x] Identify initial Kepler occurrence-rate literature.
- [x] Create an initial literature extraction.
- [ ] Finalize a consistent operational definition of an eligible planet.
- [ ] Harmonize F-, G-, K-, and M-star occurrence-rate inputs.
- [ ] Identify a defensible Milky Way stellar population model by spectral class.
- [ ] Implement and validate the astronomical population calculation $N_E$.
- [ ] Review and specify the biological transition sequence and waiting-time assumptions.
- [ ] Identify evidence and priors for the transition-rate parameters.
- [ ] Implement Monte Carlo propagation of astronomical and biological uncertainty.
- [ ] Perform sensitivity analysis and robustness checks.
- [ ] Document results, limitations, and reproducibility details.

## 8. Immediate next task: estimate Milky Way main-sequence star counts

**Goal:** build a sourced estimate of the number of relevant F-, G-, K-, and M-type main-sequence stars in the Milky Way. This supplies the $N_{\star,s}$ terms in the astronomical model.

### Step-by-step workflow

1. **Keep the population definition consistent.** The occurrence-rate studies used here target dwarf/main-sequence stars. Therefore, the matching Galactic population should initially count main-sequence stars, not all stellar objects indiscriminately.
2. **Use provisional temperature bins for the first comparison.** Kunimoto & Matthews (2020) define:
   - F: $6000 \leq T_{\mathrm{eff}} < 7300$ K
   - G: $5300 \leq T_{\mathrm{eff}} < 6000$ K
   - K: $3900 \leq T_{\mathrm{eff}} < 5300$ K
   - M: provisionally, $T_{\mathrm{eff}} < 3900$ K

   These are working boundaries, not universal definitions. Check the definition used by every population source. Hsu et al.'s M-dwarf sample also has some late-K contamination, which must be recorded rather than ignored.
3. **Find a Milky Way-wide source.** Prefer a peer-reviewed stellar mass-function, luminosity-function, or Galactic population study that estimates counts by stellar mass or spectral type. A local Solar-neighborhood percentage is not automatically representative of the entire Milky Way.
4. **Record the provenance before calculating.** For every source, note its full citation/DOI or arXiv link, Galactic component covered (disk/bulge/halo), whether it counts main-sequence stars, mass or temperature boundaries, reported fraction/count, uncertainty, and the exact page/table/figure.
5. **Calculate counts only from compatible quantities.** If a source provides a total main-sequence population and fractions defined over that same population, then:
   
   $
   N_{\star,s} = N_{\star,\mathrm{MS}} f_s
   $
   
   If a source provides counts directly, retain those instead. Do not multiply a total from one population definition by fractions from another.
6. **Create a comparison table and review it before coding.** Do not fill missing classes with guesses. Mark unavailable values as unknown and identify what additional source is needed.

### Required output table

| Spectral class | Adopted $T_{\mathrm{eff}}$ range | Population definition | Count or fraction | Uncertainty | Source and page/table | Notes |
|---|---|---|---:|---|---|---|
| F | 6000–7300 K (provisional) | Main sequence | To be researched | To be researched | To be researched | |
| G | 5300–6000 K (provisional) | Main sequence | To be researched | To be researched | To be researched | |
| K | 3900–5300 K (provisional) | Main sequence | To be researched | To be researched | To be researched | |
| M | Below 3900 K (provisional) | Main sequence | To be researched | To be researched | To be researched | |

### Do not do these things yet

- Do not calculate $N_E$ using the current occurrence-rate values as if they were final.
- Do not average Hsu, Kunimoto, and Bryson results; their definitions are not fully harmonized.
- Do not use the number of confirmed planets in the NASA Exoplanet Archive as the total number of Milky Way stars.
- Do not start the Monte Carlo simulation or choose biological waiting-time parameters yet.

**Completion condition:** this task is complete only when each adopted count/fraction has a traceable source and the population definitions are compatible. Then the astronomical inputs can be reviewed and implemented in Python.

---

## 9. Limitations

The project faces several fundamental uncertainties:

- Earth is the only known inhabited planet.
- Kepler occurrence rates are subject to finite-sample uncertainty, completeness corrections, reliability corrections, and extrapolation.
- Published studies use different planet-radius ranges, stellar samples, and habitable-zone definitions.
- The Milky Way stellar population by spectral type must be estimated separately.
- The probability distributions and dependence structure of evolutionary waiting times are not yet established.
- A sequence inferred from Earth's history may not represent every possible evolutionary pathway.
- Reaching technological capability is not the same as developing detectable communication or remaining active today.

All outputs must therefore be interpreted as conditional, model-dependent estimates rather than definitive predictions.

## 10. References

- Hsu, D. C., Ford, E. B., & Terrien, R. (2020). *Occurrence Rates of Planets Orbiting M Stars: Applying ABC to Kepler DR25, Gaia DR2, and 2MASS Data.* [arXiv:2002.02573](https://arxiv.org/abs/2002.02573).
- Kunimoto, M., & Matthews, J. M. (2020). *Searching the Entirety of Kepler Data. II. Occurrence Rate Estimates for FGK Stars.* [arXiv:2004.05296](https://arxiv.org/abs/2004.05296).
- Bryson, S., et al. (2020). *The Occurrence of Rocky Habitable Zone Planets Around Solar-Like Stars from Kepler Data.* [arXiv:2010.14812](https://arxiv.org/abs/2010.14812).
- Kopparapu, R. K., et al. (2013). *Habitable Zones Around Main-Sequence Stars: New Estimates.* [DOI: 10.1088/0004-637X/765/2/131](https://doi.org/10.1088/0004-637X/765/2/131).

---

**Project principle:** make assumptions explicit, preserve uncertainty, and keep every result traceable to its data and source.
