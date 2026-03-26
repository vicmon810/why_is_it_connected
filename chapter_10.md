---
kernelspec:
    name: python3
    display_name: Python 3
    language: python
---
# Chapter 10: Statistical Model as Simplifications 

In the previous chapter, we established two key ideas:

- **Data is generated from an underlying distribution**
- **Variables exhibit structured relationships through covariance**

However, this leads to a practical problem:

- **If the true data generating process is complex and unknown, how can we work with it?** 

So, in this chapter we will address a core idea in statistics:

- We do not try to recover reality exactly
- We build simplified representations of it. 

## Why are we need models

Consider a real world system: 
- Housing prices depend on location, size, income, interest rates, and many many unkown factors. 
- Stock returns depend on countless interacting variables
- Human behavior is influenced by unobservable and noisy processes. 

The true data-generating process is: 
- high-dimensional 
- non-linear
- partially unkown 

**In monst cases, the true distribution is too complex to fully describe.** 

This leads to a fundamental constraint: 


- **We cannot model reality exactly** 


## The idea of a Model

A statistical model is a simplified description of how data is generated. 

Instead of modeling everything, we assume a structure. 

Example: 

```{code-cell} python3
import numpy as np

# True process (unknow in practice)
x = np.random.normal(0,1,1000)
y = 3 * x + 2 + np.random.normal(0,1,1000)
```

we do not know the exact mechanism, instead, we assume a model 
$$y \approx \beta_0 + \beta_1x$$

this is a **Linear model**

## Model as Approximations

A model is not reality, it is an approximation, $\textbf{A mdoel captures part of the structure while ignoring the test}$.

For example: 
- the linear term caputres the main relationship
- the noise term caputres unexplained varation.
We can now re-write the idea conceptually: 
$$ Y = f(X) + \epsilon$$

- $f(X)$: systematic component(structure)
- $\epsilon$:randomness(unexplained variation)

This decomposition is fundamental. 

## Bias-Variance trade-off

When we building models, we face a trade-off:
- Simple models -> high bias, low variance
- Complex models -> low bias, high variance

Interpretation: 
- ***Bias***: Erro due to oversimplification
- ***Variance***: sensitivity to data fluctuation

Key Idea:
- A model that too simple misses structure
- A model taht too complex captures noise

**This trade-off is core for both statistics and machine learning** 


## Example: Fitting a Simple Model

Let us fit a linear model: 

```{code-cell} python3
from sklearn.linear_model import LinearRegression

X = x.reshape(-1,1)
model = LinearRegression()
model.fit(X,y)
print(model.coef_, model.intercept_)
```

This procudes and estimate of the underlying relationship, however it does not recover teh true process excatly, and it only approximates it based on observed data. 

## Why does a Model actually learn

This a critical conceptual point. 

A model does not learn:
- the *exact* data
- the *full distribution*

Instead, it learns:
$$\textbf{A structured approximation of the relationship between variables}$$

For regression:
$$model \approx E[Y|X]$$

For classificatin:
$$ Model \approx P(Y|X)$$

These are properties of the distribution, not arbitrary constructs.

## Underfitting & Overfitting

We can illustrate model complexity:

```{code-cell} python3
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline

model_simple = LinearRegression()
Model_complex = make_pipeline(PolynomialFeatures(5), LinearRegression())

model_simple.fit(X,y)
Model_complex.fit(X,y)

print(model_simple.coef_, model_simple.intercept_)
print(Model_complex.coef_, Model_complex.intercept_)

```
Hence:
-  Underfitting -> model too simple -> misses structure
-  Overfitting -> model too complex -> fits noise

The goal is not perfect fit, but useful approximation

## Models as compression

A powerful way to think about model: *A model compresses data into a smaller set of parameters.* Instead of storing 1000 ovservations, we store:
- a few coefficients
- a functional form

This compression captures the essential structure. 

## Why this matters in Machine Learning 

Machine Learning(ML) extends this idea:

- Linear models -> simple approximations
- Neural networks -> complex approximations
- Tree models -> rule-based approximations

All share a same principle: 
- *A model approximates the underlying distribution using a restricted form.*


