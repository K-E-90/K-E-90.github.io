---
title: Trajectory Tool
date: 2022-03-21 12:00:00 +0200
categories: [Thesis]
tags: [Godot, GDScript]
---

## Problem Statement

During my thesis I had to design trajectories for my drone. These trajectories were difficult to design manually as they had to satisfy a few conditions:
- The trajectory should stay within **position limits**
- The trajectory should stay within **velocity limits**
- The trajectory should stay within **acceleration limits**
- The **acceleration** should be **continuous**

These constraint are caused by the physical limitations of the UAV. The position limit is an exception as this is defined by the fly region. Trivial solutions to the constraints are geometrical functions such as circles, however, for more flexible flight plans an alternate solution exists: **splines**.

## Solution

I decided to make a small tool to help me create trajectories for my thesis. This tool was only developed for myself, so I decided to spend my time on the functionality of the tool and not on the GUI. Window buttons were kept to a minimum as I personally work faster with keyboard shortcuts.

For this, I used the Godot game engine with the scripting language GDScript (the scripting language of Godot).

### Creating Interactible Figures

I started of by creating an object for displaying figures. Figures are not included in godot, so I created a rectangle on which a viewort can be displayed. This viewport will contain the curves of that particular figure. The figure was also given axes with text labels. These are updated as the users scrolls or pans in the figure.

### Creating Curves

For the curve I decided that each segment could be either a line, spline or a sinusoidal segment. The spline segment has an additional parameter that dictates how many handles are used per segment. One of the most common splines is the cubuc Bezier, which has two handles. However, the continuous acceleration constraint might require higher order bezier curves in the trajectory.

Besides these options, draging the points or handles of the position versus time figure will update the splines in the velocity and acceleration figures.

A brief demo is provided here.




<iframe width="640" height="360" src="https://www.youtube.com/embed/zjZA4vuMx_E" frameborder="0" allowfullscreen></iframe>

