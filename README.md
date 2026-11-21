# Probabilistic Drake Equation

**A computational project exploring a probabilistic approach to estimating the number of carbon-based technological civilizations in the Milky Way.**

**Author:** Izzudin Priyambodo  
**Language:** Python  
**Project Type:** Computational Science / Mathematical Modeling  
**Status:** In Development

---

## 1. Overview

The Drake Equation, introduced by Frank Drake in 1961, provides a framework for estimating the number of technologically capable civilizations in the Milky Way.

The classical equation is expressed as:

$$
N = R_* \times f_p \times n_e \times f_l \times f_i \times f_c \times L
$$

Although astronomical observations have improved significantly over the past decades, several parameters remain highly uncertain, particularly those associated with the emergence and evolution of life.

This project explores a probabilistic reformulation of the Drake Equation by combining astronomical observations with statistical models from existing scientific literature.

Instead of assigning fixed values to uncertain biological parameters, this approach represents them using probability distributions. Monte Carlo simulation is then used to propagate uncertainty and examine the resulting distribution of possible technological civilizations.

The project primarily focuses on mathematical modeling, probability theory, statistical inference, and scientific computing.

## 2. Objectives

The main objectives are:

- Reformulate the classical Drake Equation into a probabilistic model.
- Explore astronomical data from the NASA Exoplanet Archive.
- Identify potentially Earth-like exoplanets using predefined physical criteria.
- Investigate existing statistical models of abiogenesis and biological evolution.
- Integrate different probability models into a unified mathematical framework.
- Implement Monte Carlo simulations using Python.
- Perform sensitivity analysis to identify the most influential parameters.

## 3. Scientific Background

### 3.1 Why Carbon-Based Life?

This project focuses on carbon-based life using water as its primary solvent.

Carbon is particularly interesting because of its ability to form stable covalent bonds with itself and many other elements. This allows the formation of complex organic molecules, including proteins, DNA, and RNA.

All currently known life on Earth relies on carbon-based biochemistry. Therefore, carbon-based life provides the strongest available empirical foundation for studying the emergence of biological complexity.

This restriction does not imply that alternative forms of life are impossible. It simply establishes a more manageable scope for the mathematical model.

### 3.2 Earth-Like Planets

The model considers terrestrial planets with characteristics resembling Earth.

The initial selection criteria include:

- Rocky planetary composition.
- Location within the circumstellar habitable zone.
- Orbit around a main-sequence star.
- Planetary mass and radius within predefined Earth-like ranges.

The habitable zone refers to the region around a star where liquid water could potentially exist on a planet's surface under suitable atmospheric conditions.

References:

- [Kopparapu et al. (2013) — Habitable Zones Around Main-Sequence Stars](https://doi.org/10.1088/0004-637X/765/2/131)
- [Schulze-Makuch et al. (2011) — A Two-Tiered Approach to Assessing the Habitability of Exoplanets](https://doi.org/10.1089/ast.2010.0592)

## 4. Mathematical Model

The initial probabilistic formulation is:

$$
N_{\mathrm{tech}} =
N_E \times P_A
\times P_{EU|A}
\times P_{M|EU}
\times P_{I|M}
\times P_{C|I}
$$

Where:

| Parameter | Description |
|---|---|
| $N_E$ | Estimated population of eligible Earth-like planets |
| $P_A$ | Probability of abiogenesis |
| $P_{EU|A}$ | Probability of eukaryotic evolution given abiogenesis |
| $P_{M|EU}$ | Probability of multicellular evolution given eukaryotic life |
| $P_{I|M}$ | Probability of intelligence given multicellular evolution |
| $P_{C|I}$ | Probability of technological civilization given intelligence |

The biological parameters are treated as uncertain quantities represented by probability distributions.

The proposed evolutionary pathway is:

**Earth-like Planet → Abiogenesis → Eukaryotic Life → Multicellularity → Intelligence → Technological Civilization**

The conditional formulation is a simplified working model based on the evolutionary history of life on Earth. Alternative evolutionary pathways may be considered as the project develops.

### Why Is the Lifetime Parameter Excluded?

The classical Drake Equation includes $L$, representing the average lifetime of a communicating civilization.

This project initially excludes $L$ because its focus is on estimating the number of eligible planets that reach technological civilization within a defined evolutionary time window, rather than the number of civilizations communicating at a particular moment.

Therefore, the resulting quantity should not be interpreted as the number of currently active civilizations.

## 5. Data Sources

### NASA Exoplanet Archive

The primary astronomical data source is the [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/).

The project uses the Planetary Systems Composite Parameters (PSCompPars) catalog as an initial source of exoplanet data.

Relevant parameters include:

- Planetary radius and mass.
- Orbital period and semi-major axis.
- Stellar mass and radius.
- Stellar effective temperature.
- Stellar luminosity.
- Planetary equilibrium temperature.

Additional resources:

- [NASA Exoplanet Archive Documentation](https://exoplanetarchive.ipac.caltech.edu/docs/intro.html)
- [PSCompPars Documentation](https://exoplanetarchive.ipac.caltech.edu/docs/pscp_about.html)
- [NASA Habitable Zone](https://science.nasa.gov/exoplanets/habitable-zone/)

**Note:** Confirmed exoplanet catalogs are incomplete observational samples. Estimating the total population of Earth-like planets requires accounting for detection biases and occurrence rates, rather than simply counting confirmed planets.

## 6. Statistical Models and Literature

The biological parameters are investigated using existing scientific models.

| Biological Process | Mathematical Approach | Main Reference |
|---|---|---|
| Abiogenesis | Bayesian inference | Spiegel & Turner (2012) |
| Eukaryotic evolution | Hard-step model | Carter (1983) |
| Multicellular evolution | Bayesian hard-step framework | Snyder-Beattie et al. |
| Emergence of intelligence | Hard-step / alternative evolutionary models | Carter (1983); Mills et al. (2025) |
| Technological civilization | Exploratory probability model | Further literature review |

### Key References

**1. Abiogenesis**

Spiegel, D. S., & Turner, E. L. (2012).

*Bayesian Analysis of the Astrobiological Implications of Life's Early Emergence on Earth.*

[DOI: 10.1073/pnas.1111694108](https://doi.org/10.1073/pnas.1111694108)

**2. Hard-Step Evolution**

Carter, B. (1983).

*The Anthropic Principle and its Implications for Biological Evolution.*

[Paper](https://sseh.uchicago.edu/doc/Carter_Phil_Trans_1983.pdf)

**3. Bayesian Hard-Step Model**

Snyder-Beattie, A. et al. (2021).

*The Timing of Evolutionary Transitions Suggests Intelligent Life is Rare.*

[DOI: 10.1089/ast.2019.2149](https://doi.org/10.1089/ast.2019.2149)

**4. Alternative Evolutionary Model**

Mills, B. J. W. et al. (2025).

*A Reassessment of the "Hard-Steps" Model for the Evolution of Intelligent Life.*

[DOI: 10.1126/sciadv.ads5698](https://doi.org/10.1126/sciadv.ads5698)

These studies provide different perspectives on the statistical interpretation of biological evolution. Their assumptions and mathematical formulations will be examined before implementation.

## 7. Computational Methods

Python will be used for data processing, mathematical modeling, and numerical simulation.

### Bayesian Inference

Used to investigate uncertain parameters, particularly the probability or rate of abiogenesis.

### Probability Distributions

Different probability distributions will be considered depending on the mathematical structure and assumptions of each biological model.

### Monte Carlo Simulation

Random samples will be generated from the selected probability distributions and propagated through the probabilistic Drake Equation.

The resulting simulations will be used to examine:

- Mean and median estimates.
- Variance and uncertainty intervals.
- Probability of zero technological civilizations.
- Probability of at least one other technological civilization.

### Sensitivity Analysis

Sensitivity analysis will investigate how uncertainty in individual parameters affects the final model output.

The initial method under consideration is Sobol sensitivity analysis.

## 8. Project Structure

```text
probabilistic-drake-equation/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_exoplanet_data.ipynb
│   ├── 02_planetary_selection.ipynb
│   ├── 03_biological_models.ipynb
│   ├── 04_monte_carlo.ipynb
│   └── 05_sensitivity_analysis.ipynb
│
├── src/
│   ├── data_processing.py
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

## 9. Development Roadmap

- [x] Define the initial project concept.
- [x] Establish the mathematical framework.
- [x] Identify relevant scientific literature.
- [ ] Retrieve NASA exoplanet data.
- [ ] Implement Earth-like planet selection.
- [ ] Investigate and implement biological probability models.
- [ ] Integrate the probability distributions.
- [ ] Implement Monte Carlo simulation.
- [ ] Perform sensitivity analysis.
- [ ] Document results and model limitations.

## 10. Limitations

This project involves several important limitations:

- Earth is currently the only known example of an inhabited planet.
- The probability of abiogenesis remains highly uncertain.
- Major evolutionary transitions may not be independent.
- The hard-step hypothesis is not universally accepted.
- The transition from intelligence to technological civilization is poorly constrained.
- Exoplanet observations are affected by detection and selection biases.

The results should therefore be interpreted as model-dependent estimates rather than definitive predictions about extraterrestrial life.

---

**Project Philosophy**

The goal is not to produce a definitive answer to whether extraterrestrial civilizations exist, but to explore how mathematical and statistical methods can be used to represent uncertainty in one of the most interesting questions in science.
