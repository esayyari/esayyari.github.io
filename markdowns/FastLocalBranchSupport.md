

# Fast Local Branch Support 


##### by Erfan Sayyari and Siavash Mirarab


# Introduction
Species tree reconstruction is complicated by effects of Incomplete
Lineage Sorting (ILS), commonly modeled by the multi-species coalescent
model. While there has been substantial progress in developing methods
that estimate a species tree given a collection of gene trees, less
attention has been paid to fast and accurate methods of quantifying
support. 

In this paper, we propose a fast algorithm to compute
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
posterior probability is implemented as a new feature in ASTRAL.


### How to install ASTRAL

The installation instruction and dependencies of the ASTRAL is available
at [ASTRAL](https://github.com/smirarab/ASTRAL/tree/master).

## How to score species tree using ASTRAL

#### Note: The following commands are used for latest version of the paper. The next set of commands are the commands used with primary version of paper. Note that we resolved some bugs for latest version of paper. You would find the details of the older versions at [arXiv](https://arxiv.org/abs/1601.07019v1).
#### Latest version of paper:
We used [ASTRAL (posteval)](https://github.com/smirarab/ASTRAL/tree/posteval)
version 4.9.1 for scoring and [ASTRAL (master)](https://github.com/smirarab/ASTRAL/tree/master)
version 4.9.8 for computing the branch length of the trees.
To have posterior probabilities of branches of main species tree and 2
other alternatives we used [posteval](https://github.com/smirarab/ASTRAL/tree/posteval):

```
 java −Xmx2000M −jar astral.4.9.1.jar −i [GENE TREES] −q [SPECIES TREE] −t 4
```

 To compute the branch lengths of main species tree we used the MAP
solution with the command [master](https://github.com/smirarab/ASTRAL/tree/master):

```
 java −Xmx2000M −jar astral.4.9.8.jar −i [GENE TREES] −q [SPECIES TREE] −t 2
```

 To compute the bootstrap support of the alternative topologies we
used [posteval](https://github.com/smirarab/ASTRAL/tree/posteval):

```
 java −Xmx2000M −jar astral.4.9.1.jar −i [BS-replicates] −q [SPECIES TREE] −t 5
```
## Datasets

There are mainly two simulated datasets that we used in this paper.

 1. [ASTRALII
dataset](https://drive.google.com/open?id=0B16sMwDmKEuuUnkzd3EzVlZhcDA).
This dataset contains estimated gene trees, true gene trees, true
species trees, and infered species trees with ASTRAL, RAxML, and NJST.
The branch length estimations available at
[ASTRALII-BL](https://drive.google.com/open?id=0B16sMwDmKEuuRElQSzBxaGFPZEU).
Also the posterior probability estimate files available at
[ASTRALII-PP](https://drive.google.com/open?id=0B16sMwDmKEuuYlZwSWRyaTkxMU0)\
 2. [avian
dataset](https://drive.google.com/open?id=0B16sMwDmKEuuWWZ3a2tnN3hkdkE).
This dataset contains true gene trees, estimated gene trees, true
species trees, and estimated species trees. It also contains bootstrap
replicates and the branch lenghths and posterior probability estimation
files. The results' csv files are available at
[results](https://drive.google.com/open?id=0B16sMwDmKEuuWk00bmRaczN2clE)

### Biological datasets

In this paper, we analyzed 4 different biological datasets. The results
and the datasets are available at [Biological
dataset](https://drive.google.com/open?id=0B16sMwDmKEuucTV4VnpTVlR1dXM):

 1. Avian biological dataset of Jarvis et. al. available at paper:
 Jarvis, Erich D., et. al. "Phylogenomic analyses data of the avian
phylogenomics project." GigaScience 4.1 (2015): 1-9.
 2. The dataset analyzed by Xi et. al. available at paper:
 Xi, Zhenxiang, Liang Liu, Joshua S Rest, and Charles C. Davis.
“Coalescent versus Concatenation Methods and the Placement of Amborella
as Sister to Water Lilies.” Systematic Biology 63, no. 6 (November 1,
2014): 919–932. doi:10.1093/sysbio/syu055.
 3. The 1KP dataset analyzed by Naim Matasci et. al. published at:
 Matasci, N., Hung, L.H., Yan, Z., Carpenter, E.J., Wickett, N.J.,
Mirarab, S., Nguyen, N., Warnow, T., Ayyampalayam, S., Barker, M. and
Burleigh, J.G., 2014. Data access for the 1,000 Plants (1KP) project.
GigaScience, 3(1), pp.1-10.
 4. The dataset analyzed by Prum et. al. available at:
 Prum, R.O., Berv, J.S., Dornburg, A., Field, D.J., Townsend, J.P.,
Lemmon, E.M. and Lemmon, A.R., 2015. A comprehensive phylogeny of birds
(Aves) using targeted next-generation DNA sequencing. Nature.

## report-bugs

contact [Siavash Mirarab](https://github.com/smirarab)
( smirarab at ucsd dot edu ), or [Erfan Sayyari] (https://github.com/esayyari)
( esayyari at eng dot ucsd dot edu ).

This page was generated by [GitHub Pages](https://pages.github.com) 

