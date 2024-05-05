An **object** is a collection of options that represent a subset of OpenGL's state. You can visualize an object like a C struct
```c++
struct object_name {
	float option1;
	int option2;
	char[] name;
};
```

Objects in OpenGL look like this
```C++
struct OpenGL_Context {
	...
	object_name* object_Window_Target;
	...
};
```
```C++
// create object
unsigned int objectId = 0;
glGenObject(1, &objectId);
// bind/assign object to context
glBindObject(GL_WINDOW_TARGET, objectId);
// set options of object currently bound to GL_WINDOW_TARGET
glSetObjectOption(GL_WINDOW_TARGET, GL_OPTION_WINDOW_WIDTH, 800);
glSetObjectOption(GL_WINDOW_TARGET, GL_OPTION_WINDOW_HEIGHT, 600);
// set context target back to default
glBindObject(GL_WINDOW_TARGET, 0);
```
The workflow here is common:
1. create an object and store a reference to it as an id
2. bind the object using its id to the target location of the context
3. set the options of the object
4. unbind the object by setting the current object id of the target location to default
The options set are stored in the object referenced by the id and restored as soon as we bind the object back to its target location (in this case, GL_WINDOW_TARGET)

#workflow 