---
title: VR Locomotion
date: 2021-04-24 12:00:00 +0200
categories: [Interactive Tools]
tags: [Godot,VR,WebXR]
---

Playing Games -> Limited options for locomotion.
Joystick, Teleport, Draging youself across the map.

No Space or budget for infinite walking platform


Attempt detect speed based on the head movement. Use Fast Fourier Transform to analyse. 


I used the webXR tools in Godot. This made my workflow easy as I didn't need to install software on the oculus quest 2, but could just load the website I just deployed. In the video the graphs helped me see behind the screen,

Direction of walking:
- head is joystick
- base follows you

encoutered issues:
- head rotation can also contribute
- oscillation detection delays may cause nausea
- correlation between oscillation and speed should be investigated.


{% include alerts/warning.html content="During this video I was moving my head a lot. Watching may cause nausea." %}


<iframe width="640" height="360" src="https://www.youtube.com/embed/CVWR7GINIkI" frameborder="0" allowfullscreen></iframe>
