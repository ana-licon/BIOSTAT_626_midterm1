# BIOSTAT_626_midterm1_Ana_Laura_Licon

## Given data
Two data fies were provided for this midterm. They are labeled ```training_data.txt``` and ```test_data.txt```. Both files are tab-delimited text files containing data signals from accelerometer and gyroscope sensors from people who were asked to preform 12 different activities. These activites are: standing, sitting, lying, walking, walking downstairs, and walking upstairs, stand-to-sit, sit-to-stand, sit-to-lie, lie-to-sit, stand-to-lie, and lie-to-stand. The data are composed of 561 features calculted from the time and frequency domain data from the sensors. 

## Tasks
There were two task for this midtem:
1. To build a binary classifier to classify the activities into static (0) and dynamic activities (1).
2. To build a multiclass classifier to classify the activites into walking (1), walking_upstairs (2), walking_downstairs 3), sitting (4), standing (5), lying (6), and static postural transition (7).

## Classifier files 
Two R files are provided with the necessary code to run the classifiers. 

The file for Binary Classification is labeled ```BIOSTAT_626_Binary_Classifier_Midterm1_1425.Rmd```.
The file for Multiclass classification is labeled ```BIOSTAT_626_Multiclass_Classifier_Midterm_1425.Rmd```

## Instructions for Binary Classification
Open the Binary Classification Rmd file in R Studio and follow the steps with the code provided.
Make sure to load/install "caret" and "dplyr" packages

step 1: Set working directory (knitr::opts_knit$set(root.dir = "") where testing and training files are saved and read in training and test data

step 2: Load the training and test data files from working directory

step 3: Make binary variable for static and dynamic activities

step 4: Remove subject variables form the data sets, and the activity variable from the training data as we will be using the BinaryClass variable created in the last step

step 5: Set seed to 626 and create data partition for training and testing the binary classifier

step 6: Run logistic models for binary classification

        notes: I ran two logistic models. The first model only uses 4 of the 561 features, and the second model uses all given 561 features. The second model will give a perfect classification, but it will return an error due to multicollinearity. This is a problem of over-fitting  due to linear dependence of the features because the model is using variables all calculated from the time and frequency domain data of the sensors. In contrast, the first model returns a classifier with about 95% accuracy, using less than 1% of the given features and no issues with over fitting. The only way to be competitive on the leader board was to use the second model
        
step 7: Make predictions with classifiers on subsetted training data to verify accuracy of classification

step 8: make prediction on test data using model 2 (glm.fit2)

step 9: write out binary classification predictions to a text file named ```binary_1425.txt```


## Instructions for Multiclass Classification
Open the Multiclass Classification Rmd file in R Studio and follow the steps with the code provided.
Make sure to load/install "e1071", "caret", and "dplyr" packages

step 1: Set working directory (knitr::opts_knit$set(root.dir = "") where testing and training files are saved and read in training and test data

step 2: Load the training and test data files from working directory

step 3: fix the data labeling for the activities labeled >= 7

step 4: Remove subject variables form the data sets

step 5: Set seed to 626 and create data partition for training and testing the multiclass classifier

step 6: Run SVM models for multiclass classification

        notes: I ran 2 svm models. The first model only uses 13 of the 561 features, while the second model uses all 561 features.The second model gives a slightly better classification (98.2% accuracy), than the first model (92.8%). However, there is a big issue of overfitting with the second classification model because there is known multicollinearity in the data set. In the data description we are told that all features are calculated from the time and frequency domain data of the sensors
        
step 7: Make predictions with classifiers on subsetted training data to verify accuracy of classification

step 8: make prediction on test data using model 2 (svm.fit2)

step 9: write out binary classification predictions to a text file named ```multiclass_1425.txt```
