Each iteration of the loop is a frame of rendering. Here is an example of the structure

```c++
// render loop
while(!glfwWindowShouldClose(window))
{
	// input
	processInput(window);

	// rendering commands here
	...

	// check all call events and swap the buffers
	glfwPollEvents();
	glfwSwapBuffers(window);
}
```