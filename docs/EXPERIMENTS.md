# Experiment notes

## Historical observations

These values were extracted from saved text outputs in the original notebooks. They are not results of a new run of the published versions.

| Experiment | Iteration | Split shown in saved log | L1 | PSNR (dB) |
| --- | ---: | --- | ---: | ---: |
| 3DGS, Truck | 30,000 | train | 0.022943 | 27.2486 |
| RF-3DGS, MPC spectrum | 40,000 | test | 0.093044 | 15.9111 |
| RF-3DGS, MPC spectrum | 40,000 | train | 0.138402 | 14.1157 |

The original 3DGS log reports `Training complete.` after 30,000 iterations. Its train metric is not held-out novel-view performance. The RF notebook starts from the 30,000-iteration visual checkpoint and ends at iteration 40,000; this is not 40,000 additional RF-training iterations.

These experiments use different domains, targets, data, and evaluation protocols. Their PSNR values are not a head-to-head algorithm comparison. The original logs are summarized here; the public notebooks have outputs cleared.

The WRF-GS+ source notebook has no saved final metric outputs. Its code describes evaluation of a fixed test split with nearest-training and mean-training baselines. No WRF-GS+ performance number is asserted in this repository. Its normalized directional-image task does not measure absolute received power, and a single-room experiment cannot establish cross-room generalization.

## Publication checks

- All three files validated against the Jupyter notebook schema.
- Every code cell compiled after IPython syntax transformation, without execution.
- WRF-GS+ code cells were checked against the original and retained verbatim.
- Outputs, execution counts, widget metadata, and embedded attachments were cleared.
- Original files were preserved. Source filenames and SHA-256 hashes are in `SOURCE_MANIFEST.json`.

No GPU training, CUDA extension build, data download, or end-to-end numerical reproduction was performed for publication. Syntax validation does not prove runtime compatibility or scientific correctness.
