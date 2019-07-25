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


