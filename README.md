# MRI Image Analysis: U-Net for Brain Tumor Segmentation

Delving into the intricate realm of medical image analysis, I've harnessed the power of a groundbreaking convolutional neural network architecture known as U-Net. This innovative approach, as outlined in the seminal paper ["U-Net: Convolutional Networks for Biomedical Image Segmentation"](https://arxiv.org/pdf/1505.04597.pdf), has been adeptly tailored to segment brain tumors from MRI images with remarkable precision.

Within the spectrum of brain pathology, we encounter three primary types of tumors:
1. Meningioma
2. Glioma
3. Pituitary tumor

## Glimpse into Predictive Power: Sample Segmentation Results

| Meningioma | Glioma | Pituitary Tumor |
|:----------:|:------:|:---------------:|
| ![Sample 1](samples/sample1.png) | ![Sample 2](samples/sample2.png) | ![Sample 3](samples/sample3.png) |
| ![Sample 4](samples/sample4.png) | ![Sample 5](samples/sample5.png) | ![Sample 6](samples/sample6.png) |
| ![Sample 7](samples/sample7.png) | ![Sample 8](samples/sample8.png) | ![Sample 9](samples/sample9.png) |

## Initiating the Journey: Setup and Preprocessing

To embark on this endeavor, let me guide you through the process of acquiring and preparing the requisite data. Utilizing the provided [notebook](https://github.com/adityajn105/brain-tumor-segmentation-unet/blob/master/brain-tumor-segmentation.ipynb), you'll seamlessly transition from data procurement to model training and evaluation.

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

At the heart of our segmentation pipeline resides the U-Net architecture, fortified by a fusion of tailored losses including binary crossentropy and dice loss, each accorded equal weightage. Leveraging Conv2D transpose layers facilitates effective upsampling within the network.

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

## Meet the Mind Behind the Model

Envisioned and brought to fruition by Aditya Jain, this endeavor reflects a passion for leveraging cutting-edge techniques to unravel the complexities of medical image analysis. For more insights into Aditya's portfolio, visit [here](https://adityajain.me).

## Further Reading

Curiosity piqued? Explore the following resources to deepen your understanding and embark on your own journey into the realm of image segmentation:
1. ["U-Net: Convolutional Networks for Biomedical Image Segmentation"](https://arxiv.org/pdf/1505.04597.pdf)
2. ["Understanding Semantic Segmentation with U-Net"](https://towardsdatascience.com/understanding-semantic-segmentation-with-unet-6be4f42d4b47)
3. ["Up-sampling with Transposed Convolution"](https://towardsdatascience.com/up-sampling-with-transposed-convolution-9ae4f2df52d0)
4. ["Lovasz Loss"](https://arxiv.org/abs/1705.08790)
5. ["Jaccard Index - Intersection over Union"](https://www.jeremyjordan.me/evaluating-image-segmentation-models/)
6. ["Understanding Dice Loss"](https://forums.fast.ai/t/understanding-the-dice-coefficient/5838)
7. [Explore another Image Segmentation Challenge](https://github.com/adityajn105/TGS-Salt-Identification-Image-Segmentation-)
