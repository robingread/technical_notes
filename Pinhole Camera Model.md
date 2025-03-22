tags: #computer_vision #ROS #maths 
related: [[Matrices]]
# Camera Intrinsics Matrix
## Mapping from 3D to 2D
The mapping from the 3D world to the 2D world is given by the following equations, where $u$ and $v$ represent the x and y coordinates in the image respectively:
$$
u = f_{x} \cdot \frac{X}{Z} + c_{x}
$$
$$
v = f_{y} \cdot \frac{Y}{Z} + c_{y}
$$
To address why adding the $c_x$ on the right hand side, this is to ensure that when $X=0$, $u=cx$.

These equations can be represented in matrix format, where $K$ is the *intrinsics* matrix:

$$
\mathbf{K} = 
\begin{bmatrix}
f_{x} & 0 & c_{x} \\ 
0 & f_{y} & c_{y} \\
0 & 0 & 1
\end{bmatrix}
$$
Projecting a point $[X, Y, Z]$ into the image is done by:

$$
\begin{bmatrix}
u \\ v \\ 1
\end{bmatrix} 
= 
\begin{bmatrix}
f_{x} & 0 & c_{x} \\ 
0 & f_{y} & c_{y} \\
0 & 0 & 1
\end{bmatrix} \cdot 
\begin{bmatrix}
\frac{X}{Z} \\ \frac{Y}{Z} \\ 1
\end{bmatrix}
$$
# Mapping from 2D to 3D
Mapping from an image back to the world coordinates is done by:
$$
\frac{X}{Z} = \frac{u - c_x}{f_x}
$$
$$
\frac{Y}{Z} = \frac{v - c_y}{f_y}
$$
More concretely, if you are working with Depth images, then you know $Z$, so:
$$
X = \frac{u - c_x}{f_x} \cdot Z
$$
$$
Y = \frac{v - c_y}{fy} \cdot Z
$$

To be expressed in matrix form, this requires the *inverse* of the intrinsics matrix, $K^{-1}$:

$$
\mathbf{K^{-1}} = 
\begin{bmatrix} 
\frac{1}{f_x} & 0 & -\frac{c_x}{f_x} \\
0 & \frac{1}{f_y} & -\frac{c_y}{f_y} \\
0 & 0 & 1 \end{bmatrix}
$$
The full matrix expression:
$$
\begin{bmatrix} \frac{X}{Z} \\ \frac{Y}{Z} \\ 1 \end{bmatrix} 
= 
\begin{bmatrix} 
\frac{1}{f_x} & 0 & -\frac{c_x}{f_x} \\
0 & \frac{1}{f_y} & -\frac{c_y}{f_y} \\
0 & 0 & 1 \end{bmatrix}
\cdot 
\begin{bmatrix} u \\ v \\ 1 \end{bmatrix}
$$

# Projection Matrix
The Projection Matrix is a 3x4 matrix used to translate points observed by the camera to the world coordinates, given the pose of the camera known in the world coordinate system. It takes the form:
$$
\mathbf{P} = \mathbf{K} \cdot
\begin{bmatrix}
\mathbf{R} | \mathbf{t}
\end{bmatrix}
$$

Where:
- $\mathbf{K}$ is the camera *instrinsics* matrix.
- $\mathbf{R}$ is the *extrinsic* rotation matrix
- $\mathbf{t}$ is the *extrinsic* translation

We can expand this equation:
$$
\mathbf{P} =
\begin{bmatrix}
f_{x} & 0 & c_{x} \\ 
0 & f_{y} & c_{y} \\
0 & 0 & 1
\end{bmatrix}
\cdot
\begin{bmatrix}
r_11 & r_12 & r_13 & t_x \\
r_21 & r_22 & r_23 & t_y \\
r_31 & r_32 & r_33 & t_z \\
\end{bmatrix}
$$

To multiply a $3 \times 3$ matrix by a $3 \times 4$ matrix, the operation is **not defined** directly, because the number of columns in the first matrix (3) does not match the number of rows in the second matrix (3). Matrix multiplication requires that the number of columns in the first matrix equals the number of rows in the second matrix.

However, if you mean a situation where you're multiplying a $3 \times 3$ intrinsic matrix $\mathbf{K}$ with a $3 \times 4$ matrix consisting of rotation and translation, like $[\mathbf{R} | \mathbf{t}]$, here’s how it works.

You **multiply** a $3 \times 3$ matrix $\mathbf{K}$ with a $3 \times 4$ matrix $\begin{bmatrix} \mathbf{R} | \mathbf{t} \end{bmatrix}$, which gives you a new $3 \times 4$ matrix.

### The Process of Multiplying $\mathbf{K} \cdot [\mathbf{R} | \mathbf{t}]$:

Given:

- $\mathbf{K} = \begin{bmatrix} f_x & 0 & c_x \\ 0 & f_y & c_y \\ 0 & 0 & 1 \end{bmatrix}$​ (3x3 intrinsic matrix).
- $[\mathbf{R} | \mathbf{t}] = \begin{bmatrix} r_{11} & r_{12} & r_{13} & t_x \\ r_{21} & r_{22} & r_{23} & t_y \\ r_{31} & r_{32} & r_{33} & t_z \end{bmatrix}$ (3x4 extrinsic matrix).

The multiplication $\mathbf{P} = \mathbf{K} \cdot [\mathbf{R} | \mathbf{t}]$ is done as follows:

$$
\mathbf{P} = \begin{bmatrix} f_x & 0 & c_x \\ 0 & f_y & c_y \\ 0 & 0 & 1 \end{bmatrix} \cdot \begin{bmatrix} r_{11} & r_{12} & r_{13} & t_x \\ r_{21} & r_{22} & r_{23} & t_y \\ r_{31} & r_{32} & r_{33} & t_z \end{bmatrix}
$$

To perform the multiplication:
1. Multiply each row of $\mathbf{K}$ with each column of $[\mathbf{R} | \mathbf{t}]$.
    
    For example, the first element of the first row of $\mathbf{P}$ would be:
    $$P_{11} = f_x \cdot r_{11} + 0 \cdot r_{21} + c_x \cdot r_{31}$$
    
    Similarly, the other elements are computed:
    
$$
P_{12} = f_x \cdot r_{12} + 0 \cdot r_{22} + c_x \cdot r_{32}
$$

$$
P_{13} = f_x \cdot r_{13} + 0 \cdot r_{23} + c_x \cdot r_{33}
$$

$$
P_{14} = f_x \cdot t_x + 0 \cdot t_y + c_x \cdot t_z​
$$
    
2. Repeat this process for the second and third rows of $\mathbf{K}$.
    

Thus, the result of $\mathbf{K} \cdot [\mathbf{R} | \mathbf{t}]$ is a $3 \times 4$ matrix:

$$\mathbf{P} = 
\begin{bmatrix} f_x r_{11} + c_x r_{31} & f_x r_{12} + c_x r_{32} & f_x r_{13} + c_x r_{33} & f_x t_x + c_x t_z \\
f_y r_{21} + c_y r_{31} & f_y r_{22} + c_y r_{32} & f_y r_{23} + c_y r_{33} & f_y t_y + c_y t_z \\
r_{31} & r_{32} & r_{33} & t_z 
\end{bmatrix}$$

This is the projection matrix $\mathbf{P}$, which projects 3D points from world coordinates to the 2D image plane.

# Useful Resources
https://www.youtube.com/watch?v=hUVyDabn1Mg&ab_channel=FirstPrinciplesofComputerVision
https://ksimek.github.io/2013/08/13/intrinsic/