# Bark Texture Images Classification 

This is a multi-class image classification challenge to classify bark texture of 50 trees using deep learning. There is a total of 5,578 images in the dataset with dimension of 303 x 404 pixels.

Dataset source:- https://www.kaggle.com/datasets/saurabhshahane/barkvn50 

## Problem Noted with the Original Dataset:
Class Imbalance was prevalent in the dataset as some classes had around 60-80 images(minority classes) while some had 100+ & 200+(majority classes). This could affect the model training and its performance so it must be solved.

### Solution (Data Augmentation) :- 
Performing upsampling for the minority classes and downsampling for majority classes to make the limit reach the median/mean class count of the original data. A Python package, Augmentor has been used for the purpose of upsampling, by performing various image processing operations like:- 
*  Zoom - performing zooming operation
*  Flip-Top-Bottom - flips an image upside down
*  Random Distortion - helps perform random distorting to 
*  Random Brightness - adjusts the image brightness by a random factor

**Note:-** All these operations are done to create new data from the existing data by bringing some alteration in the old ones.

## Dataset Creation
The dataset has been created by storing the images in lists after resizing them into 160 * 160(to bring uniform dimension and to reduce model and computation complexity). Then the image data is stored in a numpy array for faster processing and access followed by scaling down the pixel values between 0 and 1 for faster computation. Then the dataset is split in the ratio 80:20 for training and testing purpose.

## Model Training
Steps followed:- 
* The dataset size is limited with no enough samples for deep learning models to learn and extract features for a multi-class classification, a   transfer learning based approach, fine tuning is followed where a part of the network architecture is replaced by a custom one. 
* In this approach a renowned network ResNet101 is used for the image feature extraction thus part of the CNN structure and pre-trained weights are used 
  for the model instantiation before training. The fully-connected layers are then custom built for the training purpose here.
* Four layers of fully-connected network has some drop-out layers in between to handle overfitting. Relu activation has been used to bring non-linearity.
* The final layer of the network has 50 neurons corresponding to 50 classes with softmax activation, which gives probabilistic prediction for each class.
* The model is then trained for 32 epochs using Adam optimizer and categorical loss function to aid the deep neural network for classification.
* The model evaluation is performed using the metrics like accuracy, precision, recall and F1-score.

## Model Summary and Structure
### Summary
![image](https://user-images.githubusercontent.com/106440078/190657832-d657896a-d3e4-40ec-8cc3-7aa1281a83be.png)
### Network Structure
![image](https://user-images.githubusercontent.com/106440078/190657916-55812b28-c5ad-461d-b533-57f2f64569d2.png)

## Model Evaluation
### Testing Phase
![image](https://user-images.githubusercontent.com/106440078/192083369-3a9a6d00-3f16-4e9b-a4eb-97aac94f34d1.png)
![image](https://user-images.githubusercontent.com/106440078/192083390-d0ce9c1d-2a84-4e7b-adb1-7803df216cea.png)
![image](https://user-images.githubusercontent.com/106440078/192083406-9e52d50d-2348-4922-aef4-49673f0cf4d6.png)
![image](https://user-images.githubusercontent.com/106440078/192083416-b7d37c2d-16fb-456b-8b3b-06a2e80585a5.png)

### Training Phase
![image](https://user-images.githubusercontent.com/106440078/190657199-cb05fba0-6728-4b59-b3d5-0027218dfef7.png)

## Accuracy and Loss Curves
### Accuracy Curve
![image](https://user-images.githubusercontent.com/106440078/190658228-0c5fc867-73c1-46c0-b0d7-4ced5635aed2.png)
### Loss Curve
![image](https://user-images.githubusercontent.com/106440078/190658335-85835115-1027-42bf-bb7f-7fc70a2b8ad9.png)

## Classification Report
![image](https://user-images.githubusercontent.com/106440078/192083308-7788b3f9-420d-4909-863b-b51cd99fb5e9.png)



## Acknowledgment - for Data
Truong Hoang, Vinh (2020), “BarkVN-50”, Mendeley Data, V1, doi: 10.17632/gbt4tdmttn.1


