---
layout: post
title:  "Machine Learning"
date:   2018-01-27
---
## What is Machine Learning
There are tons of definitions for Machine Learning. From wikipedia, Machine Learning is a field of computer science that gives computers the ability to learn without being explicitly programmed. In practice, we use machine learning to solve two major kinds
of problems.
![Machine_Leaning](/assets/Machine_Leaning.jpg)
1. Supervised Learning
Supervised learning is the machine learning task of inferring a function from labeled training data. There are also two subcategories.
- Linear regression problems
  - e.g: In farming, given data on crop yields over the last 50 years, learn to predict next year's crop yields.
- Classification problems
  - e.g: Try to predict it will rain tomorrow based on previous data.
2. Unsupervised Learning
e.g: Given sets of medical record data from patients. Try to categorize them into different groups.

## Linear Regression
This might be one of the simplist form of machine leanrning problems to solve. But it's a good place to get started. Let's walk through a concrete example to demonstrate what linear regression is and how to solve those problems.
![Machine_Leaning](/assets/house_price.jpg)

#### This is an example of house price prediction
Following is a list of all training data, which had 2 features (size and built year) and an outcome which is the price of the house. Our goal is to predict the house price given size and built year through proper use of those data.

| size    | built year  | price   |
|:--------|:------------|:------  |
| 2104    | 1984        | 399900  |
| 1600    | 1990        | 329900  |
| 2400    | 2000        | 369000  |
| 1416    | 1989        | 232000  |

...

Linear regression let us model the data in a linear manner.  

**predictedPrice = theta0 + theta1 * size + theta2 * price**

Even if we want to model the data and a quadratic function like:

**predictedPrice = theta0 + theta1 * size^2 + theta2 * price**

we parameterize size^2 as size_square and can still deal it with the same linear regression approach

The definition of cost function:

**J(theta) = (predictedPrice0 - price0)^2 + (predictedPrice1 - price1)^2 + ...**

Cost function is used to measure the distance between the predicted result and the real result, the smaller the better. In this case, the cose function will be a function of theta(theta0, theta1 and theta2). Our job is to minimize the cose function.

By minimizing J(theta), we can find theta0, theta1 and theta2 and set up the model to do the price prediction.

#### How to minimize the cost function
1. Gradient Descent

   A first-order iterative optimization algorithm for finding the minimum of a function.
2. Normal Equation

	Linear Algebra based approach



