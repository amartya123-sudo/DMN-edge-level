# DMN Edge-Level Analysis

An exploratory data analysis and machine learning project for analyzing edge-level features in the Default Mode Network (DMN) brain connectivity, with applications to neurological disease classification and network biomarker discovery.

## Project Overview

This project investigates network edges and node features derived from Default Mode Network (DMN) fMRI data to identify stable biomarkers for distinguishing between neurological conditions (e.g., Alzheimer's Disease vs. Cognitive Normal). The analysis spans multiple scales:

- **Edge-Level Analysis**: Feature extraction, importance ranking, and model performance optimization
- **Node-Level Analysis**: Nodal feature computation with Fisher transformation and weighted aggregation
- **Population Connectivity (PCC)**: Raw connectivity data for different diagnostic groups

## Directory Structure

```
DMN-edge-level-analysis/
├── Edge-Level_Analysis/          # Primary edge-level analysis
│   ├── edge-level.ipynb          # Main edge feature extraction & analysis notebook
│   ├── final_rf.ipynb            # Random Forest model with optimized hyperparameters
│   ├── edge_features_*.csv       # Extracted edge features (absolute and z-scored)
│   ├── feature_importances_all_max_features.csv
│   ├── accuracy_vs_k.csv         # Cross-validation accuracy metrics
│   ├── stable_edges*.csv         # Consistently selected edges across k values
│   ├── stable_features/          # Top features by stability ranking
│   ├── feature_importance/       # Feature importance distributions across folds
│   ├── mannk30/                  # Results for k=30 analysis
│   └── results/                  # Final results and outputs
│
├── Nodel-Level_Analysis/         # Nodal (node-level) feature analysis
│   ├── nodal_features.ipynb      # Nodal feature computation
│   ├── random_forest.ipynb       # Node-level Random Forest classification
│   ├── metadata.csv              # Subject demographics and labels
│   ├── fisher-transformed/       # Fisher z-transformed correlations
│   └── weighted_features/        # Weighted nodal aggregations
│
├── PCC/                          # Population Connectivity Matrices
│   ├── AD/                       # Alzheimer's Disease group connectivity data
│   └── CN/                       # Cognitive Normal group connectivity data
│
└── README.md                     # This file
```

## Key Analyses

### 1. Edge-Level Analysis
- **Feature Extraction**: Derives connectivity features from edge-level DMN connections
- **Feature Importance**: Ranks edges by importance using Random Forest models
- **Stability Analysis**: Identifies stable edges across different k-fold cross-validation splits
- **Model Performance**: Evaluates classification accuracy with various hyperparameter configurations

**Key Outputs**:
- `edge_features_z.csv` / `edge_features_abs.csv`: Normalized and raw edge features
- `stable_edges_k30.csv`: Most stable/reproducible edges for k=30
- Feature importance rankings organized by fold

### 2. Node-Level Analysis
- **Nodal Feature Computation**: Aggregates edge-level information to node-level metrics
- **Fisher Transformation**: Applies Fisher z-transformation to correlation distributions
- **Classification**: Random Forest classifier for diagnostic prediction at node level
- **Metadata**: Subject demographics and diagnostic labels in `metadata.csv`

**Key Outputs**:
- `fisher-transformed/`: Z-score transformed node features
- `weighted_features/`: Weighted aggregations of node importance

### 3. Population Connectivity (PCC)
- Raw and processed connectivity matrices grouped by diagnostic category
- **AD** (Alzheimer's Disease) and **CN** (Cognitive Normal) populations
- Foundation data for all downstream analyses

## Datasets

- **Subjects**: AD (Alzheimer's Disease) and CN (Cognitive Normal) groups
- **Network**: Default Mode Network (DMN) functional connectivity
- **Features**: Edge and node-level connectivity metrics
- **Processed Data**: Multiple feature representations (raw, z-scored, Fisher-transformed)

## Usage

### Prerequisites
- Python 3.7+
- Jupyter Notebook or JupyterLab
- Required libraries: numpy, pandas, scikit-learn, scipy, matplotlib, seaborn

Install dependencies:
```bash
pip install numpy pandas scikit-learn scipy matplotlib seaborn
```

### Running the Notebooks

1. **Edge-Level Analysis**:
   ```bash
   jupyter notebook Edge-Level_Analysis/edge-level.ipynb
   ```
   Performs feature extraction, visualization, and stability analysis.

2. **Random Forest Model**:
   ```bash
   jupyter notebook Edge-Level_Analysis/final_rf.ipynb
   ```
   Trains and evaluates the optimized Random Forest classifier.

3. **Node-Level Analysis**:
   ```bash
   jupyter notebook Nodel-Level_Analysis/nodal_features.ipynb
   ```
   Computes and visualizes node-level features.

4. **Node-Level Classification**:
   ```bash
   jupyter notebook Nodel-Level_Analysis/random_forest.ipynb
   ```
   Applies Random Forest at the nodal scale.

## Key Findings

- **Stable Edges**: The project identifies a subset of reliably discriminative edges that remain stable across cross-validation folds (see `stable_edges_k30.csv`)
- **Feature Importance**: Not all edges are equally important; feature importance analysis highlights the most discriminative connections
- **Model Performance**: Edge-level features show varying classification accuracy depending on the number of selected features and hyperparameter tuning
- **Cross-Scale Analysis**: Both edge and node-level analyses provide complementary insights into network biomarkers

## Output Files

| File | Description |
|------|-------------|
| `edge_features_z.csv` | Z-scored edge features |
| `edge_features_abs.csv` | Absolute (unnormalized) edge features |
| `stable_edges_k30.csv` | Edges consistently selected in k=30 cross-validation |
| `accuracy_vs_k.csv` | Classification accuracy for different k values |
| `feature_importances_all_max_features.csv` | Feature importance scores across configurations |
| `metadata.csv` | Subject demographics and diagnostic labels |

## Methods

- **Feature Engineering**: Edge and node-level connectivity metrics
- **Feature Selection**: Recursive feature elimination and importance-based ranking
- **Classification**: Random Forest with grid search optimization
- **Cross-Validation**: k-fold cross-validation for model assessment
- **Stability Analysis**: Identification of reproducible features across validation folds
- **Normalization**: Z-score transformation and Fisher transformation for correlation data

## Next Steps & Future Work

- [ ] Validate findings in independent cohorts
- [ ] Explore other classification algorithms (SVM, gradient boosting)
- [ ] Investigate temporal dynamics if longitudinal data available
- [ ] Connect edge-level biomarkers to clinical outcomes
- [ ] Create visualizations of discriminative network substructures
- [ ] Generate publication-ready figures and tables

## Project Status

**Stage**: Exploratory analysis and model development

This is an ongoing exploratory project. Results should be interpreted as preliminary findings pending validation and replication.

## Notes

- Results organized by maximum feature configurations and k values
- Feature importance computed using permutation importance and mean decrease in impurity
- Stability assessed through repeated cross-validation folds
- Multiple feature representations provided for flexibility in downstream analyses

---

**Last Updated**: June 2026  
**Repository**: [amartya123-sudo/DMN-edge-level](https://github.com/amartya123-sudo/DMN-edge-level)
