# Clothing-Type-Classifier

## Data 

- Dataset from kaggle [Dataset](https://www.kaggle.com/datasets/agrigorev/clothing-dataset-full)

- The images.csv file contains
  * image - the ID of the image (use it to load the image from images/<ID>.jpg)
  * sender_id - the ID of a person who contributed the image
  * label - the class of the image
  * kids - flag, True if it's clothes for kids
 
 - Over 5,000 images of 20 different classes 
 - classes 
 
 ## Data handling
 
- Reading images.csv file 
- Adding extention .jpg to image coulmns
- Creating DataFrame containing only image ID, and lable 
- Mapping class name to class number 
- Splitting data to train and test
- Creating train.csv file, and test.csv file
- Creating Dataset class 
- Creating tranform function 
 * resing all images to fixed size
 * converting images to tensors with value from zero to one 
- intializing instances(trainset, testset) from Dataset class

 
