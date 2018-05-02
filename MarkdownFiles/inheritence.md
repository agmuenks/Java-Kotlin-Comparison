# Inheritance/extension

### Java
A class in Java inherits from another class using the extends keyword. A subclass inherits all non-private superclass members, and these members can be directly accessed. Constructors and members of the superclass can be invoked using the super keyword. The subclass can add additional functionality to the superclass or change it by overriding methods. Java does not support multiple inheritance, so every class can only inherit from one class. All classes in Java either directly or indirectly inherit from the Object class. If a class should not be inherited from, the final keyword is used. Java does not support extension of a class.


```java
public class Pet { //pet implicitly inherits from object
	
	int age;
    
	public Pet (int age) {
    	this.age = age;
	}
    
	public void speak() {
    	System.out.println("Pet is speaking.");
	}
    
}

public class Dog extends Pet { //Dog inherits from Pet and therefore inherits from Object
	
	String breed;
    
	public Dog (int age, String breed) {
    	super(age); //invokes Pet constructor
		this.breed = breed;
	}
    
	@Override
	public void speak() {
    	System.out.println("Bark!"); //overrides speak function in Pet
	}
}

public class Cat extends Pet { //dog inherits from pet
	
	String breed;
    
	public Dog (int age, String breed) {
    	super(age); //invokes Pet constructor
		this.breed = breed;
	}
    
	@Override
	public void speak() {
    	System.out.println("Meow!"); //overrides speak function in Pet, different implementation than Dog class
	}
}
```
```java
public final class FinalClass { //final class that cannot be extended
	//code
}
```

### Kotlin
Classes in Kotlin inherit from a superclass by placing the inherited type after a colon in the class header. All classes implicitly inherit from Any. All classes are final by default, and the open keyword must be used for other classes to inherit from a class. Derived classes must initialize the base type in their constructors. Primary constructors can do this in the class header with the parameters of the primary constructor. Secondary constructors must use the super keyword to initialize the base type. Like Java, Kotlin can override functions in the base class. However, the function in the base class must have the open annotation, and an override annotation is required for the function in the derived class. Properties can also be overridden similarly to functions. Multiple inheritance is not allowed in Kotlin.

```kotlin
open class Pet(age:Int){ //implicitly inherits from Any, able to be inherited

	open fun speak() { //function is able to be overriden
		System.out.println("Pet is speaking.");
	}
}

class Dog(age:Int, breed:String): Pet(age){ //Dog inherits from Pet
	override fun speak(){
    	System.out.println("Bark!"); //overrides speak function in Pet
	}
}

class Cat(age:Int, breed:String): Pet(String){ //Cat inherits from Pet
	override fun speak(){
    	System.out.println("Meow!"); //overrides speak function in Pet
	}
}
```

Kotlin also allows extension of classes, which allows extension of functionality without inheriting from the class. To add an extension function, the new function follows the dot-notation and the type being extended. Extension functions do not modify classes and are dispatched statically. An extension function will be overruled by a member function if they have the same name, arguments, and receiver types, but extension functions with different signatures can be used for function overloading. Along with extension functions, Kotlin allows extension properties. These properties do not have backing fields, and therefore, an extension property cannot have an initializer.

```kotlin
class Square(val length:Double) {

	fun printLength(){
		println("The length is $length")
	}
}

val Square.area: Double //extension property
	get() = length * length

fun Square.calcPerimeter(): Double { //extension function
	return 4 * this.length
}
```

[Home](../README.md)