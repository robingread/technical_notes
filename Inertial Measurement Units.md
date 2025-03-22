tags: #robotics 

---

These sensors measure:
- Angular velocities about the $x$, $y$ and $x$ axis using a **Gyroscope**.
- Linear accelerations along the $x$, $y$ and $z$ axis using a **Accelerometer**.
- Orientation with respect to the earth's magnetic field using a **Magnetometer**.

In ROS Systems, they are expected to be in a [[Robot Coordinate Systems#East-North-Up|East-North-Up]] coordinate System
## Gyroscope
- Measures angular velocity (rotation rate) around three axes (X, Y, Z).
- By integrating angular velocity over time, you can estimate orientation changes.
- Problem: Gyroscope readings drift over time due to sensor noise and bias.*
## Accelerometer
- Measures acceleration in three axes, including gravity.
- The gravity vector can be used to estimate tilt (pitch & roll).
- Problem: Can't determine yaw (rotation around the vertical axis) and is sensitive to external accelerations (e.g., movement).
### Bias
- **Constant offset** in the output readings along each axis, even when the IMU is stationary.
- **Misalignment Errors** between the output values and the IMU frame itself.
- **Scale errors** where the values are either over or under the true magnitude.
- **Temperature** can effect the output readings due to mechanical and electrical effects on the materials within the sensor.
- **The effect** of these is errors in the pitch and raw estimate as well as the linear velocity and distance calculations.
## Magnetometer
- Measures the earth's magnetic field to determine an absolute orientation relative to [magnetic north](https://en.wikipedia.org/wiki/North_magnetic_pole).
- Used to help correct direct in the Yaw from the Gyroscope.
- Susceptible to magnetic interference. 
## Sensor Fusion
In order to get an accurate estimate of the 6Dof state of the IMU, sensor fusion is used. There are three types of filter often used to estimate the state:
- Complementary Filter (simple, low-latency)
- [[Kalman Filter]] (statistical, more computationally expensive)
- Madgwick/Mahony Filters (optimised for real-time calculations)