# Guess-The-Artist

## Introduction

Predicting the artist of a painting can be a challenging task. However, with the advent of machine learning, we can train models to recognize artists by analyzing their artwork. In this project, I used a convolutional neural network to identify artists based on the colors and geometric patterns present in their paintings.

## Objective

The objective of this project is to develop an algorithm that can identify the artist of a painting with state-of-the-art precision.

## Dataset

The dataset used in this project contains a collection of artworks from the 50 most influential artists of all time. The dataset also includes basic information retrieved from Wikipedia. The dataset consists of three files:

- artists.csv: dataset of information for each artist
- images.zip: collection of full-size images, divided into folders and sequentially numbered
- resized.zip: same collection, but images have been resized and extracted from folder structure

## Approach

### Data Processing

There are paintings of 50 artists in the dataset, but only 11 artists have more than 200 paintings available. To reduce computation and improve training, I used only the paintings of these 11 artists. Since the dataset is imbalanced (Van Gogh has 877 paintings, whereas Marc Chagall has only 239), class_weight is important. In fact, it improved model performance substantially.

I used the Keras ImageDataGenerator for data augmentation. This is not a traditional object detection problem, so the augmentation approach should be used very carefully.

### Modelling and Training

I used a convolutional neural network based approach, with a pre-defined architecture as a baseline. I tried multiple architectures, but ResNet50 worked well so far. Pretrained weights on ImageNet helped the model train better.

The objective is to identify the artist, not objects in the images. So the model should understand the style of the image better rather than the final output. Hence, training of shallow layers is more important than the deeper layers. The above statement is based on my understanding of the problem and experiments and observations. Training the model for more iterations might improve the performance, but it would increase computation resources.

## Statistical Formulas

Here are the statistical formulas used in this project, represented in LaTeX:

- Mean Absolute Error: $MAE = \frac{1}{n}\sum_{i=1}^{n}|y_i - \hat{y_i}|$
- Accuracy: $Accuracy = \frac{TP + TN}{TP + TN + FP + FN}$
- Precision: $Precision = \frac{TP}{TP + FP}$
- Recall: $Recall = \frac{TP}{TP + FN}$
- F1 Score: $F1 = 2 * \frac{Precision * Recall}{Precision + Recall}$
### Results

The final model could identify the artists with an approximate accuracy of 99% on the training set and 85% on the cross-validation set.

## Additional Information

For further information, please review the narrative of our analysis in [our jupyter notebook](./Guess-The-Artist.ipynb). If you have any additional questions, please contact **shaileshettyd@gmail.com**.

## Repository Structure

```
├── README.md                    <- The top-level README for reviewers of this project.
├── Guess-The-Artist.ipynb       <- Narrative documentation of analysis in Jupyter notebook.
├── artists.csv                  <- Dataset.
└── images                       <- Generated from code.
```
