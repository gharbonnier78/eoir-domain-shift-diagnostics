# EO/IR Domain-Shift Diagnostics

[![Read the PDF](https://img.shields.io/badge/READ%20THE%20PDF-EO%2FIR%20DOMAIN%20SHIFT-B31B1B?style=for-the-badge&logo=adobeacrobatreader&logoColor=white)](dist/EOIR_Domain_Shift_Engineering_Diderot_Companion.pdf)
[![Reproducible build](https://github.com/gharbonnier78/eoir-domain-shift-diagnostics/actions/workflows/reproducible-build.yml/badge.svg)](https://github.com/gharbonnier78/eoir-domain-shift-diagnostics/actions/workflows/reproducible-build.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

**Reproducible Fisher-Rao, MMD, identifiability and directional-coverage diagnostics for EO/IR perception, with Python experiments, Diderot tools, and an auto-built LaTeX paper.**

## Canonical paper

The highlighted button above opens the committed reference PDF directly:

`dist/EOIR_Domain_Shift_Engineering_Diderot_Companion.pdf`

The document combines the research result, complete engineering view, two Diderot knowledge sheets, two interactive visual tools and their illustrated user guide.

## One-command reproduction

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
make verify
```

`make verify` regenerates the Python results, CSV files and all scientific figures, validates the numerical contracts, and compiles the complete PDF.

## Reproduced outputs

- `data/results/domain_pairs_results.csv` - all 120 Fisher-Rao/MMD regime pairs;
- `data/results/directional_diagnostics.csv` - Panel A/B rank, conditioning and per-direction diagnostics;
- `data/results/reproduction_summary.json` - seeds, parameters and headline values;
- `paper/figures/fisher_rao_vs_mmd.png`;
- `paper/figures/rho_fr_panel_A.png`;
- `paper/figures/rho_fr_panel_B.png`;
- `paper/figures/s_dir_sweep_ablation.png`;
- `dist/EOIR_Domain_Shift_Engineering_Diderot_Companion.pdf`.

## Interactive Diderot tools

Open the standalone files directly in a modern browser:

- [`interactive/diderot_fisher_rao_explorer.html`](interactive/diderot_fisher_rao_explorer.html)
- [`interactive/diderot_mmd_explorer.html`](interactive/diderot_mmd_explorer.html)

No server, package manager or Internet connection is required.

## Repository structure

```text
.
├── .github/workflows/       # reproducible CI and tagged-release publication
├── data/results/            # committed machine-readable outputs
├── dist/                    # canonical PDF
├── docs/                    # reproducibility and interpretation contract
├── interactive/             # standalone Diderot HTML explorers
├── paper/                   # LaTeX, sections, figures, screenshots, original source
├── scripts/                 # experiments, orchestration and validation
├── tests/                   # mathematical and regression tests
├── CITATION.cff
├── Makefile
└── requirements.txt
```

## Continuous integration

Every push and pull request:

1. installs the pinned Python environment;
2. regenerates all numerical evidence;
3. validates the CSV schemas and mathematical invariants;
4. builds the complete LaTeX PDF;
5. publishes the PDF, CSV, JSON, figures and HTML tools as a workflow artifact.

A tag such as `v0.1.0` additionally creates or updates a GitHub Release and attaches the canonical PDF plus machine-readable result files.

## Scientific boundary

Fisher-Rao is meaningful only within a credible statistical model. MMD depends on representation, kernel, bandwidth, sample size and calibration. The Monte-Carlo tolerance is empirical rather than a formal confidence interval. The univariate analytic bound is not silently extended to the multiband setting. Directional coverage diagnostics support guarded engineering decisions; they are not unrestricted adaptation commands.

See [`docs/REPRODUCIBILITY.md`](docs/REPRODUCIBILITY.md) for the frozen experiment contract.
