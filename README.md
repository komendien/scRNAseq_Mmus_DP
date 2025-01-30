# GeneLab single-cell RNAseq data processing

### Downstream analysis - short documentation:
* Each codeblock is a separate script. To run downstream analysis, go to Module0 - Parameters.py, then specify your working base_path and make sure, that your base path contains folder with single cell data to process.
  
* If you do not want to specify your parameters, simply run main.py

#### Updates (01.30.2025):
Module0:
- added module names before each parameter to make them more readable and accessible.

Module9:
- moved out parameters from main function to Module0
  
Module13:
- changed name "shigft" to "shift".

Module15:
- added note to sc.tl.rank_genes_groups for LogFC.

Module16:
- reorganized codeblocks for easier data analysis
- explained data sparsity with emphasysis on optionality of this process.
- Removed Heatmap and violin plotting option and left: groups, stacked_violin, dotplot, matrixplot. Note: Parameters for saving heatmaps and violin plots are still visible in Module3 - SaveData!
- Added xlabel and ylabel for matrixplot, dotplot and stacked_violin

Additionally:
- uploaded code to GitHub repository
- Printed libraries used for downstream analysis
- exported conda environment (with github link to fixed scoreCT).

#### Updates (01.28.2025):
Module0:
- Renamed filterCell_threshold to MTfilterCell_threshold

Module1:
- added new folder csv_tables, that is the output folder for: metadata, ranked_clusters,ranked_celltypes

Module9:
- Removed target_sum setting for normalization: default median count depth is used instead
- Removed the min_mean, max_mean, min_disp setting for the highly variable genes in the code
- Instead of removing, changed discarding highly variable genes as option (default is set to False)
- Added optional option of scaling the data (def. True, type=bool), added max_value parameter to None by default (type= float or None). By default is None, but must be specified by the user.

Module12:
- Removed n_neigbors value - default value is automatically used.
- Removed sc.tl.rank_genes_groups; moved them to Module13
  
Module13:
- Prepared K_top and m_bins documentation (see in module 13)
- Added K_top_param and m_bins_param as parameters to modify in Module0.
- This function calculates now tl.rank_genes for clusters (leiden) and for scoreCT (scoreCT). It also saves data in adata indivually to prevent data overwriting.

Module15:
- Modified adata as QC table that contain columns: n_cells, mt, mean_counts, pct_dropout_by_counts,total_counts,highly_variable, means, dispersions, dispersions_norm
- Added threshold of displaying table: qc_display_limit = 2000 (stored in Module0 (Parameters). If table exceed size of 2000 rows, it prints message of possibility to download QC table.
- Added option to download QC table in csv format
- Added option to download whole adata object (but it overlaps with the function from Module13).
- created interactive table with ranked genes per cluster: display first 10 rows by default and allows users to download full table (analogically like in previous modules).

Module16:
- created two main functions:
    - DE_options() that prints user all possible groups and factors to make comparison
    - DE_analysis() that generates all possible plots for DE analysis in a single sample
