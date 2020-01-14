# Estimate the fractions of immune cells from expression profiles of tissues

This method is created as described in the manuscript - "Deconvolution of bulk gene expression profiles from complex tissues to quantify subsets of immune cells".

The tool is designed to estimate the fractions of immune cells from the expression profiles of tissues, such as tumor masses, PBMCs, etc. The 8 immune cells treated in this method include naïve CD8 T cells, naïve CD4 T cells, alternatively activated macrophages, classically activated macrophages, regulatory T cells, T helper cells, natural killer cells, and dendritic cells.

# Requirements

* R
* python 3

# Tutorial

The data provided in `Pre.reference.csv` is used as the reference gene expression signatures (RefGES) for the immune cell types to be treated in this method. 

Before starting the cell deconvolution analysis, the input expression profiles with initially unknown cell composition must be pre-processed by running `pre-process.R`, which could retrieve the expression levels of the common genes shared by the input data and our RefGES. Two files, namely `Sample.csv` and `Reference.csv`, will be automatically generated by `pre-process.R`. Then it is ready for us to run `SCORE.py`, which will take the above 2 files as the input files to infer the cell composition in the our samples. 

After running `SCORE.py`, three output files will be generated, including `score.csv`, `bar.pdf` and `boxplot.dpf`. `score.csv` provides the inferred fractions of the 8 types of immune cells. `bar.pdf` and `boxplot.pdf` provide the visualization of the inferred cell fractions.

In order to allow for a quick trial of this method by the users, we provide an example file, `example_expression_profile.csv`, which can be used as the input file to infer the cell composition in the sample.

## Synopsis

    Rscript pre-process.R -i "file name of our raw data" # you may try our `example_expression_profile.csv`
    python SCORE.py

# Contribution

   Yen-Jung Chiu (holiday01) and Yen-Hua Huang created this method. holiday01 implemented the code. 

# Reference

Chiu, Y., Hsieh, Y. & Huang, Y. Improved cell composition deconvolution method of bulk gene expression profiles to quantify subsets of immune cells. BMC Med Genomics 12, 169 (2019) doi:10.1186/s12920-019-0613-5
