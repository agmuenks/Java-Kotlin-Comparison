# Errors and exception handling

### Java
Exceptions are used in Java when an error occurs while running a program. There are two types of exceptions in Java: checked and unchecked. Checked exceptions are exceptions that should be anticipated and are checked at the time of compiling. Unchecked exceptions are ignored while compiling and occur while executing. Unchecked errors all extend from RuntimeException. If a checked exception is not handled by a method, the exception must be declared by the method with the throws keyword following the method signature. A program can explicitly throw an exception using the throw keyword. Exceptions can be handled using try-catch blocks. Code that may throw an exception are placed in a try block. The try block is followed by one or more catch blocks that handle a specific exception thrown by the code in the try block. The catch block with the greatest specificity should be immediately below the try block and so on, since an exception will be handled by the first catch block that can handle it. A finally block can follow a try block or the last catch block. Code within the finally block will be executed whether an exception occurs or not. Try blocks must be followed by at least one catch or finally block.

```java

String s = "a";

try {
	Integer.parseInt(s);
}
catch (NumberFormatException e) { //catches exception thrown by parseInt
	System.out.println("String cannot be converted to Integer");
}
catch (Exception e) { //less specific exception, follows NumberFormatException
	System.out.println(e);
}
finally {
	System.out.println("Printed in finally block");
}
```

### Kotlin
Unlike Java, Kotlin only has unchecked exceptions. However, Kotlin uses try-catch blocks to handle exceptions like in Java. try is an expression and can return a value. Also like Java, the throw expression is used to explicitly throw an exception. This expression is of type Nothing, which has no types and marks unreachable areas in the code.

```kotlin
val s = "a"

//try-catch example like the Java example
try {
	s.toInt()
}
catch (e: NumberFormatException) {
	println("String cannot be converted to Int")
}
catch (e: Exception) {
	println(e)
}
finally {
	println("Printed in finally block")
}
```

```kotlin
//try expression assigned to a value
val a: Int? = try {s.toInt()} catch (e: NumberFormatException) {null} 
```

[Home](../README.md)