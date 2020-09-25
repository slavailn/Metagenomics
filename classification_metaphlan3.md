<h2>Analyzing sequencing libraries with Metaphlan3</h2>
<h3>Workflow template</h3>

<h3>Links:</h3>
[Github https://github.com/biobakery/MetaPhlAn](https://github.com/biobakery/MetaPhlAn)
[Nature methods paper: Metagenomic microbial community profiling using unique clade-specific marker genes](https://www.nature.com/articles/nmeth.2066)
[Metaphlan workflow at SevenBridges](https://github.com/stevetsa/Metaphlan-SBCGC)
[Guide to software tools for microbial analysis](https://gencore.bio.nyu.edu/beginners-guide-to-bioinformatic-tools-for-analyzing-microbiome-data/)

**1. Metaphlan3 installation**
Start with creating new conda environment:

```
conda create env meta3

```

Activate meta3 environment:

```
conda activate meta3

```

Install metaphlan in the new environment:

```
conda install -c bioconda metaphlan

```

**2. Basic usage**

Classify microbiota starting with fastq file:

```

metaphlan metagenome.fastq --input_type fastq -o profiled_metagenome.txt

```

Retain intermediate bowtie2 alignments to reuse them later to speed up any re-analysis

```

metaphlan metagenome.fastq --bowtie2out metagenome.bowtie2.bz2 --nproc 5 --input_type fastq -o profiled_metagenome.txt

```

Use intermediate bowtie alignment files in reanalysis:

```

metaphlan metagenome.bowtie2.bz2 --nproc 5 --input_type bowtie2out -o profiled_metagenome.txt

```

Run the analysis with external bowtie mapped file:

```

bowtie2 --sam-no-hd --sam-no-sq --no-unal --very-sensitive -S metagenome.sam -x metaphlan_database/mpa_v30_CHOCOPhlAn_201901 -U metagenome.fastq
metaphlan metagenome.sam --input_type sam -o profiled_metagenome.txt

```

Estimate fraction of metagenome composed of unknown microbes:

```

metaphlan metagenome.fastq --bowtie2out metagenome.bowtie2.bz2 --nproc 5 --input_type fastq --unknown_estimation -o profiled_metagenome.txt

```

** 3. Metaphlan analysis of human RNA-seq data (lung tumors)**

The analysis starts with HISAT2 bam files.

1) Filter out unmapped reads and save them as fastq using gnu parallel to speedup the process

```

fastq_lines='{print "@"$1"\n"$10"\n+\n"$11}'
parallel "samtools view -f 4 {} | awk '$fastq_lines' > {.}.unmapped.fastq" ::: *.bam

```

2) Run metaphlan for the first time. Here I specified custom location for the metaphlane database and --index 'latest' to download the latest database release.
With this run metaphlane will download the database into a specified location and create bowtie2 index, 2 output files. The output files are bowtie2out with bowtie alignments and a profile inteself. When running metaphlan for actual analysis the --bowtie2db option remains the same pointing to db location and --index option is a prefix of bowtie2 index files. With --index option we will need nothin but the prefix name not a path.

```

metaphlan <fastq> --input_type fastq --bowtie2db /path/to/metaphlan_database/ --bowtie2out <*.bowtie2out.txt> --tax_lev s --add_viruses -o <*.profile.txt> --index latest

```

3) Run metaphlan analysis in parallel on mutiple samples:

```

parallel 'metaphlan {} --input_type fastq --bowtie2db </path/to/metaphlan_database> --bowtie2out {.}.bowtie2out.txt --tax_lev s -o {.}.profile.txt --index mpa_v30_CHOCOPhlAn_201901' ::: *.unmapped.fastq

```

4) Run metaphlan in parallel on multiple samples, but this time add viruses to the classification:

```

parallel 'metaphlan {} --input_type fastq --bowtie2db </path/to/metaphlan_database> --bowtie2out {.}.bowtie2out.txt --tax_lev s --add_viruses -o {.}.profile.txt --index mpa_v30_CHOC$COPhlAn_201901' ::: *.unmapped.fastq

```

5) Merge separate profile files into OTU table using the utility script that comes with the software:
merge_metaphlan_tables.py *_profile.txt > merged_table.txt
