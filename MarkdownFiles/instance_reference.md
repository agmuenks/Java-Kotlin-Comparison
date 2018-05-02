# Instance reference name in data type

Both Java and Kotlin use the this keyword to refer to that instance of a class

### Java
```java
public class Pet {

	String name;

	public Pet (String name){
    	this.name = name; //assigns name from parameters to name field in class
    }
 
}
```

### Kotlin
```kotlin
class Pet(name: String){ //class declaration with primary constructor

	val name: String
    val gender: Char
	
    constructor(name: String, gender: Char){ //secondary constructor
    	this.name = name //assigns name from parameters to name field in class
        this.gender = gender
    }
}
```

[Home](../README.md)