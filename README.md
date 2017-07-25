# Traffic-Sign-Classifier
Model Trained using CNN / Modified LeNet architecture to classify German Road Traffic Signs

Project Pipeline Covers the following subroutines:

## Section1: Data Summary and Visualization:
  
  Data - [German Traffic Signs](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset)

  Pickled Training, validation & test datasets are used for this project. 
  Below is a visualization of the sample dataset.
  ![Sample Dataset](https://raw.github.com/aranga81/Traffic-Sign-Classifier/master/output%20images/dataset.png)
    
## SECTION – 2: Designing / testing Model Architecture:

In this section I did implement the following logic:
- Function logic to convert input training, validation and test images to GrayScale
Below is a sample image converted to Grayscale
![Sample grayscale image](https://raw.github.com/aranga81/Traffic-Sign-Classifier/master/output%20images/grayscale.png)

- Function to perform histogram equalization on the input images
Histogram equalization of image
![](https://raw.github.com/aranga81/Traffic-Sign-Classifier/master/output%20images/histogramequalization.png)

- Normalization: 
            The input images have pixel values in the range of [0 255]. Feature scaling is one such procedure which would normalize all the raw input data so that all the inputs are scaled. This would allow the gradient descent optimization search to converge faster likewise.

After completing the pre-processing step sample dataset is as shown below:
![Processed Dataset](https://raw.github.com/aranga81/Traffic-Sign-Classifier/master/output%20images/datapreprocessing.png)


### Data Augmentation:
The provided training / test data was poorly distributed - this leads to biased learning of the model. A well know approach is to augment the dataset with additional fake data such that the final training/test sets are richly distributed among all the classes.

Below figure shows distribution of the original training/validation and test data set:
![Distribution for different classes](https://raw.github.com/aranga81/Traffic-Sign-Classifier/master/output%20images/datadistribution.png)

Data augmentation techniques as described in [Yann lecun paper](http://yann.lecun.com/exdb/publis/pdf/sermanet-ijcnn-11.pdf)
was implemented in my logic. 

Three techniques used for data augmentation are:
-	Translating image data set randomly in the range of (-2, 2) pixel positions
-	Rotating the images from (-30, 30) range randomly
-	Doing perspective transformation / zooming in in the range of (-2, 2) position values.

Example of Data augmentation logic applied to a sample image:
![Data augmentation on sample image](https://raw.github.com/aranga81/Traffic-Sign-Classifier/master/output%20images/dataaugmentation.png)

### MODEL ARCHITECTURE:

The final architecture used for my training was a 6 layer modified LeNet (Refer to the Model architecture section in project writeup).

![Model Architecture](https://raw.github.com/aranga81/Traffic-Sign-Classifier/master/output%20images/ModifiedLeNetModel.PNG)

## SECTION 3: TRAINING:
HYPERPARAMETERS:

The following Hyper parameters have been used for training:

-	Learning rate: 0.001
-	EPOCHS: 20 (Considering the training time on CPU)
-	Dropout probability = 0.5
-	Batch Size = 128

For the training purpose I use the Adam optimizer logic from the tensorflow module which adaptively adjusts the learning rate. 

Batch size and Learning rate used in the final logic worked out really well and hence I fixed upon those.
For training the model mostly the normal tensorflow version on CPU was used and also did try out the g2x instance on AWS with the CUDA version of tensorflow active and running. 
Time for training on CPU with core i7 processor was about 175 seconds/epoch and on a g2x instance it was about 55 seconds/epoch.

# JOB LOGS:

•	The original LeNet architecture with the original data set converged at a validation accuracy of about ~ 86 %.

•	Final Model structure with data conditioning (Section 2): By adding the dropout layer and the additional fully connected layer validation accuracy of the model turned out to be about ~ 95.6% for the original dataset.

•	Final Model Structure with Augmented Data: Using the augmented Data I could achieve a training accuracy of 100%, validation accuracy of about 98% and test data accuracy of 98%. (Please refer to the Jupyter notebook for the code).





