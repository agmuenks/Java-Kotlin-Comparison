# Lambda expression, closures or functions as types

### Java
Lambda expressions implement methods from functional interfaces in Java. The expressions are anonymous and consist of required parameters, the arrow operator (->), and the body of the expression. The body contains the code executed by the expression. Lambda expressions can be stored as variables and passed into methods, giving the ability to have functions as types. Variables in the closure of the lambda expression cannot be changed.

```java
interface Calculator { //functional interface for lambda expression
    
	int calculate (int a, int b);
}

class FinalChallengeTester
{
	public static void main(String[] args) {

		Calculator adder = (a, b) -> a + b; //lambda expressions stored as variables
		Calculator multiplier = (a, b) -> a * b; //single line lambda expression
		Calculator average = (a,b) -> { //block lambda expression
			int sum = a + b;
			return sum/2;
		};
        
		System.out.println(adder.calculate(8,4));
		System.out.println(multiply(multiplier, 8, 4)); //lambda passed as a parameter
		System.out.println(average.calculate(8,4));

		int num = 0;
		Calculator increment = (a, b) -> {
			a++;
			num++; //error cannot modify variable in closure
			return b++;
		};
	}
    
	public static int multiply (Calculator multiplier, int a, int b) {
		return multiplier.calculate(a,b);
	}
}
```

### Kotlin
Kotlin supports higher-order functions, which either have functions as parameters or returns functions. These parameters and return types are of the function type. Function types consist of a list of parameter types and a return type. The parameter list can be empty, but there must always be a return type, even if the type is Unit. Optionally, function types can have a receiver type, and function types can be [nullable](null_references.md). To invoke a function type, its invoke operator is used, or simply write the function name and parameter list. Function types are often instantiated using lambda functions, but an instance can also be obtained by using a callable reference with [reflection](reflection.md). 

Like in Java, lambda expressions are anonymous and are not declared as functions. They can be written in alternate ways (see below), but always are surrounded by curly braces and consist of parameters, the -> sign, and a body. If a lambda is the last parameter of a higher-order function, it can be passed outside the parentheses. In lambda expressions with one parameter, the -> can be omitted and the parameter can be declared with the name it. When returning a value from a lambda expression, the last value of an expression in the body is returned implicitly. Lambda expressions have access to their closures and can modify captured variables, unlike Java.

```kotlin
fun main (args: Array<String>){
    val calculator: (Int, Int) -> Int = {a,b -> a*b} //stores lambda to a value
    val calc = {a:Int, b:Int -> a*b} //alternate way to write the lambda above

    println(calculate(2,4, calculator)) //lambda passed while stored in a value
    println(calculate(6,4) {a,b -> a*b}) //lambda passed as last parameter, outside of the parentheses

    val addOne: (Int) -> Int = {it + 1} //one parameter declared as it
    println(addOne(2)) //prints 3

    var sum = 3
    val adder = {a:Int -> sum + a} //can modify variable in closure
    println(adder(5)) //prints 8

}

fun calculate (a:Int, b:Int, calculator: (Int, Int) -> Int): Int{
    return calculator(a,b) //equivalent to calculator.invoke(a,b)
}
```

[Home](../README.md)