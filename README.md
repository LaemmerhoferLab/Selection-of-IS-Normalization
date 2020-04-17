# Selection of Internal Standard-based Normalization for MS-Data
This code performs various internal standard-based normalization methods (B-MIS, CCMN, NOMIS, RUVrandom) on MS-datasets and extracts statistical parameters and metrics of intra-group variance for comparison. Ultimately, the aim is to provide a valid and simplified tool for selection of the optimum normalization strategy.

This script was created using RStudio (Version 1.1.383)

Title: "Selection of Internal Standard based Normalization"
Author: "B. Drotleff et al."
Date: "May 22th, 2019"


Following R packages are required to run the script:
MetNorm
NormalizeMets
metabolomics
qvalue
ggplot2
sgof
caTools
ropls
tibble


To ensure correct operation, the input data file must fulfill the following requirements:
  - The R-project file must be in the same folder as the input data file
  - The input data file must be named "dataset.csv" with the file type .csv
  - Columns must have headers --> column 1: "Samples", column 2: "Class"
	- Rows in column 1 must contain individual sample names
  - Rows in column 2 must contain numeric numbers that represent the corresponding class affiliation
  - The first two classes should be the samples of interest that are compared against each other (e.g. class 1 = treated samples, class 2 = control samples)
	- Quality control samples (QCs) must must be included as class 3
	- Starting from column 3, sample-wise response values for internal standards (ISs) must be listed
	- Subsequent columns must cotain sample-wise response values for aligned features
	- Empty cells should be avoided (execute missing value imputation prior to this script)
	- Dataset-specific input parameters that have to be adjusted by the user are:
        - Vector that describes columns that contain IS response values (including 0 <- non-normalization for B-MIS)
          e.g.: 0 stands for non-normalization, values 1-5 indicate 5 IS in the first 5 rows
          ISvect<-as.vector(c(0,1,2,3,4,5))
        - Factor k for RUVrandom normalization
          e.g.: 3 factors of unwanted variation
          k=3
        
	
          
An exemplary dataset (dataset.csv) is provided. This dataset was derived from open source data in the NormalizeMets R package.
For further description of this dataset see: De Livera, Alysha M, M. Aho-Sysi, Laurent Jacob, J. Gagnon-Bartch, Sandra Castillo, J.A. Simp-son, and Terence P. Speed. 2015. Statistical methods for handling unwanted variation in metabolomicsdata.Analytical Chemistry 87 (7). American Chemical Society: 3606-15. (DOI: 10.1021/ac502439y)         
          

