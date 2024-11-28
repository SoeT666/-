setwd("C:/Users/Nina/Documents/courses/R_summer_school/GWAStutorial/GWAS_Workshop/")
library(GenABEL)# -
genodata <- load.gwaa.data(
            phenofile = "data/phenotype.dat", 
            genofile = "data/genotype.raw", 
            makemap = F, 
            sort = F)
# Get information about number of individuals
nids(genodata)
# Number of SNPs in the data
nsnps(genodata)
# Summary of the first 2 markers
summary(genodata@gtdata)[1:5, ]
chr4.idx <- which(genodata@gtdata@chromosome == 4)
maf <- summary(genodata@gtdata)[chr4.idx[1:500],"Q.2"]
plot(maf, type = 'l', main="MAF on chr 4", 
     xlab = "marker", ylab = "MAF", col = "slateblue")
# Summary of phenotypes
summary(genodata@phdata)
# Make a table with all phenotypes per individual
library(DT)
datatable(genodata@phdata,options=list(pageLength=5))
