# Automatic Breast Cancer Classification 

IEEE Published Paper: [Link](https://doi.org/10.1109/FMLDS63805.2024.00075)

Conference Slides: [pdf](https://github.com/kneshio/Breast-Cancer/blob/main/Breast%20Cancer%20Slides%20FMLDS2024.pdf)

This study leverages the pre-trained ResNet50 and VGG19 models for detecting breast cancer in histopathological images from the BreakHis dataset. 

**A.	BreakHis Dataset**

BreakHis dataset used in this study consists of 7,909 microscopic images of breast tumor tissue collected from 82 patients at various magnification factors, 40×, 100×, 200× and 400×. The dataset is divided into 8 tumor types. Four types of benign breast tumors are adenosis (A), fibroadenoma (F), phyllodes tumor (PT), and tubular adenoma (TA); and four types of malignant tumors (breast cancer) are ductal carcinoma (DC), lobular carcinoma (LC), mucinous carcinoma (MC) and papillary carcinoma (PC). 

**B.	Image Preprocessing and Classification Flow**

The images, initially sized at 700×460×3, were resized to a resolution of 224×224×3. The dataset was then partitioned into 70% for training and 30% for testing. Since the data is imbalanced, the deep learning models’ classification performance before and after data augmentation was investigated and compared. To address the imbalance, SMOTE (Synthetic Minority Over-sampling Technique) library was utilized. This involves oversampling the minority class images by randomly applying horizontal flipping, vertical flipping, and rotation, ensuring that all seven minority classes are augmented to match the size of the majority subclass. This augmentation process increases the training set from 5536 to 19323 samples, with each subclass containing 2404 samples. It's worth noting that regardless of whether data augmentation is applied, the normalization process outlined in the following subsection is implemented before training begins.

**C.  RGB Z-Score Normalization (or Standardization)**

This study utilized color z-score normalization, which is different from the normalization methods in other research. When the images are converted into PyTorch tensors, the original pixel range of [0, 255] is scaled to a PyTorch tensor range of [0.0, 1.0]. The means and standard deviations of the RGB channels across the whole training images are computed and utilized for z-score normalization. This normalization process effectively minimizes color and brightness variations, contributing to enhanced training robustness and improved accuracy.

**D.	Convolutional Neural Network and Transfer Learning**

In this study, the pre-trained VGG16 was first utilized, but the performance was not satisfied. ResNet50 and VGG19 were later selected for the classification of breast cancers from the histopathological images due to their remarkable performance in image classification, object detection, and image segmentation.

The Adam optimization function is chosen for its superior accuracy and quicker convergence compared to SGD. An adaptive learning rate strategy begins at 0.0003, gradually decreasing to 1e-5. 

**E. Results**

The results demonstrate that ResNet50 is a well-fitted model, with training loss and validation loss in proximity throughout the training process, even without data augmentation. ResNet50 achieved exceptional high accuracies of 99.03%, 93.97% and 94.73% for binary and multi-classification before and after augmentation, respectively. Data augmentation is beneficial in addressing the slight overfitting issue in VGG19, narrowing the gap between validation loss and training loss. VGG19 achieved accuracies of 96.59%, 88.33% and 92.50% for binary and multi-classification before and after augmentation, respectively. The proposed frameworks demonstrate high success in early breast cancer detection and eight-tumor-type classification, with better accuracy than other existing magnification-independent breast cancer classifier.

**F. Key Contributions**

First, unlike previous research that often separated images by magnification for classification, this study bridges this gap by constructing models for magnification-independent multi-tumor-type classification. The established transfer learning-based deep learning models for both binary and multi-class breast cancer classifications with improved accuracy are not susceptible to variations in magnification factors, offering a scalable solution across various magnification levels. 

Second, the study introduces the z-score normalization procedure for histopathological images, which has not been mentioned in previous literature on BC classification. This technique enhances consistency and reliability across different datasets. 

Finally, the impact of dataset balance on classification performance is examined by comparing models trained on balanced versus unbalanced datasets, with data augmentation applied to assess its influence on accuracy and generalizability. These findings not only address current gaps in the literature but also provide actionable insights that can inform the development of more effective diagnostic tools for breast cancer.

**F. Publication**

[2024 IEEE International Conference on Future Machine Learning and Data Science](https://www.fmlds.org/AcceptedPapers.php)
