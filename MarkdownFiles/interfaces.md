# Interfaces

### Java
Both Java and Kotlin support interfaces. Java interfaces are defined using the interface keyword followed by a block of code. The code can contain constant fields, abstract methods, and default or static methods. Java interfaces are implemented by classes using the implements keyword. A class can implement multiple interfaces, and an interface can inherit from multiple interfaces. All members in an interface are public by default

```java
interface Changeable {
	int maxNumberOfChanges = 5; //constant field in interface
    void change(); //abstract method
    default void message () { //default method
    	System.out.println("The object has been changed.");
    }
}

class Thing implements Changebale { //class implementing an interface
	int numberOfChanges = 0;
    int x = 1;
    
    @Override
    public void change() { //implementation of abstract method
    	if (numberOfchanges < maxNumberOfChanges) { //maxNumberOfChanges is a constant from the interface
        	x = x + 1;
            this.message(); //calls default method which does not need to be defined
        }
    }
}
```

### Kotlin
Kotlin interfaces are similar to Java interfaces. Like Java, an interface is defined by the interface keyword. Kotlin interfaces may contain abstract methods, methods with implementation (like default methods in Java), and properties. Properties in interfaces cannot contain state, so they must be abstract or provide implementation for accessors. Interfaces can inherit from multiple interfaces and a class can implement multiple interfaces.

```kotlin
interface Changeable {
	val maxNumberOfChanges: Int //property declared
    	get () = 5;
    fun change() //abstract method
    fun message() { //method with implementation
    	println("The object has been changed.")
    }
}

class Thing: Changeable { //class implementing an interface
	var numberOfChanges = 0
    var x = 1
    override fun change() { //implementation of abstract method
    	if(numberOfChanges < maxNumberOfChanges) {
        	x = x + 1
        }
        message() //calls method defined in interface
    }
}
```

[Home](../README.md)