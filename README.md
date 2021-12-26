# Neural Network Charity Analysis
## Overview
This analysis sought to create a model that can predict what organizations would receive funding from Alphabet Soup with a targeted accuracy of at least 75%. Using data on more than 34,000 organizations that received funding, I created a neural network model that predicted the whether or not organizations successfully received funding. I then made three attempts to optimize the model in order to create neural network models that more accurately made predictions.

## Results

### Data Processing
The data contained the following columns with information on each organization:
- EIN and NAME—Identification columns
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special consideration for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively

For the purpose of this analysis, IS_SUCCESSFUL was the target variable as this indicated whether or not an organization received funding from Alphabet Soup. EIN and NAME were removed for this analysis as both were identifiers that don't give useful information regarding the organzations. All remaining variables were used as features in this analysis.

### Compiling, Training, and Evaluating the Model

The initial neural network contains two hidden nodes with 43 neurons each. As the original data contained categorical data, the data had to be encoded in order to contain numeric data that can be analyized by a neural network. The encoded dataframe contained 43 columns, thus creating 43 features. As the general rule of thumb for the number of neurons in a model is that it should be 2~3 times the number of features, I opted to use a total of 86 neurons and divided them into two layers.

The two hidden layers used ReLu functions for their activation functions and the output layer used a sigmoid function. Due to the large number of features in this model, linear, sigmoid, and tanh functions did not seem appropriate for handling inputs in the hidden layers as they are better suited for simpler models. As the output of this model are binary, a sigmoid function seemed appropriate for the output layer.

This model, however, failed to achieve the targed accuracy. Upon evaluation, it achieved an accuracy of 72.72%.

I then attempted to increase the accuracy via the below three ways:
- Dropping other noisy variables-- In this case, I dropped AFFILIATION and ORGANIZATION. Additionally, this reduced the number of features in the encoded dataframe to 34, so I also changed the number of neurons to 34 in each hidden layer to be consistent with the rule of thumb followed in the initial model.
- Adding a third hidden layer-- I kept the same features used in the initial model, but added another hidden layer containing 43 neurons.
- Changing the activation function in the output layer-- In order to allow for slightly more complexity in the output layer, I changed the activation function from a sigmoid function to a tanh function.

However, none of the three attempts at optimizing the model achieved the target accuracy. Dropping AFFILIATION and ORGANIZATION decreased accuracy to 62.89%. Adding a third layer performed similarly to the initial model at 72.90% accuracy. Changing the activation function also performed similarly at 72.99%.

## Summary
The initial neural network model with 86 neurons and two hidden layers failed to achieve the target accuracy of 75% as did all three attempts to optimize the model.

However, a random forest model could potentially predict the success of each organization in this dataset with the same or better results. By combining multiple weak learners, random forests behave similarly to neural networks. And while neural networks are designed to handle complex data such as images and natural language, random forests are designed to handle tabular data. As this dataset lacks much of the complexity that neural networks are specialized for, a random forest model is likely to handle it without issue. Consequently, we can except a random forest model's results might be similar or possibly better than a neural network.