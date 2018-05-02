# Unique features

### Java
Given that Java is over 20 years old and one of the first object oriented languages, there are no unique features of Java that are not featured in other object oriented languages. Many features are incorporated into other languages. Kotlin is even interoperable with Java.

### Kotlin

#### if expressions
Kotlin meanwhile has many unique features. In Kotlin, some keywords that are statements in other languages are expressions. For instance, if is an expression and returns a value. 
```kotlin
//if as an expression
val a = 2
val isPositive = if (a > 0) true else false
```
#### when expression
Another expression is the when expression, which replaces the switch statement common in other languages. Branch conditions in the when expression do not need to be constants.
```kotlin
val a = 2
val b = 0
val c = "2"

when (a){
    b -> println("a is equal to b")
    c.toInt() -> println("a is equal to c")
    else -> {
        println("a is not equal to other values")
    }
}
```

#### Data classes
Kotlin also features data classes. These are classes that are meant to only hold data. By creating a data class, standard functions like toString(), equals(), and hashCode() are generated automatically by the compiler, eliminating boilerplate code. Data classes must have at least one parameter in the primary constructor, all constructor parameters must be labeled as val or var, and they cannot be abstract, open, sealed, or inner.
```kotlin
data class Student (val name:String, val id:Int)
```

#### Delegated properties
One last unique feature of Kotlin is delegated properties, which delegate their get() and set() functions to a delegate. The delegate follows the by keyword after the declaration of a property.
The delegate must define a getValue() function and a setValue() function if the delegated property is a var. Delegated properties can be used for lazy properties and observable properties.
```kotlin
class Example {
    var x:Int by MyDelegate()
}

class MyDelegate {
    operator fun getValue(thisRef: Any?, property: KProperty<*>): Int {
        println("$thisRef delegated the property")
        return 5
    }

    operator fun setValue(thisRef: Any?, property: KProperty<*>, value: Int) {
        println("Delegate has assigned $value")
    }
}

fun main (args: Array<String>){
	val ex = Example()
    println(ex.x)
    ex.x = 7
    
    //prints:
    //Example@38af9828 delegated the property
    //5
    //Delegate has assigned 7
}
```
[Home](../README.md)
