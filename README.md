# Capstone 2 - Machine Learning

# Training My Computer to Distinguish Car Types

-------

![header](./images/header.JPG)

## Mission

Cars are the main type of transportation around the globe. Being able to recognize the type of car on the roads could produce some great data.
This could be utilized to detect cars passing through traffic to collect data. Some useful metrics that could be derived:

-Road Wear
-Improving data for business metrics
-Making sure trucks are not in the left lane

## Dataset

[Stanford Cars Dataset](https://www.kaggle.com/eduardo4jesus/stanford-cars-dataset)

The dataset consists of 16,185 images of cars, of which only the 8,144 training images are labeled with car names. There are 196 unique cars within this dataset. The test set are not labeled with a description. 

Input:

Car Image

Target that came with the dataset: 

Car Description

![sample](./images/data_sample.png)

------

## EDA

Upon looking at the dataset initially, I realized that 196 unique cars (196 targets) was too many targets to predict on. I worked on boiling down the 196 car names into more elementary categories. A good chunk of time was dedicated to parsing through the car names to determine which bin it would fall under. These are the 6 bins of cars I settled on along with the numbers observed of each.

![6class](./images/Car_Type_Distribution.png)

I also wanted a MVP in case 6 classes were too difficult to distinguish for the computer, thus I decided to combine/split the 6 classes into two classes:

**Cars**: coupes, sedans, convertibles 

**Trucks**: vans, trucks, SUVs

![2Class](images/EZ_Type_Distribution.png)

## Modeling

The first thing I did was downsample the resolution to 256x256 and grayscale all the images to reduce the training time.

Initial 2 Class Model:

![2ClassSum](images/480k281.JPG)

81% Validation Accuracy

Initial 6 Class Model:

![6ClassSum](images/3_7mil637.JPG)

37% Validation Accuracy

Final 2 Class Model:

Increased complexity with more filters and dense layers.

![2ClassSum](images/1_4mil285.JPG)

![2ClassEpoch](images/2_Classes_Val_over_epoch.png)

85% Validation Accuracy

Final 6 Class Model:

Got rid of the dropout layer and decreased the complexity.

![6ClassSum](images/2mil651.JPG)

![6ClassEpoch](images/6_Classes_Val_over_epoch.png)

51% Validation Accuracy

## Struggles

### AWS

I spent over 2 days trying to figure out how to spin up a GPU instance on an EC2 instance but the EC2 linux jupyter instance kept crashing upon importing tensorflow. This issue was not remedied so I pivoted to Google Colab to utilize a GPU to train my model.

### Sigmoid

I initially had both models using the Sigmoid activation function for the final layer which presented a strange problem late into the project. I looked at the test prediction weights and they all fell on 1 or close to 1.

![sig_soft](images/sig_vs_softmax_output.JPG)

And yet the accuracy of sigmoid was quite high at 55% 

![sig_soft_acc](images/sig_vs_softmax_acc.JPG)


## Results

### Cars that the model has never seen before!

![demo](images/Cars_demo.png)

## Further Consideration

With more time I would like to focus in on where the car is and keep the ratio of the cars. The squeezing and stretching of the images to reach a perfect square likely threw off the model and caused strange angles that did not belong on that class of cars.
In the future I would also like to compare some different Neural Networks.

## Acknowledgements

**3D Object Representations for Fine-Grained Categorization**

Jonathan Krause, Michael Stark, Jia Deng, Li Fei-Fei

*4th IEEE Workshop on 3D Representation and Recognition, at ICCV 2013 (3dRR-13). Sydney, Australia. Dec. 8, 2013.*
