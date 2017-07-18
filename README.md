# Traffic-Sign-Classifier
Model Trained using CNN / Modified LeNet architecture to classify German Road Signs

Project Pipeline Covers the following:

Section1: Data Summary and Visualization:
  
  Data - German Traffic Signs
  Original Source: http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset

  Pickled Training, validation & test datasets are used for this project. 
    
SECTION – 2: Designing / testing Model Architecture:

In this section I did implement the following logic:
- Function logic to convert input training, validation and test images to GrayScale

- Function to perform histogram equalization on the input images

- Normalization: 
            The input images have pixel values in the range of [0 255]. Feature scaling is one such procedure which would normalize all the raw input data so that all the inputs are scaled. This would allow the gradient descent optimization search to converge faster likewise.


Data Augmentation:
Data augmentation techniques as described in http://yann.lecun.com/exdb/publis/pdf/sermanet-ijcnn-11.pdf
Is implemented in my logic. 

Three techniques used for data augmentation are:
-	Translating image data set randomly in the range of (-2, 2) pixel positions
-	Rotating the images from (-30, 30) range randomly
-	Doing perspective transformation / zooming in in the range of (-2, 2) position values.

MODEL ARCHITECTURE:

The final architecture used for my training was a 6 layer modified LeNet (Refer to the Model architecture section in project writeup).


SECTION 3: TRAINING:
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

JOB LOGS:

•	The original LeNet architecture with the original data set converged at a validation accuracy of about ~ 86 %.

•	Final Model structure with data conditioning (Section 2): By adding the dropout layer and the additional fully connected layer validation accuracy of the model turned out to be about ~ 95.6% for the original dataset.

•	Final Model Structure with Augmented Data: Using the augmented Data I could achieve a training accuracy of 100%, validation accuracy of about 98% and test data accuracy of 98%. (Please refer to the Jupyter notebook for the code).





