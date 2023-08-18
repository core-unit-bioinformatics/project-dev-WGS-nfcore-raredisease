# WGS nf-core raredisease test

This project aims on testing the nf-core raredisease pipeline for usage with whole-genome sequencing short-read Illumina data.

## Data

For testing we use the GIAB Ashkenazim trio patient samples:

Son: HG002
Father: HG003
Mother: HG004

These were sequenced using Illumina WGS 2x 250bp technology, more information about library prepration and sequencing can be found in the [README](data/README_NIST_Illumina_pairedend_2x250_HG002.txt).

Data was downloaded from NCBI FTP server and indexes extracted from https://github.com/genome-in-a-bottle/giab_data_indexes on 8th August 2023.

## Workflow

1. Download workflow and singularity images

`nf-core download raredisease --revision 1.1.1 --compress none --container-system singularity --container-cache-utilisation copy`

2. Download and adapt references and plugins

This workflow requires the nextflow plugins nf-validation and nf-amazon. For offline deployment, follow this [hint](https://github.com/core-unit-bioinformatics/knowledge-base/wiki/nextflow-plugins-offline).
- nf-validation v0.3.1
- nf-amazon v1.16.2

References:

The list of references needed is explained in the usage and params documentation: https://nf-co.re/raredisease/1.1.1/docs/usage & https://nf-co.re/raredisease/1.1.1/parameters

- Reference genome GRCh38
    - downloaded from GIAB
    - `wget --recursive -e robots=off --reject "index.html" --no-host-directories --cut-dirs=6 https://ftp.ncbi.nlm.nih.gov/ReferenceSamples/giab/release/references/GRCh38/ -P $PWD`
- VEP cache version 107
- strangers variant catalog file for --variant_catalog
    - from: https://github.com/Clinical-Genomics/stranger/blob/master/stranger/resources/variant_catalog_grch37.json
    - According to new usage documentation in dev branch (https://github.com/nf-core/raredisease/issues/380)
- gnomAD
    - downlaod from official website https://gnomad.broadinstitute.org/downloads#v3
    - reformatting with vembrane table `vembrane table --header 'CHROM, POS, REF, ALT, AF' 'CHROM, POS, REF, ALT, INFO["AF"]'`
    - Add comma between REF adn ALT with awk.
    - WARNING: only used chr1 for testing the first run
- CADD resources: https://cadd.gs.washington.edu/download "All possible SNVs of GRCh38/hg38" and data/annotations folder
    - for cadd_resources parameter to annotate indels: "Path to a folder containing cadd annotations. Equivalent of the data/annotations/ folder described here, and it is used to calculate CADD scores for small indels.": `annotationGRCh38_v1.6.tar.gz`
- from the official test datasets ():
    - vcfanno config (toml) and adapted resources
    - svdb
    - score_config_snv: https://github.com/nf-core/test-datasets/blob/raredisease/reference/rank_model_snv.ini
    - score_config_sv: https://github.com/nf-core/test-datasets/blob/raredisease/reference/rank_model_sv.ini

3. Run

For first run, limited analysis as following:
- gnomAD only with chr1 (due to slow download)
- skip CNV calling (missing ploidy and gcnvcaller model)

<!--
For running the test profile on HILBERT: download test datasets
#Alternative: download test datasets
`git clone git@github.com:nf-core/test-datasets.git`
`git clone git@github.com:ramprasadn/test-datasets.git`
-->

# Citation

If not indicated otherwise above, please follow [these instructions](CITATION.md) to cite this repository in your own work.
