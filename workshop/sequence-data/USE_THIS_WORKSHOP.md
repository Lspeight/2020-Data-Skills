---
title: Workshop in markdown
author: Bin He, Leslie Speight
date: 2020-03-24
---

Working with Sequence Data Tuesday Workshop 
===========================================
Leslie Speight and Anna Ward

## Get data
Go to fastx or your laptop home directory (or wherever you prefer to store 
the workshop data, and clone the following repository

```bash
$ cd <path/to/workshop> # replace the second part with your directory name
$ git clone https://github.com/hezhaobin/2020-Data-Skills.git
$ cd 2020-Data-Skills/workshop/seqeunce-data/ # hint: Tab don’t type!
$ ls
```
    
Next open Rstudio and install required packages

```r
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install('qrqc')
# This is a Bioconductor package and helps us to visualize quality distribution across bases in reads
# Now you can minimize the RStudio window and get back to the terminal

```
## Trimming low-quality bases with sickle and seqtk
now, go back to your terminal and check to makre sure that you are in the 'sequence-data'folder. Use 'ls; to see is the untreated1_chr4.fq is in the folder
```bash 
# TAB, DONT TYPE
$ ./sickle se -f untreated1_chr4.fq -t sanger -o untreated1_chr4_sickle.fq
# Note you must have the “./” before “sickle” to make this work
# you should see the following output
Total FastQ records: 204355
FastQ records kept: 203121
FastQ records discarded: 1234
# sickle takes an input file through -f, a quality type through -t, and trimmed output with -o

# trimming low quality bases with seqtk
$ ./seqtk trimfq untreated1_chr4.fq > untreated1_chr4.trimfq.fq
# this takes a single argument and outputs trimmed sequence through standard out

```
