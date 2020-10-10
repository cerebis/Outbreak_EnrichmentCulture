# Enrichment culture dataset analysis

This directory contains the data and scripts used in the analysis for the enrichment culture dataset for the Outbreak project.

* `data` directory contains metadata and small output data files generated from the analysis
* `bin` directory contains scripts and workflows used in the analysis
* `testing_scripts` directory contains scripts in testing (not necessarily working)
* `docs` directory contains usage/information of scripts and data
* `archive` directory contains old and unused scripts and old data

### Scripts usage
* [assembly-metaflye_and_polish.nf](docs/assembly-metaflye_and_polish.md)
* [shortrd-map_and_bin.nf](docs/shortrd-map_and_bin.md)
* [hic-map_and_vcf.nf](docs/hic-map_and_vcf.md)
* [chromosome_check.nf](docs/chromosome_check.md)
* run_checkm.sh - run CheckM for quality assessment on the metabat2 output and bin3c output. Dependent on CheckM version < 1.1
* cleanup.sh - to clean up the cache and work files generated by nextflow

### `data` contents
#### input_files
* directory contains runtables that detail the locations and sample ID of the HiC, short-read and long-read dataset for this project on the UTS HPC computer
#### results
* abricate antimicrobial gene screening results (using ncbi and resfinder databases)
* checkM genome quality assessment graphs
* mlplasmid prediction results
* PlsDB plasmid identification results

### Log
* *28 Aug 2020*
    * added workflow for long-read assembly (`script/assembly-metaflye_and_polish.nf`)
    * added workflow for short-read mapping and binning (`script/shortrd-map_and_bin.nf`)

* *1 Sep 2020*
    * modified `shortrd-map_and_bin.nf` to take each of SH/WG set at a time
    * unified input runtables for different scripts
    * added workflow for hiC mapping (`script/hic-map_and_bin3c.nf`)

* *4 Sep 2020*
    * renamed `script` directory to `bin` and made scripts executable
    * added ABRicate antimicrobial resistance genes screening results to `data/results`
    * added qa graphs from `checkM` genome quality assessment to `data/results`

* *9 Sep 2020*
    * added mlplasmid plasmid prediction results to `data/results`
    * added PlsDB sequence Mash plasmid identification results to `data/results`
    * renamed hiC workflow from `hic-map_and_bin3c.nf` to `hic-map_and_vcf.nf`
    * added index and bgzf steps in workflow

* *16 Sep 2020*
    * added new workflow that combined long-read assembly and short-read mapping and binning steps (`bin/assembly_map_vcall.nf`)

* *10 Oct 2020*
    * added new workflow for mash screen contigs against list of bacterial chromosome genomes (`bin/chromosome_check.nf`)
    * list of accession number downloaded for input of `chromosome_check.nf` is in `data/input_files/complete_assembly_enterobacteriaceae_chromosome_list.txt`