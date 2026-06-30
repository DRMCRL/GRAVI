## Features

# OG features
- Add 3-way comparisons # yes this! what about even more, what would this look like??
- Checks for input file consistency/structure
    *** working so far ***
- Update manual to include all recent changes\
- Incorporate motif detection # yes this too!
    *** starting on this bit, setting up for HOMER (MEME is also available but I'm more familiar with HOMER)
          1. test run- install homer via conda in rmarkdown env (in practice - add homer as dependency in this env)
          2. to group homer motifs to non-redundant JASPAR-styled motif family that can be more easily filtered/applied:
            - set up script to convert motifs in HOMER to MEME format (see homer2meme.py file)
            - combine all redundant HOMER motifs into 1 single file via cat *.motif > every.motif
            - convert motif to MEME format
            - via MEME-suite online, run: tomtom -no-ssc -oc . -verbosity 1 -min-overlap 5 -dist pearson -evalue -thresh 10.0 meme.motif db/JASPAR/JASPAR2026_CORE_non-redundant.meme
            - assign HOMER to JASPAR annotation by best fit + TF name matching + manual curation of sequence
          3. run HOMER from within R using system() using default HOMER set-up. See differential_binding.Rmd for details
  UPDATE 30/6/26 - newest dev version of GRAVI (gonna call this GRAVI_sp_ver for now) has included a motif analysis step. SO, will pause this bit for now and test that out, to see if that is sufficient to cover this portion. ***

# New features
- Add mouse cytoband information
    *** this requires information from extraChIPs package, which currently only houses hg19 and hg38 cytobands. Since this information is not super crucial, have removed it from current script to make sure script is usable across species. ***
- Have a separate fdr_alpha in config.yml for RNA-seq DEG threshold (to give more flexibility to DEG/DBS definitions)
    *** done in GRAVI_v1 ***
- Consider having a full-GRAVI version (includes QC/alignment/filtering steps that can take FASTQ input files) alongside GRAVI-lite (original GRAVI pipeline from BAM onwards). --> check with Beata on standard Tilley lab pipeline and see about consolidate this with Russell lab pipeline.
- See if deeptools plotHeatmap can replace current heatmap version (which allows for stacked subset plotting)
    *** current python version (3.14) on which the pipeline is tested, there is no compatible deepTools package version (requires python<=3.11). Attempts to recreate deepTools-styled heatmap didn't look very pretty. For now, will stick with plotProfileHeatmap plot versions (not stackable). ***
- See if deeptools Pearson/Spearman sample correlation can be included as a plot
    *** done in GRAVI_v1 ***
- Should include a ChIP-seq vs RNA-seq logFC correlation scatterplot. Consider also adding boxplot (or similar) of overall RNA-seq logFC in TF subsets (unchanged/up/down/etc). Darryl's idea: consider adding histogram of data point distribution along x/y axis (ala AUCell-style)
    *** ChIP-seq vs RNA-seq is already a plot. Density plots along x/y axes added in GRAVI_v1 ***
- Should report somewhere what methods were used for differential peak analysis (SQ/LS and IHW methods), ideally html report.
    *** Apparently already in Differential Binding outline page. Check that this swap in method description happens when using differnt method settings ***
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
    *** FIX: set up TMP folders prior to run to redirect tmp file writing away from default. See acompanied bash file for details. With this, script has been tested at core = 4, mem = 50GB *** 
- If running snakemake via Slurm from the beginning (ie no custom conda envs pre-made), conda env creation sometimes fails due to connection issues. Current fix - to set up conda envi prior to Slurm run (using snakemake --use-conda --conda-create-envs-only --cores 1)
- Pairwise comparison html file not incorporated in overall report with other html files (ie no hyperlink/tab for it)
- Current peak csv output of differential_binding.Rmd is aa bit problematic, since it is 1. on gene level, thus a peak can be assigned to more than 1 gene, 2. peaks not assigned to gene (ie intergenic peaks) are not included in this file. the accompanied rds file contains all peaks, but requires Seqinfo package to view which requires the latest version of R/Bioconductor. --> should have this full set write out as a csv as well.
