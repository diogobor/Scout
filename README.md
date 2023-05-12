# Scout
Interactomics studies play a critical role in elucidating protein structures, functions, and interactions within complex cellular environments. Cross-linking mass spectrometry with cleavable cross-linking reagents (cXL-MS) has emerged as a powerful technique for large-scale interactomics analysis by identifying proximal amino acid pairs in protein samples. However, current computational cXL-MS tools face limitations in proteomic-scale studies, such as being too slow or generating excessive false positives, particularly at the protein-protein interactions level (PPIs). 

Here, we present **Scout**, a computational methodology that enables interactomic analysis by identifying mass spectra of peptides linked with cleavable cross-linking reagents. By leveraging machine learning techniques, Scout ensures a controlled false discovery rate (FDR) at multiple levels, including cross-linked spectrum matches, residue pairs, and PPIs. Our methodology offers an efficient and accurate solution for large-scale interactomics studies, addressing the existing computational challenges.

# Equipment
## Hardware
- A computer with a minimum of 16 GB RAM and 4 computing cores is recommended.  However, the software can take advantage of superior configurations.

## Software
-	Windows 10 (64 bits) or later.
-	Python 3.10 or later.
-	The .NET Core 6.
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
  <p align="center"><img width="620" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/15459dd3-654a-4d14-bf0a-8537f4027259"><br/>
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
      Search parameters can be adjusted to optimize the search process. To modify the parameters, navigate to Utils &#8594; Parameters &#8594; Search (or press ALT + S), as illustrated in <b>Figure 2a</b>, a new window will open (<b>Figure 2b</b>).
      <p align="center"><img width="25%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/662c77a9-f88f-4fa5-9cba-d449c3ba575f"><br/>
      <b>Figure 2a: Search and Post Processing Parameters can be modified on Utils &#8594; Parameters.</b><br/><br/>
      <img width="55%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/9bc95bba-d4ce-4cbb-bf20-2e8e38d704ca"><br/>
      <b>Figure 2b: Search Parameters window</b></p><br/>
      &emsp;&emsp;2.2.4.1. <i>MS1 PPM Tolerance</i>: Specify the ppm error tolerance for the precursor mass.<br/>
		  &emsp;&emsp;2.2.4.2. <i>MS2 PPM Tolerance</i>: Specify the ppm error tolerance for fragment ions.<br/>
      &emsp;&emsp;2.2.4.3. <i>Ion Pair PPM Tolerance</i>: Specify the ppm error tolerance for ion pair mass.<br/> 
		  &emsp;&emsp;2.2.4.4. <i>Min. Peptide Length</i>: Specify the minimum number of amino acids in each connected peptide.<br/>
      &emsp;&emsp;2.2.4.5. <i>Max. Peptide Length</i>: Specify the maximum number of amino acids in each connected peptide.<br/>
      &emsp;&emsp;2.2.4.6. <i>Min. Peptide Mass</i>: Specify the minimum peptide mass in Daltons.<br/>
      &emsp;&emsp;2.2.4.7. <i>Max. Peptide Mass</i>: Specify the maximum peptide mass in Daltons.<br/>
      &emsp;&emsp;2.2.4.8. <i>Missed Cleavages</i>: Specify the maximum missed cleavages allowed in a single peptide.<br/>
      &emsp;&emsp;2.2.4.9. <i>Max. Variable Mods</i>: Specify the maximum number of variable post-translational modifications in a single peptide.<br/>
      &emsp;&emsp;2.2.4.10. <i> Enzyme</i>: Select a proteolytic enzyme for in-silico digestion.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.10.1. <i> Add Enzyme</i>: Navigate to the <i>Enzymes</i> tab and click on ‘<i>Add Enzyme</i>’ button (<b>Figure 3a</b>). A new window will be opened (<b>Figure 3b</b>).<br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/14ee608a-dafa-464f-be3c-d01003b3c83f"><br/>
      <b>Figure 3a: Enzymes window – This tab enables the addition or removal of enzymes.</b><br/><br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/2dc34fbf-95d4-4841-8ff0-69a922d34f26"><br/>
      <b>Figure 3b: New Enzyme Inclusion – This window allows users to introduce a new enzyme to the existing list of enzymes.</b>
      </p><br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.10.1.1. <i>Name</i>: Specify a name for the new enzyme.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.10.1.2. <i>Sites</i>: Specify the amino acids at which cleavage should occur. <i>Note: the amino acids should be included without spaces, for instance, the trypsin sites should appear as KR.</i><br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.10.1.3. <i>Blocked by</i>: Specify the amino acids that will impede the cleavage. <i>Note: as in ‘Sites’, the amino acids must be typed without spaces.</i><br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.10.1.4. <i>C-Terminal</i>: Check this option if the new enzyme cleaves at the C-terminus of the peptide; otherwise, cleavage will occur at the N-terminus.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Click on the ‘<i>Confirm</i>’ button to incorporate the new enzyme into the Enzymes table. Afterwards, return to <i>2.2.4.10</i>.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.10.2 To remove an Enzyme, press ‘<i>Del</i>’ key. A confirmation message will be displayed. Confirm it to proceed.<br/><br/>
&emsp;&emsp;2.2.4.11. <i>Enzyme specificity</i>: select an enzyme specificity from the list: full specific or semi-specific.<br/>
&emsp;&emsp;2.2.4.12. <i>Cleavable Reagent</i>: select a cleavable cross-linker from the list.<br/>
&emsp;&emsp;&emsp;&emsp;2.2.4.12.1. <i>Add Reagent</i>: go to XL Reagents tab and click on ‘<i>Add Reagent</i>’ button (<b>Figure 4a</b>). A new window will be opened (<b>Figure 4b</b>).<br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/b04ab7b4-6066-47b1-8e2c-dabb1eb326cc"><br/>
      <b>Figure 4a: Chemical cross-linkers window: on this tab, new reagents can be added or removed.</b><br/><br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/d555f60b-2ed5-45b4-b461-233fc3f0f796"><br/>
      <b>Figure 4b: A new reagent can be added into the list of cross-linkers.</b>
      </p><br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.12.1.1. <i>Name</i>: Specify a unique identifier for the new cleavable reagent.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.12.1.2. <i>Light Fragment Mass</i>: Specify the light fragment mass in Daltons.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.12.1.3. <i>Heavy Fragment Mass</i>: Specify the heavy fragment mass in Daltons.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.12.1.4. <i>Full Mass</i>: Specify the full mass of the reagent in Daltons.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.12.1.5. <i>Ion Pair Shift</i>: The pair will be automatically calculated according to the light and heavy fragment masses.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.12.1.6. <i>Target Residues</i>: Specify the target residues that the new cleavable cross-linker will react with. <i>Note: List residues without spaces; for example, use KSYT for DSSO.</i><br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.12.1.7. <i>N-Terminal</i>: Check this option if the new cleavable cross-linker also reacts at the N-terminus of the protein. <br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Click the ‘<i>Confirm</i>’ button to incorporate the new cleavable reagent into the XL Reagents table. Subsequently, return to <i>2.2.4.10</i>.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.12.2 To remove an XL Reagent, press ‘<i>Del</i>’ key. A confirmation message will be displayed. Confirm it to proceed.<br/><br/>
      &emsp;&emsp;2.2.4.13. <i>Deconvolute for Ion Pair Searching</i>: Check this option to deconvolute the spectra before searching the ion pairs. If enabled, the deconvolution will be performed by YADA 3.0 [16].<br/>
      &emsp;&emsp;2.2.4.14. <i>Deconvolute for Scoring</i>: Check this option to deconvolute spectra prior to searching for CSMs. If enabled, the deconvolution will be performed by YADA 3.0. [16]<br/><br/>
      &emsp;&emsp;<b>Explanation on ‘<i>deconvolution</i>’:</b> As cleavable cross-linking search relies heavily on locating ion pairs, noisy spectra can be very harmful to the overall quality of end results. As such, spectra deconvolution is generally recommended, and set as default for the ion pair searching step of Scout. In mass spectrometry, deconvolution refers to the process of de-charging and/or deisotoping a spectrum. In practical terms, this is the process of iterating the MS2 searching looking for charge envelopes and isotopic envelopes, grouping them all into a single ion at charge +1. This is particularly important for the first step of Scout’s workflow, Ion Pair Doublet Searching, as we found that being too lenient with the search for ion pairs may lead to false positives.<br/><br/>
      &emsp;&emsp;2.2.4.15. <i>Add Modification</i>: Click on this button to add a new post-translational modification (<b>Figure 5a</b>). A new window will appear (<b>Figure 5b</b>).<br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/f28ad4f7-108a-4081-93c3-8471aeda43f9"><br/>
      <b>Figure 5a: Modification Window – This tab displays all variable and static modifications.</b><br/><br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/3809f4ab-4f93-4357-b7ea-737bb3a79bbf"><br/>
      <b>Figure 5b: New Modification Inclusion – This window enables the addition of a new modification into the modifications list.</b>
      </p><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.15.1. <i>Name</i>: Specify a unique name for the new post-translational modification.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.15.2. <i>Mass Shift</i>: Specify the mass shift in Daltons.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.15.3. <i>Target Residues</i>: Specify the target residues for this new post-translational modification. Use capital letters without spaces.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.15.4. <i>C-Terminal</i>: Check this option if the new post-translational modification occurs at the C-terminus of the peptide.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.15.5. <i>N-Terminal</i>: Check this option if the new post-translational modification occurs at the N-terminus of the peptide.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.15.6. <i>Variable</i>: Check this option if the new post-translational modification is dynamic, i.e., if it may or may not occur.<br/>
      &emsp;&emsp;&emsp;&emsp;Click on the ‘<i>Confirm</i>’ button to incorporate the new modification into the Modification table.<br/>
      &emsp;&emsp;&emsp;&emsp;<b>Note: Upon completing this process, ensure the new post-translational modification is checked in ‘<u>Use</u>’ field for it to be considered in the search.</b><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.15.7 To remove a modification, press the ‘<i>Del</i>’ key. A confirmation message will be displayed. Confirm the action to proceed.<br/><br/>
      &emsp;&emsp;2.2.4.16. <i>Contaminants</i>: on this tab, the current contaminants can be modified as well as new ones added (<b>Figure 6</b>). <i>Note: all contaminants must be entered in FASTA format (similar to item 2.2.3).</i><br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/ae9bd24e-1224-451e-97b5-c41b4280dea6"><br/>
      <b>Figure 6: Contaminants tab: all contaminant sequences can be modified as well as new ones can be added.</b></p>
      &emsp;&emsp;2.2.4.17. <i>Export</i>: Choose this option to save the current parameters to a file.<br/>
      &emsp;&emsp;2.2.4.18. <i>Load</i>: Select this option to import parameters from a file.<br/>
      &emsp;&emsp;2.2.4.19. <i>As default</i>: Set the current parameters as the software’s default settings.<br/>
      &emsp;&emsp;2.2.4.20. <i>Restore</i>: Revert to factory default parameters.<br/>
      &emsp;&emsp;2.2.4.21. <i>Advanced</i>: Click on this link to customize the advanced parameters (not necessary for most searches). (<b>Figure 7</b>).<br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/8b0fed80-1c7d-4547-9e1e-6fed664cf784"><br/>
      <b>Figure 7: Edit advanced parameters: In this window, all search parameters can be modified.</b></p><br/>
      &emsp;&emsp;2.2.4.22. <b>Advanced Search Parameters</b><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.1. <i>Spectra saved in the results</i>: Check this option to save the identified experimental spectra in the results file.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.2. <i>Add contaminants</i>: Check this option to consider common mass spectrometry contaminants during the search.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.3. <i>Add decoys</i>: Check this option to add decoys before initiating the search. Note: for the FDR calculation, this option should be checked.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.4. <i>FASTA batch size</i>: Specify the maximum number of protein sequences to be loaded into memory at a given time.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.5. <i>Fragment bin tolerance</i>: Specify the bin size for binning mass spectra and for theoretical mass spectra generation.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.6. <i>Fragment bin offset</i>: Specify offset in Daltons to be considered to initiate the binning process.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.7. <i>Minimum fragment bin m/z</i>: Specify the minimum m/z to be vectorized.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.8. <i>Maximum fragment bin m/z</i>: specify the maximum m/z to be vectorized.<br/><br/>
      &emsp;&emsp;&emsp;&emsp;<b>Explanation on ‘<i>Binning</i>’</b>: We refer to binning mass spectra into vectors as the process of discretization of continuous m/z values by partitioning them into predefined bins. The process consists of establishing an offset (in Da) and a bin width (in Da) to define the initial point and bin size, respectively. Each bin encompasses a specific m/z range, and peaks are allocated to the corresponding bin based on their m/z value. Subsequently, the intensity values of peaks within each bin are aggregated, in our case, by summation. The output entails a vector of intensity values, with each entry representing a distinct bin. This vectorial representation streamlines mass spectral data manipulation and comparison, facilitating bioinformatics analyses. Therefore, the binning loosely refers to the MS/MS tolerance.<br/><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.9. <i>No. Isotopic Possibilities</i>: The precursor mass stored in raw data files may not correspond to the monoisotopic peak. This option allows the software to find the correct monoisotopic peak, which is required to identify the molecule but at the cost of opening up the search space. If a high number of isotopic possibilities is set, the search space will increase accordingly and impact Scout’s sensitivity negatively.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.10. <i>Silac Search</i>: check this option to perform SILAC search.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.22.10.1 <i>Add Silac Group</i>: a new window will open to add the groups for labelling peptides, e.g., heavy and light groups as well as their amino acids can be added in this feature.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.4.22.10.2 <i>Hybrid mode</i>: check this option to find not only heavy-heavy / light-light peptides, but also heavy-light/light-heavy ones.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.11. <i>Export: see 2.2.4.17.</i><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.12. <i>Load: see 2.2.4.18.</i><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.13. <i>As default: see 2.2.4.19.</i><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.4.22.14. <i>Restore: see 2.2.4.20.</i><br/><br/>
      &emsp;2.2.5 <b>Post Processing Parameters</b><br/>
      <p align="justify">&emsp;&emsp;&emsp;Adjusting certain post processing parameters may improve the performance of the process. To do this, navigate to Utils &#8594; Parameters &#8594; Post Processing (or use the keyboard shortcut ALT + P), as can illustrated in <b>Figure 2a</b>. A new window will appear (<b>Figure 8</b>).</p>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/8a683620-04db-4a0d-8906-45e1a443d23a"><br/>
      <b>Figure 8: Post Processing Parameters window</b></p><br/>
      &emsp;&emsp;2.2.5.1. <i>Use only unique XLs into PPIs</i>: Check this option to remove PPIs that contain shared cross-linked peptides.<br/>
      &emsp;&emsp;2.2.5.2. <i>Separate protein intra- and inter-crosslinks</i>: Check this option to apply FDR control separately to intra- and inter-crosslinks at the CSM, Residue Pair, and PPI levels.<br/>
      &emsp;&emsp;2.2.5.3. <i>Group PPIs by gene</i>: Check this option to group all protein-protein interactions by gene name.<br/>
      &emsp;&emsp;2.2.5.4. <i>FDR on CSM level</i>: Specify the FDR on CSM level.<br/>
      &emsp;&emsp;2.2.5.5. <i>FDR on Residue Pair level</i>: Specify the FDR on Residue Pair level.<br/>
      &emsp;&emsp;2.2.5.6. <i>FDR on PPI level</i>: Specify the FDR on PPI level.<br/>
      &emsp;&emsp;2.2.5.7. <i>Export: Similar to 2.2.4.17.</i><br/>
      &emsp;&emsp;2.2.5.8. <i>Load: Similar to 2.2.4.18.</i><br/>
      &emsp;&emsp;2.2.5.9. <i>As default: Similar to 2.2.4.19.</i><br/>
      &emsp;&emsp;2.2.5.10. <i>Restore: Similar to 2.2.4.20.</i><br/><br/>
      &emsp;2.2.6. <i>Export log</i>: the whole log information can be exported by going to Tools &#8594; Export log (or pressing ALT + M).<br/><br/>
  2.3. <b>Results</b><br/>
&emsp;&emsp;Upon completion of the search processing, the results are automatically saved in the same directory in which the RAW files are (<i><sup>*</sup>.scout file</i>) and presented in a new window with separate tabs: CSMs, Residue Pairs and PPIs, as well as the parameters used in the search. (<b>Figure 9</b>)
