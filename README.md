# CS 523-Final
Final project submission for BU CAS CS 523

Dataset can be downloaded here: https://www.kaggle.com/mateuszbuda/lgg-mri-segmentation



#### Our goal:



#### Describe dataset:



#### Rough Ideas:

We plan to implement a network and training strategy that relies on the strong use of data augmentation to use the available annotated samples more efficiently. The general architecture consists of a contracting path to capture the picture of tumors and a symmetric expanding path that enables the localization of where the tumors are.

In many visual tasks, especially in biomedical image processing, the desired output should include localization, i.e., a class label is supposed to be assigned to each pixel to indicate where exists the tumor. Therefore, we use a network in a sliding-window setup to predict the class label of each pixel by providing a local region (patch) around that pixel. In this "fully convolutional network", the main idea is to supplement a usual contracting network by successive layers and replace the pooling operators to upsampling operators to increase the resolution of the output. To guarantee the localization, high resolution features from the contracting path should be combined with the upsampled output. A successive convolution layer can then learn to assemble a more precise output based on this information.
