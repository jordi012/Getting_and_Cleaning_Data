---
title: "Getting and Cleaning Data-Course Project"
author: "DataRacer11"
date: "Friday, June 19, 2015"
output: html_document
---  
Please refer to References at bottom of this README.md file.

__Purpose of This Project__  
The purpose of this project is to demonstrate the ability to collect, 
work with, and clean a data set while following the project instructions.   

__Goal of This Project__  
The goal of this project is to prepare `tidy data` that can be used for later analysis. 

__Submission Requirements__

1) A `tidy data` set 
2) A `link` to a Github repository with a script for performing the analysis 
3) A `code book` that describes the variables, the data, and any 
transformations or work performed to clean up the data called CodeBook.md 
4) A `README.md` in the repo with scripts 
5) A `repo` that explains how all of the scripts work and how they are connected 

* (please refer to greater details on how the scripts work and how they are connected in `run_analysis.R` and the `CodeBook.md` file in this repro) 

__Course Project Data__

* `Wearable Computing Data` is collected from the accelerometers of a Samsung Galaxy S 
smartphone  

* A full description is available at the site where the `data` were obtained   
A [link](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones).  

* Here are the `data` for this project   
A [link](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip).

__Created one R script called `run_analysis.R` which accomplished the following__  

####1. Merged the training and the test sets to create one data set

Merged the data tables by rows

  >{dataSubject <- rbind(dataSubjectTrain, dataSubjectTest)
    dataActivity<- rbind(dataActivityTrain, dataActivityTest)
    dataFeatures<- rbind(dataFeaturesTrain, dataFeaturesTest)
   }

Set names to variables

  >{names(dataSubject)<-c("subject")    
    names(dataActivity)<- c("activity")    
    dataFeaturesNames <- read.table(file.path(path_rf, "features.txt"),head=FALSE)    
    names(dataFeatures)<- dataFeaturesNames$V2    
   }

Merged columns to obtain data 

  >{dataCombine <- cbind(dataSubject, dataActivity)
    Data <- cbind(dataFeatures, dataCombine)
   }

####2. Extracted only the measurements 

On the mean and standard deviation for each measurement 
  
  >{subdataFeaturesNames<-dataFeaturesNames$ V2[grep("mean\\(\\)|std\\(\\)"dataFeaturesNames $V2)]

Subset the data frame Data by selected names of Features

  >{selectedNames<-c(as.character(subdataFeaturesNames), 
                   "subject",       "activity" )
   Data<-subset(Data,select=selectedNames)
  }

Checked the structures of the data frame Data

  >{str(Data)
  }  
  
####3. Used descriptive activity names to name the activities in the data set

Read descriptive activity names from "activity_labels.txt"

  >{activityLabels <- read.table(file.path(path_rf, 
                                         "activity_labels.txt"),header = FALSE)
  }

Factorized variable activity in the data frame Data using descriptive activity names check:

  >{head(Data$activity,30)
  }

####4. Appropriately labeled the data set with descriptive variable names 

  >{names(Data)<-gsub("^t" , "time", names(Data))  
    names(Data)<-gsub("Acc" , "Accelerometer", names(Data))  
    names(Data)<-gsub("Gyro" , "Gyroscope", names(Data))  
    names(Data)<-gsub("^f" , "frequency", names(Data))  
    names(Data)<-gsub("Mag" , "Magnitude", names(Data))  
    names(Data)<-gsub("BodyBody" ", "Body", names(Data))  
   }  
  
####5. From the data set in step 4, created a second, independent tidy data set with the average of each variable for each activity and each subject.

  >{library(plyr)
   }

  >{Data2<-aggregate(. ~subject + activity, Data, mean)
    Data2<-Data2[order(Data2$subject,Data2$activity),]
    write.table(Data2, file = "tidydata.txt",row.name=FALSE)
   }

__Verified the following steps required for Peer Review__

1. Uploaded the `tidy data` set created in the instructions under submission requirements
2. Uploaded the `tidy data` set as a txt file created with write.table() using row.name=FALSE 
3. The dataset was not cut and pasted directly into the text box, as to curtail errors while saving the submission
4. Submitted a tidy data set to the repro
5. Met `tidy data` principles of week 1 (Each variable measured is in one column, Each different observation of the variable is in a different row)
6. Submitted a `link` to a Github repo with the code for performing the analysis
7. Included Code which includes a file `run_analysis.R` in the main directory with the Samsung data in the working directory 
8. The data reshaped output of the `tidy data` set is the data submitted for part 1 
9. This `README.md` describes how the script works and the code book describing each on each of the variables  

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
