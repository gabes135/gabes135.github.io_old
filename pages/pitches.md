---
layout: single
title: "Pitch Trajectories"
permalink: /pitches/
auhtor_profile: true 
header:
	image: "/images/header.jpg"
---
# Pitching Trajectory Mapping Using MLB Statcast Data

## PITCHf/x and Statcast
Starting in 2006, a handful Major League Baseball teams implemented the advanced camera system "PITCHf/x" into their stadiums. The cameras allowed detailed pitch speed, spin rate, and spin direction data to be tracked and analyzed in real time. Since its debut, pitch tracking technology has expanded to all stadiums, now under the name "Statcast," and the advanced stats they provide have nearly become household names. 

## Pitch Trajectories
From a Physicist's perspective, the availability of this data presented an oppurtunity to dissect the highlight reel pitches that seem to defy the laws of gravity. Using just the initial conditions of a given pitch, it's complete trajectory, from when it leaves the pitcher's hand to when it hits the catcher's mitt, can be derived, plotted, and analyzed. 

The three dominating forces that play into the motion of a baseball pitch are 
* Force of Gravity
* Drag Force
* Magnus Force

The force of gravity and the drag force are fairly intuitive; gravity on the baseball always acts down towards the ground and the drag force on the baseball always acts in the opposite direction as the pitches velocity (i.e. the direction it is moving in). The magnus force, however, is the seemingly unpredictable, Physics defying force that creates the extreme movement seen, for example, in the pitch below. 

<iframe src="/assets/videos/Sale_Slider.webm"
	width="900"
    height="400"
    align = "center"
	frameBorder="0"	>
</iframe>&nbsp;



<img align="right"
	 width="35%"
     height="35%"
     src="/assets/figures/magnus.png">
The magnus force provides lift to a spinning object in a direction perpendicular to both its velocity and spin axis, as shown in the diagram to the right (courtesy of Alan M. Nathan at the Department of Physics, University of Illinois). The faster the ball is spnning and/or moving, the greater the magnitude of magnus force. Considering these three forces in the equation of motion of the baseball, one can calculate the instantaneous acceleration vector of the moving ball and numerically integrate to trace out the pitch's trajectory. The Chris Sale Slider shown above is traced out below, showing its movement along each axis. 
<iframe src="/assets/videos/sale_sliderall.mp4"
	width="900"
   	height="400" 
    align = "center"	
    frameBorder="0"	>	
</iframe>







