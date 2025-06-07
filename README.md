Bioinformatics Pipeline for RNA-Seq Analysis of E. coli under Magainin I Treatment

Overview

This repository contains the documentation and Galaxy workflow for trimming, aligning, and quantifying RNA-Seq data from Escherichia coli strains resistant and susceptible to the antimicrobial peptide Magainin I. The analysis uses the ENA dataset SRX3733298 and leverages Galaxy’s user‑friendly interface to demonstrate a fully reproducible pipeline.

Table of Contents

Repository Structure

Data

Tools

Workflow

Parameters

Cutadapt

Bowtie2

Samtools flagstat

FeatureCounts

Results

Alignment Metrics

Top Expressed Genes

Expression Distribution

Reproducing the Analysis

Requirements

License

Acknowledgements

Repository Structure

├── workflow/            # Galaxy workflow export (.ga)
├── data/                # Scripts or links to download raw FASTQ
├── results/             # Trimmed FASTQ, BAM, count tables, plots
├── scripts/             # R script for plotting and analysis
├── LICENSE              # MIT License
└── README.md            # This file

Data

Study ID: SRX3733298

Organism: Escherichia coli

Platform: Illumina MiSeq (paired‐end)

FASTQ files: SRR6760835_1.fastq.gz, SRR6760835_2.fastq.gz

Source: European Nucleotide Archive (ENA)

Tools

Galaxy: web‐based bioinformatics platform

Cutadapt (GPU-accelerated): trimming adapters and low‐quality bases

Bowtie2: alignment to reference genome

Samtools flagstat: alignment quality metrics

FeatureCounts: read quantification per gene

R: data exploration and plotting (scripts in scripts/)

Workflow

Pre‐processing: trim raw FASTQ with Cutadapt in Galaxy.

Alignment: align trimmed reads to E. coli K-12 MG1655 (ASM584v2) with Bowtie2.

QC: collect alignment stats via Samtools flagstat.

Quantification: count reads per gene using FeatureCounts and a modified GTF.

Analysis: identify top expressed genes and plot expression distribution with R.

Parameters

Cutadapt

Paired‐end: enabled

Minimum overlap: 3 bp

Max error rate: 0.1

Wildcards in adapters: yes; in reads: no

Trim action: remove adapter + flanking

Minimum read length: 1 bp (no discards)

Pair filter: any

Bowtie2

Reference genome: ASM584v2 (E. coli K-12 MG1655)

Library type: paired‐end

Preset: default

Output: SAM/BAM

Samtools flagstat

Total reads: 14,481,266

Mapped: 96.16%

Properly paired: 91.65%

Singletons: 1.40%

FeatureCounts

Mapping quality filter: 0

Include secondary alignments: yes

Minimum overlap: 0

Ignore duplicates: no

Multi-feature assignment: no

Note: the GTF file was edited to replace contig name U00096.3 with Chromosome for compatibility with the BAM headers.

Results

Alignment Metrics

Wall Clock Time: 7 min (trimmed) vs 15 min (raw)

Max memory usage: ~4.7 GB

CPU cores allocated: 8

Top Expressed Genes

Gene ID

Feature

Raw Count

B2911

RNA 6S

867,693

B3123

RnpB (RNase P)

562,936

B4408

csrB

...

B4441

GlmY

...

B4457

CsrC

...

Expression Distribution

Log2(count+1) distribution shows the expected RNA-Seq skew: most genes have low‐to‐moderate expression, with a minority of highly expressed outliers. See results/expression_distribution.png.

Reproducing the Analysis

Import workflow/pipeline.ga into your Galaxy instance.

Upload or link the raw FASTQ files from ENA (SRX3733298).

Run the workflow end‐to‐end.

Download trimmed FASTQ, BAM, and count tables.

Execute Rscript scripts/analysis.R to generate plots in results/.

Requirements

Galaxy (v20.09 or later) with GPU support for Cutadapt (optional)

R (≥ 4.0) with ggplot2

License

This project is licensed under the MIT License – see the LICENSE file for details.

Acknowledgements

Galaxy Project

ENA, Bowtie2, Samtools, Subread (FeatureCounts)

Studies on Magainin I response in E. coli