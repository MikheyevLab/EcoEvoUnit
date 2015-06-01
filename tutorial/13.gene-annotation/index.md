---
title: The basics of gene annotation
author: martin_helmkampf
layout: page 
---
{% include _toc.html %}

After obtaining a genome assembly of sufficient quality, the next step in a genome project is assigning biological information to the raw sequence data. This process is called genome annotation, and includes, but is not limited to, the annotation of protein-coding genes (genomes contain many elements that are not genes, like non-coding, repetitive sequence). Annotation involves identifying the location, structure and function of a gene. Accomplishing this on a genome-wide basis is a complex endeavor that may include both automatic and manual steps. In most cases, manual annotation is performed to improve a previously obtained automatic annotation.

&nbsp;

#### Automatic gene annotation

Automatic annotation relies on a variety of software tools and different data sources to create gene annotations. Typically, these tools are combined into programs referred to as pipelines. The process consists of two main phases, the computation phase and the synthesis phase.

The **computation phase** itself can be broken down into the following steps: 

  * Repeat identification
  * Transcript evidence alignment
  * Protein evidence alignment
  * *Ab initio* gene prediction 

Most genomes of more complex organisms harbor an abundance of repetitive sequence which need to be excluded from subsequent steps. These repeats range from simple cases consisting of a dozen to several hundred repeats of the same 2–6 nucleotide long motif (like TATATATATATATATATATATATATATATATA) to transposable elements, mobile genes or gene fragments of viral origin cluttering their host genomes. Repetitive sequence may comprise up to well over half the total sequence of a genome, and can lead to spurious annotation results if left unchecked. Identifying and excluding (often referred to as &#8220;masking&#8221;) repeats is therefore the first step during automatic gene annotation and performed by specialized tools like RepeatMasker.

After repeat-masking, the next two steps involve [aligning][1] external evidence for genes to the genome assembly. Transcript evidence is usually obtained from [RNA-Seq or EST data][2] of the same organism, and presents the most direct and trustworthy evidence for the location and structure of a gene. In addition, it gives information about whether the gene is transcriptionally active (and thus most likely functional, that is, producing a functional protein) and whether [alternative transcripts][3] exist. Transcript evidence is also the only reliable source of information for the extent of UTRs, untranslated sequence that lead and trail the coding sequence of an mRNA. Sometimes, transcript data of related organisms are used as well, but may not align perfectly to the genome. Nonetheless, a comprehensive database of well-assembled transcript data is crucial for successful gene annotation. Tools like Exonerate specialize in the alignment of transcript data by taking boundaries between introns and exons (splice sites) into account.

Protein alignment follows the same principle, but aligns proteins from a set of closely related organisms to the genome assembly. Because the structure of orthologous genes is often conserved between related organisms, this step can be highly informative concerning gene structure in the study genome. A frequently used source of protein information other than from closely related organisms is [SwissProt/UniProt][4], a database of high-quality, manually curated protein data. Protein evidence alignment is usually performed by [BLAST][5].

As opposed to evidence-based methods, *ab initio* gene prediction (from Latin, &#8220;from the beginning&#8221;) attempts to identify genes using mathematical models. Scanning for open reading frames (ORF, stretches of sequence lacking stop codons and thus potentially coding for a protein) and relying on organisms-specific parameters like codon frequencies and typical intron-exon-structures, gene prediction algorithms are usually limited to finding coding sequence (CDS) and do not account for untranslated regions (UTRs). This approach also tends to lack in accuracy, although some tools like SNAP, Augustus or GeneMark can be trained to adjust their search parameters to organism-specific traits, thus improving accuracy.

&nbsp;

During the following **synthesis phase**, algorithms combine the results of the computation phase into a consensus set of gene models. This process involves running several gene predictors, and then choosing for each gene the prediction that is best in line with the available external evidence. Popular pipelines include [MAKER][6] and GLEAN. The consensus set along with the underlying evidence may be visualized using a [genome browser][7] and serve as a starting point for manual annotation.

&nbsp;

#### Manual gene annotation

Quality control of automatically derived gene annotations and in-depth analyses of genes of interest often requires manual gene annotation, which is the focus of this tutorial.

The first step in reviewing and editing a gene of interest is identifying its **location** in the genome. This can  be accomplished by using [BLAST][8] and a reference gene – usually a curated ortholog from a related organism – as a query, either against the genome assembly, or a set of consensus gene models produced by an automatic gene annotation pipeline.

The genomic region harboring the gene of interest can then be inspected using a genome browser and editor like WebApollo, and the **structure** of the gene can be reviewed, including the [following features][9]: 

  * <span style="line-height: 13px;">Coding sequence (CDS)</span>
  * Intron-exon boundaries (splice sites)
  * Untranslated regions (UTR)
  * Alternative transcripts

 The first two features are related, because the open reading frame (ORF) defining the encoded protein is often split across several exons. Intron-exon boundaries may break up codons and thus result in a change of the reading frame between exons. Most introns begin and end with the nucleotides &#8220;GT &#8230; AG&#8221;, the so called canonical splice sites, but sometimes non-canonical splice sites are observed as well. The correct splice sites, reading frames and related features like the position of the start and stop codon can be double-checked by aligning the resulting protein sequence to the reference gene. Though genes may differ substantially at the 3&#8242; and 5&#8242; ends, generally this approach can point to missing parts that may be corrected by adjusting the extent of the CDS or the intron-exon boundaries.

The typical number and length of exons and introns per gene differs from organism to organism. On average, genes in most more complex organisms possess 3 to 8 exons ranging in length from a few dozen to a few thousand nucleotides, with a few hundred being typical (there is an inverse relationship between exon number and length). Introns tend to be shorter on average, but have a wider range between a dozen to many thousand nucleotides. The largest gene known in the human genome, *titin*, contains over 360 exons and encodes a protein with over 30000 amino acids.

The last two features can only be informed by transcript evidence. The extent of the UTRs should thus match, and never exceed, the available evidence. 5&#8242; UTRs are typically spread across the first two exons, with the first being exclusively UTR and the second split between UTR and CDS. 3&#8242; UTRs are always found in the last exon, which harbors the end of the CDS followed by UTR. Exons missing in some transcript but not others might call for the annotation of alternative transcripts.

Once a gene&#8217;s structure and thus coding sequence has been established, its **identity** can be verified as well. This includes reviewing its homology relations to putatively orthologous genes like the reference gene, and similar genes in the same genome (potential gene duplicates or paralogs). [Homology assessment][10] is the subject of a following chapter.

Finally, assigning a **function** to a gene is part of gene annotation as well, but beyond what can be done with the tools discussed above. We will discuss this topic in a following chapter as well.

&nbsp;

Using a well-adjusted automatic gene annotation pipeline as a starting point greatly facilitates manual gene annotation, but it remains a time-consuming process. However, recent efforts to build a system allowing multiple researchers to collaborate on reviewing and editing annotations in a distributed manner have proven quite successful. Such a system revolves around a central database housing the results of an automatic annotation pipeline and made accessible through a genome browser and editor like WebApollo. Changes made are directly written back to the database, ensuring that updates are secure and available to all community members. By using WebApollo and real, newly sequenced genome data, this tutorial emulates this approach.

&nbsp;

Further reading: [A beginner&#8217;s guide to eukaryontic gene annotation][11]

&nbsp;

Next chapter: [Our study organisms: Ants][12]

&nbsp;

 [1]: ../23.align_sequences
 [2]: ../12.genome-sequencing#Transcriptome sequencing
 [3]: ../11.introduction-to-genetics#Alternative transcripts
 [4]: www.uniprot.org
 [5]: ../22.blast
 [6]: http://www.yandell-lab.org/software/maker.html
 [7]: ../21.gbrowse
 [8]: ../22.blast
 [9]: ../11.introduction-to-genetics/#Gene structure
 [10]: ../41.homology-assessment
 [11]: ../../wp-content/uploads/2013/08/Yandell_2012.pdf
 [12]: ../14.ants
