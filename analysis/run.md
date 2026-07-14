
to run: 
1. Create conda environments
snakemake --use-conda --conda-prefix '/home/a1242191/miniconda3/envs/' --conda-create-envs-only --cores 1 --until check_r_packages

2. added this merge_fdr: 0.05 to config.yml

3. I have put all .bam files directly in data/bam, without subfolders

4. test run only on one TF: ER 

5. running with the above command: 

Building DAG of jobs...
Creating conda environment workflow/envs/macs2.yml...
Downloading and installing remote packages.
Cleaning up conda package tarballs.
Environment for /scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/../envs/macs2.yml created (location: ../../../../../home/a1242191/miniconda3/envs/93bdd2a63657681da84b5f6dbdd7793d_)
Creating conda environment workflow/envs/samtools.yml...
Downloading and installing remote packages.
Cleaning up conda package tarballs.
Environment for /scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/../envs/samtools.yml created (location: ../../../../../home/a1242191/miniconda3/envs/01976d8c5a1edcdc877541d4a7740fce_)
Creating conda environment workflow/envs/bedgraph_to_bigwig.yml...
Downloading and installing remote packages.
Cleaning up conda package tarballs.
Environment for /scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/../envs/bedgraph_to_bigwig.yml created (location: ../../../../../home/a1242191/miniconda3/envs/3c27530a5e44c9f080aac357fdf2fc16_)
Creating conda environment workflow/envs/rmarkdown.yml...
Downloading and installing remote packages.

6. snakemake \
	--use-conda \
	--conda-prefix '/home/a1242191/miniconda3/envs/' \
	--allowed-rules update_extrachips \
	--cores 1

- gives me a lot of errors of missing files for rule all in Snakefile 

7. snakemake \
	-p \
	--use-conda \
	--conda-prefix '/home/a1242191/miniconda3/envs/' \
	--notemp \
	--rerun-triggers mtime \
	--keep-going \
	--cores 16

Finished jobid: 10 (Rule: make_chrom_sizes)
2 of 41 steps (5%) done
Setting stdout to  workflow/logs/initial_checks/check_r_packages.log
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:255: SyntaxWarning: invalid escape sequence '\s'
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:282: SyntaxWarning: invalid escape sequence '\s'
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:255: SyntaxWarning: invalid escape sequence '\s'
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:255: SyntaxWarning: invalid escape sequence '\s'
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:282: SyntaxWarning: invalid escape sequence '\s'
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:282: SyntaxWarning: invalid escape sequence '\s'
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:255: SyntaxWarning: invalid escape sequence '\s'
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:255: SyntaxWarning: invalid escape sequence '\s'
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:282: SyntaxWarning: invalid escape sequence '\s'
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:255: SyntaxWarning: invalid escape sequence '\s'
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:282: SyntaxWarning: invalid escape sequence '\s'
/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk:282: SyntaxWarning: invalid escape sequence '\s'
grep: library\(.+\): No such file or directory
Warning message:
In system2("egrep", c(cmd, cmd2), stdout = TRUE) :
  running command ''egrep' 'library\(.+\)' /scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/scripts/*R 'library\(.+\)' /scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/scripts/*R' had status 2
Bioconductor version 3.22 (BiocManager 1.30.27), R 4.5.3 (2026-03-11)
Installing package(s) 'SimpleUpset', 'BSgenome.Hsapiens.UCSC.hg19'
trying URL 'https://cloud.r-project.org/src/contrib/SimpleUpset_0.1.4.tar.gz'
trying URL 'https://bioconductor.org/packages/3.22/data/annotation/src/contrib/BSgenome.Hsapiens.UCSC.hg19_1.4.3.tar.gz'


RuleException:
CalledProcessError in file "/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/workflow/rules/macs2.smk", line 93:
Command 'source /home/a1242191/miniconda3/bin/activate '/home/a1242191/miniconda3/envs/8ae18d6a308beaf4fed1548ae949d4e1_'; set -euo pipefail;  Rscript --vanilla /scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/.snakemake/scripts/tmp5sfbupid.peak_qc.R' returned non-zero exit status 1.
[Fri Jun 19 13:04:47 2026]
Error in rule peak_qc:
    message: None
    jobid: 29
    input: data/bam/ER_DHT_3.bam, data/bam/ER_DHT_1.bam, data/bam/ER_Veh_2.bam, data/bam/ER_Veh_3.bam, data/bam/ER_Veh_1.bam, data/bam/ER_DHT_2.bam, output/annotations/blacklist.rds, output/greylist/greylists.rds, data/bam/ER_Input.bam, output/macs2/ER_DHT_3/ER_DHT_3_callpeak.log, output/macs2/ER_DHT_1/ER_DHT_1_callpeak.log, output/macs2/ER_Veh_2/ER_Veh_2_callpeak.log, output/macs2/ER_Veh_3/ER_Veh_3_callpeak.log, output/macs2/ER_Veh_1/ER_Veh_1_callpeak.log, output/macs2/ER_DHT_2/ER_DHT_2_callpeak.log, output/checks/r-packages.chk, output/macs2/ER_DHT_3/ER_DHT_3_peaks.narrowPeak, output/macs2/ER_DHT_1/ER_DHT_1_peaks.narrowPeak, output/macs2/ER_Veh_2/ER_Veh_2_peaks.narrowPeak, output/macs2/ER_Veh_3/ER_Veh_3_peaks.narrowPeak, output/macs2/ER_Veh_1/ER_Veh_1_peaks.narrowPeak, output/macs2/ER_DHT_2/ER_DHT_2_peaks.narrowPeak, output/annotations/seqinfo.rds, output/annotations/gene_regions.rds
    output: output/macs2/ER/ER_cross_correlations.tsv, output/macs2/ER/ER_qc_samples.tsv
    log: workflow/logs/peak_qc/ER_peak_qc.log (check log file(s) for error details)
    conda-env: /home/a1242191/miniconda3/envs/8ae18d6a308beaf4fed1548ae949d4e1_
^[[B^[[B^[[B^[[B^[[B[Fri Jun 19 13:05:32 2026]
Finished jobid: 7 (Rule: compile_annotations_html)
25 of 41 steps (61%) done
Exiting because a job execution failed. Look below for error messages
[Fri Jun 19 13:05:32 2026]
Error in rule peak_qc:
    message: None
    jobid: 29
    input: data/bam/ER_DHT_3.bam, data/bam/ER_DHT_1.bam, data/bam/ER_Veh_2.bam, data/bam/ER_Veh_3.bam, data/bam/ER_Veh_1.bam, data/bam/ER_DHT_2.bam, output/annotations/blacklist.rds, output/greylist/greylists.rds, data/bam/ER_Input.bam, output/macs2/ER_DHT_3/ER_DHT_3_callpeak.log, output/macs2/ER_DHT_1/ER_DHT_1_callpeak.log, output/macs2/ER_Veh_2/ER_Veh_2_callpeak.log, output/macs2/ER_Veh_3/ER_Veh_3_callpeak.log, output/macs2/ER_Veh_1/ER_Veh_1_callpeak.log, output/macs2/ER_DHT_2/ER_DHT_2_callpeak.log, output/checks/r-packages.chk, output/macs2/ER_DHT_3/ER_DHT_3_peaks.narrowPeak, output/macs2/ER_DHT_1/ER_DHT_1_peaks.narrowPeak, output/macs2/ER_Veh_2/ER_Veh_2_peaks.narrowPeak, output/macs2/ER_Veh_3/ER_Veh_3_peaks.narrowPeak, output/macs2/ER_Veh_1/ER_Veh_1_peaks.narrowPeak, output/macs2/ER_DHT_2/ER_DHT_2_peaks.narrowPeak, output/annotations/seqinfo.rds, output/annotations/gene_regions.rds
    output: output/macs2/ER/ER_cross_correlations.tsv, output/macs2/ER/ER_qc_samples.tsv
    log: workflow/logs/peak_qc/ER_peak_qc.log (check log file(s) for error details)
    conda-env: /home/a1242191/miniconda3/envs/8ae18d6a308beaf4fed1548ae949d4e1_
Complete log(s): /scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/.snakemake/log/2026-06-19T125936.216494.snakemake.log
WorkflowError:
At least one job did not complete successfully.

^[[B^[[B^[[B^[[B^[[B[Fri Jun 19 13:05:32 2026]
Finished jobid: 7 (Rule: compile_annotations_html)
25 of 41 steps (61%) done
Exiting because a job execution failed. Look below for error messages
[Fri Jun 19 13:05:32 2026]
Error in rule peak_qc:
    message: None
    jobid: 29
    input: data/bam/ER_DHT_3.bam, data/bam/ER_DHT_1.bam, data/bam/ER_Veh_2.bam, data/bam/ER_Veh_3.bam, data/bam/ER_Veh_1.bam, data/bam/ER_DHT_2.bam, output/annotations/blacklist.rds, output/greylist/greylists.rds, data/bam/ER_Input.bam, output/macs2/ER_DHT_3/ER_DHT_3_callpeak.log, output/macs2/ER_DHT_1/ER_DHT_1_callpeak.log, output/macs2/ER_Veh_2/ER_Veh_2_callpeak.log, output/macs2/ER_Veh_3/ER_Veh_3_callpeak.log, output/macs2/ER_Veh_1/ER_Veh_1_callpeak.log, output/macs2/ER_DHT_2/ER_DHT_2_callpeak.log, output/checks/r-packages.chk, output/macs2/ER_DHT_3/ER_DHT_3_peaks.narrowPeak, output/macs2/ER_DHT_1/ER_DHT_1_peaks.narrowPeak, output/macs2/ER_Veh_2/ER_Veh_2_peaks.narrowPeak, output/macs2/ER_Veh_3/ER_Veh_3_peaks.narrowPeak, output/macs2/ER_Veh_1/ER_Veh_1_peaks.narrowPeak, output/macs2/ER_DHT_2/ER_DHT_2_peaks.narrowPeak, output/annotations/seqinfo.rds, output/annotations/gene_regions.rds
    output: output/macs2/ER/ER_cross_correlations.tsv, output/macs2/ER/ER_qc_samples.tsv
    log: workflow/logs/peak_qc/ER_peak_qc.log (check log file(s) for error details)
    conda-env: /home/a1242191/miniconda3/envs/8ae18d6a308beaf4fed1548ae949d4e1_
Complete log(s): /scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/.snakemake/log/2026-06-19T125936.216494.snakemake.log
WorkflowError:
At least one job did not complete successfully.

8. Spoke with Claude about the error
Fix: remove the type column from samples.tsv 

9. in enrichment_fins.R 

id2gene <- setNames(gtf$gene_name, gtf$gene_id)
  # overvritten gtf <- plyrenages::select(gtf, gene_id)
  #with gtf <- gtf[, "gene_id"]
    genome(gtf) <- genome

   The fix is simple — replace plyranges::select(gtf, gene_id) with standard GRanges column subsetting, which is equivalent and doesn't depend on plyranges:

After that fix, this is left: 
Job stats:
job                            count
---------------------------  -------
compile_signal_summary_html        1
compile_index_html                 1
all                                1
total                              3

failed on script <ER>_signal_summary.Rmd
to run it interactively: rmarkdown::render_site("analysis/ER_signal_summary.Rmd")

within the Rmd, running manually: 
all packages loaded
Warning message:
In readLines(file, warn = readLines.warn) :
  incomplete final line found on '/scratchdata1/groups/phoenix-hpc-drmcrl/gravi/GRAVI/config/config.yml'
so I have added a new line

fixed part of the enrich-corrplot chunk that was creating an empty object

in cor_mat <- motif_list %>% 
    dplyr::filter(name %in% top_enrich)
replaced altname with name!

edited: 
```{r plot-total-pos-matches, eval = n_pos > 0, echo = n_pos > 0, fig.cap = glue("*All best matches by their distance from the sequence centre, without binning by position. Black lines represent the loess curve through all matches. The motif with the most matches within the enriched region is shown for each cluster, with the other motifs within the cluster indicated below in brackets.*")}
lb <- glue("{names(clust_names)}\n({clust_names})") %>% 
  setNames(names(clust_names))
top_matches <- motif_list %>% 
  dplyr::filter(altname %in% top_pos$altname) %>% 
  mutate(fct = factor(altname, levels = top_pos$altname)) %>% 
  arrange(fct)
if (nrow(top_matches) == 0) {
  message("No motifs in motif_list matched top_pos$altname — skipping positional plots.")
  knitr::knit_exit()
}