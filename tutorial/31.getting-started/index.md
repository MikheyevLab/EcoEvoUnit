---
title: Getting started
author: martin_helmkampf
layout: page 
---
{% include _toc.html %}

After having reviewed the theoretical knowledge presented in the previous chapters, it is time to put it to practical use. This chapter will introduce a group of genes that are typically very easy to annotate, and thus lend themselves to practice your annotation skills before moving on to more challenging sets of genes posing more interesting biological questions in the [next chapter][1]. This introductory group is comprised of Cytoplasmic Ribosomal Protein genes.

&nbsp;

#### Cytoplasmic Ribosomal Proteins

Ribosomal proteins are integral components of ribosomes, the macromolecular machines that govern [protein synthesis][2] in all living cells. While the catalytic core of a ribosome is composed of ribosomal RNA (rRNA, red and yellow in the figure below), ribosomal proteins (blue) reside at the surface where they perform many auxiliary functions including stabilizing the structure of the particle and mediating molecular interactions by serving as binding platforms for other protein factors involved in the process of translation.

Representing a group of genes related by function rather than a gene family with a common evolutionary origin, ribosomal proteins are both ancient and highly conserved (that is, they differ very little in sequence even between organisms that are only distantly related, like humans and insects). Eukaryotic (non-bacterial) cells possess two types of ribosomes, cytoplasmic and mitochondrial, whose proteins are encoded by two different sets of genes. Here we will focus only on Cytoplasmic Ribosomal Proteins (CRPs), of which there are about 80 in every organism. Due to the vital role of ribosomes in a cell, ribosomal protein genes are abundantly expressed, which facilitates gene annotation because experimental data in the form of RNA-Seq or ESTs is often readily available. Paired with strong sequence similarity with other organisms, this makes annotating CRPs straight-forward and an ideal set to get started.

The full set of CRPs in the fruit fly *D. melanogaster* is available [here][3], to be used as reference genes for annotation. As additional reference, you may use the [CRP set of *P. barbatus*][4]. Note that some genes exist in two highly similar copies ([paralogs][5]), indicated by lower case &#8220;a&#8221; and &#8220;b&#8221; in the gene name, like RpL34a and RpL34b. Those duplicates are specific to a single organisms or a group of organisms. In constrast, a capital &#8220;A&#8221; at the end stands for an unrelated gene (for example, RpL13 and RpL13A are two completely different genes) that is present in all organisms.

&nbsp;

<a href="../../wp-content/uploads/2013/08/Ribosome.png" class="grouped_elements" rel="tc-fancybox-group909"><img class="margin-left size-full wp-image-430" alt="Ribosome" src="../../wp-content/uploads/2013/08/Ribosome.png" width="473" height="374" /></a>

&nbsp;

#### First exercise <a id="First exercise"></a>

Please start by annotating RpL6 through RpL13 (ten genes in total) in *Wasmannia auropunctata* as describe in the chapter on [WebApollo][6]. The first three genes have already been annotated and may serve as a reference. [This file][7] provides the information required to access these genes in WebApollo. Please add the results of your own annotations to this file.

&nbsp;

Next chapter: [Project phase: Focal genes][1]

&nbsp;

 [1]: ../32.focal-genes
 [2]: ../11.introduction-to-genetics#Gene translation and the genetic code
 [3]: ../../wp-content/uploads/2013/08/Dmel_CRPs.fas
 [4]: ../../wp-content/uploads/2013/09/Pbar_CRPsAa_red.fas
 [5]: ../41.homology-assessment
 [6]: ../24.webapollo
 [7]: ../../wp-content/uploads/2013/08/Waur_CRPs.xls
