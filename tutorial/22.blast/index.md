---
title: BLAST
author: martin_helmkampf
layout: page 
---
{% include _toc.html %}

One of the most important tools in bioinformatics is **BLAST**, or Basic Local Alignment Search Tool. It is used to find and compare nucleotide or amino acid sequences, and assess their similarity. Sequences that are very similar to each other are assumed to be homologous. We will talk about the concept of homology later, but in short, homology means similarity due to common evolutionary descent. In terms of genes, common descent can apply to two genes in two different organisms, in which case both genes have evolved from a single gene present in the last common ancestor of the species (orthology). Alternatively, it can apply to two genes in the same organism, which arose from a duplication of a single ancestral gene (paralogy).

When annotating genes, it is essential to be able to identify homologous genes. For example, after identifying an unknown gene, comparing it to homologous genes from a well-studied model organism might give you a first clue about its function. On the flip side, the first step in annotating a gene is often finding it first with the help of a homologous gene from another organism. Similarly, when studying a gene family, a group of homologous (paralogous) and often functionally similar genes, finding all members of that group is key. In all of these cases, BLAST is the right tool for the job.

BLAST works by [aligning][1] segments of a query sequence (the sequence to search for) to one or many sequences to search against, identifying regions of high sequence similarity using a scoring matrix. The details of the algorithm can be found [here][2]. BLAST is implemented in many, if not all, genome project websites, including [FlyBase][3], [WormBase][4] and the [Ant Portal][5] of the Hymenoptera Genome Database. As previously, we will use the latter to demonstrate how to locate the Cytoplasmic Ribosomal Protein RpL30 gene in the Red harvester ant:

&nbsp;

<a href="../../wp-content/uploads/2013/08/BLAST_I.png" class="grouped_elements" rel="tc-fancybox-group255"><img class="alignleft size-full wp-image-259" alt="BLAST_I" src="../../wp-content/uploads/2013/08/BLAST_I.png" width="516" height="669" /></a>

#### BLAST Usage

<span style="color: #ff0000;">(1)</span> The two most important choices regarding BLAST concern the program and the database used. &#8220;Program&#8221; specifies one of five basic types of BLAST, depending on the nature of the query and target sequences: 

<p style="font-family: courier; font-size: 13px;">
  blastn — use a nucleotide query to search a nucleotide database
</p>

<p style="font-family: courier; font-size: 13px;">
  blastp — use a protein query to search a protein database
</p>

<p style="font-family: courier; font-size: 13px;">
  blastx — use a translated nucleotide query to search a protein database
</p>

<p style="font-family: courier; font-size: 13px;">
  tblastn — use a protein query to search a translated nucleotide database
</p>

<p style="font-family: courier; font-size: 13px;">
  tblastx — use a translated nucleotide query to search a translated nucleotide database
</p> Translated means that sequences are translated into all six reading frames before being compared to each other. In this case, we have chosen the protein (amino acid) sequence of our target gene RpL30 from the fruit fly 

*Drosophila melanogaster* as the query sequence. We want to see whether this gene has already been annotated in the Red harvester ant *Pogonomyrmex barbatus* and is therefore found among the Official Gene Set (OGS), a collection of automatically annotated and manually curated protein sequences representing all protein-coding genes. With both our query and target sequences in protein format, we need to select &#8220;blastp&#8221; as program from the pull-down menu.

The &#8220;Database&#8221; menu offers both genome assemblies and gene sets from several ant species. &#8220;Pbar*OGSv1.2*proteins&#8221; represents the most current OGS version of *Pogonomyrmex barbatus*.

<span style="color: #ff0000;">(2)</span>. Paste the query sequence in Fasta format into this field. The complete set of *Drosophila melanogaster* Cytoplasmic Ribosomal Protein (CRP) genes is available [here][6].

<span style="color: #ff0000;">(3)</span>. By default, BLAST does not consider highly repetitive (low complexity) regions. However, some some coding sequences may contain repetitive sequence (e.g., see Dmel_RpLP1), in which case it might be beneficial to deactivate the low complexity filter.

<span style="color: #ff0000;">(4)</span>. Click &#8220;Search&#8221; to run BLAST.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

<a href="../../wp-content/uploads/2013/08/BLAST_results_II.png" class="grouped_elements" rel="tc-fancybox-group255"><img class="alignright size-full wp-image-443" alt="BLAST_results_II" src="../../wp-content/uploads/2013/08/BLAST_results_II.png" width="669" height="746" /></a>

#### Results

<span style="color: #ff0000;">(1)</span>. The first section of the results page shows a graphical representation of the length and similarity of the sequences found by BLAST, the so-called **hits**. In our case, we have found seven hits, but only one that covers the full length of the query (the thick black bar). It is highlighted in purple, indicating high overall similarity to the query as measured by the alignment **score**. All other hits are fragmentary and of low similarity, most likely representing spurious results.

<span style="color: #ff0000;">(2)</span>. The second section lists all hits with their sequence identifiers, scores and **e-values**. The e-value is the probability that the similarity between query and target sequence is due to chance rather than homology, taking the size of the database into account (a large database is more likely to produce a chance hit). Values well below zero are usually interpreted as indicating true homology. Here, this applies only for the first hit with an e-value of 10<sup>-49</sup>.

<span style="color: #ff0000;">(3)</span>. The following section gives more detailed information about individual hits, in descending order of their score. Details include the proportions of identical (&#8220;Identities&#8221;) and chemically similar (&#8220;Positives&#8221;) positions between query and target, as well as an alignment between the two sequences. The high number of matching positions indicates that they must have evolved from a common ancestor and are therefore homologous. In contrast, the weak similarity between the query and the next best hit <span style="color: #ff0000;">(4)</span>, as shown by the positive e-value and incomplete alignment, is probably a result of chance.

The result of this BLAST analysis is therefore that the Official Gene Set of *P. barbatus* contains one gene, PB2287, which is [homologous][7] to RpL30 in *D. melanogaster*. To acquire the full protein sequence of this gene, click on any of the highlighted gene identifiers.


#### Tips and further resources

— Regions of low similarity can break up BLAST hits, which are then displayed separately as sub-hits even though they are part of the same contiguous sequence. This is especially true when blasting a protein-coding gene against genomic sequence. Interrupted by [introns][8], each exon will typically be represented by its own sub-hit. For example, try to blast our target gene above against the *P. barbatus* genome assembly (&#8220;Pbar*1.0*scaffolds.fa&#8221;) using tblastn. When comparing the sequence coordinates in the alignment of the best hit, you will notice that there is a gap of over 600 nucleotides in the genomic target sequence separating the two exons (see below).

— Some websites link their BLAST results to a genome browser. For example, you can examine the genomic context of our target gene by clicking on &#8220;See complete hit in GBrowse&#8221; (see below). Alternatively, you could search for the gene identifier PB22887 in GBrowse or use the scaffold identifier and coordinates as shown by BLAST. Mind that some genes are found on the antisense strand (watch out for a negative &#8220;Frame&#8221;), so you have to read the coordinates backwards.

&nbsp;

<a href="../../wp-content/uploads/2013/08/BLAST_intron.png" class="grouped_elements" rel="tc-fancybox-group255"><img class="margin-left size-full wp-image-341" alt="BLAST_intron" src="../../wp-content/uploads/2013/08/BLAST_intron.png" width="635" height="325" /></a>

&nbsp;

— Protein or translated nucleotide sequences usually give more robust results and should be used when possible. With only four character states compared to 20, nucleotide sequences have a higher chance to be similar due to chance and provide less resolution.

— The [NCBI BLAST][9] website allows blasting against most of NCBI&#8217;s databases, including GenBank, a comprehensive collection of sequence data from thousands of organisms. This can be used to identify unknown sequences, sometimes even to the source organism.

— BLAST is also available as a command-line operated application ([BLAST+][10]), and plug-in for BioPerl and Biopython. As such, it can be run and parsed as part of a scripted pipeline to handle larger data volumes. The official BLAST+ user manual is available [here][11], and a quick guide to the most common commands [here][12].

&nbsp;

Next chapter: [Aligning sequences][1]

&nbsp;

 [1]: ../23.align_sequences
 [2]: http://en.wikipedia.org/wiki/BLAST#Algorithm
 [3]: http://flybase.org/blast/
 [4]: http://www.wormbase.org/tools/blast_blat
 [5]: http://hymenopteragenome.org/ant_genomes/?q=blast
 [6]: ../../wp-content/uploads/2013/08/Dmel_CRPs.fas
 [7]: ../41.homology-assessment
 [8]: ../11.introduction-to-genetics#Gene structure
 [9]: http://blast.ncbi.nlm.nih.gov/Blast.cgi
 [10]: http://blast.ncbi.nlm.nih.gov/Blast.cgi?CMD=Web&PAGE_TYPE=BlastDocs&DOC_TYPE=Download
 [11]: ../../wp-content/uploads/2013/08/BLAST+_Manual.pdf
 [12]: ../../wp-content/uploads/2013/08/BLAST+_Usage.rtf
