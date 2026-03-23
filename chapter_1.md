---
kernelspec:
    name: python3
    display_name: Python 3
    language: python
---

# Chapter 1: What is Data


## Let's begin with the simplest question: *What is data?*


At a basic level, data is recorded information. It can be numbers, text, images, or signals collected from the world.

However, the meaning of “data” changes depending on the field. 
- In computer science, data is something that needs to be stored and processed.
- In statistics, data is often viewed as observations drawn from an underlying process.
-  In machine learning, data is used as examples to learn patterns.

Despite these differences, there is a common structure behind most data: it can often be represented as numbers. Once data is represented numerically, we can organize it into different forms such as vectors and matrices, which allow us to analyze and transform it.

### Scalar

A *scalar* is a single numerical value. 

The trem originates from physics, where it refer to a quantity fully described by its magnitude (e.g., temperature,mass).

In data science, we simplify this concept and treat a scalar as a single number. 

$$
 x = 1
$$

```{code-cell} python3
x = 1
print(type(x), x)
```

### Vector

A *vector* is an ordered collection of scalars.

It represents one data point with mutiple features in a multidimensional space.

For example, a person's data might be

- height
- weight
- age

which together form a vector.

Mathematically, a vector is often written as:

$$
x = (1,2,3,4,5)
$$
or as a column vector: 

$$
x = \begin{bmatrix} 1\\2\\3\\4\\5 \end{bmatrix}
$$

These represent the same vector, but in different orientations. 


```{code-cell} python3
lst = [1,2,3,4,5]
print(type(lst),lst)
```

### Matrix is a two-dimensionaly array of numbers. 

It represents *mutiple data points*, where
- each row is a vector(a data point)
- each column is a feature(a variable)

Mathematically: 
$$
x = \begin{bmatrix} 1 & 2 &3 & 4 & 5
\\6&7& 8&9 &10 
\end{bmatrix}
$$

This can be interpreted as :
- 2 data points (rows)
- 5 features(columns)

```{code-cell} python3
lst = [[1,2,3,4,5],
       [6,7,8,9,10]]
print(type(lst), lst)
```

To work with data mathematically, we need structured representations. The simplest of these are scalars, vectors and matrices.
