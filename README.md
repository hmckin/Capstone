# Capstone Project

## Motivation and Problem Area

Many people find it difficult to adhere to diets because they can be overly restrictive or require considerable effort to track calories.
There is opportunity for machine learning to eliminate time consuming and repetitive tasks related to nutrition.

## Machine Learning Solution

This project will use a CNN model to classify common food items. The project will also estimate the volume of the food items using a thumb in the image as a reference to calculate the cross-sectional area of the item. The calorie estimation can be achieved by calculating the volume using the cross-sectional area, depth, denisty of the item and approximating the item to a common shape. (ex. apple represented as a sphere)

## Users and Impact

Nutrition poses a number of positive and negative impacts to a diverse range of people. Poor nutrition can increase a person's risk of type II diabetes, heart disease, stroke and cancer. Achieving fitness goals through proper nutrition and eating healthy might also have positive effects on mental health and happiness. There are many people who could benefit from automated nutrition services such as vegetarians/vegans, people who are anemic, people with restrictive food allergies, bodybuilders, professional athletes and recreational athletes. This project can also be applicable to reducing food waste when grocery shopping and educating people on the nutritional value of certain foods.

## Dataset

The dataset consists of 3828 images. There are 17 unique food classes and 3 classes with mixed objects from the 17 classes. Each of these photos has a thumb in the reference. 

Each of these images can be further processes with rotations and recolouring to create more data for model training.

I have written a python script to locate all the image filepaths and convert them from .jpg to numpy arrays.

