

# **BRIDGE: Biologically Refined Imputation via Diffusion for Gene Expression**

The entire pipeline is controlled via config.json, ensuring dataset-agnostic execution.

### **Configuration and Dataset Selection**

* **Dataset Selection**: Switch the `selected_dataset` key to target specific dataset (e.g., `Human_Innate_T_Cell`, `Human_Lungs`, or `Baron_Human`).
* **Hyperparameter Management**: Define dataset-specific parameters including `target_percentage` (sparsity levels), `seeds_per_rate` for dropout, and `iter` for BRIDGE's diffusion iterations.

### **Execution Pipeline**

The workflow is designed to be executed sequentially through two primary modules:

#### **1. scGPT Embedding Generation**

* Handles automated Ensembl-to-Symbol ID conversion for Human Innate T cell Dataset
* Simulates technical dropout based on configured sparsity rates.
* Generates and stores biologically-informed latent representations in the **`Embeddings/`** folder for downstream use.

#### **2. BRIDGE Imputation**

* Retrieves precomputed embeddings from the **`Embeddings/`** directory.
* Constructs a cell-cell similarity graph and performs imputation.
* Evaluates the imputed data using six clustering metrics: RI, NMI, AMI, FMI, MI, and ARI. Saves the results as individual CSV files for each metric.