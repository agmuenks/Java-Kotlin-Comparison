# Singleton

### Java
There are multiple ways to implement the Singleton design pattern in Java. Whichever way it is implemented, it will include a private constructor, a private static variable of the Singleton class, and a public static method that gets the Singleton instance.

```java
public class Singleton {
	private static final Singleton instance = new Singleton(); //variable of Singleton class
	
	private Singleton(){ //private constructor
    
	}
    
	public static Singleton getInstance() { //static method to get instance
		return instance;
	}
}
```

A Singleton in Java can be lazily instantiated, so it is not created until it is needed. To lazily instantiate, the creation of the instance is moved inside the method to get the instance.

```java
public class Singleton {
	private static Singleton instance;
    
	private Singleton() {
    
	}
    
	public static Singleton getInstance() {
		if (instance == null) {
			instance = new Singleton(); // creation of Singleton object moved to getInstance method
		}
        
		return instance;
	}
}
```

The previous Singleton examples are not thread-safe. There are many ways a Singleton can be made thread-safe. An easy way is to add the synchronized keyword before the getInstance() method in the previous example.

```java
public class Singleton {
	private static Singleton instance;
    
	private Singleton() {
    
	}
    
	public static synchronized Singleton getInstance() {
		if (instance == null) {
			instance = new Singleton(); // creation of Singleton object moved to getInstance method
		}
        
		return instance;
	}
}
```

### Kotlin
To implement a Singleton in Kotlin, object declaration is used. The Singleton class name simply follows the keyword object. Object declaration is thread safe and imitates lazy instantiation. The object name is directly used to execute code in the object.

```kotlin
object Singleton {
	//code to be executed in singleton
}
```

[Home](../README.md)