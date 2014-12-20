#Using iPlant Discovery Environment for RNA-seq

Goal: Use RNA-seq to compare expression between oysters (n=3) pre and post heat shock.
___

>Based on IPlant Collaborative Tutorial 
[<img src="http://eagle.fish.washington.edu/cnidarian/skitch/RNA-Seq_tutorial_-_Education__Outreach__and_Training_-_iPlant_Collaborative_Wiki_1A45D493.png" alt="RNA-Seq_tutorial_-_Education__Outreach__and_Training_-_iPlant_Collaborative_Wiki"/>](https://pods.iplantcollaborative.org/wiki/display/eot/RNA-Seq_tutorial)

___

####Task 1: Align read data to _Crassostrea gigas_ genome.

1) Click Apps from DE workspace and select **TopHat2-SE**. Use search bar.

<img src="http://eagle.fish.washington.edu/cnidarian/skitch/_18__Discovery_Environment_1A446EF5.png" alt="_18__Discovery_Environment_1A446EF5.png"/>


2) Under 'Analysis Name' leave as defaults for make any changes.

3) Under **Input data** for FASTQ files add six fastq.gz files localed in `austral-data` with prefixes _2M, 2M-HS, 4M, 4M-HS, 6M, 6M-HS_. 

4) Under **Reference Genome** for 'Provide a reference genome file in FASTA format' select `/austral-data/Crassostrea_gigas.GCA_000297895.1.24.dna_sm.toplevel.fa` 

5) For **Reference Annoations** add the GTF file `/austral-data/Crassostrea_gigas.GCA_000297895.1.24.gtf`

6) Click **Launch Analyses** and monitor the status of you job.

7) Once complete....

- Note this takes ~10 hours 

---


####Task 2: Assemble transcripts using **Cufflinks2**

1) Open **Cufflinks2**

2) For **Input Data** add the six bam files from the `bam` subdirectory of the TopHat2 output.

3) Under **Reference Sequence** use custom option select `/austral-data/Crassostrea_gigas.GCA_000297895.1.24.dna_sm.toplevel.fa` 

4) For **Reference Annoations** add the GTF file `/austral-data/Crassostrea_gigas.GCA_000297895.1.24.gtf`

5) Click **Launch Analyses** and monitor the status of you job.

---

####Task 3: Merge all Cufflinks transcripts into a single transcriptome annotation file using Cuffmerge

