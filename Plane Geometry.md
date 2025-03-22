tags: #maths 

---
## Constructing a Plane
The typical form of a plane is the [Hessian Normal](https://en.wikipedia.org/wiki/Hesse_normal_form):
$$
ax + by + cz + d = 0
$$
Where:
- $\begin{bmatrix}a & b & c\end{bmatrix}$ represents the normal unit-vector to of the plane.
- $\begin{bmatrix}x & y & z\end{bmatrix}$ represents a point on the plane.
- $d$ is a signed perpendicular distance from the origin to the plane

In vector form, this can we written as:
$$
\mathbf{\hat{n}} \cdot \mathbf{x} + d = 0
$$
## Distance Between a Point and a Plane
Using this geometry, we can calculate the distance, $D$ a point $\mathbf{q}$ is from a plane:

$$
D = \mathbf{\hat{n}} \cdot \mathbf{q} + d
$$
## Projecting Points onto a Plane
Given the hessian coefficients, we can project point $\mathbf{q}$ onto to plane and get the projected coordinate, $\mathbf{q_{proj}}$:

$$
\mathbf{q_{proj}} = \mathbf{q} - (\mathbf{\hat{n}} \cdot \mathbf{q} + d) \mathbf{\hat{n}}
$$
Broken down:
- Compute the signed distance $t$ from $\mathbf{q}$ to the plane:
$$
t = \mathbf{\hat{n}} \cdot \mathbf{q} + d
$$
- Move the point along the normal vector:
$$
\mathbf{q_{proj}} = \mathbf{q} - t \mathbf{\hat{n}}
$$
## Useful Links
https://mathworld.wolfram.com/HessianNormalForm.html