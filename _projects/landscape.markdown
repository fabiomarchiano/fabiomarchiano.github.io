---
layout: page
title: Landscape
description: Processing - P3D
img: /assets/img/landscape.png
---

Had some fun playing with the P3D Processing's render. 
The landscape texture is build using the 2D Perlin noise, which allows us to generate smooth variations of the terrain along one of the three axis. Interesting is also playing with the functions related to lights (*light*, *ambientLight*, *directionalLight*, *pointLight* and *spotLight*) to investigate different visual effects we can give to the reflecting surfaces by changing their properties.    


<video width="640" height="360" controls>
  <source src="/assets/video/landscape.mp4" type="video/mp4" style="border-left: 0!important">
</video> 
<br>

Here some references to the documentation about <a href="https://processing.org/reference/lights_.html" target="_blank">lights</a> and basic principles regarding the <a href="https://processing.org/tutorials/p3d/" target="_blank">3D render</a> (P3D).