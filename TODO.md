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
- See what is required to extend this to non-human/non-mouse species
- Have informative error messages to inform if DBS analysis finds no signicant peaks. As of current this will throw R script errors that requires digging through the intermediary Robj to find out.
- For dummies like me - consider having an early correlation tet checkpoint for replicates within same group, and flag error early if replicates within groups show lower correlation than samples across groups.
- Darryl's idea: for RNA-seq vs ChIP-seq signal correlation plot, consider adding histogram of data point distribution along x/y axis (ala AUCell-style) --> get this working independently first

## Bugs

# OG bugs
- Add `pairwise_comparisons/{t1}_{t2}/{t1}_{ref1}_{treat1}_{t2}_{ref2}_{treat2}-de_genes.csv` to output of pairwise_comparisons when RNA-Seq data is provided

# New bugs
- High core setup crashes space allowance on Slurm
- If running snakemake via Slurm from the beginning (ie no custom conda envs pre-made), conda env creation sometimes fails due to connection issues
- Pairwise comparison html file not incorporated in overall report with other html files (ie no hyperlink/tab for it)
