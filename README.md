# DIVE-MAP: Cell DIVE Multiplex Analysis Pipeline

The Cell DIVE Multiplex Analysis Pipeline (DIVE-MAP) is a combination of scripts, notebooks and containers to make cell segmentation, clustering, analysis and interpretation of multiplex images produced by the Cell DIVE microscopy more straightforward.

To achieve this we make use of GPU-accelerated cell segmentation as well as various different existing analysis pipelines. We provide a set of repositories that make use of `Singularity` containers to deploy both in-house developed code as well external pipelines and libraries in a consistent and reproducible manner.

## System requirements
These containers have been tested to work with Ubuntu 22.04 LTS installed under the Windows Subsystem for Linux (WSL).


## 1. Whole slide image segmentation
One of the initial steps of computational image analysis is whole cell segmentation. To make cell segmentation using `DeepCell` possible for larger (> 10000px X 10000px) Cell DIVE images we developed a tiled segmentation approach on top of `Deepcell`. This `Deepcell` segmentation pipeline for Cell DIVE images is available here: https://github.com/KIR-CellDIVE/wsi-segmentation


## 2. Analysis
### 2.1 Ark analysis pipeline

Originally developed for the MIBIscope, the `ark-analysis` (https://github.com/angelolab/ark-analysis) toolbox is primarily focussed to work on multiple smaller FOVs from the same slide rather than on whole slide images. However, the whole slide image segmentation in the previous step (https://github.com/KIR-CellDIVE/wsi-segmentation) produces an `ark-analysis`-compatible file and folder structure, a segmentation mask and per-cell statistic which can be plugged into their analysis flow starting from the ["Pixel clustering with pixie" notebook](https://github.com/angelolab/ark-analysis#2-pixel-clustering-with-pixie).

To make setting up the `ark-analysis` toolbox similar to the whole slide segmentation in the previous step and also deployable on an HPC system we have created a `Singularity` container with setup instructions: https://github.com/KIR-CellDIVE/wsi-analysis-ark (WORK IN PROGRESS).



### 2.2 Generic WSI pipeline [WIP]
A work-in-progress to make the analysis workflow presented by Korsunsky et al. ([paper](https://doi.org/10.1016%2Fj.medj.2022.05.002)/[github](https://github.com/immunogenomics/fibroblastatlas2022)) more generally accessible to be used for the clustering, phenotyping and analysis of Cell DIVE images. The `Singularity` container  will be available at https://github.com/KIR-CellDIVE/wsi-analysis.


### 2.3 SpOOx - Spatial Omics Oxford analysis pipeline [WIP]
This pipeline (https://github.com/Taylor-CCB-Group/SpOOx/) was developed at the University of Oxford aiming to comprehensively analyse spatial proteomics data. It was primarily built for data produced by the Fluidigm Hyperion Imaging System. However, we are working on an integration in order to make the analysis of large Cell DIVE images possible.





## 3. Visualisation
### 3.1 MDV - Multi Dimensional Viewer
The [Multi Dimensional Viewer](https://github.com/Taylor-CCB-Group/MDV) is a powerful web based application for visualising, exploring and analysing multidimensional data such as multiplex microscopy images. The application is also developed at the University of Oxford. The output produced by the SpOOx pipeline (https://github.com/Taylor-CCB-Group/SpOOx/) can be readily plugged into the MDV for visualisation. The other analysis workflows come with their own set of visualisation tool but it would be possible to transform their output into an MDV-compatible format (but this is outside the scope of this work at this moment in time).



## How to cite
Please, directly cite the respective projects and papers referenced in the above section. 
