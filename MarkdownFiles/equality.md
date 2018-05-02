# Comparisons of references and values

### Java
For primitive data types, the == operator can be used to determine if two values are equal. For objects, the == operator only checks if the references point to the same object. To check if objects have the same value, the equals method on an object must be used.

```java
int a = 1;
int b = 1;

if(a == b) {...} //returns true

String String1 = new String("Equal");
String String2 = new String("Equal");

if (String1 == String2) {...} //returns false

if (String1.equals(String2)) {...} //returns true
```

### Kotlin
In Kotlin, the == operator is used to check for equality of values. The === operator checks for equality of references.


```kotlin
val a = 1
val b = 1

if(a==b) {...} //returns true

val String1 = buildString{"Equal"}
val String2 = buildString{"Equal"}

if (String1 == String2) {...} //returns true, compares value

if (String1 === String2) {...} //returns false, compares by reference
```

[Home](../README.md)