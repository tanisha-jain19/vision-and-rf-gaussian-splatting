# Setup and external data

## Viewing

GitHub renders the notebooks without installation. For local viewing/editing, install Jupyter in your own environment (`python -m pip install jupyterlab`) and open the `.ipynb` files. Local viewing does not make the Colab-specific GPU workflows runnable on a Windows CPU.

## 3DGS

- Use a Linux/Colab NVIDIA GPU runtime with PyTorch, a compatible CUDA toolkit, and a C++ compiler.
- Follow the [environment requirements of the fork used](https://github.com/camenduru/gaussian-splatting#optimizer). The notebook builds `diff-gaussian-rasterization` and `simple-knn` from source and installs `plyfile`.
- It downloads the T&T/DB archive used by the original notebook and selects `tandt/truck`, which requires images and COLMAP sparse data. Dataset terms remain with the original providers.
- No prebuilt Python-3.10-only wheels are assumed. Current Colab versions may require environment adjustments before the extensions compile.

## RF-3DGS

- Follow [upstream installation and dataset instructions](https://github.com/SunLab-UGA/RF-3DGS). The same general GPU/compiler constraints apply, but use this project's own environment rather than assuming it matches 3DGS.
- Place `RF-3DGS_dataset.zip` in your Google Drive root.
- After extraction, the notebook expects:

```text
/content/dataset/RF-3DGS_dataset/
  training-rf-spectrum/3dgs_MPC_100/
  blender_visual_trained/chkpnt30000.pth
```

- The training checkpoint is a trusted external dependency. Do not substitute an untrusted pickle-based checkpoint.

## WRF-GS+

The notebook is the runner for an existing local experiment package, **not a self-contained reproduction kit**. `WRFGS_Fullroom_Package.zip` is not published or downloadable from this repository. It contains room assets and supporting code beyond the three-notebook scope of this collection.

The runner requires the original `wrfgs_one_room/` package layout, including `PACKAGE_MANIFEST.json`, `setup_colab.py`, `generate_data.py`, `rf_math.py`, `train_room.py`, `test_rf_math.py`, `verify_runtime.py`, scene assets, and vendor sources. A ZIP containing only the public notebook will not work.

The original package targets Python 3.11, PyTorch 2.6 with CUDA 12.4, and Sionna RT 1.2.1; its script builds the RF rasterizer. It records WRF-GS+ commit `e564f3184463717ae08660a8b7232c6318c73ca6`. Full package dependency details are maintained within that external package.

Use your own trusted package and inspect its setup script. The notebook checks archive paths and file hashes before running it. It generates data and stores results under `MyDrive/WRFGS_fullroom/`.

## Reproducibility limits

The optical and RF notebooks historically cloned upstream branches without recording exact commit hashes. Their prepared versions print the checked-out hash for future runs, but cannot reconstruct the historical source revision. No lockfile or newly verified CUDA environment is claimed. Download links, dependency versions, and upstream behavior can change.
