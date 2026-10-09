# Gaussian Splatting for Vision & Wireless RF

**Three experiment notebooks exploring visual reconstruction and radio-frequency modeling with Gaussian splatting.**

Maintained by [Tanisha Jain](https://github.com/tanisha-jain19).

This collection brings together my practical testing of **3DGS**, **RF-3DGS**, and **WRF-GS+**. The notebooks cover GPU setup, dataset preparation, training, rendering, and evaluation using the original research implementations.

## Explore the notebooks

| Notebook | Experiment | Main workflow |
| --- | --- | --- |
| [01 · 3DGS](notebooks/01_3dgs_visual_reconstruction.ipynb) | Visual reconstruction of the Truck scene | Build CUDA extensions → train → compare views → export Gaussians |
| [02 · RF-3DGS](notebooks/02_rf_3dgs_radio_reconstruction.ipynb) | Radio radiance field reconstruction | Load visual checkpoint → train on RF spectra → render and inspect results |
| [03 · WRF-GS+](notebooks/03_wrfgs_plus_wireless_experiment.ipynb) | One-room wireless RF experiment | Simulate data → train with checkpoints → validate → evaluate against baselines |

## What this work demonstrates

- Working with Python notebooks, PyTorch, and CUDA-based research code.
- Preparing inputs and resolving extension-build/checkpoint compatibility issues.
- Training models, inspecting reconstructions, and saving experiment artifacts.
- Distinguishing training-view quality from held-out evaluation and documenting experiment limitations.

The underlying algorithms belong to their research authors. My work here is the experiment setup, execution, inspection, and documentation around those implementations.

## Getting started

1. Open a notebook on GitHub to review the workflow.
2. To run it, download the notebook or open it through Google Colab's **GitHub** notebook picker using this repository URL.
3. Select a **GPU runtime** and read the notebook prerequisites before running cells in order. Use a separate fresh runtime for each experiment.
4. Supply the required data/checkpoints described in [setup and data](docs/SETUP_AND_DATA.md).

**WRF-GS+ requires a separate room-specific source/data package that is not included here.** The public notebook documents its workflow; cloning this repository alone is insufficient to run it.

There is no shared `requirements.txt`: these implementations have different CUDA and environment requirements. Each notebook points to its own setup, and the setup guide explains the dependencies.

## Recorded results and validation

The original saved logs contain a completed 30,000-iteration Truck run and an RF-3DGS run ending at iteration 40,000. See [experiment notes](docs/EXPERIMENTS.md) for the recorded metrics and their limits.

The published notebooks have been checked for notebook validity and Python/IPython syntax. **The cleaned versions have not been rerun end-to-end on a GPU.** Saved outputs, embedded tutorial screenshots, redundant debugging cells, and personal runtime metadata have been removed. No dataset, trained model, room geometry, or result archive is bundled.

## Repository guide

```text
notebooks/                 Three curated experiment notebooks
docs/SETUP_AND_DATA.md      Runtime and external-data requirements
docs/EXPERIMENTS.md         Historical observations and validation scope
docs/SOURCE_MANIFEST.json   Original filenames, hashes, and preparation notes
THIRD_PARTY_NOTICES.md      Research credits and upstream license links
.gitignore                 Excludes datasets, weights, and generated outputs
```

## Credits

- [3D Gaussian Splatting — GRAPHDECO](https://github.com/graphdeco-inria/gaussian-splatting), used through the [camenduru fork](https://github.com/camenduru/gaussian-splatting).
- [RF-3DGS — SunLab, University of Georgia](https://github.com/SunLab-UGA/RF-3DGS).
- [WRF-GS+ — Chaozheng Wen and collaborators](https://github.com/wenchaozheng/WRF-GSplus).
- [Sionna RT — NVIDIA](https://github.com/NVlabs/sionna-rt).

See [third-party notices](THIRD_PARTY_NOTICES.md) before reusing upstream code, datasets, or models.
