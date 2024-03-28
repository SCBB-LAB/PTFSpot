# PTFSpot

<p align="center">
  <img src="logo.png" style="width:80%; height: 450px; " />
</p>


## Description

<i><b>PTFSpot</b></i>: Deep co-learning on transcription factors and their binding regions attains impeccable universality in plants.

Unlike animals, variability in transcription factors (TF) and their binding regions (TFBR) across the plants species is a major problem which most of the existing TFBR finding software fail to tackle, rendering them hardly of any use. This limitation has resulted into underdevelopment of plant regulatory research and rampant use of Arabidopsis like model species, generating misleading results. Here we report a revolutionary transformers based deep-learning approach, PTFSpot, which learns from TF structures and their binding regions co-variability to bring a universal TF-DNA interaction model to detect TFBR with complete freedom from TF and species specific models’ limitations. During a series of extensive benchmarking studies over multiple experimentally validated data, it not only outperformed the existing software by >30% lead, but also delivered consistently >90% accuracy even for those species and TF families which were never encountered during model building process. PTFSpot makes it possible now to accurately annotate TFBRs across any plant genome even in the total lack of any TF information, completely free from the bottlenecks of species and TF specific models.

## Architecture

<p align="center">
  <img src="Figure.png" style="width:70%; height: 900px; " />
</p>


<b>Figure: Implementation of the PTFSpot Deep Co-learning system using Transformers and DenseNet to identify TF binding regions across plant genomes.</b> The first part is a 14 heads attention transformers which learn from the dimeric, pentameric and heptameric words representations of any given sequence arising from anchoring prime motif’s context. In the parallel, the bound TF’s structure is learned by the DenseNet. Learning by both partners are joined finally together, which is passed on to the final fully connected layers to generate the probability score for existence of binding region in the center.


## Web server

PTFSpot can be used directly from [this](https://scbb.ihbt.res.in/PTFSpot) web-server. This server implements trained models and can process both individual sequences or fasta files. Also, a tutorial is hosted on the [PTFSpot](https://scbb.ihbt.res.in/PTFSpot/implement.php) web-server.

## Package installation

The latest version of the package can be downloaded from the GitHub [repository](https://github.com/SCBB-LAB/PTFSpot).

## Requirements

1. Python3.6 or higher
2. Numpy==1.23.5
3. keras==2.13.1
4. tensorflow==2.13.1
5. plotly==5.11.0
6. pandas==1.5.0
7. bayesian-optimization==1.2.0
8. bedops (sudo apt-get install bedops -y)
9. Bedtools (sudo apt-get install bedtools -y)

## File description

```
1. hyper_param.py = Python script build model implementing hyperparameter tuning
2. file_for_tuning: file containing label (0/1) and sequence (positive and negative instances). All in one line separated by tab for a single instance.
3. genomic_sequence = example fasta sequence.
4. PTFSpot.sh = Shell execution script.
5. bimodal.h5  = Universal Transformer-DenseNet System.
6. pdbpar.py = pdb file parser
7. ptfspot.py = universal model script
```

## Note


Always place your Alphafold2 generated TF pdb file in "pdb" folder (An example is provided).<br>
This project was executed within the Ubuntu Linux platform's Open Source OS environment.


## To build model implementing hyperparameter tuning

```
python3 hyper_param.py file_for_tuning

file_for_tuning: file containing label (0/1) and sequence (positive and negative instances). All in one line separated by tab for a single instance.
```

## Running script

Module: Transformer-DenseNet system (identify TF binding regions within sequence with the corresponding Alphafold2 generated TF protein structure)
To detect the TF binding region, In parent directory execute following command:
```
unzip deeptfactor.zip
chmod a+x PTFSpot.sh
sh PTFSpot.sh <fasta file> <folder path> <Alphafold generated PDB file> <folder path of PTFSpot>
eg: sh PTFSpot.sh genomic_sequence folderpath ABF2 /home/user/PTFSpot

To generate line plot, execute the following command:
python3 make-plot.py seq1.csv (filename) (generated plots are interactive)
```

## Output description

TFBS detection module gives output in following format 

1. ABF1_genomic_sequence.txt = TF binding regions result


## Citation

Citation: Gupta S, Kesarwani V, Bhati U, Jyoti, Shankar R (2024) Deep co-learning on transcription factors and their binding regions attains impeccable universality in plants. bioRxiv 2024. <a href="https://doi.org/10.1101/2023.11.16.567355">Read research article here</a>.

