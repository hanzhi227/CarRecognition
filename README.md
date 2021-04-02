# Capstone 2 - Machine Learning

# Training My Computer to Distinguish Car Types

  

[]()

## Mission

Wouldn't it be amazing if my computer could recognize what a car's body type is just from an image of a car? That is exactly what I set out to do.

## Dataset

[Stanford Cars Dataset](https://www.kaggle.com/eduardo4jesus/stanford-cars-dataset)

The dataset consists of 16,185 images of cars, of which only the 8,144 training images are labeled with car names. There are 196 unique cars within this dataset. The test set are not labeled with a description. 

*some images of cars from dataset here*

Input:

Car Image

Target that came with the dataset: 

Car Description

## EDA

Upon looking at the dataset initially, I realized that 196 unique cars (196 targets) was too many targets to predict on. I worked on boiling down the 196 car names into more elementary categories. A good chunk of time was dedicated to parsing through the car names to determine which bin it would fall under. These are the 6 bins of cars I settled on along with the numbers observed of each.

*6 classes distribution*

I also wanted a MVP in case 6 classes were too difficult to distinguish for the computer, thus I decided to combine/split the 6 classes into two classes:

**Cars**: coupes, sedans, convertibles 

**Trucks**: vans, trucks, SUVs

*2 classes distribution*

## Modeling

Initial 2 Class Model:

*image*

[]()

## Acknowledgements

**3D Object Representations for Fine-Grained Categorization**

Jonathan Krause, Michael Stark, Jia Deng, Li Fei-Fei

*4th IEEE Workshop on 3D Representation and Recognition, at ICCV 2013 (3dRR-13). Sydney, Australia. Dec. 8, 2013.*
