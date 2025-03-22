tags: #ROS #robotics

---
# North-East-Down (NED)
The **NED (North-East-Down)** coordinate system is a common local geodetic coordinate system used in navigation, robotics, and geospatial sciences. It's often used to represent positions and movements on the Earth's surface, especially for applications like drones, autonomous vehicles, or underwater robotics, where navigation and orientation are crucial.

## **Key Features of the NED Coordinate System:**

1. **Axes:**    
    - **North (N)**: The X-axis points towards true north (geodetic north), which is typically aligned with the Earth's axis of rotation.
    - **East (E)**: The Y-axis points towards the east, perpendicular to the North axis in the horizontal plane.
    - **Down (D)**: The Z-axis points downward, toward the center of the Earth, which is opposite to the direction of gravity at a given point.
    
2. **Orientation:**
    - The **North** direction corresponds to the positive X-axis.
    - The **East** direction corresponds to the positive Y-axis.
    - The **Down** direction corresponds to the negative Z-axis (note that "down" is negative, as it's oriented opposite to the direction of the standard Z-axis in most coordinate systems).

3. **Use in Navigation:**
    - The NED system is typically used for local-level navigation where precise coordinates in terms of latitude, longitude, and altitude (or depth) are required. The **North-East** plane is horizontal, and the **Down** direction represents vertical movement (altitude change).

4. **Coordinate Transformation:**
    - The NED coordinate system is often used in **sensor fusion** for robotics and **aerospace** applications, where the system needs to know its relative position, velocity, or acceleration within a local area rather than using global coordinates like latitude and longitude.
    - To transform between global coordinate systems (like **latitude/longitude/altitude**) and local NED coordinates, the **initial reference point** (e.g., a known GPS position) is used as the origin.
## **Conversion from Geodetic Coordinates (Lat, Lon, Alt) to NED:**

Given a reference point at a known geodetic location (latitude, longitude, and altitude), you can transform other points' geodetic coordinates to the NED frame using a transformation matrix or series of equations. Typically, the transformation involves:

- Calculating the local tangent plane (a small patch on the Earth’s surface where we approximate the Earth as flat).
- Using the **ECEF (Earth-Centered, Earth-Fixed)** frame as an intermediate step, which converts global coordinates to NED coordinates.

## **Example of Transformation Process:**

5. Convert geodetic coordinates (latitude, longitude, altitude) to **ECEF** (Earth-Centered, Earth-Fixed) coordinates.
6. Calculate the relative position (difference in latitude, longitude, and altitude) between the point of interest and the reference point.
7. Apply a coordinate transformation to convert the relative position into the **NED** system, which will give you the North, East, and Down components.

## **Advantages of NED:**

- **Local Reference System**: NED is ideal for local, short-range navigation where accurate position and motion data are needed within a small region. It allows for easy integration of local sensors (like IMUs or Doppler sensors) to estimate position, velocity, or acceleration.
- **Consistency in Mapping and Sensors**: It simplifies the interpretation of sensor data, especially in autonomous systems, where keeping the coordinate system locally fixed and aligned with physical reference frames is useful.
- **Alignment with Gravity**: The "Down" axis points in the direction of gravity, which makes it easier to integrate orientation data, especially when using accelerometers or gyroscopes.

## **Applications of NED:**

- **Robotics**: Used in mobile robot navigation, especially in aerial and underwater robots (e.g., drones, AUVs).
- **Aerospace**: The NED frame is frequently used in aircraft navigation systems to describe the relative motion of an aircraft.
- **Geospatial Science**: For precise surveying, mapping, and geolocation applications.
- **Navigation and Localization**: In GPS-based systems, NED is often used for local reference frame transformations in autonomous systems like cars or ships.

## **Summary of Axes in NED:**

- **X-axis (North)**: Positive direction is North.
- **Y-axis (East)**: Positive direction is East.
- **Z-axis (Down)**: Positive direction is Down (towards the Earth).

In conclusion, the NED coordinate system is particularly useful for applications where you need to measure motion or position in a local, Earth-centered context with respect to the North-East-Down orientation, and it's extensively used in navigation, robotics, and sensor fusion.

# East-North-Up
The **ENU (East-North-Up)** coordinate system is another widely used local geodetic coordinate system, similar to NED, but with a different orientation for the vertical axis. It is often used in navigation, geodesy, robotics, and applications involving GPS or other sensor data.

### **Key Features of the ENU Coordinate System:**

1. **Axes:**
    
    - **East (E)**: The X-axis points towards true east (along the local meridian), in the horizontal plane.
    - **North (N)**: The Y-axis points towards true north (aligned with the local meridian), also in the horizontal plane.
    - **Up (U)**: The Z-axis points upward, opposite to the direction of gravity, and it is aligned with the local vertical (toward the sky).
2. **Orientation:**
    
    - The **East** direction corresponds to the positive X-axis.
    - The **North** direction corresponds to the positive Y-axis.
    - The **Up** direction corresponds to the positive Z-axis, aligned with the gravitational vector at the location of interest.
3. **Use in Navigation:**
    
    - The ENU system is typically used when you need a **local coordinate system** based on a **local tangent plane**. It is often preferred for tasks involving **GPS systems**, geodesy, and positioning systems, especially when you are working in small regions where the Earth’s curvature can be ignored.
    - It is common in applications like **robotics**, **surveying**, and **geospatial sciences**, where accurate local positioning and movement are important.
4. **Coordinate Transformation:**
    
    - To transform between **geodetic coordinates** (latitude, longitude, altitude) and the **ENU** system, you typically start with a reference point (latitude, longitude, altitude) and use a series of coordinate transformations.
    - The transformation usually involves first converting the geodetic coordinates to a global reference system (like **ECEF** - Earth-Centered, Earth-Fixed), then performing a rotation to align the coordinate axes with the ENU system based on the reference point.

### **Conversion from Geodetic Coordinates (Lat, Lon, Alt) to ENU:**

Given a reference point at known geodetic coordinates, you can convert other geodetic positions to ENU coordinates using these steps:

1. **Convert geodetic coordinates** (latitude, longitude, altitude) to **ECEF coordinates** (Earth-Centered, Earth-Fixed).
2. **Calculate the difference** in position between the reference point and the point of interest (the point you're converting).
3. **Apply a transformation matrix** to convert the difference in position to the ENU frame.

The transformation from geodetic coordinates (latitude, longitude, altitude) to the ENU coordinate system involves:

- **ECEF conversion**: From global geodetic coordinates to Earth-Centered, Earth-Fixed coordinates.
- **ENU transformation**: Mapping ECEF coordinates to the ENU frame by using the reference point’s position.

### **Advantages of ENU:**

- **Alignment with Local Gravity**: The **Up** axis points directly upward, which is aligned with the direction of gravity at the given location. This makes it easier to integrate orientation and elevation data.
- **Intuitive Coordinate System**: The ENU system is intuitive for many geospatial applications because the **Up** direction aligns with the vertical, and **East** and **North** are standard directions on a map.
- **Simple for Local Navigation**: Like NED, the ENU coordinate system is commonly used in local, small-scale navigation where Earth's curvature can be neglected, and you're interested in precise positioning within a limited area.

### **Applications of ENU:**

- **GPS and GNSS Systems**: ENU is frequently used in GPS-based systems, where the position of a moving object is tracked relative to a fixed reference point, such as a base station.
- **Robotics**: Many robots, particularly those used in outdoor or large-scale navigation, use ENU coordinates to localize themselves based on GPS or visual odometry.
- **Geodesy**: In surveying and geodesy, ENU is often used for precise measurements in small areas, especially when working with reference stations or geodetic control points.
- **Mapping and Positioning**: For creating local maps or when aligning data with geographic regions, the ENU system helps in maintaining a locally consistent frame of reference.
- **Aerospace**: ENU is used for navigation and positioning of aircraft, where you need to track relative motion and orientation with respect to a local, fixed reference point.

### **Summary of Axes in ENU:**

- **X-axis (East)**: Points east, along the local east-west axis.
- **Y-axis (North)**: Points north, along the local north-south axis.
- **Z-axis (Up)**: Points upward, away from the Earth, aligned with the local gravitational vector.

### **Comparison of ENU and NED:**

- **Orientation of the Vertical Axis**:
    - **ENU** has the **Up** axis pointing **upward**, opposite to the direction of gravity.
    - **NED** has the **Down** axis pointing **downward**, towards the center of the Earth.
- **Coordinate System Usage**:
    - ENU is more commonly used in geospatial and GPS-based applications, where the upward direction aligns with the direction of gravity.
    - NED is often used in aerospace, underwater, and robotics applications where gravity plays an important role, but the downward axis is more intuitive for some systems.

### **Example of Transformation from Lat/Lon/Alt to ENU:**

4. **Step 1:** Convert the geodetic coordinates (latitude, longitude, altitude) of the reference point (say, the base station) to ECEF coordinates.
5. **Step 2:** Convert the geodetic coordinates of the point of interest to ECEF coordinates.
6. **Step 3:** Calculate the difference between the two ECEF positions.
7. **Step 4:** Apply the appropriate transformation matrix to map the difference to the ENU coordinate system.

In conclusion, the **ENU** coordinate system is a highly useful local reference frame for applications where precise, small-scale navigation and positioning are needed, particularly in systems relying on GPS, surveying, and robotics. It is widely adopted in geospatial science, geodesy, and autonomous systems.

# Right Handed-Coordinate System

Perhaps the most commonly used coordinate system, where:

- **X** is forward (along the direction of motion or ahead of the robot),
- **Y** is left (to the left of the robot),
- **Z** is up (in the upward direction, perpendicular to the ground),

is typically referred to as the **robot-centered** or **robot-local** coordinate system. This coordinate system is **right-handed** and is commonly used in **robotics**, particularly in the context of **manipulation**, **motion planning**, and **control**.

### **Right-Handed Coordinate System:**

- **X-axis** points forward (towards the front of the robot).
- **Y-axis** points to the left (to the robot's left side).
- **Z-axis** points upward (perpendicular to the ground, towards the ceiling).

### **Why Right-Handed?**

In a right-handed coordinate system, if you curl the fingers of your right hand from the **X-axis** (forward) to the **Y-axis** (left), your thumb will point in the direction of the **Z-axis** (upward).

### **This Coordinate System is Often Called:**

- **Robot Base Frame** or **Robot Local Frame**: It is a local reference frame used to represent the robot's position, orientation, and movement relative to itself.
- **Body Frame**: Sometimes used to refer to the robot's local coordinate system, as it is fixed to the body of the robot.

This coordinate system is particularly useful when controlling or manipulating a robot, as it provides a consistent way to describe the robot's movements and actions within its own frame of reference, without relying on external coordinate systems like GPS or global maps.

### **Common Applications in Manipulation:**

- **End-Effector Control**: The end-effector (e.g., robot hand, gripper, or tool) is often controlled using this local frame, specifying movements such as "move forward" along the X-axis, "move left" along the Y-axis, or "move up" along the Z-axis.
- **Kinematics and Dynamics**: The robot's joints and links are described relative to this coordinate system, allowing for accurate motion planning and control.

This local frame is fundamental when designing and programming robotic systems that perform tasks like grasping, assembly, or movement in space.
# Camera Optical Frames

The rotation matrix from a standard right-handed coordinate system to a camera coordinate system is:
$$
\begin{bmatrix}
0 & 0 & 1 \\
-1 & 0 & 0 \\
0 & -1 & 0 \\
\end{bmatrix}
$$
# Useful Links
- ROS [REP-105](https://ros.org/reps/rep-0105.html) - Coordinate Frames for Mobile Robots
- ROS [REP-145](https://www.ros.org/reps/rep-0145.html) - Conventions for IMU Sensor Drivers