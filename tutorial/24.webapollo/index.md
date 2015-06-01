---
title: WebApollo
author: martin_helmkampf
layout: page 
---
{% include _toc.html %}

**WebApollo** is a browser-based genome annotation viewer and editor. It features a graphical interface to browse and modify existing annotations, create new annotations, and document any changes made. It allows a community of researchers to work simultaneously on the same genome annotation project and is the most important gene annotation tool we will use in this tutorial.

&nbsp;

#### The general process of manual annotation

  1. Locate a gene or region of interest (e.g. using [BLAST][1] and/or a [genome browser][2])
  2. Create a starting gene model from [existing evidence][3] (e.g. a transcript or *ab initio* gene prediction)
  3. Check your gene model for consistency with other existing evidence
  4. Edit the gene model if necessary
  5. Export the sequence and [align][4] it to homologs to test for completeness
  6. Add comments about the changes made, [homology relations][5], etc.
  7. Save a local copy of the finished gene model and update your records

&nbsp;

#### Getting started with WebApollo

To begin, [log in][6] to our lab&#8217;s WebApollo environment using the user name and password sent to you by email.

&nbsp;

[<img class="marginleft size-full wp-image-936" alt="WA_Login" src="http://ecoevo.unit.oist.jp/lab/wp-content/uploads/2013/08/WA_Login.png" class="grouped_elements" rel="tc-fancybox-group407" width="295" height="152" />][6]

&nbsp;

This will bring you to the sequence selection screen below, where all the available reference sequences (usually [scaffolds][7]) are listed. There are two ways to access a gene to annotate in WebApollo. You can either search for it directly by clicking on &#8220;Tools | Search sequence&#8221;, which will allow you to conduct a BLAT search (an algorithm similar to BLAST) from within WebApollo using the protein sequence of your reference gene. Alternatively, the &#8220;Filter&#8221; text box <span style="color: #ff0000;">(2)</span> may be used to narrow down the list of displayed scaffolds to the one containing the gene of interest. The latter method requires you to determine the scaffold and coordinates beforehand, for example using BLAST.

<a href="../../wp-content/uploads/2013/08/WA_SeqSelection_I.png" class="grouped_elements" rel="tc-fancybox-group407"><img class="alignleft size-full wp-image-933" alt="WA_SeqSelection_I" src="../../wp-content/uploads/2013/08/WA_SeqSelection_I.png" width="1179" height="379" /></a>

&nbsp;

#### The main display

Selecting a sequence will bring up WebApollo&#8217;s main window, which is similar to the genome browser [JBrowse][8] and consists of several elements: the menu bar (more on which later), the navigation panel <span style="color: #ff0000;">(1)</span>, the user annotation panel <span style="color: #ff0000;">(2)</span>, the evidence panel <span style="color: #ff0000;">(3)</span> and a sidebar listing available evidence tracks <span style="color: #ff0000;">(4)</span>.

The navigation panel<span style="color: #ff0000;"> (1)</span> running along the top contains a text box showing the coordinates of the genomic region being displayed, in the now familiar format &#8220;scaffold identifier:start position..end position&#8221;. Changing these coordinates will adjust the displayed section accordingly, as will the zoom and scroll controls to the left. Clicking and dragging the mouse in the evidence panel will also scroll the display. The red box on top of the navigation panel indicates the position of the displayed section relative to the total scaffold.

The yellow user annotation panel <span style="color: #ff0000;">(2)</span> contains a user-created gene model and is where the manual annotation takes place. It is initially empty until activated by the user, as discussed below.

The evidence panel <span style="color: #ff0000;">(3)</span> makes up the largest part of the window, and contains all the evidence that can inform the manual annotation process. Evidence is split into tracks, with each track representing a separate source of data, including the results of automatic annotation pipelines, *ab initio* gene predictors, alignments of homologous proteins from related species, transcript data etc. (see the chapter on the [basics of gene annotation][9] to review these types of data). Active tracks are indicated by a symbol on the left of the evidence panel, and can be used to reorder tracks by dragging and dropping, and removing tracks by deleting them.

Tracks that are currently not being displayed are listed in the sidebar <span style="color: #ff0000;">(4)</span>. Dragging and dropping tracks from the sidebar into the evidence panel will display their contents.

&nbsp;

<a href="../../wp-content/uploads/2013/08/WA_MainWindow_RpL4.png" class="grouped_elements" rel="tc-fancybox-group407"><img class="marginleft size-full wp-image-941" alt="WA_MainWindow_RpL4" src="../../wp-content/uploads/2013/08/WA_MainWindow_RpL4.png" width="1035" height="615" /></a>

&nbsp;

Other options include  buttons in the top left to initiate a new sequence search (&#8220;Tools&#8221;) and the top right (not shown in the figure above) to show only the plus or minus strand (&#8220;Options&#8221;), create a link to the currently displayed annotation (&#8220;Share&#8221;; for example to share via email), and log out at the end of a session (your user name).

&nbsp;

#### Annotating a gene

In the following, we will demonstrate the use of WebApollo with the annotation of [Cytoplasmic Ribosomal Protein][10] gene RpL3 in [*Wasmannia auropunctata*][11]. From a previous BLAST search using the homologous *D. melanogaster* gene, we know that this gene is located on scaffold &#8220;scf7180000741419&#8243;, roughly between positions 1559000..1563000.

&nbsp;

##### Activating tracks

After you have navigated to your region of interest and adjusted the display to your preference, activate as many evidence tracks as necessary to inform your annotation. These should include at least three different types of evidence:

– results of an automatic annotation pipeline like MAKER

– protein alignments from related species (e.g., blastx)

– transcript alignments (e.g., a [BAM][12] file of your choice, like &#8220;bam_1d3Q&#8221;).

&nbsp;

##### Creating a user annotation

Note that genes may be found on the plus or minus strand. In our example above, the gene of interest is on the plus strand, indicated by the gene models pointing towards the right.

The first step in manually annotating a gene is to create a user annotation as a starting point. In most cases, including our example above, the best starting point is the gene model obtained by MAKER. MAKER models represent a consensus calculated from the results of several *ab initio* gene predictors like Augustus and Snap (also available as separate tracks), and the alignments of homologous proteins and transcripts. It is therefore usually the most accurate automatic annotation available.

To create a user annotation, drag and drop the MAKER gene model from the evidence panel into the yellow user annotation panel, where it will appear in light blue. Before dragging and dropping, you will need to select the gene model first, which is done by double-clicking on it until a red frame surrounding all its exons appears (a single click only selects an individual exon).

&nbsp;

<a href="../../wp-content/uploads/2013/08/WA_GeneModel.png" class="grouped_elements" rel="tc-fancybox-group407"><img class="margin-left size-full wp-image-981" alt="" src="../../wp-content/uploads/2013/08/WA_GeneModel.png" width="516" height="202" /></a>

&nbsp;

Since scaffolds can contain many closely spaced gene models, which may even overlap on opposite strands, you usually have to make sure first that the newly created annotation actually represents the gene of interest. Performing a [BLAST search][13] against the reference gene, [aligning][14] the annotation to the reference gene, or simply verifying the identifiers of aligned proteins in the evidence panel (if informative) are all strategies to do so. To acquire the new gene model&#8217;s sequence, select it as described above and choose the *Get sequence* option from the right-click menu.

After the identity of the annotation has been confirmed, you must decide whether the model is acceptable or is in need of manual modification. This is done by comparing various features of the gene model with the available evidence.

&nbsp;

##### Adding and removing exons 

From aligning the starting gene model to the reference gene, you might already have a good feeling for whether the coding sequence is complete or not. Missing or redundant exons might be apparent by long gaps in the alignment. Also compare the number and extent of exons between your gene model and the evidence, particularly protein and transcript alignments:

If you come to the conclusion that an exon needs to be removed, click on it once to highlight it (a red border should appear around it), press the right mouse button (Control-click on a Mac) and select *Delete* from the right-click menu. To add an exon (e.g., when it is indicated by transcript evidence), drag and drop it from the evidence onto the gene model, which should attach it (a green frame will appear around the gene model when the exon can be released). Alternatively, exons can also be merged or split using the *Merge* and *Split* or *Make intron* option from the right-click menu, respectively. All these manipulations may make it necessary to adjust the exon/intron boundaries, as explained below.

In our example, the fourth exon needs to be removed. Neither is it present in the protein sequences of most related species, nor is there transcript evidence (you may need to zoom in to make the BAM file data visible; transcribed sequence is shown in dark turquoise, untranscribed sequence in light turquoise). In addition, aligning the gene model to RpL3 of, for instance, *P. barbatus*, reveals an artificial [indel][4] corresponding to the redundant exon.

Note that disagreement within transcript evidence over the exon structure may also arise from the existence of alternative transcripts, whose annotation is discussed below.

&nbsp;

##### UTRs

Only transcript data may inform about the extent of UTRs, which may or may not be included in a gene model. If there is transcript evidence extending beyond the existing annotation, you may add or extend UTRs. To do so, position the cursor at the beginning of the exon that needs to be extended, bring up the right-click menu and choose the *Zoom to base level* option. Place the cursor over the edge of the exon (5’ or 3’ end exon as needed) until it becomes a black arrow, then click and drag the edge of the exon to the new coordinate position that includes the UTR. Note that UTR sequence appears as a darker, smaller blue rectangle than coding sequence. To add a new, spliced UTR to an existing annotation follow the procedure for adding an exon above.

&nbsp;

<a href="../../wp-content/uploads/2013/08/WA_BaseLevel.png" class="grouped_elements" rel="tc-fancybox-group407"><img class="margin-left size-full wp-image-982" alt="WA_BaseLevel" src="../../wp-content/uploads/2013/08/WA_BaseLevel.png" width="363" height="377" /></a>

&nbsp;

In our example, the 5&#8242; UTR needs to be extended in accordance with the longest available transcript evidence. WebApollo&#8217;s **edge-matching** function, which highlights matching boundaries between selected features like exons and evidence data as little red bars, is very useful to guide annotation in this regard.

&nbsp;

##### Splice sites

Most splice sites are characterized by GT&#8230;AG at the exon/intron boundary, with the splice sites themselves belonging to the intronic sequence. These sites are called canonical. All other types of splice sites are non-canonical, and are indicated by WebApollo by little orange exclamation marks. Some non-canonical splice sites are the result of erroneous gene prediction and need to be corrected, but others are biologically real. The frequency and type of non-canonical splice sites is dependent on the organism, but GC&#8230;AG is the most common. A non-canonical splice site can be assumed if there are no canonical splice sites nearby that result in a coding sequence that aligns well with sequences from related species (i.e., without indels). However, these cases should always be accompanied by an appropriate comment (see below).

A useful feature of WebApollo is working with the square bracket keys &#8220;[" and "]&#8221; to navigate from exon/intron boundary to the next. Use it in conjunction with the edge-matching function to check all boundaries while zoomed in to base level.

&nbsp;

##### Start and Stop codons

By default, WebApollo calculates the longest open reading frame including start and stop codons found in the exons present. You can assess whether the length of the gene model, and its start and stop signals, were determined accurately by aligning the coding sequence to know proteins, as suggested above. If it appears that WebApollo uses the wrong start codon, you can set another one manually by placing the mouse cursor over the alternative codon and selecting *Set translation start* from the right-click menu. In some cases, the exon containing the true start codon is initially missing, and has to be added as described above. Note that it is not uncommon for start codons to be found in exons that contain only UTR otherwise, making them easy to miss. The figure above shows one such example.

&nbsp;

#### Solving complex cases

The issues described above are commonly encountered and easy to fix. Sometimes, however, more complex cases arise, requiring additional techniques.

For instance, a gene model may be split across two or more sets of evidence on the same scaffold. To create a user annotation that combines both, drag two models (e.g. from MAKER) you wish to merge into the user-annotation area. Then select both models by clicking on a random intron of each model while keeping the shift key pressed, and select *Merge* from the right-click menu. Cases like this should be carefully inspected for correct splice sites, and for completeness of the coding sequence by alining with known proteins.

A gene may also be split across two scaffolds due to incomplete or inaccurate genome assembly. Since it is not possible to change the underlying genomic sequence in WebApollo, cases like this should be documented using the comment function (see below) and the complete sequence of the gene stored in a local file.

On the other hand, protein alignment artifacts may lead to erroneous fusion of two gene models that actually represent two different genes, supported by non-contiguous transcript evidence. The erroneous model may be split using the *Split* option as describe above.

Another source of error that can complicate gene annotation are sequencing errors, especially when indels (missing or superfluous bases) lead to frameshifts that truncate the encoded protein sequence. If you are positive this error is technical and not biological in nature (the latter would be a natural case of pseudogenization), for instance because it affects a highly conserved, single-copy gene, you should flag the annotation with an appropriate comment and store the corrected sequence in a local file. You may also make single base modifications using the right-click menu on the DNA track. These changes will be reflected in the sequence and structure of the annotation, but not the underlying genomic sequence, which cannot be changed.

Finally, transcript evidence may support the existence of [alternative transcripts][15], for example when certain exons are missing from a set of transcript contigs. Try to annotate as may alternative transcripts as you can by creating multiple user annotations of the same gene, adjusting them according to the evidence, and documenting all annotations using the comment function.

&nbsp;

#### Adding comments and keeping records

Careful annotation includes documenting any modifications so that others (and yourself in the future) can reconstruct what was done to obtain the final gene model. This is were the *Annotation Info Editor*, accessible through the right-click menu, comes into play. Before doing so, however, align your annotation one last time with known proteins to make sure it is complete.

&nbsp;

<a href="../../wp-content/uploads/2013/08/WA_AnnotationInfoEditor_I.png" class="grouped_elements" rel="tc-fancybox-group407"><img class="margin-left size-full wp-image-996" alt="" src="../../wp-content/uploads/2013/08/WA_AnnotationInfoEditor_I.png" width="1005" height="442" /></a>

&nbsp;

First, complete the &#8220;Symbol&#8221; text box <span style="color: #ff0000;">(1)</span> to give the gene a descriptive acronym. The convention for non-model organisms is to use the species name followed by the gene&#8217;s name, abbreviated as is customary in a related model organism. In our case, this is &#8220;Waur&#8221; for *W. auropunctata* and &#8220;RpL3&#8243; for Cytoplasmic Ribosomal Protein L3 in *D. melanogaster*, &#8220;Waur_RpL3&#8243; in total.

The &#8220;Comments&#8221; section<span style="color: #ff0000;"> (2)</span> should the be used to add additional information about the source of the annotation, including any modifications made, and the gene&#8217;s [homology relations][5]. It is good practice to use a consistent set of comments across a gene annotation project (gene annotation communities often agree on such &#8220;canned comments&#8221;). The following comments are recommended: 

<p style="padding-left: 30px;">
  SOURCE: the initial gene model on which the annotation is based, e.g. the MAKER model identifier. If multiple initial models were merged, include all. If a model had to be split, add a note here.
</p>

<p style="padding-left: 30px;">
  RESULT OF: include any lesser modifications made, for instance
</p> — 5&#8242; (or 3&#8242;, or both) UTR extended

— exon removed (or added, merged, split)

— splice site adjusted

— start (or stop) codon reset 

<p style="padding-left: 30px;">
  PROBLEMATIC: use for ambiguous or otherwise problematic observations:
</p> — gene split across scaffolds (include scaffold and gene model identifier of the other part)

— putative sequencing error (leading to frameshift)

— sequence partly unresolved (a potential sequencing or assembly artifact) 

<p style="padding-left: 30px;">
  ORTHOLOG: this is useful to include information about orthologs in well-annotated related organisms, possibly (like in our case) the reference gene
</p>

<p style="padding-left: 30px;">
  PARALOG: if the gene appears to possess paralogs in the same organism, cross-reference them here
</p>

<p style="padding-left: 30px;">
  NOTE: optional for any other observations, for example:
</p> — alternative transcripts

— non-canonical splice site

— no transcript evidence

— putative pseudogene

Finally, the &#8220;Transcript&#8221; section <span style="color: #ff0000;">(3)</span> is of interest in case of alternative transcripts. If you annotate alternative transcripts, the &#8220;Gene&#8221; section will apply to all of them, but this part can be used to add information specific to individual transcripts.

Another form of documentation that will make your life easier is to keep a [list of genes you have annotated][16] and any useful additional annotation like their position in the genome and notes relevant to the annotation. You can see an example here.

&nbsp;

#### Saving and exporting data

The final step of any gene annotation is saving your data. WebApollo automatically saves your progress, but for further analyses, you also want to keep local copies of the sequences that are the result of your annotation. As you already know, WebApollo allows you to access sequence data with the &#8220;Get sequence&#8221; option from the right-click menu once you have selected you annotation. The pop-up window provides five types of sequence: peptide, coding sequence (cds), cDNA (which includes the UTRs), genomic (which also includes intronic sequence) and genomic with additional sequence added downstream and upstream.

Copying and pasting the [peptide][17], [cds][18], and [genomic][19] sequences of each gene you annotate into a local [Fasta][20] file will allow you to quickly access these data for future reference.

&nbsp;

#### Tips and further resources

Further reading:

[Official WebApollo User Guide][21]

[Official WebApollo Wiki page][22]

[Apollo User Guide by Hymenoptera Genome Database][23]

&nbsp;

**This guide includes modifications to the instructions prepared by The WebApollo Development Team in the Bioinformatics Open-Source Projects ([BBOP][24]) group at Lawrence Berkeley National Laboratory.**

&nbsp;

**WebApollo is governed by [Copyright to the Regents of the University of California.][25]**

&nbsp;

Next chapter: [File formats][26]

&nbsp;

 [1]: ../22.blast
 [2]: ../21.gbrowse
 [3]: ../13.gene-annotation
 [4]: ../23.align_sequences
 [5]: ../41.homology-assessment
 [6]: http://ecoevo.unit.oist.jp/WebApollo/selectTrack.jsp
 [7]: ../12.genome-sequencing#Genome assembly
 [8]: ../21.gbrowse#JBrowse "Browsing genomes"
 [9]: ../13.gene-annotation  
 [10]: ../31.getting-started#Cytoplasmic Ribosomal Proteins
 [11]: ../14.ants#Wasmannia auropunctata
 [12]: ../25.file-formats#BAM "File formats"
 [13]: ../22.blast
 [14]: ../23.align_sequences
 [15]: ../11.introduction-to-genetics#Alternative transcripts
 [16]: ../../wp-content/uploads/2013/08/Waur_CRPs.xls
 [17]: ../../wp-content/uploads/2013/08/Waur_CRPs_aa.fas
 [18]: ../../wp-content/uploads/2013/08/Waur_CRPs_cds.fas
 [19]: ../../wp-content/uploads/2013/08/Waur_CRPs_genomic.fas
 [20]: ../../?page_id=451#FASTA "File formats"
 [21]: http://genomearchitect.org/web_apollo_user_guide
 [22]: http://genomearchitect.org/
 [23]: ../../wp-content/uploads/2013/08/Apollo_Guide_HGD.pdf
 [24]: http://berkeleybop.org
 [25]: https://github.com/GMOD/Apollo/blob/master/LICENSE.md
 [26]: ../25.file-formats
