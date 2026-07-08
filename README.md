This branch has been validated to work with mouse granulosa cell ChIP-seq data (GR and ERa ChIP-seq data from GSE249985 and GSE300033), and ATAC-seq data (from GSE166878), accompanied by RNA-seq result (from GSE178314) and Micro-C result (from GSE300455). The following has been tested:
- Single vs multiple replicates per group (single replicate leads to incomplete script but will generate signal_summary report)
- Differential methods (qlf vs lh vs wald)
- NFR (using ATAC data)
This version serves as the baseline working version for this pipeline.
