---
kernelspec:
    name: python3
    display_name: Python 3
    language: python
---

# Chapter 8: Distribution, Expectation, and Variance

Suppose we repeatedly observe the same phenomenon:
- daily temperature
- customer arrivals
- stock returns
- heights of randomly selected individuals

Each time we collect data, the values are different. 

If the data is always changing, what exactly are we trying to learn?

In this chapter we will addressess a fundamental question:
- **When observed vaules vary from sample to sample, waht remains stable underneath?**

## Why does **Data vary** at **ALL**?

let beging with a simple example

```{code-cell} python3
import numpy as np

np.random.seed(123)
samples = np.random.normal(loc=167, scale=5, size=55)
print(samples)
```

Even thought all values come from the "same source", they are not identical. 

This leads to an important relization:

- **Real-word data is not a fixed value repeated many times. It is the output of a variables process.**

So the central question of statistics is not:
- **"What is the value?"**

but rather:

- **"What kind of process could generate values like these?"**

## What stays table underneath changing Observations?

Imagine a hidden machine, each time we press a button, it produces one value. The outputs vary, but not arbitrarily:
- some values appear frequently
- some are rare
- some ranges are likely
- others almost never occur

This hidden rule is called a **Distribution**.

We can simulate different distributions:

```{code-cell} python3
import numpy as np
import matplotlib.pyplot as plt

x1 = np.random.normal(loc=12, scale=1, size=1000)
x2 = np.random.normal(loc=15, scale=3, size=1000)


plt.hist(x1, bins=30, alpha=0.6, density=True, label="std = 1")

plt.hist(x2, bins=30, alpha=0.6, density=True, label="std = 1")

plt.legend()
plt.title("Different distributions generate a different data pattern")

plt.show()
```

The dataset is what we **observe**, the distribution is what **generates** it.

## If a Distribution is a Rule, How do we Summarize it?

Suppose we collect thousands of observations. 

What are the first things we want to know?

Typically:

- 1. Where do the values tend to center?
- 2. How much do they vary?

Statistics formalizes these two ideas as: 

- Expectation(mean)
- Variance

## Where does the Data tend to Center?

If we repeatedly sample from the same process, the average value stabilize. 

This long run average is called the **expectation.**

```{code-cell} python3
x = np.random.normal(loc=78,scale=4.5, size=10000)
print(np.mean(x))
```

This approximates: 
$$E[X]$$

Important distinction: 
- $E[X]$: property of the distribution(unknow)
- Sample mean: computed from observed data. 

The expectation belongs to the underlying process. 

The sample mean belongs to the data we observe. 

## Why is the mean Not Enough?

Consider two datasets:

```{code-cell} python3

x1 = np.random.normal(0, 1, 1000)

x2 = np.random.normal(0, 5, 1000)

print(np.mean(x1), np.mean(x2))
print(np.var(x1), np.var(x2))
```

Both have similar means, but very different spreads.

This shows:
- Knowing the center alone is not sufficient to describe a distribution. 

We also need to measure variability.

This leads to variance.

- **Variance measure how much values deviate from expectation.**

Interpretation: 
- Small variance -> values are tightly clustered 
- Large variance -> values are widely spread. 

## Why do large samples looks more stable?

Individual observations fluctuate, yet averages become more stable as we collect more data.

**Why**

Let simulate this 

```{code-cell} python3
means = []

for n in range(1,500):
    x = np.random.normal(165,3,size=n)
    means.append(np.mean(x))

plt.plot(means)
plt.axhline(165)
plt.title("Sample mean stabilizes as sample size increase")
plt.show()
```

Observation: 
- Small samples -> high variablility
- Large samples -> stable averages


This phenomenon is know as the Law of Large Numbers. 


## Are all Distributios the same?

Not all variables behave in the same way.Some variables take discrete values:

- coin flips 
- number of arrivals

```{code-cell} python3
coin = np.random.binomial(1,0.5, size=40)
print(coin)
```

Others take continuous values:

- height 
- temperature 

```{code-cell} python3
height = np.random.normal(170,8,size=40)
print(height)
```

Cenceptually: 

- Discrete distributions assign probability to specific values. 
- Continuous distributions assign probability to range.

## Why does machine learning care about distributions?

Machine learning is often described as "**Learning patterns from data"**

A more precise statement is:
- Machine learning attempts to approximate the underlying distributino.

Examples:
- Regression aims to estimate: 
$$E [Y |X]$$
- Classification aims to estimate:
$$P(Y|X)$$

These are not arbitrary constructs.

They are properties of the data-generating process - a model is a simplified representation of the true distribution. 

## What are we really learning?

We return to the original question:

**If observed values keep changing, what are we actually trying to learn?**

we are not trying to memorize individual observations, we are trying to understand the structure that generates them.

- A **distribution** describes how data is generated
- The **expectation** describes its center

Statistics begins when we move from individual observations to the hidden structure that produces them. 