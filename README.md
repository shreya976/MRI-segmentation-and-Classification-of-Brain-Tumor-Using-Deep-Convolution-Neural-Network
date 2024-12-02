# MRI Image Analysis: U-Net for Brain Tumor Segmentation

We have successfully implimented the UNet architechure for segmenting the tumor in the MRI images.
 The paper ["U-Net: Convolutional Networks for Biomedical Image Segmentation"](https://arxiv.org/pdf/1505.04597.pdf) proposes a novel network architecture for segmenting biomedical images, such as electron microscopy stacks or cell microscopy images, with very few annotated samples.
- **Network Architecture**:
-
-   The network consists of a contracting path and an expansive path, forming a U-shaped structure. The contracting path captures the context of the input image, while the expansive path enables precise localization of the output segmentation³[3]. The network also uses skip connections to combine low-level and high-level features and applies data augmentation with elastic deformations to increase the robustness and invariance of the network. The paper demonstrates the application of the network to three different segmentation tasks: neuronal structures in EM stacks, cell segmentation in phase contrast microscopy, and cell segmentation in DIC microscopy. The network achieves state-of-the-art results on all three tasks, outperforming previous methods by a large margin. The network is also fast and can segment a 512x512 image in less than a second on a GPU .


#Data set :
We have obtained the data from the ["The Cancer Imaging Archive (TCIA)"](https://imaging.cancer.gov/informatics/cancer_imaging_archive.htm), in originally DICOM format for MRI images of brain tumors. (n = 532)
 
## Initiating the Journey: Setup and Preprocessing
 


#References


[1] [Ronneberger, Fischer, & Brox, 2015] "U-net: Convolutional networks for biomedical image segmentation". International Conference on Medical image computing and computer-assisted intervention.

[2] [Milletari, Navab, & Ahmadi, 2016] "V-net: Fully convolutional neural networks for volumetric medical image segmentation". International Conference on 3D Vision.

[3] WWW: Web page of the cell tracking challenge, http://www.codesolorzano.com/
celltrackingchallenge/Cell_Tracking_Challenge/Welcome.html
[4] WWW: Web page of the em segmentation challenge, http://brainiac2.mit.edu/
isbi_challenge/
 
*U-net implementation, trained networks and supplementary material available at ["U-net implementation"](http://lmb.informatik.uni-freiburg.de/people/ronneber/u-net)
