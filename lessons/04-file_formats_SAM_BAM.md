---
layout: lesson
root: .
title: File Format: SAM - BAM
minutes: 5
---

## Status & ToDo : Under Development
    
## Learning Objectives 

* Describe the features of a SAM alignment file format
* Explain the difference between SAM and BAM
* Use samtools to read, convert and subset files

## Lesson

### Example data set

An example dataset is available on [figshare](http://figshare.com/articles/Example_SAM_file/1460716).

This is a subset of the reads aligning to the first 100kb of the chromosome 1 of from sample Col0_C1 of [this experiment](http://www.ebi.ac.uk/arrayexpress/experiments/E-MTAB-3279).

### Purpose of SAM/BAM

The standard format for alignment of reads to a reference genome is Sequence Alignment/Map (SAM). This is a text file with for each aligned read a line (record) containing all information where and how it aligns to the reference. BAM is the binary, compressed version of SAM, which is more efficiently machine-readable and takes 3 to 4 times less space.

### Handling alignment files

[Samtools]() is used to handle SAM files. 

Download an example SAM file from [figshare](http://figshare.com/articles/Example_SAM_file/1460716).

``` 
wget http://figshare.com/articles/Example_SAM_file/1460716
```

### Sequence Alignment/Map Format

A SAM alignment file is a tab-delimited text file consisting of a header section and the body containing the actual alignments. Here we will only touch upon the most important features of the SAM format, for full details see the [SAM specification](https://samtools.github.io/hts-specs/SAMv1.pdf).

#### Header

Each header line starts with '@' and contains information on the data in the file. 
@SQ is the most common header annotation containing information on the reference SeQuence. For each chromosome (or contig) a separate line containing the name (SN) and length (SL).

```
samtools view -H inputFile
```

    @SQ	SN:1	LN:30427671
    @SQ	SN:2	LN:19698289
    @SQ	SN:3	LN:23459830
    @SQ	SN:4	LN:18585056
    @SQ	SN:5	LN:26975502
    @SQ	SN:M	LN:366924
    @SQ	SN:C	LN:154478


## Reading SAM or BAM files

```
samtools view inputFile
samtools view -h inputFile
```

## Converting SAM and BAM files

SAM to BAM

```
samtools view -b -o outputFile.bam inputFile.sam 
```

BAM to SAM

```
samtools view -o outputFile.sam inputFile.bam 
```


## Indexing BAM files

## Subsetting BAM files

