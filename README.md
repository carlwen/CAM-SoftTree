# CAM-SoftTree

Code and analysis notebooks for the paper:

**Trustworthy Tree-based Machine Learning by MoS2 Flash-based Analog CAM with Inherent Soft Boundaries**

Authors: Bo Wen, Guoyun Gao, Zhicheng Xu, Mingrui Jiang, Ruibin Mao, Xiaojuan Qi, Jiezhi Chen, Xunzhao Yin, Xiaobo Sharon Hu, Can Li.

This repository contains the notebook-based workflow used to study soft-boundary tree models implemented with analog CAM-inspired behavior. The project covers three main parts:

- training soft decision tree (SDT) and soft random forest (SRF) models derived from conventional tree models,
- robustness analysis under non-ideal device and architecture conditions,
- PySpice-based circuit simulation for scalability studies.

## Overview

The central idea of this work is to start from standard decision tree and random forest structures and then introduce soft boundaries that better match analog CAM behavior. The notebooks in this repository support model construction, training, inference analysis, robustness evaluation, and SPICE-level simulation.

The repository is organized as a research code release rather than a packaged Python library. Most workflows are implemented directly in Jupyter notebooks.

## Repository Structure

```text
CAM-SoftTree/
|-- models_training/
|   |-- soften_tree_v10_SDT_SRF_taular.ipynb
|   `-- soften_tree_v11_SDT_SRF_mnist.ipynb
|-- robustness_analysis/
|   |-- inference_soften_tree_for_analysis.ipynb
|   |-- robustness_analysis_device_variation.ipynb
|   |-- robustness_analysis_iris.ipynb
|   `-- robustness_analysis_tree_depth.ipynb
|-- spice_simulation_for_scalability/
|   |-- pyspice4columns_analysis.ipynb
|   `-- pyspice4columns_build_random_inputs.ipynb
|-- LICENSE
`-- README.md
```

## Notebook Guide

### Model Training

- `models_training/soften_tree_v10_SDT_SRF_taular.ipynb`
	- Training and evaluation workflow for tabular datasets.
	- Builds soft decision tree and soft random forest models from classical tree models.
	- Includes preprocessing, training, and saved-model related steps.

- `models_training/soften_tree_v11_SDT_SRF_mnist.ipynb`
	- Training and evaluation workflow for MNIST.
	- Uses TensorFlow/Keras to load MNIST and PyTorch for model definition and optimization.
	- Includes robustness-oriented experiments such as threshold perturbation and noisy-input evaluation.

### Robustness Analysis

- `robustness_analysis/inference_soften_tree_for_analysis.ipynb`
	- Inference-oriented notebook for analyzing trained soft tree models.
	- Useful for loading trained checkpoints and inspecting model behavior.

- `robustness_analysis/robustness_analysis_device_variation.ipynb`
	- Studies the effect of device variation and parameter perturbation on model behavior.
	- Includes loading previously trained tree and forest models and evaluating their robustness.

- `robustness_analysis/robustness_analysis_iris.ipynb`
	- Compact robustness study using the Iris dataset.
	- Useful for quick sanity checks and interpretable low-dimensional experiments.

- `robustness_analysis/robustness_analysis_tree_depth.ipynb`
	- Examines how tree depth influences behavior and robustness.
	- Focuses on trends relevant to accuracy, complexity, and trustworthiness.

### SPICE Simulation for Scalability

- `spice_simulation_for_scalability/pyspice4columns_build_random_inputs.ipynb`
	- Generates randomized inputs for circuit-level experiments.

- `spice_simulation_for_scalability/pyspice4columns_analysis.ipynb`
	- Runs and analyzes PySpice/NgSpice simulations for array-level or column-level studies.
	- Intended for scalability evaluation of the analog CAM design.

## Requirements

Because this repository is notebook-centric and does not currently ship with a pinned environment file, dependencies should be installed manually based on the notebooks you plan to run.

### Core Python Packages

The training and analysis notebooks use packages including:

- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `torch`
- `tensorflow`
- `joblib`
- `tqdm`
- `openml`
- `opencv-python`
- `mlxtend`
- `jupyter`

### Circuit Simulation Packages

The SPICE notebooks additionally require:

- `PySpice`
- a working `NgSpice` installation accessible to PySpice

### Hardware Notes

- GPU acceleration is recommended for the PyTorch-based training notebooks, especially for MNIST experiments.
- CPU execution may still be possible for smaller studies, but runtime can increase substantially.

## Suggested Environment Setup

One reasonable starting point is a clean Python environment such as Conda or `venv`, then installing the major notebook dependencies manually.

Example with `pip`:

```bash
pip install jupyter numpy pandas matplotlib seaborn scikit-learn torch tensorflow joblib tqdm openml opencv-python mlxtend PySpice
```

You will also need to install NgSpice separately according to your operating system.

If you want a fully reproducible environment for long-term archival or collaboration, creating a `requirements.txt` or Conda environment file from the packages you actually use in your local setup is recommended.

## How To Use This Repository

### 1. Train or reproduce models

Start with one of the notebooks in `models_training/`:

- use the tabular notebook for structured datasets,
- use the MNIST notebook for image-based experiments.

These notebooks define the soft tree models, initialize them from conventional tree structures, and perform optimization and evaluation.

### 2. Run robustness analysis

Open the notebooks in `robustness_analysis/` to inspect sensitivity to:

- device variation,
- dataset choice,
- tree depth,
- inference-time perturbation.

These notebooks are useful for reproducing the trustworthiness-related analyses described in the paper.

### 3. Run circuit-level simulation

Use the notebooks in `spice_simulation_for_scalability/` for PySpice-based simulation.

Before running them, make sure that:

- PySpice is installed,
- NgSpice is installed and visible to PySpice,
- any required SPICE model libraries are available in your local environment.

## Notes On Reproducibility

- The repository currently consists of notebooks rather than a packaged training pipeline.
- Some notebooks load or save intermediate artifacts locally, so path adjustments may be needed depending on your machine.
- Different library versions can affect serialized scikit-learn models and notebook outputs.
- For the most stable reproduction, use a single controlled Python environment for training and analysis.

## Citation

If you use this repository in academic work, please cite the paper:

```bibtex
@article{wen_cam_softtree,
	title={Trustworthy Tree-based Machine Learning by MoS2 Flash-based Analog CAM with Inherent Soft Boundaries},
	author={Wen, Bo and Gao, Guoyun and Xu, Zhicheng and Jiang, Mingrui and Mao, Ruibin and Qi, Xiaojuan and Chen, Jiezhi and Yin, Xunzhao and Hu, Xiaobo Sharon},
	journal={Nature Communications},
	note={accepted}
}
```

Update the BibTeX entry with volume, issue, pages, year, and DOI once the final publication metadata is available.

## License

This project is released under the MIT License. See `LICENSE` for details.





