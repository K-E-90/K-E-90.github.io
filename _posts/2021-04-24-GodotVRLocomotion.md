---
title: VR Locomotion
date: 2021-04-24 12:00:00 +0200
categories: [Interactive Tools]
tags: [Godot,VR,WebXR]
---

Having used VR for playing games, I was looking forward to experiment with this technology myself. Locomotion is a topic that has a wide range of solutions in the VR space. Some methods allow walking through the virtual world with a joystick, while others rely a teleportation mechanisme. The experience can also be build around traversing the environment by crawling with your hands or simply sit back and relax as you are driven around the virtual space with a virual trolley.

I personally like the creative methods to traverse the virtual world, but I am not fond of the teleportation mechanism. I wanted to create a continous means of locomotion without breaking the immersion. The idea I wanted to try is to be able to 'walk' throught the world by walking in place.

The concept is not that different from the walking platforms. However, the user base of those platforms is smaller than the user base of VR. Besides that, these platforms often come with a high price and take up space. 

My idea was that the velocity of the player could be based on the movement of the head. As the player walks in place, the VR headset will oscillate in height. This oscillation can be analysed and an velocity estimate can be determined. The oscillations of the height were analysed by using a fast fourier transform (FFT) to see the signal in the frequency domain. If the energy around the desired frequencies was high enough, it is assumed that the player is walking.

Now that a velocity magnitude is obtained, the direction of that velocity vector needs to be determined. There are several options: walk in the direction of the VR headsets forward vector, walk in the direction of the VR controllers or walk in the direction you physically moved. I personally do not prefer the head orientation based velocity as a sudden surprise can change the velocity direction instantly even at top speed. Alternatively, I spend the most time on the latter option, where the players position influences the direction. By walking a bit forward the direction is set to forward etcetera. 

I used the webXR tools in Godot to create this. WebXR made my workflow easy as I didn't need to install software on the oculus quest 2, but could just load the website I just deployed. In the video the graphs helped me see behind the screen,

encoutered issues that still need to be fixed:
- head rotation can also contribute to false velocity estimate.
- oscillation detection delays should be decreased to minimize chance of nausea
- correlation between oscillation and speed might vary per person.


{% include alerts/warning.html content="During this video I was moving my head a lot. Watching may cause nausea." %}

<iframe width="640" height="360" src="https://www.youtube.com/embed/CVWR7GINIkI" frameborder="0" allowfullscreen></iframe>
