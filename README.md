# The Role of White Matter Microstructure in the Association between Childhood Maltreatment and Adult Post-Traumatic Symptoms

## Citation

> Berger, L.†, Rojczyk, P.†, Seitz-Holland, J., Zhang, F., Pankatz, L., Sollmann, N., Kaufmann, E., Carrington, H., Puri, T., Coleman, M.J., Pasternak, O., Bouix, S., Rathi, Y., Cetin-Karayumak, S., O'Donnell, L.J., Falkai, P., George, M.S., McAllister, T.W., Zafonte, R., Stein, M.B., Shenton, M.E., & Koerte, I.K. (2025). The role of white matter microstructure in the association between childhood maltreatment and adult post-traumatic symptoms. *Molecular Psychiatry*. DOI: *to be updated upon publication*
>
> † Equal contribution

If you use this code, please cite the above manuscript.

---

## Overview

This repository contains the analysis code and simulated data for the above manuscript. We examined diffusion MRI parameters across white matter tracts in relation to childhood maltreatment severity in the INTRuST cohort. Analyses included multiple regression, moderation by PTSD/mTBI diagnosis, and mediation models testing white matter microstructure as a neurobiological pathway to post-traumatic symptoms.

---

## Data

The original INTRuST dataset cannot be shared due to consortium data use restrictions. A **synthetic dataset** generated with [`synthpop`](https://cran.r-project.org/package=synthpop) is provided in `data/` for computational reproducibility — it allows the full analysis pipeline to run and produces plausible output, but does not reproduce the manuscript results. This dataset does not represent real participant data.

- `data/analysis_simulated.csv` — synthetic dataset (N = 299)
- `data/codebook.csv` — variable descriptions and instrument references

To access the original INTRuST data, contact the INTRuST Consortium directly.

---

## Requirements

- **R** 4.4.1
- **RStudio** (recommended)
- **Hayes PROCESS macro**: download `process.R` from [processmacro.org](https://processmacro.org) and place it at `code/utils/process.R`.

All R package versions are managed with [`renv`](https://rstudio.github.io/renv/). To restore the exact environment:

```r
install.packages("renv")
renv::restore()
```

---

## Usage

1. Open `intrust_cm.Rproj` in RStudio.
2. Run `renv::restore()` to install all packages.
3. Place `process.R` at `code/utils/process.R`.
4. Render scripts in the order below — each reads from `data/analysis_simulated.csv` and writes output to `output/tables/` and `output/results/`.

| # | Script | Content |
|--:|--------|---------|
| 1 | `00_demographics.Rmd` | Sample characteristics (Table 1, Tables S9–S11) |
| 2 | `h1a_associations_ctq_white_matter.Rmd` | Regression CTQ → WM microstructure (Table 2) |
| 3 | `h1a_associations_ctq_white_matter_supp.Rmd` | H1a robustness: HC3 SEs, bootstrapped CIs, subscale analyses (Tables S2a, S2b, S5a–d, S6, S12) |
| 4 | `h1b_moderation_diagnoses.Rmd` | Moderation by PTSD/mTBI diagnosis; PROCESS Model 1 (Table 3) |
| 5 | `h1b_moderation_diagnoses_supp.Rmd` | H1b robustness: HC3 SEs, three-way interaction (Tables S7–S8) |
| 6 | `h2a_mediation_white_matter_pcl.Rmd` | WM mediating CTQ → PTSD severity; PROCESS Model 4 (Table S3) |
| 7 | `h2a_mediation_white_matter_pcl_supp.Rmd` | H2a robustness: additional covariates; CTQ subscale mediation (Tables S2c, S2d, S13) |
| 8 | `h2b_mediation_white_matter_rpq.Rmd` | WM mediating CTQ → post-concussive symptoms; PROCESS Model 4 (Table S4) |
| 9 | `h2b_mediation_white_matter_rpq_supp.Rmd` | H2b robustness: additional covariates; CTQ subscale mediation (Tables S2e, S2f, S14) |

Output files are not included in this repository. Running the scripts will populate `output/tables/` and `output/results/` with results based on the synthetic dataset; these are provided for computational reproducibility only and will differ from the manuscript.

---

## License

Code is released under the **MIT License** (see `LICENSE`). The synthetic dataset is provided for computational reproducibility only and does not represent real participant data.

---

## Contact

**Luisa Berger** — cBRAIN, Department of Child and Adolescent Psychiatry, LMU Munich
luisa.berger@med.uni-muenchen.de
