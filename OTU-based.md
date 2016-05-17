OTU-based analysis 
=====================================
Jenni Hultman

### Summary

In the previous session you quality filtered your data, made contigs, created OTUs and assigned taxonomy. Now we will continue with the OTUs to figure out what does the data mean. 


## Biom table for R 

You will need to create a biom-formatted file for analysis in R-studio


```
make.biom(shared=sample.shared, constaxonomy=sample.constaxonomy)
```
## Did sequencing produce more reads for some samples?
```
mothur > count.groups(shared=stability.an.shared)
```
## Phylogenetic three for betadiversity analysis

```
mothur > dist.seqs(fasta=sample.fasta, output=lt, processors=8)
mothur > clearcut(phylip=sample.phylip.dist)

```
##Alpha diversity (more in R)
These can be created in mothur or in R. For some indices you need to rarify your data. Subsampling is one of the approaches. If you subsample, check from count.groups output what is lowest number of sequence reads in your dataset. Do the calculations with subsampling and without. What do you see?

Applying the richess and diversity estimators to microbiome data is much discussed. Before using and publishing make sure you know what you are doing!

    mothur > summary.single(shared=sample.shared, calc=nseqs-coverage-sobs-invsimpson)
```
mothur > summary.single(shared=sample.shared, calc=nseqs-coverage-sobs-invsimpson, subsample=xxxx)
```


##Venn diagrams can be a good way to visualize the data. A-B-C-D refer to your samples names (the textfile with fastq-read names). 
```
mothur > venn(shared=stability.subsample.shared, groups=A-B-C-D)
```
