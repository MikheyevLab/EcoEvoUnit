---
title: Browsing genomes
author: martin_helmkampf
layout: page 
---
{% include _toc.html %}

We are now turning from a general introduction to specific techniques for the study of genomes and annotation of genes, starting with software used to browse genome data.

&nbsp;

**GBrowse** is a commonly used genome browser displaying genome assemblies and annotations. It serves as a graphical front end to various database formats, and runs interactively in an internet browser window. Many public genome projects like [FlyBase][1], [WormBase][2] or Hymenoptera Genome Database (HGD) have adopted GBrowse. In this section we will learn how to use it taking HGD&#8217;s [*P. barbatus* GBrowse][3] implementation as an example.

&nbsp;

<a href="../../wp-content/uploads/2013/08/Gbrowse_II.png" class="grouped_elements" rel="tc-fancybox-group222"><img class="margin-left size-full wp-image-226" alt="Gbrowse_II" src="../../wp-content/uploads/2013/08/Gbrowse_II.png" width="1113" height="621" /></a>

&nbsp;

#### Searching and Navigating

To display a genomic region of interest, enter its name in the search field labeled &#8220;Landmark or Region&#8221; <span style="color: #ff0000;">(1)</span>. Accepted names include chromosome names, scaffold and contig identifiers, and gene names, and must strictly match the format used in the underlying database (otherwise, an error message is displayed). In our example, scaffold names follow the format scf718000xxxxxx. Specific regions of a scaffold can be specified by their start and end coordinates, counting from the first base of the scaffold. Thus, in our example 

<p style="font-family: courier;">
  scf7180000350335:1108530..1114530
</p> will display the section above, from bases 1,108,530 to 1,114,530 on scaffold scf7180000350335.

The &#8220;Scroll/Zoom&#8221; field <span style="color: #ff0000;">(2)</span> allows you to zoom in and out of the displayed region, all the way to the full extent of the scaffold. The pull-down menu can be used to specify a span in kilobases (kbp = 1000 bases) centered around the initial search region. Scrolling is usually easier by grabbing and moving the red transparent bar in the &#8220;Region&#8221; panel with the cursor (see below). Ticking the &#8220;Flip&#8221; box causes the browser display to flip, which allows you to view genes on the antisense strand in a more intuitive orientation.

&nbsp;

#### Display and Tracks

If found, the results of your selection are shown in three graphic panels, &#8220;Overview&#8221;, &#8220;Region&#8221;, and &#8220;Details&#8221;. The first two <span style="color: #ff0000;">(3)</span> display a large portion of the assembled sequence and the more immediate portion of the genome surrounding the region of interest, respectively. Red vertical bars and a red transparent horizontal bar highlight the exact position of the search region.

The &#8220;Detail&#8221; panel <span style="color: #ff0000;">(4)</span> finally gives a close-up view of the search region. It consists of tracks containing annotated features placed on the genome sequence, like gene models, homologous genes of related organisms, or experimental evidence for gene transcripts. In our example, the first track shows gene models included in the Official Gene Set (OGS) of *Pogonomyrmex barbatus*, a consensus set of automatically predicted and manually curated genes. [Gene structure][4] is indicated according to the convention we discussed earlier. Note you can search for a specific gene from the OGS using its identifier (here for example PB22887 in the center) as a search term. The following tracks include homologous genes from the honeybee *Apis mellifera* and the fruit fly *Drosophila melanogaster* which have been aligned to the genome sequence. Here, they partially match the gene predicted in the harvester ant. The last track indicates the average content of guanine and cytosine (GC) among the bases of the sequence. Tracks may contain a wide range of annotated features. Their availability depends on which ones the administrator has included in the database. You can toggle on and off tracks from a list of available ones using the &#8220;Select Tracks&#8221; button at the bottom of the GBrowse window, or the menu bar at the top.

&nbsp;

#### Retrieving Data

The sequence data corresponding to the search region may be downloaded in Fasta format using the download field in the upper right corner (select &#8220;Download Sequence File&#8221;) <span style="color: #ff0000;">(5)</span>. This is often useful to perform further analyses based on the region of interest. The &#8220;Save Snapshot&#8221; and &#8220;Load Snapshot&#8221; buttons also allow you to store the displayed region and its settings for later viewing. Finally, clicking on elements of certain tracks will make additional data available as. For example, clicking on the gene symbol of PB22778 will open [this window][5], containing metadata and annotated sequence data of the gene model.

&nbsp;

<a href="../../wp-content/uploads/2013/08/AnnotatedSequence_I.png" class="grouped_elements" rel="tc-fancybox-group222"><img class="margin-left size-full wp-image-245" alt="AnnotatedSequence_I" src="../../wp-content/uploads/2013/08/AnnotatedSequence_I.png" width="609" height="252" /></a>

&nbsp;

#### JBrowse <a id="JBrowse"></a>

GBrowse will eventually be replaced by a newer, faster version called [JBrowse][6], which offers many of the same functions through a slightly different graphical user interface. To see it in action, see the previous link or [here][7].

&nbsp;

<a href="../../wp-content/uploads/2013/08/JBrowse.png" class="grouped_elements" rel="tc-fancybox-group222"><img class="margin-left size-full wp-image-625" alt="JBrowse" src="../../wp-content/uploads/2013/08/JBrowse.png" width="1127" height="477" /></a>

&nbsp;

&nbsp;

Further reading:

Official [GBrowse wiki][8]

Official [GBrowse usage tutorial][9]

&nbsp;

Next chapter: [BLAST][10]

&nbsp;

 [1]: http://flybase.org/cgi-bin/gbrowse/dmel/
 [2]: http://www.wormbase.org/tools/genome/gbrowse/c_elegans/
 [3]: http://hymenopteragenome.org/cgi-bin/gb2/gbrowse/pbar_10/
 [4]: ../11.introduction-to-genetics##Gene structure
 [5]: http://hymenopteragenome.org/cgi-bin/gb2/gbrowse_details/pbar_10?ref=scf7180000350335;start=1110961;end=1112267;name=PB22887;class=Sequence;feature_id=1039535;db_id=general
 [6]: http://jbrowse.org/blog/
 [7]: http://hymenopteragenome.org:8080/Pbar_1.0/jbrowse/
 [8]: http://gmod.org/wiki/GBrowse
 [9]: http://cpansearch.perl.org/src/LDS/GBrowse-2.54/htdocs/general_help.html
 [10]: ../22.blast
