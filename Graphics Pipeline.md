The **graphics pipeline** of OpenGL manages the process of transforming 3D coordinates to 2D pixels by:
1. Transforming 3D coordinates into 2D coordinates
2. Transforming the 2D coordinates in to actual colored pixels

The graphics pipeline takes a set of 3D coordinates as input and transforms them into 2D pixels on the screen. It can be divided into several steps where each step requires the output of the previous step as its input (Think basis transformations). All of these steps are specific in nature and can be executed in parallel. This is why GPUs are built with thousands of small processing cores to quickly process data. The processing cores run small programs called **shaders** on the GPU for each step of the pipeline. Shaders are written in **OpenGL Shading Language (GLSL)**.

![[Pasted image 20240425135437.png]] 
The blue regions are parts of the pipeline where we can inject our own shaders.

The **Input** is a list of 3D coordinates that form a triangle in an array called **Vertex Data**.
- Vertex data is a collection of vertices. A **vertex** is a collection of data per 3D coordinate.
- Vertex data is represented using **Vertex Attributes**.
- for simplicity's sake we'll treat a vertex as a 3D position with some color value.
OpenGL requires a hint in order to know what kind of render type we want to form with our input data. These are called **primitives**. Examples of primitives are:
- `GL_POINTS`
- `GL_TRIANGLES`
- `GL_LINE_STRIP` 

### 1. Vertex Shader
The vertex shader takes in a *single vertex* and transforms its 3D coordinates to different 3D coordinates.
### 2. Geometry Shader (Optional)
The geometry shader takes in a collection of vertices that form a primitive and is able to generate other shapes by emitting new vertices to form new primitives. (Think subdivision in the example above)
### 3. Primitive Assembly
The primitive assembly stage takes in all the vertices (or vertex if `GL_POINTS` is the primitive) from the previous stage that form one or more primitives and assembles all of the points in the primitive shape given. In other words it *connects the lines/forms the primitives*.
### 4. Rasterization Stage
The output of the primitive assembly is mapped to corresponding pixels on the final screen resulting in fragments for the [[Fragment]] shader to use. **Clipping** is also performed, meaning fragments outside of view are discarded to increase performance.
### 5. Fragment Shader
This is where the final color of a pixel is calculated, and it's where most advanced OpenGL effects like lighting and shadows occur.

### 6. Alpha Test and Blending Stage
This stage checks the corresponding depth and stencil value of the fragment to determine if the resulting fragment is in front of or behind other objects. If it is behind another object it should be discarded since it won't affect the scene.

We also check for **alpha** values, which define the *opacity* of an object, and blend the objects accordingly.