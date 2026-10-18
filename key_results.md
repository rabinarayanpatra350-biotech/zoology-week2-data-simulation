# Key results

Virtual Data Collection Simulation and Analysis — Zoology Research Assistant Internship, Week 2

Rabi Narayan Patra | 5 October 2026


## The dataset

- 981 recordings, 24 cities, 30 species
- recordings per city: 22–59
- missing: noise 3.47%, light 1.94%
- flagged low-quality: 14; flagged outliers: 7
- analysis sample after exclusions: 922 recordings

## Hypotheses and outcomes

| Hypothesis | Outcome |
|---|---|
| H1 Noise raises minimum song frequency | **Supported** — 4.48 Hz/dB (95% CI 4.07–4.90, p < 0.001) |
| H2 Light advances onset | **Supported** — -0.444 min per unit radiance (CI -0.482 to -0.406) |
| H2 Light delays cessation | **Supported** — +0.638 min (CI 0.592–0.685) |
| H3 Noise x light interaction on timing | **Not resolved** — estimate -0.0060 (p = 0.017) |
| H4 Biome moderates the noise effect | **Not supported** — no term survives Benjamini-Hochberg (adjusted p = 0.096, 0.277) |
| H5 The shift is too small to matter | **Supported** — ~128 Hz shift recovers an estimated 2.7% of lost active space |

## Recovery against the known truth

| Parameter | True | Recovered | % of true | 95% CI |
|---|---|---|---|---|
| Noise -> minimum frequency (Hz per dB) | 5.0 | 4.48 | 90% | [4.07, 4.90] |
| Body mass -> minimum frequency (Hz per log10 g) | -1757.7 | -1795.8 | 102% | [-1828.2, -1763.3] |
| Light -> onset (minutes per unit radiance) | -0.4 | -0.444 | 111% | [-0.482, -0.406] |
| Light -> cessation (minutes per unit radiance) | 0.6 | 0.638 | 106% | [0.592, 0.685] |
| Noise x light interaction -> onset | -0.002 | -0.006 | 300% (CI spans 55%–545%) | [-0.0109, -0.0011] |

## The effective-sample-size result

- recording level, species controlled: **4.48 ± 0.21 Hz/dB**
- city level, aggregated to 24 cities: **4.1 ± 3.2 Hz/dB** (p = 0.2205)
- light effects survive aggregation: onset -0.413 ± 0.024, cessation 0.641 ± 0.020

With 24 cities the confidence intervals for the site-level predictors are roughly ten times wider than the recording-level clustered intervals. This is the design's binding constraint: adding recordings within existing cities adds almost no information about a site-level predictor, whereas adding cities does.

## Ground truth (recorded before analysis)

```json
{
  "seed": 20261005,
  "n_cities": 24,
  "n_species": 30,
  "target_recordings": 960,
  "beta_noise_on_minfreq": 5.0,
  "beta_month_on_minfreq": 18.0,
  "sd_resid_minfreq": 55.0,
  "intercept_onset": -47.0,
  "beta_light_on_onset": -0.4,
  "beta_noise_on_onset": 0.12,
  "beta_interaction_on_onset": -0.02,
  "sd_resid_onset": 5.0,
  "intercept_cessation": 18.0,
  "beta_light_on_cessation": 0.6,
  "sd_resid_cessation": 6.0,
  "beta_biome_moderation": 0.0,
  "_note": "body mass acts through the allometric baseline only; its effective slope is beta_mass_on_minfreq_empirical below",
  "missing_rate_noise": 0.035,
  "missing_rate_light": 0.02,
  "outlier_rate": 0.008,
  "outlier_minfreq_inflation": 700.0,
  "low_quality_rate": 0.015,
  "beta_mass_on_minfreq_empirical": -1757.7
}
```
