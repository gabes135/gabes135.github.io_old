---
title: "Equation of Motion"
permalink: /pitches/eqs-of-motion/
excerpt: "The forces that act on a pitched baseball."
last_modified_at: 2019-06-24T15:39:00-08:00
toc: true
mathjax: true
---
## Setting up the Problem
For those who've taken an introductory Mechanics class, mapping the trajectory of a projectile should be a familiar problem. If you haven't, you've likely thrown a ball and observed that it follows a parabolic path. So what differentiates the two starkly different types of motion? The keys factors that add complexity to this beginner level physics problem are **spin** and **speed**, which I will explore and work through below. 

## Free Body Diagram
Just as in any Mechanics problem, the first step is to analyze the forces acting on the object of interest and draw out the object's free body diagram. As mentioned in the introduction the three forces in play are
* Force of Gravity: $ \vec{F_G} = -mg \hat{z} $
* Drag Force: $ \vec{F_D} = -\frac{1}{2}C_D \rho A \vec{v} $
* Magnus Force: $ \vec{F_M} = \frac{1}{2}C_L(\omega) \rho A \hat{\omega} \times \vec{v}  $

The variables in the above equations are:

| Variable        | Defintion           | Notes  |
| ------------- |:-------------:| -----:|
| $m$      		| Mass of the baseball | $0.145\textrm{kg}$ |
| $g$      		| Gravitational acceleration | $\sim 9.81 \textrm{m/s}$ |
| $C_D$     | Drag coefficient      |   Depends on geometry of the baseball, $\sim 0.3$ |
| $\rho$ | Density of air    |    Depends on climate, $\sim 1.23 \textrm{kg/m}^3$ |
| $A$      		| Cross-sectional area of baseball | $4 \pi r^2$ where $r$ is the radius of the baseball |
| $\vec{v}$     | Velocity vector of the baseball     | Defined in coordinate system shown below |
| $\vec{\omega}$ | Spin vector of the baseball   | Magnitude is baseball's spinrate and direction follows right hand rule|
| $C_L(\omega)$ | Lift coefficient   |    Depends on the geometry and spin rate of the baseball |

The corresponding free diagram and cooridante system is shown on the below. 

<img align="middle"
     width="25%"
     height="35%"
     src="/assets/figures/magnus.png">&nbsp;
<img align="middle"
     width="70%"
     height="70%"
     src="/assets/pitches/coordinates.jpg">

## Net Force and Acceleration
After we've defined the relevant forces, the instantaneous acceleration of the baseball can be derived:

$$ \vec{F_G} + \vec{F_D} + \vec{F_M} = \frac{1}{2}C_L(\omega) \rho A \hat{\omega} \times \vec{v} -\frac{1}{2}C_D \rho A \vec{v}  -mg \hat{z} = m\vec{a} $$


This equation gives the acceleration of the baseball at any point along its trajectory, but the data available from Statcast only gives us the velocity, position, and spin data at a single, initial point along the pitch's path. How can we derive the entire trajectory from just this one set of values? The solution to this issue is to use numerical integration to interpolate the these paramters along the trajectory.





