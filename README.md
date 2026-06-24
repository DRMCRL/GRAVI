This version has been validated for mouse ChIP-seq data from GSE250034 (AR, GR ChIP-seq in mouse granulosa cells), accompanied by RNA-seq (GSE178314) and Micro-C (GSE300455). BAM files for ChIP-seq from previous analysis (pre-filtered, deduplicated) on mm10.

Set-up:
- New conda environment created, from within which reinstall conda, mamba, snakemake, R and all R packages. Snakemake is run from within this environment
- Validated for run via Slurm on HPC at core = 1, memory 50GB. Cores >=4 crashed with no space available error, so will need to test this again.

Things tested:
- Single target (GR) or multiple target (AR/GR)
- IHW-region method
- SQ-LT and LS-QL methods
  
Overall changes made:
- Some modifications made to accommodate mouse genome but some info still needs amendment.
- Some modifications made to make pipeline compatible with current package versions.
- Relaxed pipeline version allowance in env log.

See TODO.md for wishlist of other things to be modified.
