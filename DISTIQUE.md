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
Trees using Induced QUartet Elements. The draft paper is available at
[paper](https://raw.githubusercontent.com/esayyari/esayyari.github.io/master/main-draft.pdf),
and the supplementary material is available at
[supplementary](https://raw.githubusercontent.com/esayyari/esayyari.github.io/master/supplementary.pdf).

The basic idea behind DISTIQUE is to infer the species tree from gene
trees by computing a distance between two species from the set of
quartets that include the two species. We have found ways to do this in
a statistically consistent manner. DISTIQUE theory allows for quadratic
running time, but our current implementation only has the O(n\^4)
versions.

### <span id="how-distique-infers-species-trees">[<span class="octicon octicon-link"></span>](#how-distique-infers-species-trees)</span>How DISTIQUE infers species trees

It first finds a distance matrix based on the quartet trees induced by
gene trees, and then infers the species trees using a distance-based
method like FASTME or PhyD\*.

### <span id="how-to-install-distique">[<span class="octicon octicon-link"></span>](#how-to-install-distique)</span>How to install DISTIQUE

You could install DISTIQUE in a couple of steps:\
 1. Clone to [DISTIQUE git
repository](https://github.com/esayyari/DISTIQUE) or download [this zip
file](https://github.com/esayyari/DISTIQUE/archive/master.zip).\
 2. Then you need to set environmental variable WS\_HOME to the
directory under which this "DISTIQUE" repository is placed 3. There are
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
DISTIQUE/src/utils/distique.py

Usage: python distique.py \[-h (show help)\] \[-a AV (The average method
to find the average quartet table. Default is mean.)\] \[-f FILENAME
(pre-computed quartet table)\] \[-g GT (read gene trees from GT)\] \[-o
OUT (working directory)\] \[-t THR (min majority consensus threshold,
default is 0.5)\] \[-m METHOD (The method to compute the distance of
taxa. The default is prod)\] \[ -v VERBOSE\]

### <span id="datasets">[<span class="octicon octicon-link"></span>](#datasets)</span>Datasets

There are mainly three datasets that we used in this paper.\
 1. [11-taxon
dataset](https://drive.google.com/a/eng.ucsd.edu/file/d/0B16sMwDmKEuucVNHbk1Ocld2dFU/view?usp=sharing).
This dataset contains gene trees, and true species trees\
 2. [avian
dataset](https://drive.google.com/a/eng.ucsd.edu/file/d/0B16sMwDmKEuudi0yV1JyT0c5NEk/view?usp=sharing).
This dataset contains estimated gene trees, true gene trees, and true
species tree\
 3. [mammalian
dataset](https://drive.google.com/a/eng.ucsd.edu/file/d/0B16sMwDmKEuuYVBBTmxlcnVPYkE/view?usp=sharing).
This dataset contains true gene trees, estimated gene trees and true
species tree

### <span id="biological-dataset">[<span class="octicon octicon-link"></span>](#biological-dataset)</span>Biological dataset

We reanalyze the avian biological dataset of Jarvis et. al. available at
paper:\
 Jarvis, Erich D., et. al. "Phylogenomic analyses data of the avian
phylogenomics project." GigaScience 4.1 (2015): 1-9.

The resulting species trees are available at [biological species
trees](https://drive.google.com/file/d/0B16sMwDmKEuuT1JVbFZWT09Id0E/view?usp=sharing).
### <span id="spieces-trees">[<span class="octicon octicon-link"></span>](#spieces-trees)</span>Spieces trees

The species trees inferred using the following methods are provided. For
more information look at [draft
paper](https://raw.githubusercontent.com/esayyari/esayyari.github.io/master/main-draft.pdf).\
 1.
[DISTIQUE-AAD](https://drive.google.com/a/eng.ucsd.edu/file/d/0B16sMwDmKEuuN184b2w5RkZ1YTQ/view?usp=sharing)\
 2.
[DISTIQUE-AMD](https://drive.google.com/a/eng.ucsd.edu/file/d/0B16sMwDmKEuuUGVIWEpUZ1V3OU0/view?usp=sharing)\
 2. [ASTRID
(NJst)](https://drive.google.com/a/eng.ucsd.edu/file/d/0B16sMwDmKEuuR2hkMFZEaG9DMmc/view?usp=sharing)\
 3.
[ASTRAL](https://drive.google.com/a/eng.ucsd.edu/file/d/0B16sMwDmKEuuZWxFMnU0RzhWTTg/view?usp=sharing)\

### <span id="report-bugs">[<span class="octicon octicon-link"></span>](#report-bugs)</span>Report bugs

contact [@esayyari](https://github.com/esayyari)
(<esayyari@eng.ucsd.edu>).

<span class="site-footer-credits">This page was generated by [GitHub
Pages](https://pages.github.com) using the [Cayman
theme](https://github.com/jasonlong/cayman-theme) by [Jason
Long](https://twitter.com/jasonlong).</span>

</div>