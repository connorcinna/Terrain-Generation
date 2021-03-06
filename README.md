# Terrain-Generation
A terrain generator written in C++ that uses Perlin noise([libnoise](http://libnoise.sourceforge.net/index.html)) to output a height map, and OpenGL to render it. Other features include: 
- Self-contained heightmap generation
- Specular lighting
- Bump mapping

## Requires
- GLFW for window creation
- GLEW for using OpenGL
- GLM for math utilities
- libnoise for Perlin noise / terrain generation
- [stb_image](https://github.com/nothings/stb/blob/master/stb_image.h) for loading image files into a texture

## How it works
1. Height map is created with libnoise and exported to an image file.
2. Vertices are filled with simple x and z coordinates(no height). Generally around 12,000,000 vertices. 
3. OpenGL is set up, vertices are sent to vertex-shader through draw call.
4. The vertex shader updates each vertex with the according height by reading it from the height map image file.
5. It then calculates the normal values by looking up the heights for the surrounding vertices and creates a normal vector, which is sent to the fragment shader.
6. Fragment shader calculates light value using normal map and light location, blends the resulting color with the terrain texture, then outputs the final color.


## Controls
- W-A-S-D for movement
- Shift to increase movement speed
- F to show wireframes
- G to hide wireframes
- Escape to close the program

## Screen Shots
512x512 height map
![Imgur](https://i.imgur.com/CgmFHQX.png)

4096x4096 height-map
![Imgur](https://i.imgur.com/TCtFCuE.jpg)

Wireframe mode
![Imgur](https://i.imgur.com/ljAyiwQ.png)

