# Literature Review: Rocky Habitable-Zone Planet Occurrence Rates

**Project:** Probabilistic Drake Equation  
**Status:** Initial source extraction; parameter harmonization is still in progress.  
**Scope:** Three Kepler-based occurrence-rate studies used to inform the astronomical part of the model.

This document records what the selected papers actually estimate. The values below are not yet a finalized set of model inputs.

## 1. What an occurrence rate means

In these studies, an occurrence rate such as \(\eta_{\oplus}\) or \(f_{\mathrm{HZ}}\) is generally an **average number of planets per target star** within a specified planet-radius and orbital/habitable-zone range.

It is not automatically the probability that a randomly selected star has at least one such planet. A star can host more than one planet, so an average occurrence rate can in principle exceed one.

A planet orbiting in the habitable zone is not necessarily habitable. The habitable zone is a climate-based orbital/irradiation criterion; actual surface conditions also depend on factors such as atmosphere, water inventory, geology, and stellar activity.

## 2. Summary of the selected studies

| Study | Stellar population | Planet-radius range | HZ definition / treatment | Main result |
|---|---|---:|---|---|
| Hsu et al. (2020) | M dwarfs (sample includes some late-K contamination) | \(0.75\)–\(1.5\,R_\oplus\) | Runaway-greenhouse to maximum-greenhouse limits from Kopparapu et al. (2013), evaluated for individual stars | \(f_{M,\mathrm{HZ}}=0.33^{+0.10}_{-0.12}\) with the baseline Dirichlet prior |
| Kunimoto & Matthews (2020) | G dwarfs, \(5300\leq T_{\mathrm{eff}}<6000\) K | \(0.75\)–\(1.5\,R_\oplus\) | Conservative HZ; for a Sun-like star, \(0.99\)–\(1.70\) AU | \(0.13^{+0.09}_{-0.06}\), or \(0.11^{+0.07}_{-0.05}\) after their reliability correction |
| Bryson et al. (2020) | Separate K and G populations | \(0.5\)–\(1.5\,R_\oplus\) | Conservative HZ; star-dependent instellation | K: \(0.32\)–\(0.42\); G: \(0.38\)–\(0.63\), depending on completeness extrapolation |

**Important:** These values should not be averaged or inserted into one parameter table without harmonizing the radius range, stellar-temperature cuts, HZ definition, and statistical treatment.

---

## 3. Hsu, Ford & Terrien (2020): M-dwarf occurrence rates

**Paper:** *Occurrence Rates of Planets Orbiting M Stars: Applying ABC to Kepler DR25, Gaia DR2, and 2MASS Data*  
**Source:** [arXiv:2002.02573](https://arxiv.org/abs/2002.02573)

### Data and method

The authors combine the Kepler DR25 planet-candidate catalogue with updated stellar information from Gaia DR2 and the 2MASS Point Source Catalog. Their selected sample contains:

- 1,746 Kepler M-dwarf targets.
- 89 associated planet candidates.
- A sample dominated by early M dwarfs; approximately 80% are earlier than M4.5 according to the paper's adopted classification.

They use Approximate Bayesian Computation (ABC), including a forward model for planet detection and vetting. The study evaluates two prior choices for the occurrence-rate model:

1. A Dirichlet prior on the relative rates across radius bins, with a prior on the total rate.
2. Independent uniform priors for the occurrence rates in individual bins.

The authors identify the Dirichlet-prior results as their baseline results.

### Habitable-zone definition

The paper defines the habitable zone using the runaway-greenhouse and maximum-greenhouse limits from Kopparapu et al. (2013), calculated on a star-by-star basis.

The reported HZ occurrence rate is marginalized over the M-star target sample. The authors note that the sample is dominated by early M dwarfs, so it should not be interpreted as a uniformly representative sample of every M-dwarf subtype.

### Result relevant to this project

For planets with radii \(0.75\)–\(1.5\,R_\oplus\), the authors report:

| Prior | HZ occurrence rate |
|---|---:|
| Dirichlet (authors' baseline) | \(0.33^{+0.10}_{-0.12}\) planets per star |
| Uniform | \(0.44^{+0.29}_{-0.17}\) planets per star |

The difference is material: the estimate is sensitive to the prior, particularly because the sample is relatively small.

### Limitations to retain in the project notes

- The target sample is small compared with the FGK samples used in some Kepler studies.
- The result changes with prior choice; the Dirichlet result is the authors' baseline, not a prior-free measurement.
- The M-dwarf sample includes some late-K stars and is dominated by early-M stars.
- The authors apply an FGK-derived detection-efficiency model because the available M-dwarf injection tests are insufficient for a fully independent M-dwarf detection model.
- The paper discusses the limitations of treating the sample as representative of the full M-dwarf population.

**Project interpretation:** \(0.33\) is a useful literature-based starting point for an M-dwarf comparison at \(0.75\)–\(1.5\,R_\oplus\), but its posterior/prior sensitivity must be carried into the uncertainty analysis.

---

## 4. Kunimoto & Matthews (2020): FGK occurrence rates

**Paper:** *Searching the Entirety of Kepler Data. II. Occurrence Rate Estimates for FGK Stars*  
**Source:** [arXiv:2004.05296](https://arxiv.org/abs/2004.05296)

### Data and method

The study builds an independent Kepler planet catalogue and estimates occurrence rates using Approximate Bayesian Computation. It accounts for detection efficiency, vetting efficiency, uncertainty in planet radius, and catalogue reliability against transit-like noise.

The stellar sample contains 96,280 FGK stars, divided using the paper's effective-temperature cuts:

- F: \(6000\leq T_{\mathrm{eff}}<7300\) K.
- G: \(5300\leq T_{\mathrm{eff}}<6000\) K.
- K: \(3900\leq T_{\mathrm{eff}}<5300\) K.

The G-star sample contains 39,173 targets.

### Habitable-zone definition and extrapolation

For a Sun-like G star, the paper uses the conservative habitable zone from Kopparapu et al. (2013), approximately \(0.99\)–\(1.70\) AU. This corresponds to orbital periods of approximately 360–809 days.

The Kepler sensitivity and completeness constraints make this regime difficult to measure directly. The authors therefore extrapolate occurrence-rate information from the 237–500 day period range to cover the conservative-HZ period range. They explicitly caution that such extrapolations are uncertain and that the resulting estimates should be interpreted as upper limits.

### Result relevant to this project

For G-type stars and planets with radii \(0.75\)–\(1.5\,R_\oplus\), the conservative-HZ estimate is:

| Treatment | Occurrence rate |
|---|---:|
| Baseline estimate | \(0.13^{+0.09}_{-0.06}\) planets per star |
| Including catalogue reliability correction | \(0.11^{+0.07}_{-0.05}\) planets per star |

The abstract also reports an 84.1st-percentile upper limit of less than 0.18 planets per G-type star for this radius and HZ definition.

### Limitations to retain in the project notes

- The relevant HZ periods extend beyond the range where Kepler completeness is well constrained.
- The result depends on extrapolating from shorter periods.
- The authors state that the estimates should be treated as upper limits because the relevant long-period, small-planet bins are poorly constrained and have no detections in the relevant parameter ranges.
- The reported value changes when catalogue reliability is incorporated.

**Project interpretation:** The reliability-corrected value \(0.11^{+0.07}_{-0.05}\) is a useful G-dwarf reference for a \(0.75\)–\(1.5\,R_\oplus\) comparison, but it is not a precise direct count of Earth analogues.

---

## 5. Bryson et al. (2020): rocky HZ occurrence around solar-like stars

**Paper:** *The Occurrence of Rocky Habitable Zone Planets Around Solar-Like Stars from Kepler Data*  
**Source:** [arXiv:2010.14812](https://arxiv.org/abs/2010.14812)

### Data and method

The study uses the Kepler DR25 planet-candidate catalogue and Gaia-based stellar properties. It corrects for catalogue completeness and reliability and includes uncertainties in planet radius, instellation, and stellar effective temperature.

The authors use both a Poisson-likelihood Bayesian method and Approximate Bayesian Computation. They examine multiple population models and recommend Model 1 as their baseline.

### Relevant stellar populations and result

Table 5 reports Model 1 results from the Poisson-likelihood method for the conservative HZ, with uncertainties in planet radius, instellation, and stellar effective temperature included.

For planets with radii \(0.5\)–\(1.5\,R_\oplus\):

| Stellar population | Low occurrence-rate bound | High occurrence-rate bound |
|---|---:|---:|
| K dwarfs, \(3900\)–\(5300\) K | \(0.32^{+0.35}_{-0.17}\) | \(0.42^{+0.50}_{-0.23}\) |
| G dwarfs, \(5300\)–\(6000\) K | \(0.38^{+0.50}_{-0.22}\) | \(0.63^{+0.94}_{-0.38}\) |

These are planets per star. The low and high occurrence-rate bounds correspond to two different assumptions about completeness beyond 500 days:

- **Low bound:** constant-completeness extrapolation beyond 500 days.
- **High bound:** zero-completeness extrapolation beyond 500 days.

The uncertainties shown alongside each value are the paper's 68% credible intervals. The low/high values are not themselves a single 68% credible interval.

For context, the abstract reports a conservative-HZ occurrence range of \(0.37^{+0.48}_{-0.21}\) to \(0.60^{+0.90}_{-0.36}\) planets per star for the broader \(4800\)–\(6300\) K population and \(0.5\)–\(1.5\,R_\oplus\) planets.

### Limitations to retain in the project notes

- Kepler completeness products are available only up to orbital periods of approximately 500 days; occurrence rates beyond this require extrapolation.
- The two extrapolation assumptions produce a broad range of estimates.
- The number of detected small HZ planets is low, producing large uncertainties.
- The separate K- and G-star values use a \(0.5\)–\(1.5\,R_\oplus\) radius range, which differs from the \(0.75\)–\(1.5\,R_\oplus\) range used in the Hsu and Kunimoto comparison above.

**Project interpretation:** This paper is especially useful because it reports separate G- and K-dwarf results and explicitly quantifies the impact of completeness extrapolation. Its tabulated values should remain a separate comparison until the radius range is harmonized.

---

## 6. Cross-study interpretation

### What can be compared

Hsu et al. and Kunimoto & Matthews both report HZ occurrence rates for the \(0.75\)–\(1.5\,R_\oplus\) radius range. Their estimates provide a preliminary comparison between M- and G-star populations:

- M stars: \(0.33^{+0.10}_{-0.12}\) planets per star using Hsu et al.'s baseline Dirichlet prior.
- G stars: \(0.11^{+0.07}_{-0.05}\) planets per star using Kunimoto & Matthews' reliability-corrected estimate.

This is a comparison between two different studies, samples, and inference pipelines. It should not be interpreted as a controlled experiment isolating stellar spectral type.

### What cannot yet be combined

The Bryson et al. K- and G-star values use \(0.5\)–\(1.5\,R_\oplus\), not \(0.75\)–\(1.5\,R_\oplus\). They also report a low/high range caused by alternative completeness extrapolations. These estimates cannot simply be averaged with the other two studies.

The selected papers do not yet provide a harmonized set of F-, G-, K-, and M-star occurrence-rate posteriors under one common definition.

### Provisional project decision

For the next stage, \(0.75\)–\(1.5\,R_\oplus\) is a practical **working comparison range** because it is reported by both Hsu et al. and Kunimoto & Matthews. It is not yet a final definition of an Earth-like planet.

Bryson et al. should be retained as a sensitivity/comparison source until a matching \(0.75\)–\(1.5\,R_\oplus\) estimate can be extracted or derived from a suitable posterior/model output.

## 7. Implications for the probabilistic Drake model

The astronomical component is intended to estimate the expected number of eligible planets:

\[
N_E = \sum_{s\in\{F,G,K,M\}} N_{\star,s}\,\eta_{\mathrm{HZ},s}
\]

where:

- \(N_{\star,s}\) is the Milky Way population of stars in spectral class \(s\).
- \(\eta_{\mathrm{HZ},s}\) is the average number of planets per star meeting the adopted radius and HZ criteria for that class.
- \(N_E\) is an expected population, not a direct count of confirmed planets.

The occurrence-rate literature alone does not provide \(N_{\star,s}\). A separate, defensible estimate of the Milky Way stellar population by spectral type is required.

The final implementation should also propagate uncertainty in the occurrence rates. It should not treat the central values in this document as exact constants. If the full posterior samples are unavailable, any approximation to the published posterior must be documented as an approximation rather than presented as the original posterior.

## 8. Open questions and next research tasks

1. **Finalize the operational planet definition.** Decide whether the working \(0.75\)–\(1.5\,R_\oplus\) range is appropriate, and state clearly that radius plus HZ location does not prove habitability or rocky composition.
2. **Harmonize occurrence rates.** Find or derive comparable F-, G-, K-, and M-star estimates using consistent radius and HZ definitions.
3. **Find Milky Way stellar population counts.** Obtain \(N_{\star,F}\), \(N_{\star,G}\), \(N_{\star,K}\), and \(N_{\star,M}\) from a defensible stellar-population source.
4. **Represent uncertainty correctly.** Prefer published posterior samples or distributions. If only quantiles are available, document the approximation used to sample them.
5. **Calculate the astronomical population.** Implement and test the calculation of \(N_E\) before connecting it to the biological model.
6. **Then calibrate the biological waiting-time model.** Keep assumptions about evolutionary waiting times separate from the astronomical occurrence-rate inputs.

## References

1. Hsu, D. C., Ford, E. B., & Terrien, R. (2020). *Occurrence Rates of Planets Orbiting M Stars: Applying ABC to Kepler DR25, Gaia DR2, and 2MASS Data.* [arXiv:2002.02573](https://arxiv.org/abs/2002.02573).
2. Kunimoto, M., & Matthews, J. M. (2020). *Searching the Entirety of Kepler Data. II. Occurrence Rate Estimates for FGK Stars.* [arXiv:2004.05296](https://arxiv.org/abs/2004.05296).
3. Bryson, S., et al. (2020). *The Occurrence of Rocky Habitable Zone Planets Around Solar-Like Stars from Kepler Data.* [arXiv:2010.14812](https://arxiv.org/abs/2010.14812).
4. Kopparapu, R. K., et al. (2013). *Habitable Zones Around Main-Sequence Stars: New Estimates.* [DOI: 10.1088/0004-637X/765/2/131](https://doi.org/10.1088/0004-637X/765/2/131).

---

**Review status:** Initial extraction completed for the three selected papers. No final F/G/K/M parameter set has been adopted.
