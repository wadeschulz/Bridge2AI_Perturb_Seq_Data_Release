# Creating Functional Correlation Networks from Perturb-Seq Data
In this challenge, you will:
 - Learn about the data structure of processed perturb-seq data, using a dataset for Perturb-Seq performed on 108 chromatin modifying genes in KOLF2.1J Stem Cells
 - Create a visualization showing which perturbations induce similar phenotypes
 - Perform differential gene expression analysis for each perturbation
  

### Getting Started
- Git clone this [repository](https://github.com/y-doctor/Bridge2AI_Perturb_Seq_Data_Release)
- `pip install -r requirements.txt`
- Open the `Jamboree_Code_Fest_3_15_24_workbook.ipynb` which is a skeleton jupyter notebook to fill in that will guide you through the analysis

### Visualizing perturbation similarities through correlation analysis
1. The data provided to you has been filtered through the entire [single cell best practices](https://www.sc-best-practices.org/conditions/perturbation_modeling.html#analysing-single-pooled-crispr-screens) pipeline as described in the earlier talk (link).
2. Download the data (link) and to read the .h5ad into Python. Read up on the data structure of [AnnData objects](https://anndata.readthedocs.io/en/latest/). The .X is the X_pert layer computed by [pertpy](https://pertpy.readthedocs.io/en/latest/tutorials/notebooks/mixscape.html), and is filtered down to top 6000 highly variable genes.
3. Compute a mean gene expression vector for each perturbation.
4. Compute the pairwise Pearson correlation matrix between all perturbations.
5. Read on generally what [UMAP](https://umap-learn.readthedocs.io/en/latest/) does. Use the correlation matrix as a precomputed feature matrix as input to UMAP to get a 2-dimensional embedding of each perturbation. 6. Use the nearest n=3 neighbors with spread = 1.0 to compute the UMAP.
7. Use [networkx](https://networkx.org/documentation/stable/tutorial.html) to plot each perturbation as a node, using the UMAP embeddings as the X/Y position of each node. Draw edges between each node and the top 5 person correlates.
8. What perturbations cluster together in the network? Do these have known biological relationships? How does the clustering change as a function of changing the number of UMAP neighbors?

### Computing Differentially Expressed Genes
1. For each perturbation, compute the number of differentialy expressed genes relative to NTCs. What is an appropriate DE test to use (e.g. parametric or non-parametric?) What are the FDR and Log Folders Change cutoffs chosen? Justify the selection
2. Investigate the DEGs for a perturbation of interest. Is there any interesting biological relationship between them?
3. Can you leverage parallel computing to significantly speed up the differential expression analysis?