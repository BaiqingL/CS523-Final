# CS 523-Final
Final project submission for BU CAS CS 523

Dataset can be downloaded here: https://www.kaggle.com/mateuszbuda/lgg-mri-segmentation



#### Our goal:



#### Describe dataset:
The dataset contains brain MR images together with manual FLAIR abnormality segmentation masks.
The images were obtained from The Cancer Imaging Archive (TCIA).
They correspond to 110 patients included in The Cancer Genome Atlas (TCGA) lower-grade glioma collection with at least fluid-attenuated inversion recovery (FLAIR) sequence and genomic cluster data available.
Tumor genomic clusters and patient data is provided in data.csv file.

All images are provided in .tif format with 3 channels per image.
For 101 cases, 3 sequences are available, i.e. pre-contrast, FLAIR, post-contrast (in this order of channels).
For 9 cases, post-contrast sequence is missing and for 6 cases, pre-contrast sequence is missing.
Missing sequences are replaced with FLAIR sequence to make all images 3-channel.
Masks are binary, 1-channel images.
They segment FLAIR abnormality present in the FLAIR sequence (available for all cases).

The dataset is organized into 110 folders named after case ID that contains information about source institution.
Each folder contains MR images with the following naming convention:

TCGA<institution-code><patient-id>_<slice-number>.tif

Corresponding masks have a _mask suffix.


#### Rough Ideas:

We want to first filter the 
We plan to implement a network and training strategy that relies on the strong use of data augmentation to use the available annotated samples more efficiently. The general architecture consists of a contracting path to capture the picture of tumors and a symmetric expanding path that enables the localization of where the tumors are.

In many visual tasks, especially in biomedical image processing, the desired output should include localization, i.e., a class label is supposed to be assigned to each pixel to indicate where exists the tumor. Therefore, we use a network in a sliding-window setup to predict the class label of each pixel by providing a local region (patch) around that pixel. In this "fully convolutional network", the main idea is to supplement a usual contracting network by successive layers and replace the pooling operators to upsampling operators to increase the resolution of the output. To guarantee the localization, high resolution features from the contracting path should be combined with the upsampled output. A successive convolution layer can then learn to assemble a more precise output based on this information.
