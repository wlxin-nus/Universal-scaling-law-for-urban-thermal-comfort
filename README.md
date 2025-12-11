# Scaling Laws of Urban Configuration’s Influence on Thermal Comfort

This repository contains the core dataset and implementation code for the study on **A universal scaling law governs urban thermal comfort and enables precision heat mitigation**. It provides a comprehensive framework for quantifying how urban forms affect thermal comfort across different spatiotemporal scales using Graph Neural Networks (GNNs) and Causal Inference.

## 📂 Repository Structure

### 1. Data Directory (`data/`)
This folder contains the raw training and analysis data required to run the notebooks.
* **`Input/`**: Contains raw input features regarding urban configuration (e.g., building height, vegetation fraction, impervious surfaces).
* **`Output/`**: Contains the corresponding thermal comfort metrics (e.g., UTCI) used as ground truth for model training and analysis.

### 2. Code Workflow
The analysis is divided into four sequential steps. Please run the notebooks in the following order:

* **`01_Data_Process.ipynb`**: 
    * Preprocessing of raw input/output data.
    * Meteorological data processing using `pvlib` (solar position, wind, humidity).
    * Construction of spatial graphs.
* **`02_Model_Architecture.ipynb`**: 
    * Implementation of the deep learning architecture.
    * Combines **RGCN** (Relational Graph Convolutional Networks) for spatial dependencies and **LSTM/Transformer** structures for temporal dynamics.
    * Includes training loops and validation procedures.
* **`03_Scaling_Law_Analysis.ipynb`**: 
    * Performs multi-scale resampling of landscape features.
    * Quantifies thermal effects and fits Power Laws to calculate scaling exponents.
    * Identifies scale breaks and intervention efficiency thresholds.
* **`04_Causal_Effects.ipynb`**: 
    * Causal Inference implementation using **DoWhy** and **EconML**.
    * Estimates Average Causal Effects (ACE) and Conditional Average Treatment Effects (CATE).
    * Validates the causal graph structure.

### 3. Summary Results
* **`final_summary_with_climate.csv`**: 
    * This dataset contains the **Spatiotemporal Assessment** data corresponding to **Figure 3F** in the study.
    * It provides a comprehensive view of:
        * **Break Patterns**: Identifies critical scale breaks (sign-invariant vs. sign-changing).
        * **Efficiency Modes**: Classifies intervention efficiency as superlinear or sublinear.
        * **Scaling Exponents ($\beta$)**: Quantifies the intensity of scaling relationships across all urban elements.
        * **Meteorological Correlations**: Correlates these scaling laws with specific meteorological factors.

## 🛠 Dependencies

This project relies on the following key libraries. Please ensure your environment is configured with:

**Core Data & Geospatial:**
* `numpy`, `pandas`, `scipy`
* `geopandas`, `rasterio`, `shapely`
* `matplotlib_scalebar`

**Deep Learning (Graph & Time-series):**
* `torch` (PyTorch)
* `torch_geometric` (PyG)
* `torchprofile` (for FLOPs calculation)

**Causal Inference & Machine Learning:**
* `dowhy`, `econml`, `causal-learn`
* `scikit-learn`, `xgboost`
* `networkx`, `pydot`

**Others:**
* `pvlib` (Solar position calculation)
* `matplotlib`, `seaborn` (Visualization)
* `tqdm` (Progress tracking)

## 🚀 Usage

1.  **Clone the repository** (Recommended via GitHub Desktop to handle large files).
2.  **Environment Setup**: Install the dependencies listed above.
3.  **Data Check**: Ensure the `data/Input` and `data/Output` folders are populated.
4.  **Execution**: Run the notebooks in numerical order (`01` through `04`).

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.