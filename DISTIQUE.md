<div class="section page-header">

DISTIQUE {#distique .project-name}
========

DISTIQUE by Erfan Sayyari {#distique-by-erfan-sayyari .project-tagline}
-------------------------

</div>

<div class="section main-content">

### <span id="distique">[<span class="octicon octicon-link"></span>](#distique)</span>DISTIQUE

DISTIQUE is a python based tool for inferring species trees from gene
trees. It is a forced acronym for Distance-based Inference of Species
Trees using Induced QUartet Elements.

The basic idea behind DISTIQUE is to infer the species tree from gene
trees by computing a distance between two species from the set of
quartets that include the two species. We have found ways to do this in
a statistically consistent manner. DISTIQUE introduces a family of distance-based tree inference methods, 
with running times ranging between quadratic to quartic in the number of leaves

### <span id="how-distique-infers-species-trees">[<span class="octicon octicon-link"></span>](#how-distique-infers-species-trees)</span>How DISTIQUE infers species trees

It first finds a distance matrix based on the quartet trees induced by
gene trees, and then infers the species trees using a distance-based
method like FASTME or PhyD. \*

### <span id="how-to-install-distique">[<span class="octicon octicon-link"></span>](#how-to-install-distique)</span>How to install DISTIQUE

You could install DISTIQUE in a couple of steps:\
 1. Clone to [DISTIQUE git
repository](https://github.com/esayyari/DISTIQUE) or download [this zip
file](https://github.com/esayyari/DISTIQUE/archive/master.zip).\
 2. Then you need to set environmental variable WS\_HOME to the
directory under which this "DISTIQUE" repository is placed. There are
a couple of dependencies that you need to install at this step as well.

### <span id="dependencies">[<span class="octicon octicon-link"></span>](#dependencies)</span>Dependencies

1.  FASTME 2.0 is now available at [this
    link](http://www.atgc-montpellier.fr/fastme/binaries.php).
    [FASTME](http://www.atgc-montpellier.fr/fastme/binaries.php) is a
    distance based method that produces species trees based on the
    provided distance matrix. Put it under your WS\_HOME.
2.  PhyD\* is another distance based method that could handle missing
    values in distance matrix reasonably. You could download it from
    [this link](http://www.atgc-montpellier.fr/phyd/binaries.php). Then
    put it under you WS\_HOME.\
3.  Quartet code from [this thesis](http://jensjohansen.com/thesis/).
    Make sure that you set the QUARTETS flag to "1" for compiling it.
    After compilation put the executable code quart\_bin under
    DISTIQUE/bin.\
4.  The set of tools at [this git
    repository](https://github.com/smirarab/global). They are written in
    different languages, but installing it is supper easy.\
5.  DendroPy 4.0.3, which is a Python library for
    phylogenetic computing.

### <span id="how-distique-works">[<span class="octicon octicon-link"></span>](#how-distique-works)</span>How DISTIQUE works

The main file to use DISTIQUE is available under
DISTIQUE/src/utils/distique-2.py

Usage: python distique-2.py \[-h (show help)\] \[-f FILENAME
(pre-computed quartet table)\] \[-g GT (read gene trees from GT)\] \[-o
OUT (working directory)\] \[-t THR (min majority consensus threshold,
default is 0.5)\] \[-m METHOD (The method to compute the distance of
taxa. The default is prod)\] \[-a AV (The average method
to find the average quartet table. Default is mean.)\] \[ -v VERBOSE\]

The Distance-Sum version of DISTIQUE is available under DISTIQUE/src/utils/distique-v5.py


Usage: python distique-v5.py \[-h (show help)\] \[-f FILENAME
(pre-computed quartet table)\] \[-g GT (read gene trees from GT)\] \[-o
OUT (working directory)\] \[-t THR (min majority consensus threshold,
default is 0.5)\] \[-m METHOD (The method to compute the distance of
taxa. The default is prod)\] \[-a AV (The average method
to find the average quartet table. Default is mean.)\] \[ -v VERBOSE\]
\[-n NUM, --numStep=NUM (#rounds of anchoring, default is 2)\]
\[-u SUMPROG  (The summerize method program to build species tree from distance matrix. Default is fastme)\]
\[-z SUMPROGOPTION  (The distance method to build the tree.)\]


The Tree-Sum version of DISTIQUE is available under DISTIQUE/src/utils/distique-v8.py


Usage: python distique-v8.py \[-h (show help)\] \[-f FILENAME
(pre-computed quartet table)\] \[-g GT (read gene trees from GT)\] \[-o
OUT (working directory)\] \[-t THR (min majority consensus threshold,
default is 0.5)\] \[-m METHOD (The method to compute the distance of
taxa. The default is prod)\] \[-a AV (The average method
to find the average quartet table. Default is mean.)\] \[ -v VERBOSE\]
\[-n NUM, --numStep=NUM (#rounds of anchoring, default is 2)\]
\[-u SUMPROG  (The summerize method program to build species tree from distance matrix. Default is fastme)\]
\[-z SUMPROGOPTION  (The distance method to build the tree.)\]


### <span id="datasets">[<span class="octicon octicon-link"></span>](#datasets)</span>Datasets

There are mainly three datasets that we used in this paper.\
 1. [avian dataset]().
This dataset contains estimated gene trees, true gene trees, and true
species tree\
 2. [mammalian dataset]().
This dataset contains true gene trees, estimated gene trees and true
species tree

### <span id="biological-dataset">[<span class="octicon octicon-link"></span>](#biological-dataset)</span>Biological dataset

We reanalyze the avian biological dataset of Jarvis et. al. available at
paper:\
 Jarvis, Erich D., et. al. "Phylogenomic analyses data of the avian
phylogenomics project." GigaScience 4.1 (2015): 1-9.

The resulting species trees are available at [biological species
trees]().
### <span id="spieces-trees">[<span class="octicon octicon-link"></span>](#spieces-trees)</span>Spieces trees

The species trees inferred using the following methods are provided. \
 1.
[DISTIQUE-AAD]()\
 2.
[DISTIQUE-AMD]()\
 2. [ASTRID
(NJst)]()\
 3.
[ASTRAL]()\

### <span id="report-bugs">[<span class="octicon octicon-link"></span>](#report-bugs)</span>Report bugs

contact [@esayyari](https://github.com/esayyari)
(<esayyari@eng.ucsd.edu>).

<span class="site-footer-credits">This page was generated by [GitHub
Pages](https://pages.github.com) using the [Cayman
theme](https://github.com/jasonlong/cayman-theme) by [Jason
Long](https://twitter.com/jasonlong).</span>

</div>
