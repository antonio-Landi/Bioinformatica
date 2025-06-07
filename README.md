# Bioinformatics Pipeline for RNA-Seq Analysis of *E. coli* under Magainin I Treatment

![License](https://img.shields.io/badge/license-MIT-green) ![Galaxy Workflow](https://img.shields.io/badge/Galaxy%20Workflow-v1.0-blue)

---

## Overview

Questo repository contiene la documentazione, il workflow e i metadati per una pipeline Galaxy completamente riproducibile che esegue trimming, allineamento e quantificazione di dati RNA-Seq da ceppi di *Escherichia coli* trattati con il peptide antimicrobico Magainin I (dataset ENA **SRX3733298**).

---

## Table of Contents

- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [Data](#data)
- [Data Availability](#data-availability)
- [Tools](#tools)
- [Workflow](#workflow)
- [Reproducing the Analysis](#reproducing-the-analysis)
- [Requirements](#requirements)
- [License](#license)
- [Acknowledgements](#acknowledgements)

---

## Repository Structure

```bash
├── docs/                # Documentazione (PDF)
├── slides/              # Presentazioni (PowerPoint)
├── counts/              # FeatureCounts outputs (tabular counts and summary)
├── results/
│   └── plots/           # Resulting plots (PNG files)
├── LICENSE              # Licenza MIT
└── README.md            # Questo file

```

## Data

Study ID: SRX3733298

Organism: Escherichia coli

Platform: Illumina MiSeq (paired‐end)

FASTQ files: SRR6760835_1.fastq.gz, SRR6760835_2.fastq.gz

Source: European Nucleotide Archive (ENA)

## Data Availability
Raw sequencing data
ENA dataset SRX3733298
```bash
Download:
https://www.ebi.ac.uk/ena/browser/view/SRX3733298
```
Processed data & results
Disponibili nella release v1.0:
```bash
https://github.com/antonio-Landi/Bioinformatica/releases/tag/v1.0.0
```
Assets inclusi:
project_data_v1.0.zip
Trimmed FASTQ
BAM alignment files

## Tools

Galaxy: web‐based bioinformatics platform

Cutadapt (GPU-accelerated): trimming adapters and low‐quality bases

Bowtie2: alignment to reference genome

Samtools flagstat: alignment quality metrics

FeatureCounts: read quantification per gene

R: data exploration and plotting (scripts in scripts/)

## Workflow

Pre‑processing: trim raw FASTQ with Cutadapt in Galaxy.

Alignment: map trimmed reads to E. coli K‑12 MG1655 (ASM584v2) with Bowtie2.

QC: collect stats via Samtools flagstat.

Quantification: count reads per gene using FeatureCounts and a modified GTF.

Analysis: identify top expressed genes and generate distribution plots with R.

## Reproducing the Analysis

Download raw data from ENA (SRX3733298).

Download processed assets from the v1.0 release.

Import workflow/pipeline.ga into Galaxy.

Review QC, alignment, and count tables in the release.


## Requirements
Galaxy
R ≥ 4.0 con pacchetto ggplot2

## License
Questo progetto è distribuito sotto la MIT License. Vedi LICENSE per il testo completo.

## Acknowledgements

Galaxy Project

ENA, Bowtie2, Samtools, Subread (FeatureCounts)

Studies on Magainin I response in E. coli