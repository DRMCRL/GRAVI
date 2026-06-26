## Features

# OG features
- Add 3-way comparisons # yes this! what about even more, what would this look like??
- Incorporate motif detection # yes this too!
- Checks for input file consistency/structure
- Update manual to include all recent changes

# New features
- Add mouse cytoband information
- Have a separate fdr_alpha in config.yml for RNA-seq DEG threshold (to give more flexibility to DEG/DBS definitions)
- Consider having a full-GRAVI version (includes QC/alignment/filtering steps that can take FASTQ input files) alongside GRAVI-lite (original GRAVI pipeline from BAM onwards). --> check with Beata on standard Tilley lab pipeline and see about consolidate this with Russell lab pipeline.
- See if deeptools plotHeatmap can replace current heatmap version (which allows for stacked subset plotting)
- See if deeptools Pearson/Spearman sample correlation can be included as a plot
- Should include a ChIP-seq vs RNA-seq logFC correlation scatterplot. Consider also adding boxplot (or similar) of overall RNA-seq logFC in TF subsets (unchanged/up/down/etc). Darryl's idea: consider adding histogram of data point distribution along x/y axis (ala AUCell-style)
- Should report somewhere what methods were used for differential peak analysis (SQ/LS and IHW methods), ideally html report. 
- Consider upgrade to MACS3, which presumably handles large file / memory better
- Consider adding decoupleR analysis to RNA-seq and incorporate findings with motif enrichment (Ash has pretty heatmap option)
- See what is required to extend this to non-human/non-mouse species
- Have informative error messages to inform if DBS analysis finds no signicant peaks. As of current this will throw R script errors that requires digging through the intermediary Robj to find out.
- For dummies like me - consider having an early correlation test checkpoint for replicates within same group, and flag error early if replicates within groups show lower correlation than samples across groups.


## Bugs

# OG bugs
- Add `pairwise_comparisons/{t1}_{t2}/{t1}_{ref1}_{treat1}_{t2}_{ref2}_{treat2}-de_genes.csv` to output of pairwise_comparisons when RNA-Seq data is provided

# New bugs
- High core setup crashes space allowance on Slurm. Currently only  --core 1 doesn't crash on Slurm.
- If running snakemake via Slurm from the beginning (ie no custom conda envs pre-made), conda env creation sometimes fails due to connection issues. Current fix - to set up conda envi prior to Slurm run (using snakemake --use-conda --conda-create-envs-only --cores 1)
- Pairwise comparison html file not incorporated in overall report with other html files (ie no hyperlink/tab for it)
