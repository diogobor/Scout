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
-	Scout saves results in its _*.scout_ format and in the [mzIdentML 1.2](http://www.psidev.info/mzidentml#mzid12) proposed by [HUPO Proteomics Standard Initiative](http://www.psidev.info/) support the identification of cross-linked peptides. We note this is able to perform complete submissions of XL-MS data to PRIDE[12], and is therefore compatible with the PRIDE Inspector software[13]. Additionally, the software supports exporting all CSMs, Residue Pairs and PPIs as CSV files, as well as all results to [XlinkCyNET](https://apps.cytoscape.org/apps/xlinkcynet)[14] for visualization within [Cytoscape](https://cytoscape.org/)[15].

# Procedures

1. **Software installation:**<br/>
  1.1 Download Scout by clicking on <i>Scout_setup_64bit.msi</i> in the [latest release](https://github.com/diogobor/Scout/releases/).
  <br/>1.2 Install it by double-clicking the previous downloaded file.

1. **Workflow:**<br/>
The following workflow demonstrates how to perform a search using _Scout_.<br/>
  2.1. Launch <i>Scout</i>: Open the Scout application to access its main window as shown in <b>Figure 1</b>.<br/>
  <p align="center"><img width="620" alt="image" src="https://user-images.githubusercontent.com/7681148/236540207-c29f52ea-bae5-434b-b09b-8688777b1208.png"><br/>
  <b>Figure 1: Graphical User Interface of Scout’s main window.</b></p>
  2.2. <b>Initial Setup</b><br/>
     &emsp;2.2.1. Searching a single file: Select the ‘<i>Raw File</i>’ radio button and then select a tandem mass spectra file (<i>e.g.</i>, MS2, MGF or Thermo® RAW), for searching a single file.<br/>
     &emsp;2.2.2. Batch searching: Select the ‘<i>Raw folder</i>’ radio button and then specify a directory containing the tandem mass spectra files.<br/>
     &emsp;2.2.3. <i>Fasta File</i>: Select a file containing the protein sequences. The file format must be in FASTA format, typically obtained from <a href="https://www.uniprot.org/">Uniprot</a>. <i>For instance</i>:<br/>
&emsp;&emsp;>protein name<br/>
&emsp;&emsp;PROTEINSEQUENCE<br/>
<br/>
      &emsp;Click on <i>‘Start’</i> button to initiate the search by using the default parameters. Once the search is complete, the results page will open (see item <i>2.3</i>).<br/><br/>
      &emsp;2.2.4 <b>Search Parameters</b><br/>
      Search parameters can be adjusted to optimize the search process. To modify the parameters, navigate to Utils &#8594; Parameters &#8594; Search (or press ALT + S), as illustrated in <b>Figure 2a</b>, a new window will open (<b>Figure 2b</b>).
      <p align="center"><img width="25%" alt="image" src="https://user-images.githubusercontent.com/7681148/236543160-8b85a3e5-9586-45d1-9c91-337f4ba1c7bc.png"><br/>
      <b>Figure 2a: Search and Post Processing Parameters can be modified on Utils &#8594; Parameters.</b><br/><br/>
      <img width="55%" alt="image" src="https://user-images.githubusercontent.com/7681148/236543400-f9916751-0caa-4549-b9b6-a3ab34b8e262.png"><br/>
      <b>Figure 2b: Search Parameters window</b></p>
