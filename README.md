# Effects of Different Normalization Techniques on Perturbed Images


##  Overview

This project investigates how different normalization techniques affect the robustness of Convolutional Neural Networks (CNNs) when classifying both clean and perturbed images. We evaluate **Batch Normalization (BN)** and **Group Normalization (GN)** applied to two popular CNN architectures: **ResNet50** and **VGG11**.


##  Motivation

While CNNs perform well on clean datasets, they are highly sensitive to image perturbations like blur, noise, and brightness variations. This study aims to determine which normalization methods help models maintain higher accuracy under such corruptions.

##  Dataset

We use the [CIFAR-10 dataset](https://www.cs.toronto.edu/~kriz/cifar.html), which includes:

* 60,000 32x32 color images across 10 classes.
* Split: 50,000 training images and 10,000 test images.
* A **custom corrupted test set** was created with perturbations like Gaussian blur, motion blur, zoom blur, brightness shifts, and synthetic snow.

🔗 **[Download the perturbed test set](https://drive.google.com/drive/folders/1_uErDFZr-nIxXtl2U5kjSvJMV771Nlkf?usp=drive_link)**


## Methodology

### Models and Normalization Techniques

We trained the following variants:

* ResNet50 with Batch Normalization (BN)
* ResNet50 with Group Normalization (GN)
* VGG11 with Batch Normalization (BN)
* VGG11 with Group Normalization (GN)

### Training Details

* **Optimizer:**

  * Adam for ResNet models
  * SGD for VGG models
* **Learning rate:** 0.001
* **Training dataset:** CIFAR-10 training set (50k images)
* **Test sets:** CIFAR-10 test set + corrupted version


## 📊 Results

| Model       | Normal Test Accuracy (%) | Corrupted Test Accuracy (%) |
| ----------- | ------------------------ | --------------------------- |
| ResNet50 BN | 81.87                    | 33.52                       |
| ResNet50 GN | 45.19                    | 36.60                       |
| VGG11 BN    | 10.22                    | 9.49                        |
| VGG11 GN    | 22.77                    | 20.19                       |


## Experimental Insights

* **ResNet50 BN** achieves the highest accuracy on clean images but is highly sensitive to perturbations.
* **ResNet50 GN** has better robustness under corruption, showing less performance drop.
* **VGG11 GN** outperforms VGG11 BN, though both show limited generalization on corrupted images.
* Trade-offs between clean accuracy and robustness highlight the potential of Group Normalization in real-world, noisy settings.


## Conclusion

Group Normalization helps improve model robustness at the cost of some accuracy on clean images. This study contributes to understanding how normalization affects CNN behavior in challenging environments and suggests promising directions for building more resilient models.


## 📌 Project Status

This is a completed academic project submitted as part of a course at IISER Bhopal. The work is not peer-reviewed or published but is made publicly available for learning, reproducibility, and reference purposes.

---

