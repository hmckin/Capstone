# Capstone Project

## Results:

<div style="display:flex">
  <img src="https://raw.githubusercontent.com/hmckin/Capstone/master/ResultsScreenshots/PredictedApple.png" alt="Screenshot 1" width="800" height="500">
  <img src="https://raw.githubusercontent.com/hmckin/Capstone/master/ResultsScreenshots/PredictedBread.png" alt="Screenshot 2" width="800" height="500">
</div>

## Motivation and Problem Area

Many individuals find it challenging to adhere to proper nutrition due to restrictive diets and/or the laborious task of tracking calories. Recognizing the potential for machine learning to simplify nutrition-related tasks, this project aims to utilize artificial intelligence to automate the classification of common food items and estimate their caloric content.

## Machine Learning Solutions

### Transfer Learning for Food Classification (EfficientNet B0)
To address food classification, the project employs transfer learning with EfficientNet B0, a pre-trained convolutional neural network. The baseline model is established by freezing the weights of the convolutional layers, capitalizing on insights learned from the Imagenet dataset. Additional layers, such as Global Average Pooling, dense layers, dropout, and a final dense layer matching the number of classes, are introduced to complete the architecture. **The code for this approach is demonstrated in the Jupyter Notebook called BaselineModelling.**

### Volume Estimation and Caloric Approximation (Faster RCNN + InceptionResNet V2)
To address the absence of bounding box annotations or caloric labels in my dataset, a dual-approach is implemented. I use an off-the-shelf object detection model, combining Faster RCNN and InceptionResNet V2 from TensorFlow Hub to estimate the calories. Based on the confidence score for the objects detected, either a thumb or a plate in the image is chosen as a reference. The reference is then used to predict dimensions for the food item and the volume is calculated by approximating food items as 3D objects (spheres, cylinders, and prisms). Using tabulated values for food densities, the volume is used to derive the mass of the food item. Finally, the nutrition is calculated using tabulated values for calories per unit mass. **The code is demonstrated in the Jupyter Notebook named AdvancedModelling.**

## Users and Impact

Nutrition poses a number of positive and negative impacts to a diverse range of people. Poor nutrition can increase a person's risk of type II diabetes, heart disease, stroke and cancer. Achieving fitness goals through proper nutrition and eating healthy might also have positive effects on mental health and happiness. There are many people who could benefit from automated nutrition services such as vegetarians/vegans, people who are anemic, people with restrictive food allergies, bodybuilders, professional athletes and recreational athletes. This project can also be applicable to reducing food waste when grocery shopping and educating people on the nutritional value of certain foods.

## Dataset

The dataset comprises 3281 images, each belonging to one of 16 unique food classes. All images feature either a thumb or a plate as a reference. Prior to training, images are resized as NumPy arrays with a size of (224, 224, 3), a resolution suitable for EfficientNet B0. 

In the object detection model, the images are loaded directly from JPEG files using TensorFlow methods.

## Exploratory Data Analysis (EDA)

The EDA focuses on visualizing pixel value intensity histograms and reconstructing average images using mean values from NumPy arrays. This process uncovers implicit features that convolutional neural networks (CNNs) may learn during training. Pixel intensity histograms visually represent the distribution of pixel values, showing patterns specific to different food items. The reconstruction of average images provides insights into the characteristic appearance of each class, contributing to an understanding of features influencing model discernibility. Overall, this EDA strategically explores image characteristics, shedding light on features crucial for accurate classification in the learning process of CNNs.

## Model Evaluation

The classification model's performance was assessed using loss and accuracy curves. The highest validation accuracy seen during training was 99.4%. These curves are shown here:

<div style="display:flex">
  <img src="https://raw.githubusercontent.com/hmckin/Capstone/master/ResultsScreenshots/LossCurves.png" alt="Screenshot 1" width="400" height="400">
  <img src="https://raw.githubusercontent.com/hmckin/Capstone/master/ResultsScreenshots/AccuracyCurves.png" alt="Screenshot 1" width="400" height="400">
</div>

A confusion matrix is employed to evaluate the classification results, offering a comprehensive view of the model's strengths and areas for improvement. Precision, recall and f-1 scores were not used as evaluation metrics as the model performs well across all classes, except for apples and peppers. These were the two most confused classes. The confusion matrix is shown here:

<div style="display: flex; justify-content: center; align-items: center;">
  <img src="https://raw.githubusercontent.com/hmckin/Capstone/master/ResultsScreenshots/ConfusionMatrix.png" alt="Screenshot 1" width="600" height="500">
</div>

Without ground truth labels for calories, there was no method for evaluating the accuracy of the object detection model.

