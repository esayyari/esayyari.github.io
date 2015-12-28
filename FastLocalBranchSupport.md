---
generator: pandoc
...

<div class="section page-header">

Fast Local Branch Support {#FastLocalBranchSupport .project-name}
=========================

Fast Local Branch Support by Erfan Sayyari {#FastLocalBranchSupport-by-erfan-sayyari .project-tagline}
------------------------------------------

</div>

<div class="section main-content">

### <span id="Introduction">[<span class="octicon octicon-link"></span>](#Introduction)</span>Introduction

Species tree reconstruction is complicated by effects of Incomplete
Lineage Sorting (ILS), commonly modeled by the multi-species coalescent
model. While there has been substantial progress in developing methods
that estimate a species tree given a collection of gene trees, less
attention has been paid to fast and accurate methods of quantifying
support. In this paper, we propose a fast algorithm to compute
quartet-based support for each branch of a given species tree with
regard to a given set of gene trees. We then show how the quartet
support can be used in the context of the multi-species coalescent model
to compute i) the local posterior probability that the branch is in the
species tree and ii) the length of the branch in coalescent units. We
evaluate the precision and recall of the local posterior probability on
a wide set of simulated and biological data, and show that it has very
high precision and improved recall compared to multi-locus
bootstrapping. The estimated branch lengths are highly accurate when
gene trees have little error, but are underestimated when gene tree
estimation error increases. Computation of both branch length and local
posterior probability is implemented as a new feature in ASTRAL. The
draft paper is available at [paper](), and the supplementary material is
available at [supplementary]()\*.

### <span id="how-ASTRAL-calculates-posterior-probability-for-species-trees">[<span class="octicon octicon-link"></span>](#hhow-ASTRAL-calculates-posterior-probability-for-species-trees)</span>How ASTRAL calculates posterior probability for species trees

### <span id="how-to-install-ASTRAL">[<span class="octicon octicon-link"></span>](#how-to-install-ASTRAL)</span>How to install ASTRAL

The installation instruction and dependencies of the ASTRAL is available
at \[ASTRAL\] (https://github.com/smirarab/ASTRAL/tree/posteval). Use
the version available at posteval branch.

### <span id="how-to-score-species-tree-using-astral">[<span class="how-to-score-species-tree-using-astral"></span>](#how-distique-works)</span>How to score species tree using ASTRAL

We used [ASTRAL](https://github.com/smirarab/ASTRAL/tree/posteval)
version 4.9.1 for scoring and computing the branch length of the trees.
To have posterior probabilities of branches of main species tree and 2
other alternatives we used:\
 java −Xmx2000M −jar astral .4.9.1.jar −i \[GENE TREES\] −q \[SPECIES
TREE\] −t 4\
 To compute the branch lengths of main species tree we used the MAP
solution with the command:\
 java −Xmx2000M −jar astral .4.9.1.jar −i \[GENE TREES\] −q \[SPECIES
TREE\] −t 2\
 To compute the bootstrap support of the alternative topologies we
used:\
 java −Xmx2000M −jar astral .4.9.1.jar −i \[BS-replicates\] −q \[SPECIES
TREE\] −t 5\

### <span id="datasets">[<span class="octicon octicon-link"></span>](#datasets)</span>Datasets

There are mainly two simulated datasets that we used in this paper.\
 1. [ASTRALII
dataset](https://drive.google.com/open?id=0B16sMwDmKEuuUnkzd3EzVlZhcDA).
This dataset contains estimated gene trees, true gene trees, true
species trees, and infered species trees with ASTRAL, RAxML, and NJST.
The branch length estimations available at
[ASTRALII-BL](https://drive.google.com/open?id=0B16sMwDmKEuuRElQSzBxaGFPZEU).
Also the posterior probability estimate files available at
[ASTRALII-PP](https://drive.google.com/open?id=0B16sMwDmKEuuOVRGSGc5dERmTUU)\
 2. [avian
dataset](https://drive.google.com/open?id=0B16sMwDmKEuuTE9ZcC1aVWREUk0).
This dataset contains true gene trees, estimated gene trees, true
species trees, and estimated species trees. It also contains bootstrap
replicates and the branch lenghths and posterior probability estimation
files. The results' csv files are available at
[results](https://drive.google.com/open?id=0B16sMwDmKEuuQWtocmMtWmhMejg)

### <span id="biological-datasets">[<span class="octicon octicon-link"></span>](#biological-datasets)</span>Biological datasets

In this paper, we analyzed 4 different biological datasets. The results
and the datasets are available at [Biological
dataset](https://drive.google.com/open?id=0B16sMwDmKEuucTV4VnpTVlR1dXM):\
 1. Avian biological dataset of Jarvis et. al. available at paper:\
 Jarvis, Erich D., et. al. "Phylogenomic analyses data of the avian
phylogenomics project." GigaScience 4.1 (2015): 1-9.\
 2. The dataset analyzed by Xi et. al. available at paper:\
 Xi, Zhenxiang, Liang Liu, Joshua S Rest, and Charles C. Davis.
“Coalescent versus Concatenation Methods and the Placement of Amborella
as Sister to Water Lilies.” Systematic Biology 63, no. 6 (November 1,
2014): 919–932. doi:10.1093/sysbio/syu055.\
 3. The 1KP dataset analyzed by Naim Matasci et. al. published at:\
 Matasci, N., Hung, L.H., Yan, Z., Carpenter, E.J., Wickett, N.J.,
Mirarab, S., Nguyen, N., Warnow, T., Ayyampalayam, S., Barker, M. and
Burleigh, J.G., 2014. Data access for the 1,000 Plants (1KP) project.
GigaScience, 3(1), pp.1-10.\
 4. The dataset analyzed by Prum et. al. available at:\
 Prum, R.O., Berv, J.S., Dornburg, A., Field, D.J., Townsend, J.P.,
Lemmon, E.M. and Lemmon, A.R., 2015. A comprehensive phylogeny of birds
(Aves) using targeted next-generation DNA sequencing. Nature.

### <span id="report-bugs">[<span class="octicon octicon-link"></span>](#report-bugs)</span>Report bugs

contact <span
class="citation">\[@esayyari\]</span>(https://github.com/esayyari) (
esayyari at eng dot ucsd dot edu
).
<span class="site-footer-credits">This page was generated by [GitHub
Pages](https://pages.github.com) using the [Cayman
theme](https://github.com/jasonlong/cayman-theme) by [Jason
Long](https://twitter.com/jasonlong).</span>

</div>
