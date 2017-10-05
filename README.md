# Post-imputation checklist before running PRS:

Steps to do post-imputation but before running PRS:
  1) Combine all ethinicity .vcf files into 1
  2) Extract Mother and Child into separate .vcf files
  3) Convert .vcf to plink format for smartpca
  4) Using PLINK: 
    a) Apply MAF filter of 0.05 (or 5%) to remove rare variants
    b) LD-pruning applied due to regions of high LD (such as HLA regions) can overly influence PC model (Price et al., 2008, AJHG, 83,    
       132-135): window = 50, step size = 5, r^2 = 0.2 
       # note that PLINK 1.07 has a bug with r^2 when there is missing data so PLINK 1.9 must be used for any LD-pruning step.
       # At least 50,000 independent autosomal SNPs after LD-pruning would be needed for PCA (Anderson et al., 2010, NProt, 5, 1564-1573).
