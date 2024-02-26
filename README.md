# PTFSpot

<p align="center">
  <img src="logo.png" style="width:80%; height: 450px; " />
</p>


## Description

<b>PTFSpot</b>: Deep co-learning on transcription factors and their binding regions attains impeccable universality in plants.
<br><br>
Unlike animals, variability in transcription factors (TF) and their binding sites (TFBS) across the plants species is a major problem which most of the existing TFBS finding software fail to tackle, rendering them hardly of any use. This limitation has resulted into underdevelopment of plant regulatory research and rampant misuse of Arabidopsis models, generating misleading results. Here we report a ground-breaking transformers based deep-learning approach, PTFSpot, which learns from TF structures and their binding sites to bring a universal TF-DNA interaction model. During a series of extensive bench-marking studies, it not only outperformed the existing software by >30% lead, but also delivered consistently >90% accuracy even for those species and TF families which were never encountered during model building process. PTFSpot makes it possible now to accurately annotate TFBS across novel plant genomes even in the total lack of any TF information.


## Architecture

<p align="center">
  <img src="Figure.png" style="width:70%; height: 900px; " />
</p>


<b>Figure: Implementation of the PTFSpot Deep Co-learning system using Transformers and DenseNet to identify TF binding regions across plant genomes.</b> The first part is a 14 heads attention transformers which learn from the dimeric, pentameric and heptameric words representations of any given sequence arising from anchoring prime motif’s context. In the parallel, the bound TF’s structure is learned by the DenseNet. Learning by both partners are joined finally together, which is passed on to the final fully connected layers to generate the probability score for existence of binding region in the center.


## Web server

PTFSpot can be used directly from [this](https://scbb.ihbt.res.in/PTFSpot) web server. This server implements trained model and can process both individual sequences or fasta files.

## Package installation

The latest version of the package can be downloaded from the GitHub [repository](https://github.com/SCBB-LAB/PTFSpot).

## Requirements
```
1. Python3.6 or higher
2. python module Numpy, keras, tensorflow, plotly, pandas, bayesian-optimization
3. bedops (sudo apt-get install bedops)
4. Bedtools (sudo apt-get install bedtools)
5. Alphafold2 (https://alphafold.ebi.ac.uk/) generated PDB files 
```

## File description
```
1. hyper_param.py = Python script build model implementing hyperparameter tuning
2. file_for_tuning: file containing label (0/1) and sequence (positive and negative instances). All in one line separated by tab for a single instance.
3. PTFSpot.py = Python script for detecting binding regions from sequences provided.
4. genomic_sequence = dummy fasta sequence.
5. M2 = Execution script.
6. bimodal.h5  = Universal Transformer-DenseNet System (Sequence and [Alphafold2](https://alphafold.ebi.ac.uk/) generated PDB file).
7. pdbpar.py = pdb file parser
8. ptfspot.py = universal model script
```

## Note

Always place your Alphafold2 (https://alphafold.ebi.ac.uk/) generated TF pdb file in "pdb" folder (an example is provided).


## To build model implementing hyperparameter tuning

```
python3 hyper_param.py file_for_tuning

file_for_tuning: file containing label (0/1) and sequence (positive and negative instances). All in one line separated by tab for a single instance.
```

## Running script

To detect the TF binding region, In parent directory execute following command:
Module: Transformer-DenseNet system (identify TF regions within sequence with the corresponding aplhafold2 generated TF protein structure)
```
unzip deeptfactor.zip
sh PTFSpot.sh <fasta file> <folder path> <Alphafold2 generated PDB file> <folder path of PTFSpot>
eg: sh PTFSpot.sh genomic_sequence folderpath ABF2 /home/user/PTFSpot

To generate line plot, execute the following command:
python3 make-plot.py seq1.csv (filename) (generated plots are interactive)
```

## Output description

TFbinding regions detection module gives output in following format 

1. ABF2_genomic_sequence.txt = TF binding regions result (Final result: ID, Start, End)


## Citation

Citation: Gupta S, Kesarwani V, Bhati U, Jyoti, Shankar R (2024) Deep co-learning on transcription factors and their binding regions attains impeccable universality in plants. bioRxiv 2024. <a href="https://doi.org/10.1101/2023.11.16.567355">Read research article here</a>.
