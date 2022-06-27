---
title: Game Server Architecture
date: 2022-02-08 12:00:00 +0200
categories: [Interactive Tools]
tags: [Godot,GDScript,Encryption]
image_server: /assets/images/GameServerArchitecture.png
---

Being able to interact with other people online opens up a lot of new possibilities. But creating things such as multiplayer games introduces complexities.

What I wanted to learn:
- Client-server connection
- Account creation
- Lag compensation

![]({{ page.image_server| relative_url}})

These were some of the things I worked on while exploring the topic of servers. Due to the experimental nature, I did not feel confident enough that my servers were secure, which led me to deployed the servers on a local network.

Although I learned a lot from this, there is still more to learn:
- Load balancing
- Advanced lag compensation methods
