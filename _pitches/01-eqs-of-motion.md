---
title: "Equations of Motion"
permalink: /pitches/eqs-of-motion/
excerpt: "The forces that act on a pitched baseball and the resultalt motion."
last_modified_at: 2019-06-24T15:39:00-08:00
toc: true
mathjax: true
---
## Setting up the Problem
For those who've taken an introductory Mechanics class, mapping the trajectory of a projectile should be a familiar problem. If you haven't, you've likely thrown a ball and observed that it follows a parabolic path. So what differentiates the two starkly different types of motion? The keys factors that add complexity to this beginner level physics problem are **spin** and **speed**, which I will explore and work through below. 

## Free Body Diagram
Just as in any Mechanics problem, the first step is to analyze the forces acting on the object of interest and draw out the object's free body diagram. As mentioned in the introduction the three forces in play are
* Force of Gravity: $ F_G = -mg \hat{z} $
* Drag Force: $ F_d = -\frac{1}{2}C_D \rho A \vec{v} $
* Magnus Force: $ F_m = -\frac{1}{2}C_L(\omega) \rho A \vec{v} \times \hat{\omega} $

The variables in the above equations are:

| Variable        | Defintion           | Notes  |
| ------------- |:-------------:| -----:|
| $g$      		| Gravitational acceleration | $\sim 9.81 \textrm{m/s}$ |
| $C_D$     | Drag coefficient      |   Depends on geometry of the baseball, $\sim 0.3$ |
| $\rho$ | Density of air    |    Depends on climate, $\sim 1.23 \textrm{kg/m}^3$ |
| $A$      		| Cross-sectional area of baseball | $4 \pi r^2$ where $r$ is the radius of the baseball |
| $\vec{v}$     | Velocity vector of the baseball     | Defined in coordinate system shown below |
| $\vec{\omega}$ | Spin vector of the baseball   | Magnitude is baseball's spinrate and direction follows right hand rule|
| $C_L(\omega)$ | Lift coefficient   |    Depends on the geometry and spin rate of the baseball |



<img align="right"
     width="25%"
     height="35%"
     src="/assets/figures/magnus.png">
<img align="left"
     width="25%"
     height="25%"
     src="/assets/pitches/coordinates.jpg">

The corresponding free diagram and cooridante system is shown on the right. 