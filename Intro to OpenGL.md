OpenGL is a specification made by graphics card developers.

### Why not learn the newest version of OpenGL?
New versions of OpenGL add slight optimizations, but only the most modern graphics cards can take advantage of these. Thus, developers target lower versions of OpenGL and provide the option to enable higher version functionality

### State Machine
OpenGL is a state machine, or a collection of variables that define how OpenGL should currently operate. The state of OpenGL is called the **context**. OpenGL features **state-changing** functions that change the context and **state-using** functions that perform some operation based on the current state of OpenGL.

Since OpenGL libraries are written in C, it takes advantage of [[objects]].