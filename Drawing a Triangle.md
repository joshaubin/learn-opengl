1. Create our vertex input, an array of float vertices. We set Z to 0 because we are creating a 2d object. We use **normalized device coordinates** between -1.0 and 1.0, as anything outside of this range will not be visible on the screen.
```C
float vertices[] = {
    -0.5f, -0.5f, 0.0f,
     0.5f, -0.5f, 0.0f,
     0.0f,  0.5f, 0.0f
};  
```

Next we need to send this as input to the vertex shader (first part of the [[Graphics Pipeline]])
To do this, we
2. use a **vertex buffer object (VBO)** that we can use to send large batches of data to the graphics card. (See #buffers)
```C
unsigned int VBO;
glGenBuffers(1, &VBO);  
glBindBuffer(GL_ARRAY_BUFFER, VBO);
glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);
```

Now the vertex data is stored in our GPU, so we need to make **[[Fragment]] Shaders** and **[[Vertex Shaders]]** so the GPU knows how to actually render them.