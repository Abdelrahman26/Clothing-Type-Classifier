# Clothing-Type-Classifier

## Data 

- Dataset from kaggle [Dataset](https://www.kaggle.com/datasets/agrigorev/clothing-dataset-full)

- The images.csv file contains
  * image - the ID of the image (use it to load the image from images/<ID>.jpg)
  * sender_id - the ID of a person who contributed the image
  * label - the class of the image
  * kids - flag, True if it's clothes for kids
 
 - Over 5,000 images of 20 different classes 

 
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
- intializing trainloader and testloader
- mapping trainloader and testloader to train and test in dataloader
- Instaling vgg16(Architecture and pre-trained weights)
 
## Approaches
 
- since the dataset is a small dataset, then building network and run it from scratch will cause overfitting
- Transfer Learning may be a good solution!
  * used vgg16 trained on ImageNet as a pre-trained network
  * Freezing the body of the network, removing the head layers, adding new layer in the head including conv2d, RelU, AdaptiveAvgpool2d, and final dense layer
  * used Adam optimizer to adapt with learning rate  
  * Training the data with 3 epochs
    - loss decreasing
    - training accuracy increasing 
    - testing accuracy is almost fixed(indecation to almost overfitting!) 
    - training acc. = 0.56
    - testing  acc. = 0.42
 
  * Unfreezing the body layers, training 3 epochs
    - loss decrasing first then had a little change
    - training acc. = 0.18
    - testing  acc. = 0.20
    - need more epochs!
 
  * Unfreezing the body layers, training another 5 epochs
    - loss is almost fixed, stucking in local minmum
 
  * Unfreezing the body layers, training another 2 epoch
    - change optimizer to SGD with learinig rate = 0.1 and momuntem = 0.9 (Trying to go out of local minmum)
    - loss is still fixed, stucking in local minmum too
 
  * freezing the body again, 5 epochs
    - loss is still fixed
 
  * Ignoreing learned parameters and training with intial weights of vgg16, 10 epochs, body freezed
   - loss decreasing over epochs 
   - training acc. = 0.83
   - testing  acc. = 0.44 
   - overfitting

 
