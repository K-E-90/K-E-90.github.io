---
title: Autonomous Hybrid UAV
date: 2022-06-24 12:00:00 +0200
categories: [Thesis]
tags: [C,Matlab,Drone]
---


<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

## Problem Statement

Unmanned aerial vehicles (UAVs), such as quadcopters,
are used in multiple applications varying from photography,
package delivery, geographic mapping, crop monitoring, safety
inspections, surveillance, reconnaissance, and many other applications. With an increase in UAV applications, the mission profile of the UAV can vary based on the application itself.
More tasks will require long endurance and an extended range.
Applications for endurance and range are disaster management
and package delivery respectively.
Hybrid UAVs combine the advantages of aircraft and quadcopters by being able to take-off and land vertically and being efficient in forward flight. However, due to the nonlinear behavior of the aerodynamic surfaces, a control system has to be designed that can handle the nonlinear behavior of the UAV.


## Setup

The Hybrid UAV I used during my Thesis is the [Quadshot](https://transition-robotics.com/pages/frontpage). It is equipped with a [Lisa/MX](https://wiki.paparazziuav.org/wiki/Lisa/MX) autopilot. To program this autopilot, I used the open-source software [Paparazzi](https://github.com/paparazzi/paparazzi). Paparazzi is a project that encompasses both the autopilot systems as well as the ground station and is mainly written in C. This gave me a better understanding of C, as my module also had to be developed in C.


## Control System

The basics of my control system are summed up by looking at the sum of all the forces acting on the drone.

$$ \textbf{a} = \textbf{g} + \frac{1}{m}\textbf{L}_{wing}(\eta,V) + \textbf{D}_{wing}(\eta,V) + \textbf{D}_{side}(\eta,V) + \textbf{T}(\eta,T) $$

Here $$\textbf{L}$$ and $$\textbf{D}$$ are the Lift and Drag forces respectively. They are dependent on the orientation $$\eta$$ and the freestream velocity $$V$$. The last term $$\textbf{T}$$ represents the Thrust vector, dependent on the orientation $$\eta$$ and the thrust magnitude $$T$$. Taking the Taylor Series expansion of this equation results: 


$$ \textbf{a} - \textbf{a}_{\textbf{0}}  = G (\textbf{u} - \textbf{u}_{\textbf{0}}) $$

Where:

$$ \textbf{u} = \begin{bmatrix}
\eta \\
 T
\end{bmatrix}  = \begin{bmatrix}
\phi \\
\theta \\
\psi \\
T
\end{bmatrix}  $$

And $$G$$ is the partial derivative matrix that encompasses the influences of the forces acting on the body for a given change in orientation or thrust. This matrix is also called the control effectivenes. The vectorized notation of the equation is displayed below.

$$     \begin{bmatrix}
\Delta a_{X_B} \\
\Delta a_{Y_B} \\
\Delta a_{Z_B}
\end{bmatrix}
= 
\begin{bmatrix}
\frac{\partial  a_{X_B}}{\partial \phi} & \frac{\partial  a_{X_B}}{\partial \theta}  & \frac{\partial  a_{X_B}}{\partial \psi}  & \frac{\partial  a_{X_B}}{\partial T}  \\
\frac{\partial  a_{Y_B}}{\partial \phi} & \frac{\partial  a_{Y_B}}{\partial \theta}  & \frac{\partial  a_{Y_B}}{\partial \psi}  & \frac{\partial  a_{Y_B}}{\partial T}  \\
\frac{\partial  a_{Z_B}}{\partial \phi} & \frac{\partial  a_{Z_B}}{\partial \theta}  & \frac{\partial  a_{Z_B}}{\partial \psi}  & \frac{\partial  a_{Z_B}}{\partial T}  
\end{bmatrix}
\begin{bmatrix}
\Delta \phi \\
\Delta\theta \\
\Delta \psi \\
\Delta T
\end{bmatrix} $$

My contribution is mainly to the esitmation of the control effectiveness matrix $$G$$ to track the desired acceleration. The acceleration is achieved by incrementing the input vector $$\textbf{u}$$, similar to gradient decent algorithms.

## Demonstrations 

Here are some videos of my implementation. The first video demonstrates a circular trajectory inside, while the second video is performed outside.

<iframe width="640" height="360" src="https://www.youtube.com/embed/_3_ReLRHYw8" frameborder="0" allowfullscreen></iframe>


<iframe width="640" height="360" src="https://www.youtube.com/embed/ipHRP4i74Wc" frameborder="0" allowfullscreen></iframe>
