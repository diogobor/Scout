# Scout
Interactomics studies play a critical role in elucidating protein structures, functions, and interactions within complex cellular environments. Cross-linking mass spectrometry with cleavable cross-linking reagents (cXL-MS) has emerged as a powerful technique for large-scale interactomics analysis by identifying proximal amino acid pairs in protein samples. However, current computational cXL-MS tools face limitations in proteomic-scale studies, such as being too slow or generating excessive false positives, particularly at the protein-protein interactions level (PPIs). 

Here, we present **Scout**, a computational methodology that enables interactomic analysis by identifying mass spectra of peptides linked with cleavable cross-linking reagents. By leveraging machine learning techniques, Scout ensures a controlled false discovery rate (FDR) at multiple levels, including cross-linked spectrum matches, residue pairs, and PPIs. Our methodology offers an efficient and accurate solution for large-scale interactomics studies, addressing the existing computational challenges.

_<b>Please cite our paper:</b>_<br/>
_Clasen, MA, et al., [“Proteome-scale recombinant standards and a robust high-speed search engine to advance cross-linking MS-based interactomics”](https://doi.org/10.1038/s41592-024-02478-1), Nature Methods, 2024._

# Equipment
## Hardware
- A computer with a minimum of 16 GB RAM and 4 computing cores is recommended.  However, the software can take advantage of superior configurations.

## Software
-	Windows 10 (64 bits) or later.
-	Python 3.10 or later.
-	The .NET Core 6 or later.
-	The Scout software, available for download at https://github.com/diogobor/Scout/releases

## Data files
-	Scout is compatible with data files in the formats MS2, Mascot Generic Format (MGF), Bruker® .d files, and Thermo® RAW files.
-	Scout saves results in its _*.scout_ format, in the [mzIdentML 1.2](http://www.psidev.info/mzidentml#mzid12) and [mzIdentML 1.3](http://www.psidev.info/mzidentml#mzid13) proposed by [HUPO Proteomics Standard Initiative](http://www.psidev.info/) to support the identification of cross-linked peptides. We note this is able to perform complete submissions of XL-MS data to PRIDE[<a href="#lib_1">1</a>], and is therefore compatible with the PRIDE Inspector software[<a href="#lib_2">2</a>]. Additionally, the software supports exporting all CSMs, Residue Pairs and PPIs as CSV files, as well as all results to [XlinkCyNET](https://apps.cytoscape.org/apps/xlinkcynet)[<a href="#lib_3">3</a>] for visualization within [Cytoscape](https://cytoscape.org/)[<a href="#lib_4">4</a>].

# Procedures

1. ## Software installation
   1.1 Download Scout by clicking on <i>Scout_setup_64bit.msi</i> in the [latest release](https://github.com/diogobor/Scout/releases/).
  <br/>1.2 Install it by double-clicking the previous downloaded file.

2. ## Workflow
   The following workflow demonstrates how to perform a search using _Scout_.<br/>If you are interested to run the software in _Automation_ mode, go to <a href="#ref_2_6">2.6</a></i>.<br/><br/>
   2.1 Launch <i>Scout</i>: Open the Scout application to access its main window, as shown in <b>Figure 1</b>.<br/>
  <p align="center"><img width="55%" alt="image" src="https://github.com/user-attachments/assets/c4bd6ee3-5585-43f3-a8d8-ba1a0ef0f989"><br/>
  <b>Figure 1: Graphical User Interface of Scout’s main window.</b></p>
   2.2 <b>Initial Setup</b><br/>
     &emsp;2.2.1. Searching selected file(s): Check the ‘<i>Raw File(s)</i>’ radio button and then select at least one tandem mass spectra file (<i>e.g.</i>, MS2, MGF or Thermo® RAW).<br/>
     &emsp;&emsp;<i>PS: For Bruker® .d files, select the folder that contains the name of the file.</i><br/>
     &emsp;2.2.2. Batch searching: Check the ‘<i>Raw folder</i>’ radio button and then specify a directory containing the tandem mass spectra files.
     <div id="ref_2_2_3">&emsp;2.2.3. <i>Fasta File</i>: Select a file containing the protein sequences. The file format must be in FASTA format, typically obtained from <a href="https://www.uniprot.org/">Uniprot</a>. <i>For instance</i>:</div>
&emsp;&emsp;>protein name<br/>
&emsp;&emsp;PROTEINSEQUENCE<br/>
<br/>
      &emsp;2.2.4 <i>Output Folder:</i> Select a folder where the results will be saved.<br/><br/>
      &emsp;&#8658; Click on <i>'Start'</i> button to initiate the search by using the default parameters. Once the search is complete, the results window will be opened (see item <i><a href="#ref_2_3">2.3</a></i>).<br/>
      &emsp;&#8658; To stop the search, click on <i>'Cancel'</i> button and confirm.<br/>
      &emsp;<i>PS: If for some reason the Scout closes, the search can continue from the point it was paused. To do this, just set the same parameters again and press the start button.</i><br/>
      &emsp;&#8658; All procedures will be recorded in the <i>Log</i> box. To export it, go to File &#8594; Export log (or press ALT + M).<br/><br/>
      &emsp;2.2.5 <b>Search Parameters</b><br/>
      Search parameters can be adjusted to optimize the search process. To modify the parameters, navigate to Parameters &#8594; Search (or press ALT + S), as illustrated in <b>Figure 2a</b>, a new window will open (<b>Figure 2b</b>).<br/><br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/255baf3a-aaa1-477a-8b20-eecfedbba462"><br/>
      <b>Figure 2a: Search and Post Processing Parameters can be modified on Parameters menu.</b><br/><br/>
      <img width="55%" alt="image" src="https://github.com/user-attachments/assets/47ab3d19-df1d-4eee-b199-35dcd78afb46"><br/>
      <b>Figure 2b: Search Parameters window</b></p>
      &emsp;&emsp;2.2.5.1. <i>MS1 PPM Tolerance</i>: Specify the ppm error tolerance for the precursor mass.<br/>
      &emsp;&emsp;2.2.5.2. <i>MS2 PPM Tolerance</i>: Specify the ppm error tolerance for fragment ions.<br/>
      &emsp;&emsp;2.2.5.3. <i>Ion Pair PPM Tolerance</i>: Specify the ppm error tolerance for ion pair mass.<br/> 
      &emsp;&emsp;2.2.5.4. <i>Min. Peptide Length</i>: Specify the minimum number of amino acids in each connected peptide.<br/>
      &emsp;&emsp;2.2.5.5. <i>Max. Peptide Length</i>: Specify the maximum number of amino acids in each connected peptide.<br/>
      &emsp;&emsp;2.2.5.6. <i>Min. Peptide Mass</i>: Specify the minimum peptide mass in Daltons.<br/>
      &emsp;&emsp;2.2.5.7. <i>Max. Peptide Mass</i>: Specify the maximum peptide mass in Daltons.<br/>
      &emsp;&emsp;2.2.5.8. <i>Missed Cleavages</i>: Specify the maximum missed cleavages allowed in a single peptide.<br/>
      &emsp;&emsp;2.2.5.9. <i>Max. Variable Mods</i>: Specify the maximum number of variable post-translational modifications in a single peptide.
      <div id="ref_2_2_5_10">&emsp;&emsp;2.2.5.10. <i> Enzyme</i>: Select a proteolytic enzyme for <i>in-silico</i> digestion.</div>
      &emsp;&emsp;&emsp;&emsp;2.2.5.10.1. <i> Add Enzyme</i>: Navigate to the <i>Enzymes</i> tab and click on ‘<i>Add Enzyme</i>’ button (<b>Figure 3a</b>). A new window will be opened (<b>Figure 3b</b>).<br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/14ee608a-dafa-464f-be3c-d01003b3c83f"><br/>
      <b>Figure 3a: Enzymes window – This tab enables the addition or removal of enzymes.</b><br/><br/>
      <img width="35%" alt="image" src="https://github.com/user-attachments/assets/54deb2c1-1e81-490c-8c81-6ee6353c7bf6"><br/>
      <b>Figure 3b: New Enzyme Inclusion – This window allows users to introduce a new enzyme to the existing list of enzymes.</b>
      </p>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.10.1.1. <i>Name</i>: Specify a name for the new enzyme.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.10.1.2. <i>Sites</i>: Specify the amino acids at which cleavage should occur. <i>PS: The amino acids should be included without spaces, for instance, the trypsin sites should appear as KR.</i><br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.10.1.3. <i>Blocked by</i>: Specify the amino acids that will impede the cleavage. <i>PS: As in ‘Sites’, the amino acids must be typed without spaces.</i><br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.10.1.4. <i>C-Terminal</i>: Check this option if the new enzyme cleaves at the C-terminus of the peptide; otherwise, cleavage will occur at the N-terminus.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Click on the ‘<i>Confirm</i>’ button to incorporate the new enzyme into the Enzymes table. Afterwards, return to <i><a href="#ref_2_2_5_10">2.2.5.10</a></i>.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.10.2 To remove an Enzyme, press ‘<i>Del</i>’ key. A confirmation message will be displayed. Confirm it to proceed.<br/><br/>
&emsp;&emsp;2.2.5.11. <i>Enzyme specificity</i>: Select an enzyme specificity from the list: full specific or semi-specific.<br/>
&emsp;&emsp;2.2.5.12. <i>Cleavable Reagent</i>: Select a cleavable cross-linker from the list.<br/>
&emsp;&emsp;&emsp;&emsp;2.2.5.12.1. <i>Add Reagent</i>: Go to XL Reagents tab and click on ‘<i>Add Reagent</i>’ button (<b>Figure 4a</b>). A new window will be opened (<b>Figure 4b</b>).<br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/b04ab7b4-6066-47b1-8e2c-dabb1eb326cc"><br/>
      <b>Figure 4a: Chemical cross-linkers window: on this tab, new reagents can be added or removed.</b><br/><br/>
      <img width="35%" alt="image" src="https://github.com/user-attachments/assets/3e2ffe0d-5d84-40ce-b3c5-3c6640f37eee"><br/>
      <b>Figure 4b: A new reagent can be added into the list of cross-linkers.</b>
      </p>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.12.1.1. <i>Name</i>: Specify a unique identifier for the new cleavable reagent.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.12.1.2. <i>Light Fragment Mass</i>: Specify the light fragment mass in Daltons.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.12.1.3. <i>Heavy Fragment Mass</i>: Specify the heavy fragment mass in Daltons.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.12.1.4. <i>Full Mass</i>: Specify the full mass of the reagent in Daltons.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.12.1.5. <i>Ion Pair Shift</i>: The pair will be automatically calculated according to the light and heavy fragment masses.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.12.1.6. <i>Target Residues</i>: Specify the target residues that the new cleavable cross-linker will react with. <i>PS: List residues without spaces; for example, use KSYT for DSSO.</i><br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.12.1.7. <i>N-Terminal</i>: Check this option if the new cleavable cross-linker also reacts at the N-terminus of the protein. <br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Click the ‘<i>Confirm</i>’ button to incorporate the new cleavable reagent into the XL Reagents table. Subsequently, return to <i><a href="#ref_2_2_5_10">2.2.5.10</a></i>.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.12.2 To remove an XL Reagent, press ‘<i>Del</i>’ key. A confirmation message will be displayed. Confirm it to proceed.<br/><br/>
      &emsp;&emsp;2.2.5.13. <i>Deconvolute for Ion Pair Searching</i>: Check this option to deconvolute the spectra before searching the ion pairs. If enabled, the deconvolution will be performed by YADA 3.0 [<a href="#lib_5">5</a>].<br/>
      &emsp;&emsp;2.2.5.14. <i>Deconvolute for Scoring</i>: Check this option to deconvolute spectra prior to searching for CSMs. If enabled, the deconvolution will be performed by YADA 3.0. [<a href="#lib_5">5</a>]<br/><br/>
      &emsp;&emsp;<b>Explanation on ‘<i>deconvolution</i>’:</b> As cleavable cross-linking search relies heavily on locating ion pairs, noisy spectra can be very harmful to the overall quality of end results. As such, spectra deconvolution is generally recommended, and set as default for the ion pair searching step of Scout. In mass spectrometry, deconvolution refers to the process of de-charging and/or deisotoping a spectrum. In practical terms, this is the process of iterating the MS2 searching looking for charge envelopes and isotopic envelopes, grouping them all into a single ion at charge +1. This is particularly important for the first step of Scout’s workflow, Ion Pair Doublet Searching, as we found that being too lenient with the search for ion pairs may lead to false positives.<br/><br/>
      &emsp;&emsp;2.2.5.15. <i>Add Modification</i>: Click on this button to add a new post-translational modification (<b>Figure 5a</b>). A new window will appear (<b>Figure 5b</b>).<br/>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/f28ad4f7-108a-4081-93c3-8471aeda43f9"><br/>
      <b>Figure 5a: Modification Window – This tab displays all variable and static modifications.</b><br/><br/>
      <img width="35%" alt="image" src="https://github.com/user-attachments/assets/03a4d35e-c7d4-4519-8948-b3958cae3312"><br/>
      <b>Figure 5b: New Modification Inclusion – This window enables the addition of a new modification into the modifications list.</b>
      </p>
      &emsp;&emsp;&emsp;&emsp;2.2.5.15.1. <i>Name</i>: Specify a unique name for the new post-translational modification.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.15.2. <i>Mass Shift</i>: Specify the mass shift in Daltons.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.15.3. <i>Target Residues</i>: Specify the target residues for this new post-translational modification. Use capital letters without spaces.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.15.4. <i>C-Terminal</i>: Check this option if the new post-translational modification occurs at the C-terminus of the peptide.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.15.5. <i>N-Terminal</i>: Check this option if the new post-translational modification occurs at the N-terminus of the peptide.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.15.6. <i>Variable</i>: Check this option if the new post-translational modification is dynamic, i.e., if it may or may not occur.<br/>
      &emsp;&emsp;&emsp;&emsp;Click on the ‘<i>Confirm</i>’ button to incorporate the new modification into the Modification table.<br/>
      &emsp;&emsp;&emsp;&emsp;<i><b>PS: Upon completing this process, ensure the new post-translational modification is checked in ‘<u>Use</u>’ field for it to be considered in the search.</b></i><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.15.7 To remove a modification, press the ‘<i>Del</i>’ key. A confirmation message will be displayed. Confirm the action to proceed.<br/><br/>
      &emsp;&emsp;2.2.5.16. <i>Contaminants</i>: On this tab, the current contaminants can be modified as well as new ones added (<b>Figure 6</b>). <i>PS: All contaminants must be entered in FASTA format (similar to item <a href="#ref_2_2_3">2.2.3</a>).</i>
      <p align="center"><br/><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/ae9bd24e-1224-451e-97b5-c41b4280dea6"><br/>
      <b>Figure 6: Contaminants tab: all contaminant sequences can be modified as well as new ones can be added.</b></p>
      <div id="ref_2_2_5_17">&emsp;&emsp;2.2.5.17. <i>Export</i>: Choose this option to save the current parameters to a file.</div>
      <div id="ref_2_2_5_18">&emsp;&emsp;2.2.5.18. <i>Load</i>: Select this option to import parameters from a file.</div>
      <div id="ref_2_2_5_19">&emsp;&emsp;2.2.5.19. <i>As default</i>: Set the current parameters as the software’s default settings.</div>
      <div id="ref_2_2_5_20">&emsp;&emsp;2.2.5.20. <i>Restore</i>: Revert to factory default parameters.</div>
      &emsp;&emsp;2.2.5.21. <i>Advanced</i>: Click on this link to customize the advanced parameters (not necessary for most searches). (<b>Figure 7</b>).
      <p align="center"><br/><img width="35%" alt="image" src="https://github.com/user-attachments/assets/3be5a12a-664b-402c-9d7d-b4f6c3a413c1"><br/>
      <b>Figure 7: Edit advanced parameters: In this window, all search parameters can be modified.</b></p>
      &emsp;&emsp;2.2.5.22. <b>Advanced Search Parameters</b><br/>
      <div id="ref_2_2_5_22_1">&emsp;&emsp;&emsp;&emsp;2.2.5.22.1. <i>Save spectra in results file</i>: Check this option to save the identified experimental spectra in the results file.<br/></div>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.2. <i>Add contaminants</i>: Check this option to consider common mass spectrometry contaminants during the search.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.3. <i>Add decoys</i>: Check this option to add decoys before initiating the search. Note: for the FDR calculation, this option should be checked.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.4. <i>Fasta batch size</i>: Specify the maximum number of protein sequences to be loaded into memory at a given time.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.5. <i>Fragment bin tolerance</i>: Specify the bin size for binning mass spectra and for theoretical mass spectra generation.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.6. <i>Fragment bin offset</i>: Specify offset in Daltons to be considered to initiate the binning process.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.7. <i>Minimum fragment bin m/z</i>: Specify the minimum m/z to be vectorized.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.8. <i>Maximum fragment bin m/z</i>: Specify the maximum m/z to be vectorized.<br/><br/>
      &emsp;&emsp;&emsp;&emsp;<b>Explanation on ‘<i>Binning</i>’</b>: We refer to binning mass spectra into vectors as the process of discretization of continuous m/z values by partitioning them into predefined bins. The process consists of establishing an offset (in Da) and a bin width (in Da) to define the initial point and bin size, respectively. Each bin encompasses a specific m/z range, and peaks are allocated to the corresponding bin based on their m/z value. Subsequently, the intensity values of peaks within each bin are aggregated, in our case, by summation. The output entails a vector of intensity values, with each entry representing a distinct bin. This vectorial representation streamlines mass spectral data manipulation and comparison, facilitating bioinformatics analyses. Therefore, the binning loosely refers to the MS/MS tolerance.<br/><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.9. <i>No. Isotopic Possibilities</i>: The precursor mass stored in raw data files may not correspond to the monoisotopic peak. This option allows the software to find the correct monoisotopic peak, which is required to identify the molecule but at the cost of opening up the search space. If a high number of isotopic possibilities is set, the search space will increase accordingly and impact Scout’s sensitivity negatively.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.10. <i>Metabolic labelling search</i>: Check this option to perform SILAC search.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.22.10.1 <i>Add Group</i>: A new window will open to add the groups for labelling peptides, e.g., heavy and light groups as well as their amino acids can be added in this feature.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.22.10.2 <i>Hybrid mode</i>: Check this option to find not only heavy-heavy / light-light peptides, but also heavy-light/light-heavy ones.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.11. <i>Isobaric labelling search</i>: Check this option to perform Isobaric labelling search (e.g., TMT, iTRAQ).<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.22.11.1 <i>Add Reagent</i>: A new window will open to set the reagent up.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.22.11.1.1 <i>Reagent</i>: Select a reagent. If the desired reagent is not in the list, click on the <i>'Add'</i> button.<br/>
      &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.2.5.22.11.1.2 <i>Free residue tolerance</i>: Set the minimum number of residues that TMT will not react.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.12. <i>Target-decoy fusion mode</i>: Check this option to perform a search integrating the target and decoy protein sequences into a single sequence.<br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.13. <i>Export</i>: See <i><a href="#ref_2_2_5_17">2.2.5.17</a>.</i><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.14. <i>Load</i>: See <i><a href="#ref_2_2_5_18">2.2.5.18</a>.</i><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.15. <i>As default</i>: See <i><a href="#ref_2_2_5_19">2.2.5.19</a>.</i><br/>
      &emsp;&emsp;&emsp;&emsp;2.2.5.22.16. <i>Restore</i>: See <i><a href="#ref_2_2_5_20">2.2.5.20</a>.</i><br/><br/>
      <div id="ref_2_2_6">&emsp;2.2.6 <b>Post Processing Parameters</b><br/></div>
      <p align="justify">&emsp;&emsp;&emsp;Adjusting certain post processing parameters may improve the performance of the process. To do this, navigate to Parameters &#8594; Post Processing (or use the keyboard shortcut ALT + P), as can be illustrated in <b>Figure 2a</b>. A new window will appear (<b>Figure 8</b>).</p>
      <p align="center"><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/8a683620-04db-4a0d-8906-45e1a443d23a"><br/>
      <b>Figure 8: Post Processing Parameters window</b></p>
      &emsp;&emsp;2.2.6.1. <i>Use only unique XLs into PPIs</i>: Check this option to remove PPIs that contain shared cross-linked peptides.<br/>
      &emsp;&emsp;2.2.6.2. <i>Separate protein intra- and inter-crosslinks</i>: Check this option to apply FDR control separately to intra- and inter-crosslinks at the CSM, Residue Pair, and PPI levels.<br/>
      &emsp;&emsp;2.2.6.3. <i>Group PPIs by gene</i>: Check this option to group all protein-protein interactions by gene name.<br/>
      &emsp;&emsp;2.2.6.4. <i>FDR on CSM level</i>: Specify the FDR on CSM level.<br/>
      &emsp;&emsp;2.2.6.5. <i>FDR on Residue Pair level</i>: Specify the FDR on Residue Pair level.<br/>
      &emsp;&emsp;2.2.6.6. <i>FDR on PPI level</i>: Specify the FDR on PPI level.<br/>
      &emsp;&emsp;<div id="ref_2_2_6_7">2.2.6.7. <i>Export</i>: Similar to <i><a href="#ref_2_2_5_17">2.2.5.17</a>.</i></div><br/>
      &emsp;&emsp;2.2.6.8. <i>Load</i>: Similar to <i><a href="#ref_2_2_5_18">2.2.5.18</a>.</i><br/>
      &emsp;&emsp;2.2.6.9. <i>As default</i>: Similar to <i><a href="#ref_2_2_5_19">2.2.5.19</a>.</i><br/>
      &emsp;&emsp;2.2.6.10. <i>Restore</i>: Similar to <i><a href="#ref_2_2_5_20">2.2.5.20</a>.</i><br/><br/>
  <div id="ref_2_3">2.3. <b>Results</b></div>
&emsp;&emsp;Upon completion of the search processing, the results are automatically saved in the same directory in which the RAW files are (<i><sup>*</sup>.scout file</i>) and presented in a new window with separate tabs: CSMs, Residue Pairs and PPIs, as well as the parameters used in the search. (<b>Figure 9</b>)
      <p align="center"><img width="65%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/1a309b27-a80e-49d1-8af4-0487cc90d5dc"><br/>
      <b>Figure 9: Results window.</b></p>
&emsp;&emsp;Double-clicking on a row containing a CSM result opens the spectrum viewer displaying the spectrum from which it was identified*. The sequence coverage (<b>Figure 10a</b>) and the standard deviation plot (<i>m/z vs ppm</i>) of all identified peaks (<b>Figure 10b</b>) can be visualized through this window as well as all fragment ions (<b>Figure 10c</b>). Double-clicking a cross-link opens a list of CSMs from which it is derived (<b>Figure 10d</b>). Double-clicking a PPI displays all cross-links belonging to the PPI (<b>Figure 10e</b>) and an additional click reveals all CSMs associated with the respective cross-link.<br/>
<i>*PS: The spectrum viewer will be opened if the RAW file is in the directory or the mass spectrum was saved in <sup>*</sup>.scout file (see item <a href="#ref_2_3_8">2.3.8</a>).</i>
      <p align="center"><br/><img width="55%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/049c95ec-036e-42a2-878d-b80611cef34a"><br/>
      <b>Figure 10a: Sequence coverage annotation & spectrum visualization.</b><br/><br/>
      <img width="55%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/74be95cd-4564-41be-94c8-606b20424b13"><br/>
      <b>Figure 10b: Standard deviation plot of all identified peaks.</b><br/><br/>
      <img width="55%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/3f12bb10-4160-49ca-b355-6f7a24164155"><br/>
      <b>Figure 10c: Theoretical fragment ions.</b><br/><br/>
      <img width="55%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/5c1fa346-16cc-4653-ae83-240ca506edbd"><br/>
      <b>Figure 10d: List of CSMs from a specific Residue Pair.</b><br/><br/>
      <img width="55%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/d4e583ab-80ab-40ef-aa58-e2a473f506ea"><br/>
      <b>Figure 10e: List of Residue Pairs from a specific PPI.</b>
      </p>
      &emsp;2.3.1 <b>Filter results</b>: Results contain FDR filtered identifications on all levels – in the graphical user interface, personal filters can be applied:</br>
      &emsp;&emsp;2.3.1.1. <b><i>CSM level</i></b>: In this tab (<b>Figure 9</b>), the CSMs are displayed according to the specified filter parameters.</br>
      &emsp;&emsp;&emsp;&emsp;2.3.1.1.1 <i>Scan</i>: Specify the scan number to be displayed.</br>
      &emsp;&emsp;&emsp;&emsp;2.3.1.1.2 <i>Score</i>: Specify the score cutoff. All CSMs with a score greater than ‘<i>Score</i>’ will be displayed.</br>
      &emsp;&emsp;&emsp;&emsp;2.3.1.1.3 <i>Search</i>: Type the &alpha; or/and &beta; peptide (separated by <i>'-'</i>) as well as the protein 1 or/and protein 2 (separated by <i>'-'</i>), or even gene 1 or/and gene 2 (separated by <i>'-'</i>) to be displayed. <i>PS: Type at least four characters</i>.</br>
      &emsp;&emsp;&emsp;&emsp;2.3.1.1.4 <i>Files</i>: Select the file(s) that the results to be displayed belong to. If no files or ‘<i>All files</i>’ is selected, all results will be displayed.</br>
      &emsp;&emsp;&emsp;&emsp;2.3.1.1.5 <i>Show inter-protein links only</i>: Check this option to display only the CSMs that belong to inter-protein interactions.</br>
      &emsp;&emsp;&emsp;&emsp;2.3.1.1.6 <i>Show decoys</i>: Check this option to display decoy identifications.</br>
      &emsp;&emsp;&emsp;&emsp;2.3.1.1.7 Click on ‘<i>Filter</i>’ button or press <i>Enter</i> to perform the filter.</br>
      &emsp;&emsp;&emsp;&emsp;2.3.1.1.8 Click on ‘<i>Reset</i>’ button to restore default result display.</br>
      &emsp;&emsp;&emsp;&emsp;2.3.1.1.9. <i>Summary</i>: In this box, the number of identified CSMs will be displayed as well as the calculated FDR.</br><br/>
      &emsp;&emsp;2.3.1.2. <b><i>Residue Pair level</i></b>: On this tab, the residue pairs will be displayed according to the specified filter parameters (<b>Figure 11</b>).</br>
      <p align="center"><br/><img width="55%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/1eaa24e7-20f4-482a-9b4f-ebbaa209065a"><br/>
      <b>Figure 11: Residue Pairs tab</b></p>
      &emsp;&emsp;&emsp;&emsp;2.3.1.2.1 <i>Score</i>: Specify the score cutoff. All Residue Pairs with a score greater than ‘Score’ will be displayed.<br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.2.2 <i>Search</i>: Type the &alpha; or/and &beta; (separated by <i>'-'</i>) peptide as well as the protein 1 or/and protein 2 (separated by <i>'-'</i>) or even gene 1 or/and gene 2 (separated by <i>'-'</i>) to be displayed. <i>PS: Type at least four characters.</i><br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.2.3 <i>Show inter-protein links only</i>: Check this option to display only the Residue Pairs that belong to inter-protein interactions.<br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.2.4 <i>Show decoys</i>: Check this option to display decoy identifications.<br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.2.5 Click on ‘<i>Filter</i>’ button or press <i>Enter</i> to perform the filter.<br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.2.6 Click on ‘<i>Reset</i>’ button to restore the results.<br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.2.7. <i>Summary</i>: In this box, the number of identified Residue Pairs will be displayed as well as the calculated FDR.<br/><br/>
      &emsp;&emsp;2.3.1.3. <b><i>PPI level</i></b>: On this tab, the PPIs will be displayed according to the specified filter parameters (<b>Figure 12</b>)
      <p align="center"><br/><img width="55%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/d79c669f-b8e5-4323-93d2-b3999644e6dc"><br/>
      <b>Figure 12: PPIs tab</b></p>
      &emsp;&emsp;&emsp;&emsp;2.3.1.3.1 <i>Score</i>: Specify the score cutoff. All PPIs with a score greater than ‘<i>Score</i>’ will be displayed.<br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.3.2 <i>Search</i>: Type protein 1 or/and protein 2 (separated by <i>'-'</i>) as well as gene 1 or/and gene 2 (separated by <i>'-'</i>) to be displayed. <i>PS: Type at least four characters.</i><br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.3.3 <i>Show inter-protein links only</i>: Check this option to display only the identifications that belong to inter-protein interactions.<br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.3.4 <i>Show decoys</i>: Check this option to display decoy identifications.<br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.3.5 <i>Group PPIs by gene</i>: Check this option to group all protein-protein interactions by gene name.<br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.3.6 Click on ‘<i>Filter</i>’ button or press <i>Enter</i> to filter the results.<br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.3.7 Click on ‘<i>Reset</i>’ button to restore the results.<br/>
      &emsp;&emsp;&emsp;&emsp;2.3.1.3.8. <i>Summary</i>: in this box, the number of identified PPIs will be displayed as well as the calculated FDR.<br/><br/>
      <div id="ref_2_3_2">&emsp;&emsp;2.3.2 <b><i>Parameters</i></b>: Both search and post processing parameters used in the search can be visualized on this tab. (<b>Figure 13a and b</b>)</div>
      <p align="center"><br/><img width="30%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/bb7bb3b4-1a8f-44e6-afea-d2a457c70212">&emsp;<img width="29.95%" alt="image" src="https://github.com/user-attachments/assets/a1e6e959-77ee-4ab5-968c-d9067815c471"><br/>
      <b>Figure 13: Search and post processing parameters can be visualized on this tab (Figure 13a and 13b, respectively).</b></p>
      &emsp;&emsp;2.3.2.1 <b>Post processing parameters</b>: The parameters used to perform FDR on CSM, Residue Pair and PPI levels can be modified to improve the results. To do so, click on <i>'Edit'</i> button and change the parameters (<b>Figure 13 b</b>) (<i>Similar to <a href="#ref_2_2_6">2.2.6</a></i>). Afterwards, a new filter will be performed.<br/><br/>
      &emsp;2.3.3 <b>Open Results</b>: New Scout results can be opened (<i>*.scout file</i>). To do so, go to File &#8594; Open Results (or press CTRL + O), as can be seen in <b>Figure 14a</b>. <i>PS: Multiple files can be opened if all of them used the same parameters in the search</i>.<br/>
      &emsp;&#8658; Results can also be opened from the Scout starting page by clicking on File menu &#8594; Open Results (or pressing CTRL + O).<br/><br/>
      &emsp;2.3.4 <b>Save Results</b>: The current results can be saved to preserve them. To do so, go to File &#8594; Save &#8594; Results (or press CTRL + S), as can be seen in <b>Figure 14a</b>.
      <p align="center"><br/><img width="35%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/6d18e873-7936-4c0f-b5fe-d957c80ff505"><br/>
      <b>Figure 14a: Open and Save results as well as the parameters used in the search.</b></p>
      &emsp;&emsp;2.3.4.1 <b>Save Results as mzIdentML file</b>: The current results can also be saved in mzIdentML 1.2 or mzIdentML 1.3 format. To do so, after going to ‘<i>Save Results</i>’, a new window will open ('<i>Save as</i>'), then change ‘<i>Save as type</i>’ to mzIdentML 1.2 (or 1.3) Result File (<i>.mzid</i>), as can be seen in <b>Figure 14b</b>. Type a file name and click on '<i>Save</i>' (or press enter).<br/>
      &emsp;&emsp;&#8658; <i>PS: Besides the mzIdentML file, a *-specID.ms2 file will also be saved, which holds all the identified MS/MS spectra. Both files are required to proceed with the 'Complete Submission' in the PRIDE[<a href="#lib_1">1</a>] system.</i>
      <p align="center"><br/><img width="45%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/22e7d726-8b2d-496a-b504-ab707fc8a065"><br/>
      <b>Figure 14b: Save the results in mzIdentML 1.2 or mzIdentML 1.3 format.</b></p>
      &emsp;2.3.5 <b>Save Parameters</b>: the search and post processing parameters used in the search can be exported. To do so, go to File &#8594; Save &#8594; Parameters (or press ALT + W), as can be seen in <b>Figure 15</b>.<br/><br/>
      &emsp;2.3.6 <b>Report</b>: Scout allows to export displayed reports, such as CSMs (filtered results), Residue Pairs, PPIs and unfiltered CSMs as well as the import file used on XlinkCyNET to visualize the protein-protein interaction network. (<b>Figure 15</b>)
      <p align="center"><br/><img width="45%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/ca034b3c-5a8e-46c8-930b-b861e421a5c3"><br/>
      <b>Figure 15: Export reports as well as the input file used on XlinkCyNET.</b></p>
      &emsp;2.3.7 <b>Reprocess FDR</b>: The results can be filtered again by using the current post-processing parameters (that can be modified, see item <i><a href="#ref_2_3_2">2.3.2</a></i>). To do so, go to Tools &#8594; Reprocess FDR (or press ALT + F).(<b>Figure 16</b>)
      <p align="center"><br/><img width="30%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/8933dd8e-bcae-4f40-afe2-252abe0dd7d4"><br/>
      <b>Figure 16: Reprocess FDR, Import spectra and Statistical analysis features accessed by Tools menu.</b></p>
      <div id="ref_2_3_8">&emsp;2.3.8 <b>Import Spectra</b>: If the option ‘<i>Save spectra in results file</i>’ is unchecked (see item <i><a href="#ref_2_2_5_22_1">2.2.5.22.1</a></i>), the identified spectra will not be displayed if the RAW file is not present in the same directory of the results. To import the identified spectra, go to Tools &#8594; Import Spectra (or press CTRL+ I) and specify where the RAW files are. (<b>Figure 16</b>)<br/><br/></div>
      &emsp;2.3.9 <b>Statistics</b>: The user can obtain some statistical analysis from the results, such as, the precursor charge distribution (<b>Figure 17a</b>) as well as reaction sites distribution (<b>Figure 17b</b>) based on the identified cross-links. To do so, go to Tools &#8594; Statistical analysis (or press CTRL + Y). (<b>Figure 16</b>)<br/><br/>
      <p align="center"><img width="55%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/7876ba52-2f92-41b2-a8f3-90470ce390a4"><br/>
      <b>Figure 17a: Precursor charge distribution of the identified cross-links.</b><br/><br/>
      <img width="55%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/449c0ee6-8c05-44ef-bc1a-9c457d264b57"><br/>
      <b>Figure 17b: Reaction sites distribution taking into account all identified cross-links.</b>
      </p>
  2.4. <b>Filter from the Scout starting page</b><br/>
  <p align="justify">&emsp;&emsp;The results can be filtered again with a different FDR from the one that was used for the first round by I) switching to the tab ‘<i>Filter</i>’; II) specifying the FASTA file; III) selecting the folder that contains the identification files (<i>*.buf</i>); IV) selecting the folder where the new resuts will be saved; V) modifying the post-processing parameters (see item <i><a href="#ref_2_2_6">2.2.6</a></i>); and clicking on ‘<i>Filter</i>’ button (<b>Figure 18</b>). When the filter is finished, a result window opens (see item <i><a href="#ref_2_3">2.3</a></i>).</p>
  &emsp;&#8658; To stop the filter, click on <i>'Cancel'</i> button and confirm.<br/><br/>
  <p align="center"><img width="55%" alt="image" src="https://github.com/user-attachments/assets/b6269a1e-09bc-498c-b1a0-5ac09e7b43e3"><br/>
  <b>Figure 18: Filter tab window</b></p><br/>
  2.5. <b>Check for updates</b><br/>
  <p align="justify">&emsp;&emsp;Scout checks for updates on software startup. Additionally, on Help &#8594; Check for updates, the user can visualize all releases (and their notes) as well as whether Scout is updated. If the current Scout version is not up-to-date, users will have the option to update within this window. (<b>Figure 19</b>)</p>
  <p align="center"><img width="25%" alt="image" src="https://github.com/diogobor/Scout/assets/7681148/58dabec2-a326-43da-b0a4-c2229662d5e8"><br/>
  <b>Figure 19: Check for updates window.</b></p><br/>
  <div id="ref_2_6">2.6. <b>Automation</b><br/>
   &emsp;&emsp;Scout supports automation from command line.<br/><br/>
     2.6.1. To do so, open a Terminal (press Win+R, type <i>cmd</i> and press enter).<br/>
     &emsp;&emsp;2.6.1.1 Navigate to the directory where <i>Scout</i> has been installed, <i>e.g.</i>, cd C:\Program Files\Scout.<br/>
     2.6.2 To start a search, the following arguments are required:<br/>
     &emsp;&emsp;2.6.2.1 <code>scout.exe -search search_params_file.json filter_params_file.json</code>.<br/>
     &emsp;&emsp;&emsp;&emsp;2.6.2.1.1 In <code>search_params_file.json</code>, the following parameters must be filled:<br/>
     <div id="ref_2_6_2_1_1_1">&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.6.2.1.1.1 <b><i>FastaFile</i></b>: The database file needs to be defined with its directory, <i>e.g., C:\my_search\my_db.fasta</i>.</div>
     &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.6.2.1.1.2 <b><i>RawPath</i></b>: The raw file(s) need(s) to be defined with its directory, <i>e.g., C:\my_search\my_raw_file.raw</i>. Multiple raw files must be separeted with ';', <i>e.g., C:\my_search\my_raw_file_1.raw;C:\my_search\my_raw_file_2.raw;C:\my_search\my_raw_file_3.raw</i>. A folder where the raw files are can be defined instead of raw file(s). In this case, define only the directory, <i>e.g., C:\my_search</i>.<br/>
     <div id="ref_2_6_2_1_1_3">&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.6.2.1.1.3 <b><i>OutputFolder</i></b>: Define a folder where the results will be saved, <i>e.g., C:\my_search\results</i>.</div>
     &emsp;&emsp;&emsp;&emsp;&#8658; The <code>search_params_file.json</code> can be generated according to <a href="#ref_2_2_5_17">2.2.5.17</a>.<br/>
     <div id="ref_2_6_2_1_2">&emsp;&emsp;&emsp;&emsp;2.6.2.1.2 In <code>filter_params_file.json</code>, the following parameters must be filled:</div>
     &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;2.6.2.1.2.1 <b><i>CSM_FDR</i>, <i>ResPair_FDR</i>, <i>PPI_FDR</i></b>: The FDR values need to be defined with a value between 0 and 1.<br/>
     &emsp;&emsp;&emsp;&emsp;&#8658; The <code>filter_params_file.json</code> can be generated according to <a href="#ref_2_2_6_7">2.2.6.7</a>.<br/><br/>
     &emsp;&emsp;&emsp;&emsp;&#8658; Once the search starts, a log file will be generated in the output folder.<br/><br/>
     2.6.3 To filter only the results, the following arguments are required:<br/>
     &emsp;&emsp;2.6.3.1 <code>scout.exe -filter filter_params_file -fasta fasta_file -i path_search_result_files -o path_to_output_files</code>.<br/>
     &emsp;&emsp;&emsp;&emsp;2.6.3.1.1 <code>filter_params_file.json</code>: Similar to <a href="#ref_2_6_2_1_2">2.6.2.1.2</a><br/>
     &emsp;&emsp;&emsp;&emsp;2.6.3.1.2 <code>fasta_file</code>: Similar to <a href="#ref_2_6_2_1_1_1">2.6.2.1.1.1</a><br/>
     &emsp;&emsp;&emsp;&emsp;2.6.3.1.3 <code>path_search_result_files</code>: Define a directory where the search resuts files (*.buf) are.<br/>
     &emsp;&emsp;&emsp;&emsp;2.6.3.1.4 <code>path_to_output_files</code>: Similar to <a href="#ref_2_6_2_1_1_3">2.6.2.1.1.3</a><br/>
     
  </div>

# Closing remarks
  <p>&emsp;&emsp;In conclusion, Scout is a powerful tool for identifying protein-protein interactions using cleavable cross-linkers in proteomic datasets. Its user-friendly interface, customizable search and post-processing parameters, and multiple filtering options make it a versatile tool for protein interaction analysis. Scout can be particularly useful for studying complex biological systems when identifying protein-protein interactions is crucial for understanding their function.  Overall, Scout provides a valuable resource for researchers interested in studying protein-protein interactions at a large scale.</p>

# References
<div id="lib_1">[1]	J. A. Vizcaíno et al., “The PRoteomics IDEntifications (PRIDE) database and associated tools: status in 2013,” Nucleic Acids Res., vol. 41, no. Database issue, pp. D1063-1069, Jan. 2013, doi: <a href="https://doi.org/10.1093/nar/gks1262" target="_blank">10.1093/nar/gks1262</a>.</div>
<div id="lib_2">[2]	Y. Perez-Riverol et al., “PRIDE Inspector Toolsuite: Moving Toward a Universal Visualization Tool for Proteomics Data Standard Formats and Quality Assessment of ProteomeXchange Datasets,” Mol. Cell Proteomics, vol. 15, no. 1, pp. 305–317, Jan. 2016, doi: <a href="https://doi.org/10.1074/mcp.O115.050229" target="_blank">10.1074/mcp.O115.050229</a>.</div>
<div id="lib_3">[3]	D. B. Lima, Y. Zhu, and F. Liu, “XlinkCyNET: A Cytoscape Application for Visualization of Protein Interaction Networks Based on Cross-Linking Mass Spectrometry Identifications,” J. Proteome Res., vol. 20, no. 4, pp. 1943–1950, Apr. 2021, doi: <a href="https://doi.org/10.1021/acs.jproteome.0c00957" target="_blank">10.1021/acs.jproteome.0c00957</a>.</div>
<div id="lib_4">[4]	P. Shannon et al., “Cytoscape: A Software Environment for Integrated Models of Biomolecular Interaction Networks,” Genome Res., vol. 13, no. 11, pp. 2498–2504, Nov. 2003, doi: <a href="https://doi.org/10.1101/gr.1239303" target="_blank">10.1101/gr.1239303</a>.</div>
<div id="lib_5">[5]	M. A. Clasen et al., “Increasing confidence in proteomic spectral deconvolution through mass defect,” Bioinformatics, vol. 38, no. 22, pp. 5119–5120, Nov. 2022, doi: <a href="https://doi.org/10.1093/bioinformatics/btac638" target="_blank">10.1093/bioinformatics/btac638</a>.</div>
