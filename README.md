# Scout
Interactomics studies play a critical role in elucidating protein structures, functions, and interactions within complex cellular environments. Cross-linking mass spectrometry with cleavable cross-linking reagents (cXL-MS) has emerged as a powerful technique for large-scale interactomics analysis by identifying proximal amino acid pairs in protein samples. However, current computational cXL-MS tools face limitations in proteomic-scale studies, such as being too slow or generating excessive false positives, particularly at the protein-protein interactions level (PPIs). 

Here, we present **Scout**, a computational methodology that enables interactomic analysis by identifying mass spectra of peptides linked with cleavable cross-linking reagents. By leveraging machine learning techniques, Scout ensures a controlled false discovery rate (FDR) at multiple levels, including cross-linked spectrum matches, residue pairs, and PPIs. Our methodology offers an efficient and accurate solution for large-scale interactomics studies, addressing the existing computational challenges.

# Equipment
## Hardware
- A computer with a minimum of 16 GB RAM and 4 computing cores is recommended.  However, the software can take advantage of superior configurations.

## Software
-	Windows 10 (64 bits) or later.
-	Python 3.10 or later.
-	The .NET 6 framework.
-	The Scout software, available for download at https://github.com/diogobor/Scout/releases

## Data files
-	Scout v1.0 is compatible with data files in the formats MS2, Mascot Generic Format (MGF) and Thermo® RAW files.
-	Scout saves results in its *.scout* format and in the [mzIdentML 1.2](http://www.psidev.info/mzidentml#mzid12) proposed by [HUPO Proteomics Standard Initiative](http://www.psidev.info/) support the identification of cross-linked peptides. We note this is able to perform complete submissions of XL-MS data to PRIDE[12], and is therefore compatible with the PRIDE Inspector software[13]. Additionally, the software supports exporting all CSMs, Residue Pairs and PPIs as CSV files, as well as all results to [XlinkCyNET](https://apps.cytoscape.org/apps/xlinkcynet)[14] for visualization within [Cytoscape](https://cytoscape.org/)[15].
