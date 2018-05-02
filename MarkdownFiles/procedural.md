# Procedural programming

### Java
Java does not allow methods to exist outside of a class and is committed to an OO programming paradigm. Therefore, procedural programming is not supported in Java. 

### Kotlin
Kotlin is a multi-paradigm programming language and supports procedural programming. The following can be done in Kotlin and not in Java.

```kotlin
fun main (args: Array<String>) {
    val x = 6
    val y = 4

    println(calculateArea(x,y)) //prints out 24
}

fun calculateArea(length: Int, width: Int): Int {
    return length * width
}
```

[Home](../README.md)