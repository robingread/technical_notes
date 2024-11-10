tags: #computer_vision #ROS 

Following on from the [[Pinhole Camera Model]]

# Disparity
# Projecting Disparity to 3D
## Projection Matrix in ROS `CameraInfo`

In the case of stereo vision, the ROS `sensor_msgs::CameraInfo` messages, the **projection matrix of the right camera** has the format:
$$
\mathbf{P}_R = 
\begin{bmatrix}
f_x & 0 & c_x & -f_x \cdot B \\
0 & f_y & c_y & 0 \\
0 & 0 & 1 & 0 \\
\end{bmatrix}
$$

This makes the assumption that the translation from the right camera to the left is only along the $x$ axis, and is the magnitude of $B$.

$$
\mathbf{P}_R = 
\begin{bmatrix}
f_{x} & 0 & c_{x} \\ 
0 & f_{y} & c_{y} \\
0 & 0 & 1
\end{bmatrix} 
\cdot
\begin{bmatrix}
1 & 0 & 0 & -B \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
\end{bmatrix}
$$
> [!important] 
> The unit of $P_{13}$ is not a pixel or real world unit. Rather it is a scale!
