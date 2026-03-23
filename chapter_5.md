---
kernelspec:
    name: python3
    display_name: Python 3
    language: python
---


# Chapter5. Matrices as Transformations

In this Chapter we will answer the following questions:

- <strong>What is a matrix transformation and how to interpret one?</strong>

- <strong>What are common types of matrix transformations?</strong> 

### What is a matrix transformation?

In mathematics and computer science a matrix transformation is just a function. It takes a vector as input and outputs a new vector.

We write $A\mathbf{v} = \mathbf{v}'$ to say that we apply the matrix $A$ to the vector $\mathbf{v}$ to get a new vector $\mathbf{v}'$. The matrix moves


### What are common types of matrix transformations?

#### (1) Scaling

The idea: multiply each component of a vector by some number. You're stretching or squishing along each axis independently.



Real world scenario: imagine v\mathbf{v}
$\mathbf{v}$ represents a person's data — height (1m) and weight (2kg, simplified). Your two features are on completely different scales. The scaling matrix stretches each dimension so they're comparable. This is also known as standardisation in Data Science.

#### (2) Rotation

The idea: spin the vector around the origin by some angle. Nothing stretches or shrinks — the arrow just points in a new direction.

This is a 90° rotation.

Real world scenario: imagine v\mathbf{v}
$\mathbf{v}$ is a 2D dataset where feature 1 and feature 2 are correlated (a tilted cloud of points).
PCA finds a rotation matrix that spins your axes to align with the actual spread of the data. After rotation, the new "feature 1" captures the most variance, and the new "feature 2" captures the rest.

#### (3) Projection

The idea: flatten a vector onto a line or plane. You lose information — the result lives in a lower-dimensional space.

Real world: imagine v\mathbf{v}
$\mathbf{v}$ is a student's actual exam score.
Linear regression finds the best-fit line through your data, and the fitted values y^\hat{\mathbf{y}}
y^​ are the projection of your observed scores onto that line. The residuals — the errors — are exactly the part of v\mathbf{v}
v that got "dropped" by the projection. Geometrically, residuals are always perpendicular to the fitted line.

#### (4) Shear

The idea: push one axis sideways in proportion to the other. Squares become parallelograms. Nothing scales, nothing rotates — things just slant.

The y component stayed the same. 
The x component got pushed by the value of y.

Real world: imagine v\mathbf{v}
v is a data point entering a neural network layer. The weight matrix is a general linear transformation — it shears, scales, and rotates the data representation all at once. After many such layers, the network has warped the data into a shape where a simple boundary can separate cats from dogs, spam from not-spam, and so on.

### How do these terms relate between CS, Statistics and Data science?

| Transformation | Computer Science | Statistics | Data Science |
|---|---|---|---|
| **Scaling** | Normalisation / coordinate scaling | Standardisation ($z$-score), variance stabilisation | Feature scaling, data preprocessing |
| **Rotation** | Coordinate system change, camera transform | Change of basis, eigenvector decomposition | PCA, whitening |
| **Projection** | Orthographic projection (3D → 2D), shadow mapping | OLS regression, hat matrix $H = X(X^TX)^{-1}X^T$ | Dimensionality reduction, linear regression |
| **Shear** | Affine transform, texture mapping | Correlated variable transform | Fully connected layer (neural net weight matrix) |
