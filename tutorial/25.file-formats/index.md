---
title: File formats
author: martin_helmkampf
layout: page 
---
{% include _toc.html %}

Bioinformatics uses many different file formats to store and manipulate genetic sequence information. Most are plain text files, meaning they consist of basic, unformatted text as for instance prepared by a text editor. Some of the most commonly encountered formats are:

&nbsp;

#### FASTA <a id="FASTA"></a>

Fasta files have become a standard to store nucleotide and protein sequences, and may contain a single or multiple sequences or entries. Each entry consists of a single-line description, followed by one or multiple lines of sequence data. The description line is preceded by a greater sign (&#8220;>&#8221;) and includes a sequence identifier (the first word) and an optional description. The following lines, up to the next &#8220;>&#8221;, harbor the sequence data. [BLAST][1] and many programs to [calculate alignments][2] or phylogenetic trees accept Fasta files (by including gap symbols, &#8220;–&#8221;, they may also be used to store alignments). There is no standard file extension, though &#8220;.fas&#8221; is commonly used.

&nbsp; 

<pre>&gt;PB11175 | Pogonomyrmex barbatus RpL4 (amino acid sequence)
MSLSTARPLITVYTDKNEASGDVISLPSVFKAPIRPDIVNVVHQLISTNRRQPYCVSKEAGHQTSAESWGTGRAVARIPRVRGGGTHRSGQGAFGNMCRG
GRMFAPTKSWRRWHHRVNVNQKRYALVSAIAASGVPALVQSKGHLIQEVPEFPLVVSNKIQEYTKTKQAVIFLRRIKAWNDIQKVYKSQRFRAGKGKMRN
RRRIQRRGPLIVYGHDQGIRKAFRNIPGVSLMNINKMNLLKLAPGGHVGRFVIWTKSAFEQLDALYGTWRKESQLKKGYNLPFPKMANTDLSRLLKSEEI
RKVLRAPRKKVVRRVKKLNPLTNTRAMLRLNPYAAVLKRAAVLTAQKRQREKDVLLAEKRGVKLPKKTSKAIGLLARRKEQLTKYKKTTKKTMVQTKAEK
DTGKTASKQQAKK</pre> &nbsp;

#### GFF <a id="GFF"></a>

GFF or Generic Feature Format files are commonly used to store genome annotation data. The current version is GFF3. GFF files are plain text files consisting of nine tab-delimited columns, specifying positional information of genomic features, often in a nested manner. For instance, the following GFF file represents the *P. barbatus* gene RpL9 with its various annotated sub-features:

&nbsp; 

<pre>##gff-version 3
pbar<em>scf7180000350383   .   gene    1850263 1851998 .   +   .   ID=PB25915;Name=pbar</em>RpL9
pbar<em>scf7180000350383   .   mRNA    1850263 1851998 .   +   .   ID=PB25915-mRNA-1;Name=pbar</em>RpL9-1;Parent=PB25915
pbar<em>scf7180000350383   .   exon    1850263 1850290 .   +   .   Parent=PB25915-mRNA-1
pbar</em>scf7180000350383   .   exon    1851069 1851207 .   +   .   Parent=PB25915-mRNA-1
pbar<em>scf7180000350383   .   exon    1851416 1851743 .   +   .   Parent=PB25915-mRNA-1
pbar</em>scf7180000350383   .   exon    1851814 1851998 .   +   .   Parent=PB25915-mRNA-1
pbar<em>scf7180000350383   .   CDS     1851070 1851207 .   +   .   Parent=PB25915-mRNA-1
pbar</em>scf7180000350383   .   CDS     1851416 1851743 .   +   .   Parent=PB25915-mRNA-1
pbar_scf7180000350383   .   CDS     1851814 1851920 .   +   .   Parent=PB25915-mRNA-1</pre> &nbsp;

The type of each feature is given in column 3, followed by its start (column 4) and end (column 5) coordinates, and the strand it is found on (column 7). Coordinates and strandedness refer to the sequence or landmark found in column 1. The ID and parent attributes in column 9 establish the nested structure of this set of features: the top-level feature, the gene, contains a single mRNA, which in turn consists of four exons, part of which are coding sequence (CDS; the non-overlapping part is by definition untranslated region, UTR). The remaining columns house optional information, with &#8220;.&#8221; standing for unknown or not-applicable. Details about these columns as well as additional attributes in column 9 can be found [here][3].

The output of many different sources can be represented in GFF. These sources include gene predictors, programs to identify repetitive sequence (e.g. RepeatMasker), programs to refine splice sites (e.g. Exonerate), or [BLAST][1] results. Combined into a database, a genome browser like [GBrowse][4] or Apollo may be used to display them, with tracks containing individual sources. Conversely, when using an annotation editor to create manual or modify existing annotations, the data is frequently saved back in GFF.

&nbsp;

#### Clustal <a id="Clustal"></a>

Clustal is a file format for aligned nucleotide or proteins sequences, which is easily readable by humans (as opposed to, for instance, Fasta). Notably, homologous position are arranged in columns, and special characters (* : .) are used to indicate similarity for quick reference. The following example, introduced in the section on [aligning sequences][2], is in Clustal format:

&nbsp;

<a href="../../wp-content/uploads/2013/08/Clustal.png" class="grouped_elements" rel="tc-fancybox-group451"><img class="margin-left size-full wp-image-648" alt="Clustal" src="../../wp-content/uploads/2013/08/Clustal.png" width="621" height="198" /></a>

&nbsp;

Further details about this format can be found [here][5].

&nbsp;

#### BAM <a id="BAM"></a>

&nbsp;

Next chapter: [Getting started with training genes][6]

&nbsp;

 [1]: ../22.blast
 [2]: ../23.align_sequences
 [3]: http://gmod.org/wiki/GFF
 [4]: http://ecoevo.unit.oist.jp/lab/21.gbrowse
 [5]: http://meme.nbcr.net/meme/doc/clustalw-format.html
 [6]: ../31.getting-started
