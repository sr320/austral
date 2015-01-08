#Crassostrea gigas RNA-Seq

##Tophat via iPlant

Goal: Use RNA-seq to compare expression between oysters (n=3) pre and post heat shock.
___

>Based on IPlant Collaborative Tutorial      
[<img src="http://eagle.fish.washington.edu/cnidarian/skitch/RNA-Seq_tutorial_-_Education__Outreach__and_Training_-_iPlant_Collaborative_Wiki_1A45D493.png" alt="RNA-Seq_tutorial_-_Education__Outreach__and_Training_-_iPlant_Collaborative_Wiki"/>](https://pods.iplantcollaborative.org/wiki/display/eot/RNA-Seq_tutorial)
<https://pods.iplantcollaborative.org/wiki/display/eot/RNA-Seq_tutorial>

___

####Task 1: Align read data to _Crassostrea gigas_ genome.
Tophat is a specialized alignment software for RNA-seq reads that is aware of splice junctions when aligning to a reference assembly.

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
Cufflinks assembles RNA-Seq alignments into a parsimonious set of transcripts, then estimates the relative abundances of these transcripts based on how many reads support each one, taking into account biases in library preparation protocols. A detailed manual can be found at http://cufflinks.cbcb.umd.edu/manual.html.

1) Open **Cufflinks2**

2) For **Input Data** add the six bam files from the `bam` subdirectory of the TopHat2 output.

3) Under **Reference Sequence** use custom option select `/austral-data/Crassostrea_gigas.GCA_000297895.1.24.dna_sm.toplevel.fa` 

4) For **Reference Annoations** add the GTF file `/austral-data/Crassostrea_gigas.GCA_000297895.1.24.gtf`

5) Click **Launch Analyses** and monitor the status of you job.

- Note this takes ~2 hours 

---

####Task 3: Merge all Cufflinks transcripts into a single transcriptome annotation file using **Cuffmerge2**
Cuffmerge merges together several Cufflinks assemblies. It handles also handles running Cuffcompare. The main purpose of this application is to make it easier to make an assembly GTF file suitable for use with Cuffdiff. A merged, empirical annotation file will be more accurate than using the standard reference annotation, as the expression of rare or novel genes and alternative splicing isoforms seen in this experiment will be better reflected in the empirical transcriptome assemblies. 

1) Open the **Cuffmerge2** app. Under 'Input Data', browse to the results of the cufflinks analyses (abovee) and add the 6 gtf files located in the `gtf` subdirectory.

2) For **Reference Annoations** add the GTF file `/austral-data/Crassostrea_gigas.GCA_000297895.1.24.gtf`

3) Under **Reference Sequence** use custom option select `/austral-data/Crassostrea_gigas.GCA_000297895.1.24.dna_sm.toplevel.fa` 

4) Click **Launch Analyses** and monitor the status of you job.


---
####Task 4: Compare expression analysis using CuffDiff2
Cuffdiff is a program that uses the Cufflinks transcript quantification engine to calculate gene and transcript expression levels in more than one condition and test them for significant differences. <http://cufflinks.cbcb.umd.edu/manual.html>

1) Open **Cuffdiff2**. For 'Input Data' Sample 1 Name enter Pre adn add three bam file from Tophat analysis..

<img src="http://eagle.fish.washington.edu/cnidarian/skitch/_39__Discovery_Environment_1A462B43.png" alt="_39__Discovery_Environment_1A462B43.png"/>

For Sample 2 enter post and add other three bam files ...

<img src="http://eagle.fish.washington.edu/cnidarian/skitch/_39__Discovery_Environment_1A462B91.png" alt="_39__Discovery_Environment_1A462B91.png"/>

2) Next, open the **Reference Annotations** section and add a custom reference annotation file using the `merged_with_ref_ids.gtf` file from the cuffmerge output folder. 

3) Click **Launch Analyses** and monitor the status of you job.

---



