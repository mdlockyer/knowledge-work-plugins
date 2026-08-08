# Bio-Research Plugin

Connect to preclinical research tools and databases (literature search, genomics analysis, target prioritization) to accelerate early-stage life sciences R&D. Use with [Cowork](https://claude.com/product/cowork) or install directly in Claude Code.

This plugin consolidates 5 analysis skills into a single package for life science researchers.

## What's Included

### Skills (Analysis Workflows)

#### Single-Cell RNA QC
Automated quality control for scRNA-seq data following scverse best practices. Supports `.h5ad` and `.h5` files with MAD-based filtering and comprehensive visualizations.

#### scvi-tools
Deep learning toolkit for single-cell omics. Covers scVI, scANVI, totalVI, PeakVI, MultiVI, DestVI, veloVI, and sysVI models for integration, batch correction, label transfer, and multi-modal analysis.

#### Nextflow Pipelines
Run nf-core bioinformatics pipelines on local or public GEO/SRA sequencing data:
- **rnaseq** — Gene expression and differential expression
- **sarek** — Germline and somatic variant calling (WGS/WES)
- **atacseq** — Chromatin accessibility analysis

#### Instrument Data to Allotrope
Convert laboratory instrument output files (PDF, CSV, Excel, TXT) to Allotrope Simple Model (ASM) format. Supports 40+ instrument types including cell counters, spectrophotometers, plate readers, qPCR, and chromatography systems.

#### Scientific Problem Selection
Systematic framework for research problem selection based on Fischbach & Walsh's framework. Includes 9 skills covering ideation, risk assessment, optimization, decision trees, adversity planning, and synthesis.

## Getting Started

```bash
# Install the plugin
/install anthropics/knowledge-work-plugins bio-research

# Run the start command to see available tools
/start
```

## Common Workflows

**Literature Review**
Share papers, search results, or your library export for literature review; create figures from your data.

**Single-Cell Analysis**
Run QC on scRNA-seq data, then use scvi-tools for integration, batch correction, and cell type annotation.

**Sequencing Pipeline**
Download public data from GEO/SRA, run nf-core pipelines (RNA-seq, variant calling, ATAC-seq), and verify outputs.

**Drug Discovery**
Analyze compound data, prioritize drug targets, and review clinical trial data you provide.

**Research Strategy**
Pitch a new idea, troubleshoot a stuck project, or evaluate strategic decisions using the scientific problem selection framework.

## License

Skills are licensed under Apache 2.0.
