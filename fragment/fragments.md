# Fragmentary gene sequences negatively impact gene tree and species tree reconstruction

## Abstract
Species tree reconstruction from genome-wide data is increasingly being attempted, in most cases using a two-step
approach of first estimating individual gene trees and then summarizing them to obtain a species tree. The accuracy of
this approach, which promises to account for gene tree discordance, depends on the quality of the inferred gene trees. At
the same time, phylogenomic and phylotranscriptomic analyses typically use involved bioinformatics pipelines for data
preparation. Errors and shortcomings resulting from these preprocessing steps may impact the species tree analyses at
the other end of the pipeline. In this article, we first show that the presence of fragmentary data for some species in a
gene alignment, as often seen on real data, can result in substantial deterioration of gene trees, and as a result, the species
tree. We then investigate a simple filtering strategy where individual fragmentary sequences are removed from individual
genes but the rest of the gene is retained. Both in simulations and by reanalyzing a large insect phylotranscriptomic data
set, we show the effectiveness of this simple filtering strategy.
## Experiments and Codes

##### Please note that all codes are available on [this github repository](https://github.com/esayyari/Fragments/). They use python2 or bash, and dependencies are [dendropy4](https://dendropy.org/), [nwcik utility](http://cegg.unige.ch/newick_utils) and [PASTA](https://github.com/smirarab/pasta).

In this section we will describe the commands we used for generating and performing the simulations as well as the biological analyses.

 

### Generate simulated dataset
We used __draw\_parameters.py__ (please check the comments inside the code for more information) and the following files to generate the fragmentary stats for each species in each gene.
 
* __average\_branch\_lengths.csv__: average tip-to-root distances for biological Insects gene trees
* __fragmentary\_augmented.csv__: frequency of gap characters for the biological Insects dataset
* __simulated\_average\_branch\_lengths.csv__: average tip-to-root distances for biological Insects gene trees per each replicate.

To generate the sequence files we used __generateFragmentary.py__ passing the output of __draw\_parameters.py__. 

### Inferring gene trees

#### RAxML 


```
raxmlHPC -m <model> -n best -s <input_phylip> -p <seed_num> -N 10

raxmlHPC-PTHREADS -T <CPU> -m <model> -n best -s <input_phylip> -p <seed_num> -N 10
```
where $s is the seed number, and for NA, model is GTRGAMMA, and for amino acids we let RAxML find the best model automatically using the command:


```
perl ProteinModelSelection.pl <input_phylip> > ../bestModel.<alignname>

model=PROTGAMMA`sed -e "s/.* //g" bestModel.<alignname>`

```

Please note that for the simulated dataset we used RAxML with 2 starting trees, while for biological analysis, we used 10 starting trees.

#### FastTree

For nucleotide alignment we use this command:

```
fasttree -gtr -gamma -nt <input_phylip> > fasttree.tre.best 2> ft.log.best
```

and for protein alignment we use the default substitution model (JTT+CAT):

```
fasttree <input_phylip> > fasttree.tre.best 2> ft.log.best
```

### Inferring species trees

#### ASTRAL
```
java -jar astral.4.11.1.jar -i <genetrees> -o <species_tree> > logfile 2>&1

```

### Filtering sequences
We first filter sites that have less than **site\_threshold** non-gap characters and then filter the sequences that have less than **sequence\_threshold** non-gap sequences. 

```
python run_seqtools.py  -infile <input_sequence> -masksites <site_threshold> -outfile <site_filtered_sequence> > <logfile> 2>&1

python run_seqtools.py -infile <site_filtered_sequence> -filterfragments <sequence_threshold> -outfile <filtered_sequence> > <logfile> 2>&1
```

## Data
We used simulated as well as biological data to study the effects of fragmentary data on the quality of gene trees and species trees. 

### Simulations

In simulations, we study impacts of fragmentary data and the filtering strategy on the accuracy of gene trees and eventually the accuracy of the species trees. 
The simulated dataset is available [here](https://drive.google.com/open?id=1NuF0eG5cO3jxEHVoCgdIjiQ35qBQCuYv). The simulated dataset has 50 replicates (in 50 separate folders), with 101 species (one outgroup). For each replicate, we provide original gene sequences (all-genes.phylip), and the fragments inserted version (all-genes-fragAdded.phylip). We also provide the FastTree (using double precision), e.g. in FNA-genes.fragAdded-mask1sites.mask1taxa, and RAxML, e.g. in FNA-genes.fragAdded-mask1sites.mask1taxa-raxml, gene trees (using 50, 200, and 1000 genes) and the corresponding estimated species trees. Folders with __raxml__ at the end of their name contain RAxML gene trees. To indicate the filtering strategy, we use this format: __mask[x%]sites.mask[y%]taxa__, which indicates that we removed all sites with less than _x%_ non-gap characters, and we removed all species that has less than _y%_ non-gap characters. 

### Biological

We studied an empirical transcriptomic data set of insects consisting of 1,478 protein-coding genes of 144 taxa, where
27% of the alignment is gaps (Misof et al. 2014). We now share the biological sequences, gene trees and species trees:

* RAxML log files are available here [here](https://github.com/esayyari/Fragments/blob/master/data/Biological_InfoFiles.tar.gz)
* gene trees and species trees are avaialble [here](https://drive.google.com/open?id=1QpB9FdwMAU1bkHBS7lHfAfw-P5EdL2WZ)
* sequences are available [here](https://drive.google.com/open?id=19Z8y5FX16Oh-GYPnAvpuw7Hmv0d0DlIZ)

## References
* A. Stamatakis: "RAxML Version 8: A tool for Phylogenetic Analysis and Post-Analysis of Large Phylogenies". In Bioinformatics, 2014
* Junier, T. and Zdobnov, E.M., 2010. The Newick utilities: high-throughput phylogenetic tree processing in the UNIX shell. Bioinformatics, 26(13), pp.1669-1670.
* Mirarab, S., Nguyen, N., Guo, S., Wang, L.S., Kim, J. and Warnow, T., 2015. PASTA: ultra-large multiple sequence alignment for nucleotide and amino-acid sequences. Journal of Computational Biology, 22(5), pp.377-386.
* Misof B, Liu S, Meusemann K, Peters RS, Donath A, Mayer C, Frandsen PB, Ware J, Flouri T, Beutel RG, Niehuis O, Petersen M. 2014. Phylogenomics resolves the timing and pattern of insect evolution. Science 346(6210): 763–767.
* Price, M.N., Dehal, P.S. and Arkin, A.P., 2010. FastTree 2–approximately maximum-likelihood trees for large alignments. PloS one, 5(3), p.e9490.
