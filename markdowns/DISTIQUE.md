<section class="page-header">

# DISTIQUE

## DISTIQUE by Erfan Sayyari

</section>

<section class="main-content">

### DISTIQUE ###

DISTIQUE is a python based tool for inferring species trees from gene trees. It is a forced acronym for Distance-based Inference of Species Trees using Induced QUartet Elements.

The basic idea behind DISTIQUE is to infer the species tree from gene trees by computing a distance between two species from the set of quartets that include the two species. We have found ways to do this in a statistically consistent manner. DISTIQUE introduces a family of distance-based tree inference methods, with running times ranging between quadratic to quartic in the number of leaves

### How DISTIQUE infers species trees ###

It first finds a distance matrix based on the quartet trees induced by gene trees, and then infers the species trees using a distance-based method like FastME[^fastme] or PhyD\* [^phyd].

### How to install DISTIQUE ###

You could install DISTIQUE in a couple of steps:  

1. Clone to [DISTIQUE git repository](https://github.com/esayyari/DISTIQUE) or download [this zip file](https://github.com/esayyari/DISTIQUE/archive/master.zip).  
2. Then you need to set environmental variable __WS_HOME__ to the directory under which this "DISTIQUE" repository is placed. There are a couple of dependencies that you need to install at this step as well.

### Dependencies ###

1.  __FASTME 2.0__ is now available at [this link](http://www.atgc-montpellier.fr/fastme/binaries.php). FastME is a distance based method that produces species trees based on the provided distance matrix. Put it under your __WS_HOME__.
2. .  __[DendroPy 4.0.3](https://pythonhosted.org/DendroPy/)__, which is a Python library for phylogenetic computing. You would install it by using the command ```sudo pip install "dendropy>=4"```. If you don't have root access, you would install __DendroPy__ locally by using the command ```pip install "dendropy>=4" --user```.

### Optional Dependencies ###
1.  __PhyD*__ is another distance based method that could handle missing values in distance matrix reasonably. You could download it from [this link](http://www.atgc-montpellier.fr/phyd/binaries.php), then put it under your __WS_HOME__. The default distance based software is FastME.

2.  Quartet code from [this thesis](http://jensjohansen.com/thesis/). Make sure that you set the QUARTETS compiler flag. After compilation place the executable code __quart_bin__ under __DISTIQUE/bin__. This code is used for **DISTIQUE-all-pairs**.

3.  The set of tools at [this git repository](https://github.com/smirarab/global). They are written in different languages, and different versions of Dendropy. Download or clone this repository and put it under your __WS_HOME__. Some of the bash script tools in DISTIQUE depend on these set of tools.


### How DISTIQUE works ###

The main file to use DISTIQUE is available under DISTIQUE/src/utils/distique-2.py

~~~	
	Usage: distique.py [options]
	Options:
  		-h, --help      				Show this help message and exit
 		-t STRAT, --strategy=STRAT		The version of DISTIQUE to be run 1 (all-paris, prod),
                        				2 (all-paris, max), 3 (Distance-sum), and 4 (Tree-
                        				sum), default is DISTIQUE Distance-SUM (3)
  		-f FILENAME, --file=FILENAME	Read quartet table from FILENAME
  		-g GT, --gene=GT				Read genetrees from FILENAME
  		-o OUT, --output=OUT  			The PATH to write the generated files
	  	-y THR, --threshold=THR			The minimum frequency that consensus will use. Default is 0.5
  		-v VERBOSE, --verbose=VERBOSE   Verbose
  		-u SUMPROG       				The distance based program to find species tree from distance matrix.
  										The options are ninja, fastme, phydstar. Default is fastme
  		-z SUMPROGOPTION 				The distance method to build the tree. If sumProg is set to fastme 
  										the options are TaxAdd_(B)alME (-s) (Default), TaxAdd_(B2)alME (-n), 
  										(D) default of fastme, TaxAdd_(O)LSME (-s), TaxAdd_(O2)LSME (-n),
  										B(I)ONJ, (N)J. The default in this case is TaxAdd_(B)alME. if the  
  										sumProg is set to phydstar, The options are BioNJ, MVR, and NJ. 
  		-s SP, --sp=SP        			Species tree
  		-n NUM, --numStep=NUM			The #rounds of anchoring, default is 2
  		-r OUTLIER            			The strategy for outlier removal. This options is only effective with tree-sum.
  										The options are pairwise1, pairwise2, consensus10, or consensus3. 
  										Default is consensus3
  		-x SUMMARY            			The summary method that will be used to summarize inferred species trees. 
  										Only effective with tree-sum. Default is MRL.
  		-a AV, --averagemethod=AV		The strategy to find the average quartet tables.
				                        Options are geometric mean (gmean), averaging (mean),
                        				or root mean square (otherwise). Default is mean.
  		-p MET                			The method to summarize quartet results around each
                        				node, freq, or log, Default is freq
  		-l FILLMETHOD         			The method to fill empty cells in distance tables, used with distance-sum
  									 	or tree-sum. Options are const, rand, or normConst. Default is const
  		-m METHOD, --distmethod=METHOD	The method to compute distances between pairs of species. 
  										Options are prod (default) or min. 
~~~


### Datasets ###


There are mainly three datasets that we used in this paper.  

* [Avian dataset](https://www.ideals.illinois.edu/bitstream/handle/2142/55685/README%20for%20Mirarab%20et%20al_fixed.html?sequence=5) dataset is a 45-taxon dataset, based on biological data, and have a single true species tree. [This file](https://drive.google.com/open?id=0B16sMwDmKEuudi0yV1JyT0c5NEk) contains model species tree, and true and estimated gene trees. 
* [Mammalian](https://www.ideals.illinois.edu/bitstream/handle/2142/55685/README%20for%20Mirarab%20et%20al_fixed.html?sequence=5) dataset is a 37-taxon dataset, based on biological data, and have a single true species tree. contains estimated gene trees, true gene trees. [This file](https://drive.google.com/open?id=0B16sMwDmKEuuYVBBTmxlcnVPYkE) contains model species tree, and true and estimated gene trees. 

These two datasets used to evaluate performance of DISTIQUE on datasets with relative small number of species, varying ILS, and number of genes. For more details about these two datasets visit [link](https://www.ideals.illinois.edu/bitstream/handle/2142/55685/README%20for%20Mirarab%20et%20al_fixed.html?sequence=5)

We analyzed these two datasets with different methods. Inferred species trees are available [here](https://drive.google.com/open?id=0B16sMwDmKEuuUXJaYzRQS1gxaFU). The methods that we used for our analyses are **ASTRID (NJst)**[^astrid], **ASTRAL**, **DISTIQUE-AAD**, **DISTIQUE-AMD**, **DISTIQUE all pairs** inferred with different distance methods (i.e. different methods implemented in FastME, and PhyD\*), __DISTIQUE distance sum__ with 1, 2, 4, and 8 rounds of anchor sampling around each polytomy, and __DISTIQUE tree sum__ with 1, 2, 4, and 8 rounds of anchor sampling around each polytomy.  


* [Simphy](http://www.cs.utexas.edu/~phylo/datasets/astral2/) dataset was also used for evaluating __ASTRAL-II__ and is simulated using [SimPhy](https://github.com/adamallo/SimPhy/) [^simphy]. True and estimated gene trees, and also true and estimated species trees using ASTRAL-II are available at [ASTRAL-II](http://www.cs.utexas.edu/~phylo/datasets/astral2/).  
We also provide the [inferred species trees](https://drive.google.com/open?id=0B16sMwDmKEuubjFXdGlCSTlPUVE) using __DISTIQUE all-pairs__ (for some model conditions), __DISTIQUE distance sum__ with 2 and 8 rounds of anchor sampling, and __ASTRID__ for this dataset. 

The RF distances between true and inferred species trees are available at this [link](https://drive.google.com/open?id=0B16sMwDmKEuuTTFYNVBjRDkwLTA) for avian and mammalian, and [here](https://drive.google.com/open?id=0B16sMwDmKEuuR1lpMUNFb01wVTg) for simphy dataset (in csv format). You would find the running times for the __simphy__ dataset at the following [link](https://drive.google.com/open?id=0B16sMwDmKEuuR1lpMUNFb01wVTg).

### Commands and Version numbers ###

** Important Note:** All of the results published in this paper, are produced with this [release](https://github.com/esayyari/DISTIQUE/tree/V0) of DISTIQUE. In this version of DISTIQUE, a specific random seed number was not, and as a result, there is some randomness across different runs of DISTIQUE on the same exact dataset. This can translate to small changes in the final results of the DISTIQUE-distance-sum and the DISTIQUE-tree-sum algorithms. The lack of determinism typically results in very small changes. In future versions of DISTIQUE, we plan to specify a random seed number, such that the results become reproducible.


* __AAD__

```bash
python distique.py -a mean -m prod -t 1 -u fastme -z D -g [GENE TREES] -o [OUTPUT DIR] 
```

* __AMD__

~~~bash
python distique.py -a mean -m prod -t 2  -u fastme -z D -g [GENE TREES] -o [OUTPUT DIR]
~~~

* __DISTIQUE all pairs__ with different summary methods

~~~bash
python distique.py -a mean -m prod -t 2  -u fastme -z D -g [GENE TREES] -o [OUTPUT DIR]
~~~

* __DISTIQUE distance-sum__ 

~~~bash
python distique.py -a mean -m prod -t 3  -u fastme -z B -g [GENE TREES] -o [OUTPUT DIR]
~~~

* __DISTIQUE tree-sum__

~~~bash
python distique.py -a mean -m prod -t 4 -u fastme -z B -g [GENE TREES] -o [OUTPUT DIR]
~~~

* __ASTRID__

~~~bash
python ASTRID.py −m fastme2 −i [GENE TREES] −o [OUTPUT SPECIES TREE]
~~~

*__ASTRAL__

~~~bash
java −Xmx2000M −jar astral.4.7.8.jar −i [GENE TREES] −o [OUTPUT SPECIES TREE]
~~~

### Biological dataset ###

We reanalyze the avian biological dataset of Jarvis et. al. 
This dataset is a dataset of 2022 supergene trees from an avian dataset.[^avian] The resulting species trees are available at [biological species trees](https://drive.google.com/open?id=0B16sMwDmKEuublBoWTFiNnQ2VUE).<span id="spieces-trees">[<span class="octicon octicon-link"></span>](#spieces-trees)</span>




### Report bugs ###

Contact [Erfan Sayyari](esayyari@eng.ucsd.edu)



<span class="site-footer-credits">This page was generated by [GitHub Pages](https://pages.github.com) using the [Cayman theme](https://github.com/jasonlong/cayman-theme) by [Jason Long](https://twitter.com/jasonlong).</span>

[^fastme]: Lefort, Vincent, Richard Desper, and Olivier Gascuel. "FastME 2.0: a comprehensive, accurate, and fast distance-based phylogeny inference program." Molecular biology and evolution 32.10 (2015): 2798-2800.
[^phyd]: Criscuolo, Alexis, and Olivier Gascuel. "Fast NJ-like algorithms to deal with incomplete distance matrices." BMC bioinformatics 9.1 (2008): 166.
[^astral]: Mirarab, Siavash, and Tandy Warnow. "ASTRAL-II: coalescent-based species tree estimation with many hundreds of taxa and thousands of genes." Bioinformatics 31.12 (2015): i44-i52. [ASTRAL](https://github.com/smirarab/ASTRAL)
[^astrid]: Vachaspati, Pranjal, and Tandy Warnow. "ASTRID: accurate species trees from internode distances." BMC genomics 16.Suppl 10 (2015): S3.[ASTRID](https://github.com/pranjalv123/ASTRID)
[^avian]: Jarvis, Erich D., et. al. "Phylogenomic analyses data of the avian phylogenomics project." GigaScience 4.1 (2015): 1-9.
[^simphy]: Mallo, Diego, Leonardo De Oliveira Martins, and David Posada. "SimPhy: Phylogenomic Simulation of Gene, Locus, and Species Trees." Systematic biology 65.2 (2016): 334-344.

