# Classes

### Java
Classes in Java are defined as below with a constructor. They can be defined with the public or default access modifier. Constructors consist of the name of the class with a list of parameters. Multiple constructors can be created with different parameter lists. A new instance of a class is instantiated with the new keyword and a call to a constructor. There is no destructor in Java since it is a garbage collected language.

```java
public class Pet {

	String petName;

	public Pet (String name){ //Pet constructor that creates pet object with name as petName
    		petName = name;
    	}
    
	//code in class
}
```

```java
Pet pet = new Pet("Sally"); //creates a new instance of Pet class
```

### Kotlin
A class in Kotlin is defined as below. Classes can have primary or secondary constructors. Primary constructors follow the class name in the class header. No code can be contained in primary constructors. Blocks with preceded by the init keyword are used for initialization code. Secondary constructors are implemented by blocks preceded by the constructor keyword. To instantiate a class, a call to the constructor is made without a new keyword. Kotlin does not have a method for deinitializing an object.

```kotlin
class Pet(name: String){ //class declaration with primary constructor

    	val name: String
    	val gender: Char
	
    	init{
    		println("Initializer block")
   	}
    
    	constructor(name: String, gender: Char){ //secondary constructor
    		this.name = name
        	this.gender = gender
    	}
}
```
```kotlin
val pet = Pet("Sally")
```

[Home](../README.md)
