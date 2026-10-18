# Virtual Data Collection Simulation and Analysis

**Zoology Research Assistant Internship — Week 2** | Rabi Narayan Patra | 5 October 2026

A virtual data collection framework for a zoological field question, a simulated dataset generated from that
framework, and an initial statistical analysis of it — performed against a **known ground truth**, so that the
analysis can be validated rather than merely described.

## The theme

How **traffic noise** and **artificial light at night** relate to the vocal behaviour of birds. This continues
the preceding week's research plan, so that the plan serves as the blueprint for the collection.

## What makes this simulation different

A simulated dataset is usually a convenience. Here it is the point: because the generative parameters were
**recorded before analysis**, the report can state whether the method recovered the truth — a stronger claim
than "the effect was significant". The effect sizes themselves were taken from published estimates rather than
invented, so the simulated relationships are of the magnitude the literature reports.

## The dataset

**981 recordings · 24 cities · 30 species**, with the imperfections real archives have:

- site noise spans 38–72 dB; night-time light is right-skewed, as real radiance is
- sampling effort varies from 22 to 59 recordings per city
- missing predictor values (3.5% noise, 1.9% light), low-quality files **flagged rather than deleted**, and 7
  equipment artefacts
- minimum frequency spans 804–4,244 Hz, driven mainly by body mass

## Results

| Hypothesis | Outcome |
|---|---|
| H1 Noise raises minimum song frequency | **Supported** — 4.48 Hz per dB (95% CI 4.07–4.90, p < 0.001) |
| H2 Light advances onset and delays cessation | **Supported** — −0.444 min (CI −0.482 to −0.406) and +0.638 min (CI 0.592–0.685) |
| H3 Noise × light interaction on timing | **Not resolved** — the estimate is larger than the truth but with a confidence interval too wide to call |
| H4 Biome moderates the noise effect | **Not supported** — no term survives Benjamini–Hochberg correction |
| H5 The spectral shift is too small to matter | **Supported** — the ~128 Hz shift recovers an estimated **2.7%** of the lost active space |

**Recovery against the truth:** the noise coefficient at 90% of its true value, body mass at 102%, and the two
light effects at 111% and 106%.

## The most consequential finding

Noise and light are properties of a **site**, so the effective sample size for their effects is the number of
**cities**, not the number of recordings:

- with species composition controlled, the noise effect is estimated precisely at recording level — 4.48 ± 0.21 Hz/dB
- aggregated to the 24 cities, the same effect becomes **4.1 ± 3.2 Hz/dB** and is no longer distinguishable from zero

For a site-level predictor, adding recordings inside existing cities adds almost no information; adding cities
does. That changes how a collection plan should spend its effort, and it would not have been visible without a
ground truth to check against.

## Repository contents

```
├── README.md
├── Zoology_Data_Simulation_and_Analysis_Report.docx   # the report (17 pages, ~4,700 words)
├── Zoology_Data_Simulation_and_Analysis_Report.pdf
├── data_dictionary.csv                                # every variable, its role and its definition
└── key_results.md                                     # hypotheses, outcomes and the recovery table
```

**In the v1.0 release bundle** (the full reproducibility package):

```
├── simulated_acoustic_dataset.csv                     # the simulated dataset (981 rows, 22 columns)
├── figures/                                           # all six figures
├── scripts/                                           # simulation, analysis, figures and report code
├── data/  results/                                    # the dataset, ground truth and all outputs
└── the report (DOCX and PDF)
```

## Reproducing it

```bash
python3 scripts/01_simulate_dataset.py   # writes the dataset and the ground truth
python3 scripts/02_analyse.py            # descriptive statistics and models
python3 scripts/03_make_figures.py       # all six figures
python3 scripts/04_build_report.py       # assembles this report
```

The simulation is seeded, so the dataset is identical on every run.

## Author

**Rabi Narayan Patra** — Zoology Research Assistant Intern, 2026.
GitHub: [@rabinarayanpatra350-biotech](https://github.com/rabinarayanpatra350-biotech)
