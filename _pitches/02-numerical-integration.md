---
title: "Numerical Integration"
permalink: /pitches/numerical-int/
excerpt: "Interpolating the trajectory of a pitch."
last_modified_at: 2019-06-25T11:53:00-08:00
toc: true
mathjax: true
---
## Numerical Integration
Given the acceleration, velocity, and position of an object at a single point in time, its position and velocity a short amount of time in the future (or past) can be approximated using numerical techniques. If you're able to update the acceleration at this interpolated moment, the process can be continued up to any point. This is the process used to map the trajectory of a pitch using just its initial paramters.


## Runge Kutta 2
There are many variations of computational numerical integration techniques for interpolatting a changing varaible using its derivatives (in our case mapping position using its first derivative, velocity, and second derivative, acceleration). However, they all follow a similar process:
1. Calculate the object's acceleration vector using its position and velocity
2. Multiply each component of the object's acceleration and velocity vectors by a small time increment  $dt$
3. Use the results as approximate changes in the components of the object's velocity and position, respectively
4. Repeat the process using the new position and velocity until the desired time elapsed/distance travelled is achieved

The accuracy of this method can be improved by using a trial step at the midpoint of the time interval  $dt$ to cancel out lower-order error terms. This technique is referred to as Runge Kutta 2 (RK2) and is applied as follows:


<img align="right"
     width="25%"
     height="35%"
     src="https://commons.wikimedia.org/wiki/File:Runge-Kutta_slopes.svg#/media/File:Runge-Kutta_slopes.svg">
$ \vec{k _ { 1, v }} = dt * \vec{a} \left(\vec{v} _ { n } \right) $

$ \vec{k _ { 1, x }} = dt * \vec{v} _ { n } \left(\vec{x} _ { n } \right) $


$ \vec{k _ { 2, v }} = dt * \vec{a} \left(\vec{v} _ { n } + \frac{1}{2} \vec{k _ { 1, v }} \right) $

$ \vec{k _ { 2, x }} = dt * \left(\vec{v} _ { n } + \frac{1}{2} \vec{k _ { 1, v }} \right) $


$\vec{v} _ {n+1} = \vec{v} _ {n} + \vec{k _ { 2, v }} $

$\vec{x} _ {n+1} = \vec{x} _ {n} + \vec{k _ { 2, x }} $

