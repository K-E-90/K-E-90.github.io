---
title: 3D Web Graphics
date: 2021-11-19 12:00:00 +0200
categories: [Interactive Tools]
tags: [Three.js, Javascript]
---

I also experimented with Three.js, a 3D JavaScript library. The plan is to encorporate this in my [modeled drone]({% post_url 2021-09-05-BlenderDroneModel %}) post. Here is an example of a simple scene with a torus and a light. Rotating is possible with the left mouse button.

<style type="text/css" rel="stylesheet">
#cube {
    position: relative;
    top: 0;
    left: 0;
    height: 50%;
    width: 100%;
    background-color: navy;
}
#bg {
    position: relative;
    top: 0;
    left: 0;
    height: 50%;
    width: 100%;
    background-color: navy;
}
</style>

{% include mycomponent.html %}

{% include alerts/note.html content="The content of the page is not responsive and may appear squashed on smartphones and tables." %}
