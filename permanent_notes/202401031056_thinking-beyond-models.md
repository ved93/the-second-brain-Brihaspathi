---
id: '202401031056'
tags: []
related: []
from:
---

# title

This is talk material which I may present in future 

## Introduction

I have been doing data science from the past 10 years. Most importantly I have been to places where data science failed to create impact and where it created impact. I have seen the good, bad and ugly of data science.
I believe my learning could be highly beneficial to the people who dont work at companies where data science is pretty well structured. Think it about in this way, you are driving a car on 4-lane straight highway and you think you are pretty good at driving. But once you drive to hill place and single lane road, you will realize that you are not that good at driving.
You are really good at what you do but scope is not that bigger.

The scope of talk will be focused on thinking beyond models. 


## Data Science is not just .fit and .predict



## Problem formulations

## Data collection

## Data Engineering Fundamentals

## Data cleaning

## Data exploration

## Start with Simple model first

This will become a good baseline. 

## Look at the data

Codes can be buggy. Data can be buggy. Always manually look at a few samples to verify that the data is what you expect it to be.
Use data validation tools to check for data anomalies.


## Look at the predictions


## Look at the errors

## Understand the model and its limitations

Sometime your usecase requires that your model should be interpretable. You should be able to explain why your model is predicting what it is predicting.

Sometimes your model predictions has lot of variance and highly dependent on the data. You may require a model which is more stable and less dependent on the data.
i.e. SVM 


## Understand how its going to be used

i.e. if you are building a classification model for a marketing campaign. You optimize the model for classification accuracy, but the usecase is best suited for AUC where you just need to rank the customers.
Another example is that business asks you give probability of churn. Based on probability, they are going to give discount to the customers. In this case, you need to calibrate the probability because your model does not provide actual probability. 
If you understand the usecase, your model can be more effective and sometimes becomes easier to build. 


