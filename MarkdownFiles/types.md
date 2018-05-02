# Types

### Java
In Java, there are 8 primitive data types (byte, short, int, long, float, double, char, and boolean). All of these types are value types. There are also class types in Java that are reference types. Types in Java are mutable unless the const keyword is used. New value types cannot be created.

```java
int number; //value type int
const double height = 12.4; //immutable value type
Integer num; //class type that is a reference
```

### Kotlin
All data types are objects and are reference types. Types can be an immutable val type or a mutable var type. Kotlin incorporates type inference, so the data type does not need to be explicitly stated. The basic types in Kotlin are numbers, characters, booleans, arrays, and strings. Although value types are not supported, [data classes](unique_features.md) can be created with the main purpose of holding values.

```kotlin
var number: Int //variable type with explicit typing
val height = 12.4 //immutable type with inferred typing
data class student (val name: String, val id: Int) //data class created to hold data of student type
```

[Home](../README.md)