# MRI Image Analysis: U-Net for Brain Tumor Segmentation

Delving into the intricate realm of medical image analysis, I've harnessed the power of a groundbreaking convolutional neural network architecture known as U-Net. This innovative approach, as outlined in the seminal paper ["U-Net: Convolutional Networks for Biomedical Image Segmentation"](https://arxiv.org/pdf/1505.04597.pdf), has been adeptly tailored to segment brain tumors from MRI images with remarkable precision. 
 The paper ["U-Net: Convolutional Networks for Biomedical Image Segmentation"](https://arxiv.org/pdf/1505.04597.pdf) proposes a novel network architecture for segmenting biomedical images, such as electron microscopy stacks or cell microscopy images, with very few annotated samples.
- **Network Architecture**:
-
-   The network consists of a contracting path and an expansive path, forming a U-shaped structure. The contracting path captures the context of the input image, while the expansive path enables precise localization of the output segmentation³[3]. The network also uses skip connections to combine low-level and high-level features and applies data augmentation with elastic deformations to increase the robustness and invariance of the network. The paper demonstrates the application of the network to three different segmentation tasks: neuronal structures in EM stacks, cell segmentation in phase contrast microscopy, and cell segmentation in DIC microscopy. The network achieves state-of-the-art results on all three tasks, outperforming previous methods by a large margin. The network is also fast and can segment a 512x512 image in less than a second on a GPU .


#Data set :
We have obtained the data from the ["The Cancer Imaging Archive (TCIA)"](https://imaging.cancer.gov/informatics/cancer_imaging_archive.htm), in originally DICOM format for MRI images of brain tumors. (n = 532)
 
## Initiating the Journey: Setup and Preprocessing
 

### Prerequisites

Ensure your Python environment (version 3.x.x) is equipped with necessary dependencies by swiftly installing them via the provided `requirements.txt`.
```bash
pip install -r requirements.txt
```

### Data Acquisition

The indispensable foundation of any machine learning endeavor lies in the availability of quality data. By executing the `download_data.sh` shell script, you'll effortlessly procure a comprehensive dataset comprising 3064 MRI images accompanied by their respective masks.
```bash
bash tumor-segmentation-unet/download_data.sh
```

Subsequently, transform this raw data into a usable format with a simple Python script:
```bash
python tumor-segmentation-unet/mat_to_numpy.py brain_tumor_dataset/
```

## Architectural Blueprint: Unveiling the U-Net

At the heart of our segmentation pipeline resides the U-Net architecture, fortified by a fusion of tailored losses including binary cross-entropy and dice loss, each accorded equal weightage. Leveraging Conv2D transpose layers facilitates effective upsampling within the network.

Monitoring the training progress is simplified through the utilization of the Intersection over Union (IOU) metric. Adam optimizer steers the training process across 40-60 epochs, with a decaying learning rate ranging from 1e-3 to 1e-4. Augmenting the data with horizontal flips enhances model robustness.

![Model Performance](screenshots/performance2.png)

For those craving deeper insights, behold the detailed architecture:

![U-Net Architecture](screenshots/unet-tumor-seg.png)

## Pathways to Progress: Future Enhancements

As with any evolving field, avenues for refinement abound. Consider the following avenues for further exploration and enhancement:
1. Embrace transfer learning paradigms by integrating pre-trained models such as VGG, Inception, or ResNet.
2. Enrich the augmentation repertoire with diverse transformations like vertical flips, brightness adjustments, or zoom operations.
3. Explore the incorporation of advanced loss functions such as Lovasz loss, potentially assigning higher weightage to augment model performance.
4. Delve into the realm of Hypercolumns to harness richer feature representations.

#References


[1] [Ronneberger, Fischer, & Brox, 2015] "U-net: Convolutional networks for biomedical image segmentation". International Conference on Medical image computing and computer-assisted intervention.

[2] [Milletari, Navab, & Ahmadi, 2016] "V-net: Fully convolutional neural networks for volumetric medical image segmentation". International Conference on 3D Vision.

[3] WWW: Web page of the cell tracking challenge, http://www.codesolorzano.com/
celltrackingchallenge/Cell_Tracking_Challenge/Welcome.html
[4] WWW: Web page of the em segmentation challenge, http://brainiac2.mit.edu/
isbi_challenge/
 
*U-net implementation, trained networks and supplementary material available at ["U-net implementation"](http://lmb.informatik.uni-freiburg.de/people/ronneber/u-net)
