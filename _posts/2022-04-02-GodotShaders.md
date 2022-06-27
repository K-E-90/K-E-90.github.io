---
title: Interactive Shaders
date: 2022-04-02 12:00:00 +0200
categories: [Interactive Tools]
tags: [Godot,Shaders,GLSL]
image_bullet: /assets/images/SmartDamageBullet.png
image_burn: /assets/images/SmartDamage.png
---

## Portal

Wanting to experiment with shaders I created this portal shader. This shader can be applied to the object within a scene. If the players activates the portal, new objects apear on the other side of the portal.

This is basically a transparency shader, where the mask of the shader is either expressed in global coordinates or in screen coordinates. The thing I wanted to obtain from this is the ability to 'go to a different dimension' while still keeping some of the spatial aspects for orientation purposes.

The objects in the room have there own collision layer based on their 'dimension'. 

<iframe width="640" height="360" src="https://www.youtube.com/embed/hoybgKiIci4" frameborder="0" allowfullscreen></iframe>

## Damage

Godot does not have decals, a crucial way to project images to meshes. Game engines such as Unity and Unreal provide this functionality. To get similar functionality, I created a shader that I could use to display damage on meshes.

I started with creating a viewport that would render the damage texture of the mesh in question. If a player shot the mesh with a raycast, an image will be drawn in the damage texture at UV coordinates of the raycast hit.

Since the damage texture can be any format, I chose to use the RGB8 format. This means that I have three channels containing 8-bit damage info. I used the green channel to indicate the integrity of the mesh. Low integrity will cause the shader to displace the vertices and create a noisy normal map in that area, mimicking broken concrete. The red channel was used to indicate the amount of soot deposited on the mesh. Finally, blue indicates wetness and will cause the shader to adjust the roughness.

In the video the shader is shown for the folowing damage paterns. The left one represents projectile type damage, while the right image represent a more impactfull/explosive type of damage.

![]({{ page.image_bullet| relative_url}})
![]({{ page.image_burn| relative_url}})

The last part of this video show a level of detail (LOD) system I created to reduce the number of faces in an object far away. For illustration purposes the number of faces in this video are reduced. 

<iframe width="640" height="360" src="https://www.youtube.com/embed/DfSGTXd2XT0" frameborder="0" allowfullscreen></iframe>