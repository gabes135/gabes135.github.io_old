---
title: "Python Implementation"
permalink: /pitches/python/
excerpt: "Implementing the pitch trajectory interpolation in Python"
last_modified_at: 2019-06-25T14:31:00-08:00
toc: true
mathjax: true
---
## Processing Pipeline
The trajectory generation is preformed using Python (the code used can be found on [GitHub](https://github.com/gabes135). There are **four** main steps in the trajectory calculation process for a single pitch: acquiring the pitch data, calculating its spin axis direction, interpolatting the trajectory, and producing the animated flight path.

## Acquring the Pitch Data
Before the widespread integration of Statcast in stadiums, broadcasts, and sports vernacular, attaining pitch data was the largest hurdle to overcome in this entire process. You'd have to scrape MLB's website for the raw data, convert it to a readable format, and sift through the thousands of pitches thrown in a single day to find the pitch you were looking for. This has changed drasctically and the data is now more or less completely available to the public.

The website [Baseball Savant](https://baseballsavant.mlb.com/) was one of the first to make PITCHf/x and Stacast data easily downloadable for public use. It allowed you to query their immense data base to pinpoint specific pitches, pitchers, results, among many other filters. Extending this to make the data even more accesible, James LeDoux developed the Python package [pybaseball](https://github.com/jldbc/pybaseball), inspired by Bill Petti's R package [baseballr](https://github.com/billpetti/baseballr). This package allows you to preform Baseball Savant queries in Python and retrieve the results as [pandas](https://pandas.pydata.org/) DataFrames for easy use. 

More information on the functions available in the pybaseball package can be found in its documentation on GitHub, but the general process is:
1. Identify the at bat in which the pitch of interest was thrown (pitcher name and batter name)
2. Query for all pitches thrown by the pitch to the batter in the time frame of interest (the day before the at bat to the day of the at bat)
3. Filter the resultant DataFrame by the specific paramters of the pitch of interest, such as:
	* Pitch result (Strike Looking, Strike Swinging, Ground Ball, etc.)
	* Pitch type
	* The inning
	* The count

If done correctly, the result should by a single rowed DataFrame with columns for each pitch attribute.

## Calculating the Spin Axis Direction
Before Statcast was implemented, the pitch data provided by PITCHf/x included the direction of the spin axis, a paramter necessary to calculate the spin vector $\vec{\omega}$. However, this value was never measured but instead infered from the camera-measured acceleration of the pitch and has since been excluded in Baseball Savant's database. 

The method of deriving the pitch spin axis is a bit involved, but thankfully Baseball-Physics legend [Alan M. Nathan](http://baseball.physics.illinois.edu/) of the University of Illinois has done the hard work for us in his [paper on the subject](http://baseball.physics.illinois.edu/trackman/SpinAxis.pdf). He has even provided a dynamic Excel Spredsheet where you can input specific pitch parameters and the resultant spin axis direction is spit out. I suggest reviewing his paper on the subject for more details, but the general idea is to remove the spin independant factors for the camera-measured acceleration (gravity and drag) and use the given velocity to identify the spin vector component perpendicular to the velocity. Since this term is dierctly proportional to the Magnus component of the acceleration, it can be used in conjuction with the Stacast provided spin rate to construct the spin axis vector and spin axis direction. 

In addition, Alan Nathan's method gives a more accurate calculation of both the lift and drag coefficients used in the equation of motion. Rather than using emperically derived values, his parameters extract them from the given information.

We now have everything we need to produce the pitch trajectory.

## Interpolatting the Trajectory
The numerical integration method used is described on the previous page. The pitch attributes needed for this process are:

`'release_pos_x', 'release_pos_y', 'release_pos_z','vxR', 'vyR', 'vzR', 'release_spin_rate', 'phi', 'Cl', 'Cd'`

These values correspond to the three position components and three velocity components at the pitch's release point, the baseball's spin rate, the baseball's spin axis direction, and the two coefficients. More information of these parameters can be found in Alan Nathan's article referenced above and in the documentation in my code.

The trajectory generation function recieves these 10 inputs and the distance from homeplate that you'd like to integrate until (0 if the entire trajectory is desired). The function interpolates to the end position, as well as "backwards in time" to the pitchers mound. Although different pitchers release the ball from different distances from the mound, I found that integrating back gave the most complete perspective of the pitch motion.

The result is a three column array containing the position of the baseball from the mound to homeplate ready for plotting. 

## Producing the Animated Flight Path
The last step is to plot the data in a easy to digest, visually appealing manner to (A) ensure the process has accurately mapped the pitch trajectory and (B) produce a product that allows you to truly dig deeper into the Physics at play.

The plotting library [matplotlib](https://matplotlib.org/) provides a great tool to plot data in 3D. It can be viewed dynamically, allowing the user to rotate the axes and view the pitch's flight path and differentangles, or statically at preset angles. I've chosen to produce a graphic that displays the pitch in motion from three angles to show its vertical movement (z-axis), horizontal movement (x-axis), as well as straight on to most closely match what you'd see in a game broadcast. For pitches like Sliders, the view showing the horizontal movement is most fascinating, where as for Curvballs, the vertical movement is primarly of interest. I prefer the straight on view for pitches that snap back and paint the corners, such as the Two Seam Fastball shown in the [intro]({% link _pages/pitches-intro.md %}). 

The trajectories are animated using [matplotlib's animation class](https://matplotlib.org/3.1.1/api/animation_api.html), which allows you to easily export the pitch trajectory as an mp4 file. 

---

With the details of this tool fleshed out, we can check out some examples of it in use. 




