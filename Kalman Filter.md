tags: #maths #robotics 
related: [[Matrices]], [[Covariance Matrices]]

---
# Overview of Kalman Filter Matrices

| Matrix           | Description           | Dimensions   |
| ---------------- | --------------------- | ------------ |
| $\mathbf{x}_{k}$ | State estimate vector | $n \times 1$ |
| $\mathbf{z}_{k}$ | Measurement vector    | $m \times 1$ |
Where:
- $k$ is the current time step
- $m$ is the number of measurements 
## State Estimation Vector ($\mathbf{x}_{k}$)

This is the vector that captures the system state at time $k$. These are the quantities that are being estimated by the filter.

Dimensions: $n \times 1$, where $n$ is the number of state variables.
Example: For a robot tracking 2D position and velocity:

$$
\mathbf{x}_{k}
=
\begin{bmatrix}
x_{k} \\
y_{k} \\
\dot{x}_{k} \\
\dot{y}_{k} \\
\end{bmatrix}
$$

## Measurement Vector ($\mathbf{z}_{k}$)
## State Transition Matrix ($\mathbf{F}_{k}$)
## Process Noise Covariance Matrix ($\mathbf{Q}_{k}$)
## Measurement Matrix ($\mathbf{H}_{k}$)
- Relates the state vector ($\mathbf{x}_{k}$) to the measurement vector ($\mathbf{z}_{k}$).
- It is used to map the predicted state to the measurement space, allowing us to calculate an error between the actual measurement and the predicted measurement.
- Dimensions: $m \times n$, where rows correspond to the measurement vector, columns correspond to the state vector.
- Example: For a robot which can only measure position:
$$
\mathbf{H}_{k}
=
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
\end{bmatrix}
$$
## Measurement Noise Covariance Matrix ($\mathbf{R}_{k}$)
