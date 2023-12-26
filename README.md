# Capstone Project

## Results

<div style="display:flex">
  <img src="https://raw.githubusercontent.com/hmckin/Capstone/master/ResultsScreenshots/PredictedApple.png" alt="Screenshot 1" width="400" height="250">
  <img src="https://raw.githubusercontent.com/hmckin/Capstone/master/ResultsScreenshots/PredictedBread.png" alt="Screenshot 2" width="400" height="250">
</div>

## Motivation and Problem Area

Many people find it difficult to adhere to diets because they can be overly restrictive or require considerable effort to track calories.
There is opportunity for machine learning to eliminate time consuming and repetitive tasks related to nutrition.

## Machine Learning Solution

This project will use a pre-trained CNN model to classify common food items. The project will also estimate the volume of the food items using a thumb in the image as a reference to calculate the cross-sectional area of the item. This will be done using an off-the-shelf model from Tensorflow API. The calorie estimation can be achieved by calculating the volume using the cross-sectional area, depth, denisty of the item and approximating the item to a common shape. (ex. apple represented as a sphere)

## Users and Impact

Nutrition poses a number of positive and negative impacts to a diverse range of people. Poor nutrition can increase a person's risk of type II diabetes, heart disease, stroke and cancer. Achieving fitness goals through proper nutrition and eating healthy might also have positive effects on mental health and happiness. There are many people who could benefit from automated nutrition services such as vegetarians/vegans, people who are anemic, people with restrictive food allergies, bodybuilders, professional athletes and recreational athletes. This project can also be applicable to reducing food waste when grocery shopping and educating people on the nutritional value of certain foods.

## Dataset

The dataset consists of 3281 images. There are 16 unique food classes that I will be classifying. Each of these photos has a thumb in the reference. 

I have resized each of these images to a resolution of (224,224,3) which is required for EfficientNet B0. 

## EDA

I focus my EDA on investigating class imbalances, plotting pixel value intensity histograms and reconstructing the average image from each class using the mean values of the NumPy arrays. 

## Model Architecture

I have developed a baseline model that uses EfficientNet B0 as the backbone. I have frozen the weights in the convolutional layers to take advantage of training on the Imagenet dataset. 

I then added a Global Average Pooling layer, a dense layer, dropout and a final dense layer matching the number of classes in the dataset. 

## Model Evaluation

I evaluate the model using loss and accuracy curves as well as a confusion matrix.
