# Multithreading

### Java
Concurrent execution is accomplished in Java through multithreading. Threads are lightweight parts of a process and are executed independently of other threads. A thread can be created by extending the Thread class or implementing the Runnable interface. A thread class must override the run() function, which contains the code for the thread to execute. To start executing a thread, the start() method is called, which in turn invokes the run() method.

```java
class ExtendedThread extends Thread {

	@Override
	public void run() {
		for (int i = 0; i < 1000; i++){
			System.out.println(i);
		}
	}
}

class RunnableThread implements Runnable {

	@Override
	public void run() {
		for (int i = 0; i < 1000; i++){
			System.out.println(i);
		}
	}
}

class Multithread
{
	public static void main(String[] args)
	{
		ExtendedThread thread1 = new ExtendedThread(); //thread created from extending Thread class
		thread1.start(); //starts execution
		Thread thread2 = new Thread(new RunnableThread()); //thread created from implementing Runnable interface
		thread2.start();
	}
}
```

### Kotlin
Multithreading is available in Kotlin as well, but Kotlin removes all of the boilerplate code involved in creating a thread in Java. To create a thread, simply call the thread function.

```kotlin
import kotlin.concurrent.thread

thread() {
	for(i in 0..999){
		println(i)
	}
}
```

Kotlin also has coroutines for multitasking. Coroutines can be thought of as lightweight threads and are very cheap to create. A coroutine is started using the launch() function. A value cannot be returned when the launch() function is used. To return a value from a coroutine, use the async() function and store the returned object. The await() function can be called on the returned object to return the result of the coroutine. The await() function cannot be called outside a coroutine. Coroutines currently have the experimental status in Kotlin.

```kotlin
launch { //simple coroutine example
	for(i in 0..999){
		println(i)
	}
}
```
```kotlin
val job = async { //coroutine with a value
	val counter = 0
	for(i in 0..999){
		println(i)
		counter += 1
	}
}

launch { //await() can only be called in a coroutine
	val number = job.await()
	println(number)
}
```

[Home](../README.md)