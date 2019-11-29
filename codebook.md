Codebook:
This document is a codebook that provides descriptions of the variables, the data, and all transformations and work performed to clean the data.

Cleaning and Getting Data: Course Project CODEBOOK
A script run_analysis.R was created in order to complete the challenge to read the processed experiment data and performs a number of steps to get it into summary form.

Download the dataset
This is the dataset https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip in order to continue with the experiment. 
Dataset downloaded and extracted to the following folder data/UCI-HAR-Dataset

Variables used at the script
features <- features.txt : 561 rows, 2 columns

activities <- activity_labels.txt : 6 rows, 2 columns

subject_test <- test/subject_test.txt : 2947 rows, 1 column

x_test <- test/X_test.txt : 2947 rows, 561 columns

y_test <- test/y_test.txt : 2947 rows, 1 columns

subject_train <- test/subject_train.txt : 7352 rows, 1 column

x_train <- test/X_train.txt : 7352 rows, 561 columns

y_train <- test/y_train.txt : 7352 rows, 1 columns


#1 Merges the training and the test sets to create one data set
X (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function

Y (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function

Subject (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function

Merged_Data (10299 rows, 563 column) is created by merging Subject, Y and X using cbind() function


#2 Extracts only the measurements on the mean and standard deviation for each measurement
tidyData (10299 rows, 88 columns) was created by subsetting merged_data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

#3Uses descriptive activity names to name the activities in the data set
Numbers in code column of the tidyData replaced with corresponding activity taken from second column of the activities variable

#4 Appropriately labels the data set with descriptive variable names
code column in tidyData renamed into activities
All Acc in column’s name replaced by Accelerometer

All Gyro words in column’s name replaced by Gyroscope

All BodyBody words in column’s name replaced by Body

All Mag words in column’s name replaced by Magnitude

All words started with character f in column’s name replaced by Frequency

All words started with character t in column’s name replaced by Time


#5 From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject

finalData (180 rows, 88 columns) is created by sumarizing tidyData taking the means of each variable for each activity and each subject, after groupped by subject and activity.

Export finalData into finalData.txt
