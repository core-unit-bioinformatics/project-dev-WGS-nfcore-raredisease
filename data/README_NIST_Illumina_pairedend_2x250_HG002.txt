This README describes the library preparation and sequencing performed at NIST for the AJ Trio for the 2x250bp overlapping libraries with nominally 350bp insert size, designed for DISCOVAR assembly.  This folder contains the data for HG002, the AJ son, only.  The folder â€œreadsâ€ contains fastq files from one flow cell, containing ~40-50x coverage.  

Library Preparation:
For each Reference Material, 1 library was prepared using the Illumina TruSeq (LT) DNA PCR-Free Sample Prep Kits (FC-121-3001). 

DNA concentrations were measured using a Qubit 2.0 fluorometer (Life Technologies). Genomic DNA (1.5 ug) was fragmented using a Covaris S2 focused ultrasonicator in micro TUBE AFA Fiber Pre-Slit Snap-Cap 6x16mm micro tubes and the Covaris MicroTUBE holder (covaris part numbers 520045 and 500114, respectively) under the following conditions for a target insert size of 350 base pairs. Size selection was done using a 96-well 0.8 mL plate (Fisher Scientific Part # AB-0859), a magnetic stand-96 (Ambion part # AM10027) and the Illumina sample purification beads according to the 350 bp insert protocol.

Adenylation of 3â€™ ends was done in 0.2 mL PCR tubes on an MJ Research PTC-200 thermal cycler. The optional A-Tailing control was not used.  Ligation of indexed paired-end adapters was done in 0.2 mL PCR tubes using the DNA adapter tubes included in the Illumina TruSeq (LT) DNA PCR-Free Sample Prep Kit on an MJ Research PTC-200 thermal cycler. The optional ligation control was not used. The libraries were cleaned up in a 96-well 0.8 mL plate (Fisher Scientific Part # AB-0859) and a magnetic stand-96 (Ambion part # AM10027) using the Illumina sample purification beads. The final libraries were run on an Agilent 2100 Bioanalyzer HS-DNA chip to verify fragment size distribution. Final library concentration was measured via qPCR using the KAPA library quantification kit for Illumina sequencing platforms (KAPA part # KK4835). 

Sequencing:

The TruSeq libraries were run on an Illumina HiSeq 2500 in Rapid mode (v2) with 2x250 paired end reads. Pooled Libraries were initially loaded at a concentration of 10 pM. loading concentration was adjusted accordingly on subsequent runs to balance the libraries as well as possible. 
