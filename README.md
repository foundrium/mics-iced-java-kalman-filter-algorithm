# Kalman Filter

A few quotes to start

> For statistics and control theory, Kalman filtering, also known as linear quadratic estimation (LQE), is an algorithm that uses a series of measurements observed over time, including statistical noise and other inaccuracies, and produces estimates of unknown variables that tend to be more accurate than those based on a single measurement alone, by estimating a joint probability distribution over the variables for each timeframe.

[Citation](https://en.wikipedia.org/wiki/Kalman_filter)

> The Kalman Filter is one of the most important and common estimation algorithms. The Kalman Filter produces estimates of hidden variables based on inaccurate and uncertain measurements. Also, the Kalman Filter predicts the future system state based on past estimations.

[Citation](https://www.kalmanfilter.net/default.aspx)

Kalman filters are one of the most important algorithms in computer science and its uses reaches across a large number of technology and scientific disciplines.

**In its simplest form a Kalman filter can predict an unknown variable based on previous measurements and a current measurement _despite uncertainty or error in the measurement process_.**

# Example

Lets look at a simple example: [Citation](https://www.kalmanfilter.net/alphabeta.html)

If we wanted to estimate the position of a constant velocity aircraft in one dimension, how would we do it? Well let's make a few assumptions first

- We have a sensor that will measure the position of our aircraft such as radar
- Since we are in one dimension, the aircraft is staying at a constant altitude
- Since we are in one direction, the aircraft is moving away from our sensor
- The sensor measures the position of the aircraft on a uniform and periodic basis such as every one minute.

![graph](/docs/example01.png "graph")
[Citation](https://www.geeksforgeeks.org/dijkstras-shortest-path-algorithm-greedy-algo-7/)

If we lived in a theoretical world where an aircraft could in fact remain at a constant velocity, then it is trivial to compute the estimated distance. Distance is just velocity multiplied by the the time that has passed or

$$
\Delta x = \upsilon t
$$

We know though that we don't live in a perfect world. There could be any number of real world issues that occur to break the theoretical model

- Perhaps the aircraft hits additional air resistenance and is required to decelerate temporarily
- The radar is not properly calibrated
- A pilot accelerates because its more fun

What do you imagine will happen if we continue to estimate the position of an aircraft based on the simple formula above? Above time, more error will accumulate from either our sensor measurements or other real world challenges until the estimated position and the actual position are not even close to each other.

The Kalman Filter is an algorithm that helps provide more accurate estimates for situations such as this.

# Kalman Filter

Remember we said that an alorithm is just a set of tasks performed to accomplish a goal. Here is the algorithm in a flow chart form

![kalman-algorithm](/docs/kalman-filter-algorithm.png "kalman-algorithm")
[Citation](https://www.cs.cmu.edu/~rasc/Download/AMRobots5.pdf)

If we simplify that a bit we have

1. Perform initial measurement
2. Perform a second measurement (Kalman filters require at least two initial data points to perform)
3. Receive measurement from sensor
4. Perform estimation
5. Update current history/state with latest estimation
6. Repeat steps 3 through 5.

# Implementation

In this repository you can find an example using a Kalman filter to estimate the position of an object. We are using Python here because the math libraries for Python are typically better than its Java counterparts in terms of depth.

There is some math that is pretty advanced within the implementation of a Kalman filter. Luckily most of that has already been done in libraries like Python's numpy or in FRCs Wplib.

The code referenced here is from [machinelearningspace.com](https://machinelearningspace.com/object-tracking-python/) and can be also found in their Github repository [here](https://github.com/RahmadSadli/Kalman-Filter).
