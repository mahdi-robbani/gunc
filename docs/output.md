# gunc: Output

## Introduction

This document describes the output produced by the pipeline. 

The directories listed below will be created in the results directory after the pipeline has finished. All paths are relative to the top-level results directory.

## Pipeline overview

The pipeline is built using [Nextflow](https://www.nextflow.io/) and processes data using the following steps:

- [CheckM](#CheckM) - Quality Control with CheckM 
- [GUNC](#GUNC) - Detect chimerism and contamination with GUNC and combine with CheckM results
- [Pipeline information](#pipeline-information) - Report metrics generated during the workflow execution

### CheckM

<details markdown="1">
<summary>Output files</summary>

- `CheckM/`
  - `*_wf.tsv`: Summary tables for each sample
  - `*_qa.txt`: Quality assessment files
  - `bins/`: Contains genes and HMM analysis files for each metagenomic bin.
  - `storage/`:  Stores extended bin statistics and marker gene stats.

</details>

[CheckM](https://ecogenomics.github.io/CheckM/) provides detailed quality assessment for metagenomic bins. Its output can be found under the `CheckM` directory.

### GUNC

<details markdown="1">
<summary>Output files</summary>

- `gunc/`
  - `raw/`: Contains raw GUNC analysis files for each sample
  - `checkmmerged/`: Provides merged GUNC and CheckM results for comprehensive analysis

</details>

[GUNC](https://grp-bork.embl-community.io/gunc/) identifies chimerism and contamination in genomic bins. The relevant outputs are located in the `GUNC` directory.

### Pipeline information

<details markdown="1">
<summary>Output files</summary>

- `pipeline_info/`
  - Reports generated by Nextflow: `execution_report.html`, `execution_timeline.html`, `execution_trace.txt` and `pipeline_dag.dot`/`pipeline_dag.svg`.
  - Reformatted samplesheet files used as input to the pipeline: `samplesheet.valid.csv`.
  - Parameters used by the pipeline run: `params.json`.

</details>

[Nextflow](https://www.nextflow.io/docs/latest/tracing.html) provides excellent functionality for generating various reports relevant to the running and execution of the pipeline. This will allow you to troubleshoot errors with the running of the pipeline, and also provide you with other information such as launch commands, run times and resource usage.
