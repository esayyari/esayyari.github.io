### DISTIQUE
DISTIQUE is a python based tool to infer species trees from gene trees. It is a forced acronym for Distance-based Inference of Species Trees using Induced Quartet Elements. The draft paper is available at [paper](), and the supplementary material available at [supplementary]().


Its basic idea is to infer the species tree from gene trees by computing a distance between two species from the set of quartets that include the two species. We have found ways to do this in a statistically consistent manner and are exploring ways to make this run in quadratic running time.   

### How DISTIQUE infers species trees
It first finds a distance matrix based on the gene trees' quartets, and then infers the species trees using a distance-based method like FASTME or PhyD*.

### How to install DISTIQUE
You could install DISTIQUE in a couple of steps:  
1. Clone to [DISTIQUE git repository](https://github.com/esayyari/DISTIQUE) or download  [this zip file]().   
2. Then you need to set environmental variable WS_HOME to the directory under which this "DISTIQUE" repository is placed 
3. There are a couple of dependencies that you need to install at this step as well. 

### Dependencies
1. FASTME 2.0 is now available at [this link] (http://www.atgc-montpellier.fr/fastme/binaries.php). [FASTME] (http://www.atgc-montpellier.fr/fastme/binaries.php) is a distance based method that produces species trees based on the provided distance matrix. Put it under your WS_HOME. 
2. PhyD* is another distance based method that could handle missing values in distance matrix reasonably. You could download it from [this link] (http://www.atgc-montpellier.fr/phyd/binaries.php). Then put it under you WS_HOME.  
3. Quartet code from [this thesis](http://jensjohansen.com/thesis/). Make sure that you set the QUARTETS flag to "1" for compiling it. After compilation put the executable code quart_bin under DISTIQUE/bin.   
4. The set of tools at [this git repository] (https://github.com/smirarab/global). They are written in different languages, but installing it is supper easy.  
5. DendroPy 4.0.3, which is a Python library for phylogenetic computing.

### How DISTIQUE works
The main file to use DISTIQUE is available under DISTIQUE/src/utils/distique.py  

Usage: python distique.py \[-h (show help)\] \[-f FILENAME\] \[-g GT (read gene trees from GT)\] \[-o OUT (working directory)\] \[-t THR (min majority consensus threshold, default is 0.5)\] \[-m METHOD (The method to compute the distance of taxa. The default is prod)\] \[ -v VERBOSE\]  

### Datasets
There are mainly three datasets that we used in this paper.  
1. [11-taxon dataset] (). This dataset contains gene trees, and true species trees  
2. [avian dataset] (). This dataset contains estimated gene trees, true gene trees, and true species tree  
3. [mammalian dataset] (). This dataset contains true gene trees, estimated gene trees and true species tree  

### Biological dataset
We reanalyze the avian biological dataset of ED Jarvis et. al. available at paper:  
Jarvis, Erich D., et. al. "Phylogenomic analyses data of the avian phylogenomics project." GigaScience 4.1 (2015): 1-9.

### Spieces trees
We now publish the species trees inferred using the following methods. For more information look at [draft paper]().  
1. [DISTIQUE-AAD] ()  
2. [DISTIQUE-AMD] ()  
2. [ASTRID (NJst)] ()  
3. [ASTRAL] ()  
4. [RAxML] ()  

### Report bugs
contact @esayyari (esayyari@eng.ucsd.edu).


