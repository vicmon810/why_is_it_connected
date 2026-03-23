---
kernelspec:
    name: python3
    display_name: Python 3
    language: python
---

# Chapter 2: From Scalars to Vectors to Matrices

## Why do we need structure?

In Chapter 1, we said that data can be represented as numbers. But real-world data is rarely just a single number often it comes in groups. 

To work with data effectively, we need a way to organize these numbers.

- Scalar(one number)
- Vector(a list of numbers)
- Matrix(a table of numbers)
  
## Scalar - a single value

A scalar is just one number. 

Think of it as measuring *one thing*:

- temperature = 20 
- age = 25
- price = 100 


## Vector - a list of values

A vector is a list of numbers. 

Think of it as describing one object using multiple measurements. 

For example, a person can be described by:
- height = 170
- weight = 65
- age = 39

we combine them into one vector

```{code-cell} python3
x = [170, 65, 39]
```

A vector represents *one data point with mutiple features*.

## Matrix - a table of values

A matrix is a table of numbers.

Think of it as many data points stacked together.

```{code-cell} python3
X = [
    [170, 65, 25],
    [180, 75, 30],
    [160, 55, 22]
]
```


Now We connect the three ideas:
- Scalar -> one number
- Vector -> one data point
- Matrix -> many data points

Therefore we can now understand why data grows in structure from a single value to a list and a list to a table.
