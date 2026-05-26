# Project 3: Procedural Shapes Using WebGL Shaders

## Table of Contents
* [Milestone 1: Wireframe Triangle](triangle.html)
* [Milestone 2: 10-Sided Disk](disk.html)
* [Milestone 3: Five-Pointed Star](star.html)
* [Milestone 4: Rotating Star](rotating.html)
* [Extra Credit: Glow Shader Star](rotating-colorful.html)

---

## Project Milestones

### 1. Wireframe Triangle (`triangle.html`)
A simple unfilled triangle. It uses a vertex shader to calculate a triangle using gl_VertexID. It just draws the outline of a yellow triangle using gl.LINE_LOOP.

### 2. 10-Sided Disk (`disk.html`)
A 10 sided filled disk. The lines were switched to a solid using `gl.TRIANGLE_FAN`. Switching to N for the number of vertices made it significantly easier to change the number of vertices seamlessly. Setting it to 12 allows us to make a 10 sided disk because of the shared center point and eleven to make the remaining triangles.

### 3. Five-Pointed Star (`star.html`)
A star with 5 points. This was created by switching the distances each vertex is drawn from the center. by decreasing the distance of some of the points, we're able to create the indents that make the star shape.

### 4. Rotating Star (`rotating.html`)
This is simply just the 5 pointed star but it rotates. This was achieved by using an increasing variable to calculate the rotation of the star, and by cinstantly changing it, the star is constantly redrawn making it look animated.

### 5. Extra Credit: Glow Shader Star (`rotating-colorful.html`)
For extra credit, we passed the radius variable out of the vertex shader and into the fragment shader. Because WebGL blends numbers between points automatically, it creates a really cool color gradient that glows from the center out to the tips instead of just being flat yellow.