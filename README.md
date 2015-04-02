# BackSPIN algorithm

The BackSPIN biclustering algorithm was described in Zeisel et al. *Cell types in the mouse cortex and hippocampus revealed by single-cell RNA-seq* **Science** 2015 (PMID: [25700174](http://www.ncbi.nlm.nih.gov/pubmed/25700174), doi: [10.1126/science.aaa1934](http://dx.doi.org/10.1126/science.aaa1934)). Please cite this paper if you use the BackSPIN algorithm in your work.

Original MATLAB implementation by Amit Zeisel. This repo contains a standalone command-line version of BackSPIN, implemented in Python by Gioele La Manno. 

## Getting started

**Note: BackSPIN is currently under development and there is no production-ready version.**

You can download an alpha version for Mac OS X on the [release page](https://github.com/linnarsson-lab/BackSPIN/releases).

For other platforms, download the source and run from Python. BackSPIN requires [numpy](http://www.numpy.org).

BackSPIN takes input in CEF format and produces an annotated CEF file as output. Use [ceftools](https://github.com/linnarsson-lab/ceftools) to create and manipulate CEF files.


## Synopsis

       -i [inputfile]
       --input=[inputfile]
              Path of the tab delimited file.
              Rows should be genes and columns single cells/samples

       -o [outputfolder]
       --output=[outputfolder]
              The name of the folder where the output will be written (output will be a 
              file named results_ddMMyyhhmmss.cef)

       -d [int]
              Depth/Number of levels: The number of nested splits that will be tried by the algorythm
       -t [int]
              Number of the iterations used in the preparatory SPIN.
              Defaults to 10
       -f [int]   
              Feature selection is performed before backSPIN. Argument controls how many genes are seleceted.
       -s [float]
              Controls the decrease rate of the wid parameter used in the preparatory SPIN.
              Smaller values will increase the number of SPIN iterations and result in higher 
              precision in the first step but longer execution time.
              Defaults to 0.05
       -T [int]
              Number of the iterations used for every wid parameter.
              Does not apply on the first run (use -t instead)
              Defaults to 8
       -S [float]
              Controls the decrease rate of the wid parameter.
              Smaller values will increase the number of SPIN iterations and result in higher 
              precision but longer execution time.
              Does not apply on the first run (use -s isntead)
              Defaults to 0.25
       -g [int]
              Minimal number of genes that a group must contain for splitting to be allowed.
              Defaults to 2
       -c [int]
              Minimal number of cells that a group must contain for splitting to be allowed.
              Defaults to 2
       -k [float]
              Minimum score that a breaking point has to reach to be suitable for splitting.
              Defaults to 1.15
       -r [float]
              If the difference between the average expression of two groups is lower than threshold the algorythm 
              uses higly correlated gens to assign the gene to one of the two groups
              Defaults to 0.2
       -b [axisvalue]
              Run normal SPIN instead of backSPIN.
              Normal spin accepts the parameters -T -S
              An axis value 0 to only sort genes (rows), 1 to only sort cells (columns) or 'both' for both
              must be passed
       -v  
              Verbose. Print  to the stdoutput extra details of what is happening

