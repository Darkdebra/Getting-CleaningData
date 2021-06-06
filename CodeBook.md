## The analysis_program.R script performs the data preparation and 
## then follows the 5 steps required for this project 
## described in the course project's definition.

## 1.- Downloading the dataset.
  ## At the beginning, the program download and extracts the dataset 
  ## into a folder called UCI HAR Dataset.
  
## 2.- Assign data to variables.
  ## features <- features.txt: 561 rows, 2 columns
  ## "The features selected for this database come from the accelerometer and 
  ## gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ"
  
  ## activities <- activity_labels.txt: 6 rows, 2 columns
  ## "List of activities performed when the corresponding measurements were 
  ## taken and its codes (labels)".
  
  ## subject_test <-test/subject_test.txt: 2947 rows, 1 column
  ## "Contains test data of 9/30 volunteer test subjects being observed" 
  
  ## x_test <- test/X_test.txt: 2947 rows, 561 columns
  ## "Contains recorded features test data".
  
  ## y_test <- test/y_test.txt: 2947 rows, 1 column
  ## "Contains test data of activities' code labels".
  
  ## subject_train <- train/subject_train.txt: 7352 rows, 1 column
  ## "Contains train data of 21/30 volunteer subjects being ovserved"
  
  ## x_train <- train/X_train.txt: 7352 rows, 561 columns
  ## "Contains recorded features train data".
  
  ## y_train <- train/y_train.txt: 7352 rows, 1 column
  ## "Contains train data of activities' code labels"
  
## 3.- Merges the training and the test sets to create one data set
  ## X (10299 rows, 561 columns) 
  ## It is created by merging x_train and x_test by the rbind() function
  
  ## Y (10299 rows, 1 column) 
  ## It is created by merging y_train and y_test by the rbind() function
  
  ## Subject (10299 rows, 1 column)
  ## It is created by merging subject_train and subject_test by the rbind() function
  
  ## Merged_Data (10299 rows, 563 columns)
  ## It is created by merging Subject, Y and X by the cbind() function.
  
## 4.- Extracts just the measurements on the mean and standar deviation for each measurement
  ## TidiData (10299 rows, 88 columns)
  ## It is created by subsetting Merged_Data using the select() function and
  ## selecting only the columns subject, code, and the measurements on the mean 
  ## and std (standar deviation) for each measurement.
  
## 5.- Uses descriptive activity names to name the activities in the data set
  ## Entire numbers in code column of the TidiData replaced with corresponding 
  ## activity taken from the second column of the activities variable.
  
## 6.- Appropriately labels the data set with descriptive variable names.
  ## code column in TidyData renamed into activities
  ## All cc, Gyro, BodyBody and Mag in column's names replaced by Accelerometer, 
  ## Gyroscope, Body and Magnitude.
  ## All start with character t and start with character f in column's name replaced by
  ## Time and Frequency.
  
## 7.- From the dataset in step 4, creates a second, independent tidy dataset with the
## average of each variable for each activity and each subject
  ## NewData (180 rows, 88 columns)
  ## It is created by grouping TidyData by subject and activity and then summarizing
  ## it by taking the means of each variable for each activity and each subject.
  
  ## Then, the code exports this dataset (NewData) into a text file called NewData.txt
