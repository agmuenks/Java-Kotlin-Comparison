# Null/nil references

### Java
A reference that is not pointing to anything is a null reference in Java. Java does not have built in null safety features. The developer must manually implement handling null references. Accessing a null reference will throw a null pointer exception.

```java
Object obj;

if (obj != null) { //programmer must manually check for null pointers
	//do something
}
```

### Kotlin
References in Kotlin either can or can not hold null references. By default, a reference can not hold null. If a reference is to be nullable, a ? is used. The non-null references will never cause null pointer exceptions. If a nullable type is used, there are multiple ways to check for null. An explicit if statement can be used like in Java. The safe call operator (?.) checks if a reference is null. It will return null if it is, or return the value of the property or function if it is not. The elvis operator (?:) is used to as a shorthand for an if-else statement. If the expression is null, the value on the left is returned, and if not, the value on the right is returned. Finally, the not-null assertion operator (!!) converts a value to a non-null type if it is not null and throws a null pointer exception if it is.

```kotlin
val x: Int = 2 //can not be null
val y: Int? = 2 //can be null

x = null //compiler error
y = null //compiles

val a = x.times(2) //compiles
val b = y.times(2) //error, y can be null

val c = y?.times(2) //safe call operator, if y is not null computes, else returns null

val d = y?.times(2) ?: 0 //elvis operator, computes if y is not null, else returns 0

val e = y!!.times(2) //not-null assertion operator, converts y to non-null type or throws a null pointer exception
```

[Home](../README.md)
