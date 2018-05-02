# Memory Management

### Java
Java relies on the Java Virtual Machine (JVM) for memory allocation and management, so the developer does not need to manually track memory. There are two parts of memory in the JVM: the stack and the heap. The stack contains local variables and references to objects while the heap contains memory for the objects themselves. The heap is much larger than the stack. Memory in the heap is deallocated through garbage collection. During garbage collection, the collector checks if an object on the heap is still in use by the program. If an object is not referenced in the program anymore, the garbage collector deallocates the memory of the unused object. The developer cannot decide when to garbage collect. Garbage collection is triggered by the JVM, and all other threads are stopped when the garbage collector thread is operating.

### Kotlin
Kotlin runs on the JVM so manages memory like Java. Also, there is Kotlin/Native which compiles Kotlin without a virtual machine which manages memory through cyclical garbage collection from an automated refence counter.
