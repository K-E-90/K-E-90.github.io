---
title: Visualizing Flight Data
date: 2022-01-11 12:00:00 +0200
categories: [Thesis]
tags: [Godot, GDScript]
---

During my thesis I used paparazzi and matlab for flying my drone and analysing the data respectively. However, sometimes the reading the orientation of the drone can become tiresome, especially when represented in quaternion format.

Therefor I decided to read out the flight data in Godot with its scripting language GDScript and visualise the orientaion of the drone next to the other relevant data. With the data I rotated a previously [modeled drone]({% post_url 2021-09-05-BlenderDroneModel %}) in a seperate 3D viewport. Besides that I created my own figure plotter in godot and created a quick interface to scroll through the timeline. 

<iframe width="640" height="360" src="https://www.youtube.com/embed/7CnRuaznDZ4" frameborder="0" allowfullscreen></iframe>

This was not a tool to actively analyse all the data, but it was usefull to check if the data was correct. I further improved my own figure object with text labels in the [trajectory tool]({% post_url 2022-03-21-GodotTrajectoryTool %}).