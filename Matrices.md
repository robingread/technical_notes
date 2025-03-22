tags: #maths

---
# Matrix Multiplication
- Calculates the [dot product](https://en.wikipedia.org/wiki/Dot_product) of the *rows* in the first matrix, and the *columns* in the second.

The size (dimensions) of the resulting matrix from matrix multiplication is determined by the dimensions of the two matrices being multiplied. Specifically, if you multiply an $M \times N$ matrix by an $N \times P$ matrix, the result is a $M \times P$ matrix:

- The **first matrix** has $M$ rows and $N$ columns.
- The **second matrix** has $N$ rows and $P$ columns.
- The **inner dimensions** ($N$ from both matrices) must match for the multiplication to be valid.
- The **outer dimensions** ($M$ and $P$) define the size of the resulting matrix.
## Examples
$$
\begin{bmatrix}
a & b \\
c & d \\
e & f \\
\end{bmatrix}

\cdot

\begin{bmatrix}
g \\
h \\
\end{bmatrix}

= 

\begin{bmatrix}
ag + bh \\
cg + dh \\
eg + fh \\
\end{bmatrix}
$$
---
$$
\begin{bmatrix}
a & b \\
c & d \\
\end{bmatrix}

\cdot 

\begin{bmatrix}
e & f \\
g & h \\
\end{bmatrix}

= 

\begin{bmatrix}
(ae + bg) & (af + bh) \\
(ce + dg) & (cf + dh)
\end{bmatrix}
$$

---
$$
\begin{bmatrix}
a & b & c \\
d & e & f \\
\end{bmatrix}

\cdot

\begin{bmatrix}
g & h \\
i & j \\
k & l \\
\end{bmatrix}

= 

\begin{bmatrix}
(ag + bi + ck) & (ah + bj + cl) \\
(dg + ei + fk) & (dh + ej + fl)
\end{bmatrix}
$$
---
$$
\begin{bmatrix}
a & b \\
c & d \\
e & f \\
\end{bmatrix}

\cdot 

\begin{bmatrix}
g & h & i \\
j & k & l \\
\end{bmatrix}

= 

\begin{bmatrix}
(ag + bj) & (ah + bk) & (ai + bl) \\
(cg + dj) & (ch + ck) & (ci + dl) \\
(eh + fj) & (eh + fk) & (ei + fl) \\
\end{bmatrix}
$$
---
$$
\begin{bmatrix}
a & b \\
c & d \\
e & f \\
h & i \\
\end{bmatrix}

\cdot 

\begin{bmatrix}
j & k & l \\
m & n & o \\
\end{bmatrix}

= 

\begin{bmatrix}
(aj + bm) & (ak + bn) & (al + bo) \\
(cj + dm) & (ck + dn) & (cl + do) \\
(ej + fm) & (ek + fn) & (el + fo) \\
(hj + im) & (hk + in) & (hl + io) \\
\end{bmatrix}
$$
# Identity Matrix

$$
\mathbf{I}_{3} = \begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1 \\
\end{bmatrix}
$$

Identity matrices are symmetrical:
$$
\mathbf{I}_{3} = (\mathbf{I}_{3})^{T}
$$
