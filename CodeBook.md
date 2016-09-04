---
title: "Getting and Cleaning Data CodeBook"
author: "DataRacer11"
date: "Saturday, June 20, 2015"
output: html_document
---

This CodeBook describes the `Values of the Project Variables`, the `Course Project Data`, as well as `Transformations` and `Work Performed to Clean-up the Data` called CodeBook.md. 

__Values of Project Variables__ (please refer to greater details on each of the variables in `run_analysis.R` and the `README.md` file in this repro)  

1. Values of Variables Activity consist of data from "Y_train.txt" and "Y_test.txt"
2. Values of Variables Subject consist of data from "subject_train.txt" and subject_test.txt"
3. Values of Variables Features consist of data from "X_train.txt" and "X_test.txt"
4. Names of Variables Features comes from "features.txt"
5. Levels of Variable Activity comes from "activity_labels.txt"

__Course Project Data__
* `Wearable Computing Data` is collected from the accelerometers of a Samsung Galaxy S 
smartphone  

* A full description is available at the site where the `data` were obtained   
A [link](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones).  

* Here are the `data` for the project   
A [link](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip).

* Details of the files that will be used to load data are listed as follows  
1. 'README.txt'  
2. 'features_info.txt': Shows information about the variables used on the feature vector  
3. 'features.txt': List of all features  
4. 'activity_labels.txt': Links the class labels with their activity name  
5. 'train/X_train.txt': Training set  
6. 'train/y_train.txt': Training labels  
7. 'test/X_test.txt': Test set 
8. 'test/y_test.txt': Test labels  

*Notes
1. Features are normalized and bounded within [-1,1].
2. Each feature vector is a row on the text file.
3. For more information about this dataset contact: activityrecognition@smartlab.ws
    
__Transformation and Work Performed to Clean-up the Data__  

1. The `Activity`, `Subject` and` Features` were used as part of descriptive variable names for data in the data frames   
2. Read data from the files into the variables  
3. Read the `Activity` files  
4. Read the` Subject` files  
5. Read` Features` files  
6. Looked at the properties of each of the variables  
7. __*Project step #1*__ Merged the training and the test sets to create one data set  
8. Merged the data tables by rows  
9. Set names to variables  
10. Merged columns to get the data frame data for all Data  
11. __*Project step #2*__ Extracted only the measurements on the mean and standard deviation     for each measurement  
12. Subset the data frame data by selected names of Features  
13. Checked the structures of the data frame Data  
14. __*Project step #3*__ Used descriptive activity names to name the activities in the data set  
15. Read descriptive activity names from "activity_labels.txt"  
16. Factorized variable activity in the data frame data using descriptive   
activity names check  
18. __*Project step #4*__ Appropriately labeled the data set with descriptive variable names    
19 Listed names of Features were labeled using descriptive variable names  
20. Data set -- replaced by -- Descriptive variable names  
21. Conducted names check   
22. __*Project step #5*__ Created a second, independent tidy data set and output it  
23. Conducted Data Reshaping with (reshape2) and (melt)  
24. Completed with `library(knitr)`  
25. Created Codebook with `knit2html(input="run_analysis.R", output="codebook.Rmd")`    

__Reference__   
Getting and Cleaning Data Course Project
October 26, 2014, Last updated 2014-10-26 15:02:47 using R version 3.1.1 (2014-07-10)
file:///E:/Getting%20and%20Cleaning%20Data%20Course%20Project.html 
Community TA  David Hood

__Reference__   
Human Activity Recognition Using Smartphones Dataset  
Version 1.0
Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto.
Smartlab - Non Linear Complex Systems Laboratory
DITEN - Università degli Studi di Genova.
Via Opera Pia 11A, I-16145, Genoa, Italy.
activityrecognition@smartlab.ws
www.smartlab.ws  

__License__  
Use of this dataset in publications must be acknowledged by referencing the following publication  
[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. 
Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support 
Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). 
Vitoria-Gasteiz, Spain. Dec 2012
This dataset is distributed AS-IS and no responsibility implied or explicit can be addressed to the authors or their institutions for its use or misuse. Any commercial use is prohibited.
Jorge L. Reyes-Ortiz, Alessandro Ghio, Luca Oneto, Davide Anguita. November 2012.

