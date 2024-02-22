:orphan:

.. _odometry:

Odometry
---------

Odometry is defined as the use of data from moving sensors to estimate change in position over time. In particular, the sensors involved are a wheel speed sensor and an Inertial Measurement Unit (IMU).

Inertial Measurement Unit:

Diagram
=======

.. image:: images/odometry_1.png
    :width: 500 px
    :height: 500px
    :alt: "KPI framework Overview"


Odometry signal mainly consist of spacial data, as a term of space coordinates (on the plane, x, y) and yaw angle (for a more detailed description, please refer to this page) with respect to a specific reference system with its origin placed at the beginning of the vehicle starting point. In particular, the reference system is a right-handed Cartesian one, with the x-axis pointing along the the vehicle direction, while the y-axis pointing left on a plane parallel to the ground.

It is important to notice that the x and y positions are limited due to hardware reasons in the range [0, 65.52]m, thus they under/overflow when those limits are exceeded. By definition, also the yaw angle is limited in the range [0, 360]°. The odometry signals are recorded with a default sampling frequency which is fixed in time.



Due to the definition of the odometry signal limits, a x-y pair of values does not define uniquely the position of the vehicle with respect to the starting point of the motion: an undefined number of different spacial configurations corresponds to the pair (x, y), such as shown in Fig. (a). Additionally, if a line is continuously drawn in time reporting the x, y odometry values on a graph Fig. (b) is the result which can be obtained. For this reason, the odometry signal alone is not sufficient to describe the vehicle motion and needs to be "unwrapped", evaluating an accumulated odometry.
