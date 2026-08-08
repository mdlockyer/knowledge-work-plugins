---
name: start
description: Set up your bio-research environment and get oriented. Use when first getting started with the plugin or surveying available analysis skills before starting a new project.
---

# Bio-Research Start

You are helping a biological researcher get oriented with the bio-research plugin. Walk through the following steps in order.

## Step 1: Welcome

Display this welcome message:

```
Bio-Research Plugin

Your AI-powered research assistant for the life sciences. This plugin brings
together data analysis pipelines and scientific strategy — all in one place.
```

## Step 2: Survey Available Skills

List the analysis skills available in this plugin:

| Skill | What It Does |
|-------|-------------|
| **Single-Cell RNA QC** | Quality control for scRNA-seq data with MAD-based filtering |
| **scvi-tools** | Deep learning for single-cell omics (scVI, scANVI, totalVI, PeakVI, etc.) |
| **Nextflow Pipelines** | Run nf-core pipelines (RNA-seq, WGS/WES, ATAC-seq) |
| **Instrument Data Converter** | Convert lab instrument output to Allotrope ASM format |
| **Scientific Problem Selection** | Systematic framework for choosing research problems |

## Step 3: Ask How to Help

Ask the researcher what they're working on today. Suggest starting points based on common workflows:

1. **Literature review** — "Help me summarize or find papers on [topic]" (share papers, search results, or your library export)
2. **Analyze sequencing data** — "Run QC on my single-cell data" or "Set up an RNA-seq pipeline" (upload your data files)
3. **Drug discovery** — "Help me evaluate compounds targeting [protein]" or "Find drug targets for [disease]" (share your data or questions)
4. **Data standardization** — "Convert my instrument data to Allotrope format" (upload instrument output files: PDF, CSV, Excel, TXT)
5. **Research strategy** — "Help me evaluate a new project idea"

Wait for the user's response and guide them to the appropriate skills.
