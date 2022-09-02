# SG10K Health

the National Precision Medicine (NPM) program represents a whole-of-government ten-year strategy to establish precision medicine as a peak of research excellence for Singapore. Phase I (2017-2021) was a "proof-of-concept" phase demonstrating the feasibility of large-scale genomic data generation with linkage to electronic health data. A headline deliverable of NPM Phase I was generating a genomic reference database of 10,000 healthy Singaporeans (SG10K_Health).

## Data production

* Whole Genome Sequencing of 10,323 healthy Singaporean was performed.
* Single-sample gVCF files were obtained following GATK4 "germline short variant per-sample calling" reference implementation defined parameters and companion files (GATK resource bundle GRCh38).
* msVCF files were obtained by performing a joint-calling step.

## Sample QC & annotation

* Variants failing VQSR filter were removed
* Sex was imputed based on the mean depth ratio of chrX/chr20  and chrY/chr20 of each sample, and samples with abnormal ploidy were excluded.
* Samples with call rate < 95%, contamination rate > 2%, and error rate > 1.5% were excluded.
* Median Average Deviation (MAD) was computed on autosome only for ratio insertion/deletion, ratio transition/transversion, and ratio heterozygote/homozygote alternative. Samples with a deviation of more than 6xMAD were excluded
* Genotypes on chr X and Y were corrected according to the imputed sex. 
* Genotype with allele balance (AB) > 0.8 or AB < 0.2, read depth (DP) < 5 or genotype quality < 20 were excluded.
* Remaining variants were annotated using VEP95 in merged mode (Gencode + Refseq reference).

> Access to SG10K_Health genomic data on request to the NPM Data Access Committee (DAC) via (contact_npco@gis.a-star.edu.sg).
>
> Data available:
>
> * sites-only VCFs
> * multi-sample VCFs
> * hail matrix tables

## Analysis

Analysis is performed via a collection of Jupyter notebook with Hail library and access to SG10K_Health hail matrix tables.

* **SG10K_Health-Statistics** explore current release and compute relevant statistics.

---
