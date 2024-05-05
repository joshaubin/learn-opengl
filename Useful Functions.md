#configuring
- `glfwInit()`
- `glfwWindowHint(int hint, int value)` 
	- sets hints for the next call to `glfwCreateWindow`, hint is an ENUM [list of ENUMS found here](https://www.glfw.org/docs/latest/window.html#window_hints)
-  `GLFW_CONTEXT_VERSION_(MAJOR/MINOR)` - sets glfw version
#window_creation
- `GLFWwindow` object
- `glfwCreateWindow(int width, int height, const char* title, GLFWmonitor* monitor, GLFWwindow* share)`
	- *monitor* is the monitor to use for full screen mode, NULL = windowed mode
	- *share* is the window whose context to share resources with, NULL to not share resources
- `glfwMakeContextCurrent(GLFWwindow* window)`
	- make the context of the specified window current for the calling thread
- `glViewPort(GLint x, GLint y, GLsizei width, GLsizei height)`
	- specifies the render window
	- *x*: left x-coordinate of the viewport rectangle
	- *y*: bottom y-coordinate of the viewport rectangle

#render_loop see [[render loop]]
- `glfwWindowShouldClose(GLFWwindow* window)`
	- checks if the window has been instructed to close
- `glfwSwapBuffers(GLFWwindow* window)`
	- swap the color buffer and show the output on screen. see [[Double Buffering]] 
- `glfwPollEvents()`
	- checks for events such as keyboard inputs

#input
- `glfwGetKey(GLFWwindow *window, int key)`
	- returns `GLFW_PRESS` or `GLFW_RELEASE`

#buffers
- `glGenBuffers(GLsizei size, GLuint* buffers)` 
	- generate a vertex buffer object
	- *size* = number of buffer objects to generate
	- *buffer* = array where glGenBuffers will store its resulting buffer reference IDs
- `glBindBuffer(GLenum target, GLuint buffer)` 
	- binds a buffer object to the current buffer type target
	- *target* - target buffer object, most common are `GL_ARRAY_BUFFER` and `GL_ELEMENT_ARRAY_BUFFER`
	- *buffer* - the buffer object's reference ID of the buffer you want to bind
- `glBufferData(GLenum mode, GLsizeiptr size, const GLvoid* data, GLenum usage)`
	- Copy user-defined data into the currently bound buffer
	- *mode* - target buffer we want to copy into
	- *size* - size of the data we want to pass into the buffer
	- *data* - pointer to data that will be copied. `NULL` if you want to just allocate empty memory
	- *usage* - specifies the expected usage pattern of the data
		- Most common are `GL_STATIC_DRAW, GL_DYNAMIC_DRAW, GL_STREAM_DRAW` 