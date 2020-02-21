# Classification of sequences using CLARK

###*Problem:* classify sequencing reads against a collection of genomes using CLARK

###*Alternative tools:*
	1) NBC - naive bayessian classification, DNA-DNA http://nbc.ece.drexel.edu/;
        2) KRAKEN - k-mer based, DNA-DNA https://ccb.jhu.edu/software/kraken/;
        3) KrakenUniq - k-mer based classification combined with k-mer cardinality estimation, some useful additional features https://github.com/fbreitwieser/krakenuniq;
        4) Bracken - provides imroves species abundance estimates based on KRAKEN1/2 output https://ccb.jhu.edu/software/bracken/;
        5) MALT - ultrafast alignment tool alignment tool integrated with MEGAN for analysis https://uni-tuebingen.de/fakultaeten/mathematisch-naturwissenschaftliche-fakultaet/fachbereiche/informatik/lehrstuehle/algorithms-in-bioinformatics/software/malt/;
        6) Centrifuge - uses BWT and FM index to fast and memmory efficient processing of metagenomics data, can be run on desktop computer https://ccb.jhu.edu/software/centrifuge/;
        7) PathSeq - part of GATK, reports potential microbes in human dataset http://software.broadinstitute.org/pathseq/;
        8) DIAMOND - DNA-protein alignment tool 20000 faster than BLASTX https://uni-tuebingen.de/fakultaeten/mathematisch-naturwissenschaftliche-fakultaet/fachbereiche/informatik/lehrstuehle/algorithms-in-bioinformatics/software/diamond/;
        9) Kaiju - DNA-protein classification tool http://kaiju.binf.ku.dk/;
        10) MetaPhlan2 - classification based in unique marker genes http://huttenhower.sph.harvard.edu/metaphlan2.

###*Useful papers:*

Ye SH, Siddle KJ, Park DJ, Sabeti PC. Benchmarking Metagenomics Tools for Taxonomic Classification. Cell. 2019 Aug 8;178(4):779-794. doi: 10.1016/j.cell.2019.07.010. Review. PubMed PMID: 31398336; PubMed Central PMCID: PMC6716367.

McIntyre ABR, Ounit R, Afshinnekoo E, Prill RJ, Hénaff E, Alexander N, Minot SS, Danko D, Foox J, Ahsanuddin S, Tighe S, Hasan NA, Subramanian P, Moffat K, Levy S, Lonardi S, Greenfield N, Colwell RR, Rosen GL, Mason CE. Comprehensive benchmarking and ensemble approaches for metagenomic classifiers. Genome Biol. 2017 Sep 21;18(1):182. doi: 10.1186/s13059-017-1299-7. Erratum in: Genome Biol. 2019 Apr 5;20(1):72. PubMed PMID: 28934964; PubMed Central PMCID: PMC5609029.

Velsko IM, Frantz LAF, Herbig A, Larson G, Warinner C. Selection of Appropriate Metagenome Taxonomic Classifiers for Ancient Microbiome Research. mSystems. 2018 Jul 17;3(4). pii: e00080-18. doi: 10.1128/Systems.00080-18. eCollection 2018 Jul-Aug. PubMed PMID: 30035235; PubMed Central PMCID: PMC6050634.

Thomas AM, Manghi P, Asnicar F, Pasolli E, Armanini F, Zolfo M, Beghini F, Manara S, Karcher N, Pozzi C, Gandini S, Serrano D, Tarallo S, Francavilla A, Gallo G, Trompetto M, Ferrero G, Mizutani S, Shiroma H, Shiba S, Shibata T, Yachida S, Yamada T, Wirbel J, Schrotz-King P, Ulrich CM, Brenner H, Arumugam M, Bork P, Zeller G, Cordero F, Dias-Neto E, Setubal JC, Tett A, Pardini B, Rescigno M, Waldron L, Naccarati A, Segata N. Metagenomic analysis of colorectal cancer datasets identifies cross-cohort microbial diagnostic signatures and a link with choline degradation. Nat Med. 2019 Apr;25(4):667-678. doi: 10.1038/s41591-019-0405-7. Epub 2019 Apr 1. Erratum in: Nat Med. 2019 Dec;25(12):1948. PubMed PMID: 30936548.

Apopa PL, Alley L, Penney RB, Arnaoutakis K, Steliga MA, Jeffus S, Bircan E, Gopalan B, Jin J, Patumcharoenpol P, Jenjaroenpun P, Wongsurawat T, Shah N, Boysen G, Ussery D, Nookaew I, Fagan P, Bebek G, Orloff MS. PARP1 Is Up-Regulated in Non-small Cell Lung Cancer Tissues in the Presence of the Cyanobacterial Toxin Microcystin. Front Microbiol. 2018 Aug 6;9:1757. doi: 10.3389/fmicb.2018.01757. eCollection 2018. PubMed PMID: 30127774; PubMed Central PMCID: PMC6087756.

Huang D, Su X, Yuan M, Zhang S, He J, Deng Q, Qiu W, Dong H, Cai S. The characterization of lung microbiome in lung cancer patients with different clinicopathology. Am J Cancer Res. 2019 Sep 1;9(9): 047-2063. eCollection 2019. PubMed PMID: 31598405; PubMed Central PMCID: PMC6780665.

Jankauskaitė L, Misevičienė V, Vaidelienė L, Kėvalas R. Lower Airway Virology in Health and Disease-From Invaders to Symbionts. Medicina (Kaunas). 2018 Oct 13;54(5). pii: E72. doi: 10.3390/ medicina54050072. Review. PubMed PMID: 30344303; PubMed Central PMCID: PMC6262431.

Segal LN, Rom WN, Weiden MD. Lung microbiome for clinicians. New discoveries about bugs in healthy and diseased lungs. Ann Am Thorac Soc. 2014 Jan;11(1):108-16. doi: 10.1513/AnnalsATS.201310-339FR. Review. PubMed PMID: 24460444; PubMed Central PMCID: PMC3972985.

Gomes S, Cavadas B, Ferreira JC, Marques PI, Monteiro C, Sucena M, Sousa C, Vaz Rodrigues L, Teixeira G, Pinto P, Tavares de Abreu T, Bárbara C, Semedo J, Mota L, Carvalho AS, Matthiesen R, Pereira L, Seixas S. Profiling of lung microbiota discloses differences in adenocarcinoma and squamous cell carcinoma. Sci Rep. 2019 Sep 6;9(1):12838. doi: 10.1038/s41598-019-49195-w. PubMed PMID: 31492894; PubMed Central PMCID: PMC6731246.


###*CLARK materials:*
+ Paper: https://bmcgenomics.biomedcentral.com/articles/10.1186/s12864-015-1419-2
+ Downloads and documentation: http://clark.cs.ucr.edu/


###*CLARK workflow:*

CLARK uses k-mer based approach to classify sequencing reads (objects) against a database of genomes or any other sequences of interest (targets).

**INSTALLATION**
Download CLARK, unzip and expand the arhive. Change to CLARK direcctory and run *install.sh* script.

**Description of CLARK scripts**
 + set_targets.sh and classify_metagenome.sh: classify metagenomic samples databases. For example bacteria/archaea or virus (NCBI/RefSeq database), and Human (latest GRCh38). They will be downloaded automatically if needed. Any local database can be used/

 + buildSpacedDB.sh: Creates discriminate spaced k-mers from the selected databases (CLARK-S).

+ clean.sh: It will erase permanently all data downloaded/generated inside the database directory defined at the last call of "set_target.sh".

+ estimate_abundance.sh: Computes the abundance estimation (count and proportion for each target identified in CLARK results). Can produce input for the Krona executable ktImportTaxonomy, as well as results in the mpa format.

+ evaluate_density_confidence.sh, evaluate_density_gamma.sh: They take in input one or several CLARK results (containing confidence scores) and they output/plot the distribution of assignments per confidence score or gamma score.

+ resetCustomDB.sh: It resets the targets definition with sequences (newly added/modified) of the customized database. Any call of this script must be followed by a run of set_target.sh.

+ updateTaxonomy.sh: To update your local copy of the latest taxonomy data (taxonomy id, accession numbers, etc.) from the NCBI website.

+ makeSummaryTables.sh (new): To build two spreadsheet summarizing results from several CLARK report files. Given a rank r and a minimum abundance level a (i.e., the ratio between the number of reads classified to a taxon and the total number of reads in the report file) expressed in percent, this script produces the following report files:
	- "TableSummary_per_Report.csv":
	For each report file, this table indicates the number of reads, the number of assigned or classified reads, the alpha-diversity (using the Shannon-index) of the sample, the minimum abundance level 	used, the proportion of reads classified in percentage, and the r most dominant taxa/organisms with abundance higher than a (they are ordered by decreasing order of the abundance). The taxa are 	reported with scientific name and NCBI taxonomy id.
	- "TableSummary_per_Taxon.csv":
	For each taxon/organism identified across all the report files, this table indicates the taxonomy id of the taxon, the domain of the taxon, the minimum abundance level used, the number of reports 	the taxon was found (within the top r taxa with abundance higher than a), and some statistics about the abundance of the taxon (i.e., minimum, maximum, average and standard-deviation in percent).
	"TableSummary_HitCount.csv":
	This table provides the hit count distribution of the targets identified per report, as well as the total number of reads, the total number of reads classified and the alpha-diversity.

+ getTargetsKmers_distribution.sh: To print out the distribution of the target-specific k-mers in a file entitled "targets.distribution.csv" in the working database. The parameters for this script are the key parameters used for creating the database, i.e., the k-mer length and the minimum k-mers frequency (default 0).

+ extractSequences.sh (new) To extract/filter from the input data, the sequences identified to a specific taxon once the classification is done. This can be used for downstream analysis (analysis of contaminants, genome assembly, etc.).

**Commands**
Standard analysis with k-mer length 31 (default)

```

Create targets for microorganisms only analysis:
CLARKSCV1.2.6.1/set_targets.sh <TARGETS_DIR> bacteria viruses fungi --species
# We can change taxonomic level of the analysis by changing --species to, say, --genus, etc

```

```

Create targets full analysis:
set_targets.sh <TARGETS_DIR> custom human bacteria viruses fungi --species

```

After the target database is built we can classify metagenome.

```

Classify metagenome:
classify_metagenome.sh -P <R1.fastq.gz> <R2.fastq.gz> -R <result> -k 31 -m 1 --gzipped -n 4

```

The results files contain assigment of each individual reads to the target sequence like so:

Object_ID, Length, Assignment
K00243:168:H7LCKBBXY:5:1101:4604:1173,200,3483
K00243:168:H7LCKBBXY:5:1101:6289:1173,200,3483


```

Estimate abundances in parallel
parallel --eta -j 2 '~/programs/CLARKSCV1.2.6.1/estimate_abundance.sh -D <TARGETS_DB> -F {} -a 0 > {.}.abundance.csv' ::: *_result.csv


```










































