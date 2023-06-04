# Selection of Antibodies Humanized by Scaffolding

Done by Nikita Vyatkin

This project aims to implement an in silico method for predicting humanized monoclonal antibody (mAb) candidates with high binding affinities based on their behavior in molecular dynamics (MD) simulations. The project is supervised by Georgii Mamistvalov, Natalia Zenkova, and Vladislav Strashko from BIOCAD.

## Introduction

The development of therapeutic mAbs is an important area of research in the field of biotechnology. However, the use of murine mAbs in humans can lead to immune responses that reduce the efficacy and safety of the treatment. Humanization of murine mAbs is therefore necessary to reduce the immunogenicity and improve the efficacy of therapeutic mAbs. In this project, we aim to use MD simulations to predict humanized mAb candidates with high binding affinities.

## Goal and objectives of the project
**Goal:** To implement an in silico method for predicting humanized candidates with a high binding affinity based on their behavior in molecular dynamics simulations.

**Objectives:**
* Read articles on the topic, study the MD simulation method, master the tools: PyMOL, VMD, GROMACS
* Collect data: structures of mouse antibodies (anti-TNF-α, anti-EGFR, anti-GPC3, etc.) and sequences of humanized candidates
* Build 3D structures of humanized mAb candidates and run molecular dynamics simulations
* Analyze the obtained trajectories, calculate metrics (wRMSD) and compare them with the results from the article (Hsieh et al., 2022)

## Methodology

To predict humanized monoclonal antibody (mAb) candidates with high binding affinities, we developed an in silico method which based on comparing the complementarity-determining regions (CDRs) between mouse mAbs and their humanized candidates using homology modeling and molecular dynamics (MD) simulation. Here is an overview of the steps involved:

1. Collect data: We obtained the structure of mouse antibody (anti-TNF-α) and sequences of humanized candidates.

2. Build 3D structures of humanized mAb candidates: We used ABodyBuilder to build the 3D structures of humanized mAb candidates based on the sequence data.

3. Run molecular dynamics simulations: We used GROMACS to perform all-atom MD simulations.

4. Analyze the obtained trajectories: We calculated the root-mean-square deviation (RMSD) between the candidate antibody and the reference antibody and used this to calculate the weighted RMSD (wRMSD) based on the accessibility and movability of each residue.

This method could significantly reduce the time and cost required for selecting suitable human mAb templates and subsequent back mutations and help in predicting humanized candidates with high binding affinities, leading to the development of more effective therapeutic mAbs.

### Molecular Dynamics Simulation using GROMACS

**Code in** `md_simulations/MD_pipeline.ipynb` 

We have provided a Jupyter Notebook `MD_pipeline` that contains the full pipeline for molecular dynamics simulations for this project. The notebook is available in .ipynb format and can be found in the `md_simulations/` directory.

The notebook uses Gromacs, a popular package for molecular dynamics simulations, and includes all the necessary steps for setting up and running simulations for humanizing the murine antibody. The notebook is organized into sections that correspond to the different stages of the pipeline, including environment setup, system generation, energy minimization, equilibrations, production run, trajectory processing, SASA calculation, and movability calculation. 

The notebook also includes detailed comments and explanations for each step, making it easy to follow and understand. It is recommended that you go through the notebook carefully before attempting to run any simulations.

To use the notebook, you will need to have Gromacs installed on your system. You will also need to provide the necessary input files, including the PDB structure file for the antibody. Once you have set up the necessary files and directories, you can run the notebook and follow the instructions provided.

### wRMSD Calculation

**Code in** `wRMSD_calculation.ipynb` 

The wRMSD_calculation notebook is a Jupyter Notebook that analyzes the results of molecular dynamics simulations of antibody molecules. It calculates the root-mean-square deviation (RMSD) between the candidate antibody and the reference antibody and uses this to calculate the weighted RMSD (wRMSD) based on the accessibility and movability of each residue. The notebook requires the MDAnalysis library to be installed.

You can find the notebook in the parent directory.

To run the notebook, you need to have the following files in the md_simulations/remicade_humanization directory:

Structures:
- remicade/structures/newbox.gro
- candidate_Aa/structures/newbox.gro
- candidate_Bb/structures/newbox.gro
- candidate_Cb/structures/newbox.gro

and trajectories:
- remicade/prod_0_80/prod_0_80_noPBC_center.xtc
- candidate_Aa/prod_0_80/prod_0_80_noPBC_center.xtc
- candidate_Bb/prod_0_80/prod_0_80_noPBC_center.xtc
- candidate_Cb/prod_0_80/prod_0_80_noPBC_center.xtc

The notebook reads the SASA and RMSF values from the `sasa_0_80.xvg` and `rmsf_0_80.xvg` files, respectively. They located in `md_simulations/remicade_humanization/remicade/analysis` directory and can be reproduced by `MD_pipeline` notebook. The read_xvg_file function in the notebook reads the data from these files.

## Data Collection and Preparation

In this section, we describe the data collection and preparation steps. We obtained the structures of murine mAbs from the Protein Data Bank (PDB) and the sequences of their humanized candidates from the article (Hsieh et al., 2022). We used PyMOL, VMD and ABoduBuilder to prepare the structures and GROMACS to prepare the input files for the MD simulations.

## Results

We performed molecular dynamics simulations of several humanized monoclonal antibody (mAb) candidates and compared their behavior with that of the original murine mAb. Here are some of our findings:

### RMSF
The root-mean-square-fluctuation (RMSF) is used to determine the movability weights. Figure 1 shows the RMSF plot for the original murine mAb, which indicates the fluctuation of the Cα atoms.

![RMSF Plot](presentation/rmsf_80ns.png)
*Figure 1: RMSF plot showing the fluctuation of the Cα atoms of the original murine mAb.*

### wRMSD

We calculated the weighted root-mean-square-deviation (wRMSD) between the humanized mAb candidates and the original murine mAb to evaluate their similarity. Smaller wRMSD values are indicative of a more similar behavior of the humanized candidate to the murine antibody. Figure 2 shows the wRMSD density plot and the wRMSD plot for one of the humanized candidates.

![wRMSD density](presentation/wRMSD_density.png)

*Figure 2: wRMSD density plot showing the distribution of wRMSD values for one of the humanized candidates.*

![wRMSD](presentation/wRMSD_plot.png)

*Figure 3: wRMSD plot showing the similarity between one of the humanized candidates and the original murine mAb over time.*

## Significance and Implications

Our results demonstrate the feasibility of using MD simulations to predict humanized mAb candidates with high binding affinities. This can significantly reduce the time and cost required for selecting suitable human mAb templates and subsequent back mutations. Our method can also help in predicting humanized candidates with high binding affinities, leading to the development of more effective therapeutic mAbs.

## Acknowledgments

I would like to thank Georgii Mamistvalov, Natalia Zenkova, and Vladislav Strashko from BIOCAD for their supervision and support.
