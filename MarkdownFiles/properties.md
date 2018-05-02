# Properties

### Java
In Java, properties of a class are referred to as fields. Fields require you to create your own getters and setters. Java lacks many abilities of modern programming languages, including backing variables and computed properties.

```java
public class Pet {

	String name; //field of class Pet

	public Pet (String name){
    	this.name = name; //assigns name from parameters to name field in class
    }
	
	public String getName(){
		return name;
	}
	
	public void setName(String name){
		this.name = name
	}
 
}
```

### Kotlin
Kotlin, however, does have some of these features. Getter and setters are optional. They can be provided as below, or they will be auto generated and called internally when accessed or modified. Kotlin provides backing fields automatically when needed by a property. These can be accessed by the keyword field and are only accessed in a variable’s accessors. Computed properties are not featured in Kotlin. However, they can be simulated by including computations in a customized getter.

```kotlin
class Class{
	var x = 1 //declaration of property x
    	get() = field //field keyword gives access to a field's value
        set(value) { field = value }
}
```

Example of “computed property”
```kotlin
class Example  {
    var number1 = 1
    var number2 = 2
    val sum: Int //get function makes sum act like a computed property
        get() {
            return number1 + number2
        }
}
```

[Home](../README.md)