---
id: '202401090937'
tags: []
related: []
from:
---

# Baseline model 

Before I dive further into details, lets just recap what exactly is a baseline model.

A baseline model is a model that is used as a benchmark against which all other models are compared. It is a very simple model. It is used to check if the new model we are building is better than the baseline model or not.


## Why do we need a baseline model?

Whenever we start building models for a given problem. We hardly build a simple model and directly jump into building complex models. I am seeing a common pattern where data science enthusiasts feel excited about building fancy models. 

It has the following downsides:

- It takes time to build complex models as you first start gathering the data and then build the models. 
- Error analysis becomes difficult as you have to debug the complex model. Trust me machine learning is hard. 
- Often you need to rephrase the problem statement as you know more about the problem. All effort goes in vain. 

## How to build a baseline model?

If you started working on an existing problem, then sync up with product/business team to understand what is the current solution they are using. It will also help you understand the problem better.
This becomes your intelligent baseline model to compare if you are beating the current solution or not.

Now, for building the baseline model, take a few more features and build a simple model. Keep in mind that your goal is to build this model within a day or two.
See if you are able to beat the current solution or not. If you are not able to beat the current solution, then you need to rethink your approach.
If not better, you should at least be able to match the current solution. 
i.e. your company wants to identify the customers who are likely to churn. 


Think for a minute, how would you go about it and then read further.

One way is, you think this is a simple problem, and you directly jump into building a complex model. You gather the data, build a complex model and look at accuracy numbers. The base rate of churn is 10%. You are a decent smart person and know that accuracy is not the right metric for this scenario. 
So you look at precision and recall numbers. You iterate over the model and tune the parameters for the model well. You are able to get 80% precision and 70% recall. You set up a meeting with business team to share the results.

When you share those numbers, the business team doesn't look amused. They say that they have a simple rule based model which is able to identify 80% of the customers who are likely to churn. What they do is just look at last day of activity of the customer. If the customer has not done any activity in last 7 days, then they are likely to churn. Then they target those customers.  

Boom! You did not expect this. You are not even able to match the current solution. 

This is a pretty simple model yet powerful. No maintenance or training is required. They just run a query and get all the customers who are likely to churn. 
Business team has come to you, if you can do better than them. 

Now lets understand the implications of this scenario.
first, you have wasted a lot of time in building a complex model. We did not know the target or when should we say that our model is good enough.
second, It might be the case that this is the first time you interacted with the business team and we could have used this opportunity to strengthen our relationship with them. But we missed it. 

Now lets see how we could have done better.
We could have discussed with the business team to understand their current solution and get their domain knowledge. The business team know their business well and they might have some domain insights which we might not be aware of. After this discussion, we know that the business team is using a simple rule based model. This becomes our baseline to beat. We build a simple model with a few more features based on interactions with them. This model will be able to match the baseline model if not better. Now, We also know that the business team is not concerned about the probability threshold. AUC metric would make more sense here. They were targeting a lot more users to find churned users. You can create buckets of users based on probability and show that top 20% users are giving around 70% churned users. They were targeting 40% of users. With a simple model, you have matched the current solution and also have optimized the targeting. Now, the business team is happy with the results and you have done this within 1-2 days. 

## How to build a baseline model for a new problem?

We have seen how to build a baseline model for an existing problem. Now lets see how to build a baseline model for a new problem.

For a new problem, you dont have an existing solution to compare with. But this does not mean that you should not have a baseline model. You should always have a baseline model.

Lets say, we want to find orders which are going to be cancelled. For an ecommerce company, its important to find these orders as soon as possible. So that they could take action appropriately. Brain-storm about the problem. Think about the features that you can use. If you have a stakeholder, then discuss with them if they have done anything to solve the problem. Try to identify the behavior of the cancelled orders. 
You can use features like time to order, time to delivery, is COD, is prepaid, is first order, order value, is new user, item category etc. Quickly analyse the historical canceled data and find cancelled rate among the features we have discussed.  
Just by looking at the data, you can see that canceled rate is high for COD orders, orders with high value, orders with new users etc.
You will create a simple rule based model based on COD order, order value > 1000 and new user. You might see that you are able to identify 20%-40% of the orders which are going to be canceled and it has 70% precision.  
This becomes your first baseline model. 
Now you can start building a simple ML model to beat this model. You can use the features that we have discussed. You can use a simple logistic regression model.  You can use precision and recall numbers. Once you have a model which is able to beat the baseline model, you can start iterating over the model to improve the performance. 
You might wonder why did we build a rule-based model? We could have directly built a simple ML model.
The reason is that we need to have an idea about the problem. We need to know that features we are going to use make sense. It helps you understand the problem better.
When you start building an ML model, there are many things can go wrong i.e. target leakage, data quality issues, overfitting etc. If you have a simple rule based model, you can compare the results of ML model with the rule-based model. If the ML model results are not better or similar, then you know that something is wrong with the ML model. You can debug the ML model, feature engineering steps and fix the issues. 
If you are confident about the features and the problem, then you can directly build a simple ML model. This model serves as a baseline model. 

## Conclusion

Simply put, a baseline model is like a basic foundation. It helps us start working on more advanced and effective models. It's like a reality check, making sure we have a good starting point and can measure improvements as we develop more complex models. This way, we make sure that the fancy models we build are actually needed and work better than the simpler ones.




