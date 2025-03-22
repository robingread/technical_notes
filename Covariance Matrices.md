tags: #robotics #maths 
related: [[Matrices]]

---

Covariance Matrices, in the context of robot sensor data, are matrices that represent the uncertainty about the sensor readings themselves. They take the form of a square $M \times M$ matrix where $M$ represents the different dimensions of the sensor reading.

$$
C = \begin{bmatrix}
Var(X) & Cov(X,Y) & Cov(X,Z) \\
Cov(Y,X) & Var(Y) & Cov(Y, Z) \\
Cov(Z,X) & Cov(Z,Y) & Var(Z)
\end{bmatrix}
$$

Covariance matrices have the following properties:
- Symmetrical: $C = C^{T}$
- Singular (it is non-invertable): $det(C) = 0$

There two main aspects to the matrix:
- The *diagonal* values
- The *off-diagonal* values
# Diagonal Values
The diagonal values represent the **variance** for each of the dimensions of the sensor reading. These values **must** be positive and reflect the units that the sensor data is in.

$$
C = \begin{bmatrix}
Var(X) & 0 & 0 \\
0 & Var(Y) & 0 \\
0 & 0 & Var(Z)
\end{bmatrix}
$$
$$
Var(X) = \frac{1}{N} \sum_{i=0}^{N}(x_{i} - \bar{x})^2
$$
$$
\bar{x} = \frac{1}{N} \sum_{i=0}^{N} x_{i}
$$
Where:
- $N$ is the number of samples.
- $\bar{x}$ is the mean of the samples: $\bar{x} = \frac{1}{N} \sum_{i=0}^{N} x_{i}$
- $x_{i}$ is the value of sample $i$.

# Off-Diagonal Values
The off-diagonal values represent how different data dimensions are related. More specifically, how they are *correlated*. 

$$
Cov(X,Y) = \frac{1}{N-1} \sum_{i=0}^{N} (x_{i} - \bar{x})(y_{i} - \bar{y})
$$
This correction (using $N−1$ instead of $N$) accounts for the fact that we're working with a **sample** rather than the entire population.

The reason that the covariance matrix is symmetrical is because of how this equation is formulated:

$$
Cov(X, Y) = Cov(Y, X)
$$