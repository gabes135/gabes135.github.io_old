---
title: "Python Implementation"
permalink: /pitches/python/
excerpt: "Implementing the pitch trajectory interpolation in Python"
last_modified_at: 2019-06-25T14:31:00-08:00
toc: true
mathjax: true
---
## Processing Pipeline
The trajectory generation is preformed using Python (the code used can be found on [GitHub](https://github.com/gabes135). There are **four** main steps in the trajectory calculation process for a single pitch: acquiring the pitch data, calculating its spin axis direction, interpolatting the trajectory, and exporting the animated flight path.

## Acquring the Pitch Data
Before the widespread integration of Statcast in stadiums, broadcasts, and sports vernacular, attaining pitch data was the largest hurdle to overcome in this entire process. You'd have to scrape MLB's website for the raw data, convert it to a readable format, and sift through the thousands of pitches thrown in a single day to find the pitch you were looking for. This has changed drasctically and the data is now more or less completely available to the public.

The website [Baseball Savant](https://baseballsavant.mlb.com/) was one of the first to make PITCHf/x and Stacast data easily downloadable for public use. It allowed you to query their immense data base to pinpoint specific pitches, pitchers, results, among many other filters. Extending this to make the data even more accesible, James LeDoux developed the Python package [pybaseball](https://github.com/jldbc/pybaseball), inspired by Bill Petti's R package [baseballr](https://github.com/billpetti/baseballr). This package allows you to preform Baseball Savant queries in Python and retrieve the results as [Pandas](https://pandas.pydata.org/) DataFrames for easy use. 

More information on the functions available in the pybaseball package can be found in its documentation on GitHub, by the general process is:
1. Identify the at bat in which the pitch of interest was thrown (pitcher name and batter name)
2. Query for all pitches thrown by the pitch to the batter in the time frame of interest (the day before the at bat to the day of the at bat)
3. Filter the resultant DataFrame by the specific paramters of the pitch of interest, such as:
	* Pitch result (Strike Looking, Strike Swinging, Ground Ball, etc.)
	* The inning
	* The count

If done correctly, the result should by a single rowed DataFrame with columns for each pitch attribute.

## Calculating the Spin Axis Direction
Before Statcast was implemented, the pitch data provided by PITCHf/x included the direction of the spin axis, a paramter necessary to calculate the spin vector $\vec{\omega}$. However, this value was never measured but instead infered from the camera-measured acceleration of the pitch and has since been excluded in Baseball Savant's database. 

The method of deriving the pitch spin axis is a bit involved, but thankfully Baseball-Physics legend [Alan M. Nathan](http://baseball.physics.illinois.edu/) of the University of Illinois has done the hard work for us in his [paper on the subject](http://baseball.physics.illinois.edu/trackman/SpinAxis.pdf). He has even provided a dynamic Excel Spredsheet where you can input specific pitch parameters and the resultant spin axis direction is spit out. I suggest reviewing his paper on the subject for more details, but the general idea is to remove the spin independant factors for the camera-measured acceleration (gravity and drag) and use the given velocity to identify the spin vector component perpendicular to the velocity. Since this term is dierctly proportional to the Magnus component of the acceleration, it can be used in conjuction with the Stacast provided spin rate to construct the spin axis vector and spin axis direction. 

In addition, Alan Nathan's method gives a more accurate calculation of both the lift and drag coefficients used in the equation of motion. Rather than using emperically derived values, his parameters extract them from the given information.

We now have everything we need to produce the pitch trajectory.



