# Reflection

### Java
Reflection is the ability in Java to examine and change the behavior of a program at runtime. Through reflection, the all the members and constructors of a class can be obtained without needing to know the name of the members. Additionally, fields can be get and set and methods can be invoked, even if they are private.

```java
class Rectangle {
    
	public double height;
	private double width;
    
	public Rectangle (double height, double width) {
		this.height = height;
		this.width = width;
	}
    
	public void printPerimeter(){
		System.out.println(2 * height + 2 * width);
	}
    
	private void printArea(){
		System.out.println(height * width);
	}
}

class FinalChallengeTester
{
	public static void main(String[] args) throws NoSuchFieldException, IllegalAccessException, NoSuchMethodException, IllegalArgumentException, InvocationTargetException {
        
		Rectangle rectangle = new Rectangle(2.5, 5.0);
        
		Class testClass = rectangle.getClass(); //gets the class of rectangle object
		System.out.println("Class name is " + testClass.getName());
        
        
		Constructor constructor = testClass.getConstructor(double.class, double.class);
		System.out.println("Constuctor name is " + constructor.getName());
		for (Parameter parameter: constructor.getParameters()){
			System.out.println("Constructor parameter: " + parameter.getType());
		}
            
        
		Field[] fields = testClass.getFields(); //gets all the  public fields in the class
		for(Field field: fields){
			System.out.println("Field name " + field.getName() + " of type " + field.getType());
		}
        
		Field field = testClass.getDeclaredField("width"); //can get private field
		field.setAccessible(true); //gives access to field
		System.out.println(field.get(rectangle)); //gets the width, prints 5.0
		field.set(rectangle, 4.0); //sets width
		System.out.println(field.get(rectangle)); //prints 4.0
        
		Method[] methods = testClass.getMethods(); //gets all the  public methods in the class
		for(Method method: methods){
			System.out.println("Method name " + method.getName() + " with return type " + method.getReturnType());
		}
        
		Method method = testClass.getDeclaredMethod("printArea"); //gets private method
		method.setAccessible(true); //allows access to private method
		method.invoke(rectangle); //calls print area
 }
 ```
 
 ### Kotlin
Reflection in Kotlin has similar capabilities as reflection in Java. The :: operator is used to create a reference for a class (returning a value of type KClass), its members, properties, and functions. Along with introspective purposes, member references and individual property and function references can be used as instances of [function types](lambdas.md) and be called. Reference of properties, functions, and constructors can be bound references, in which the reference’s receiver is tied to the reference.

```kotlin
 fun main (args: Array<String>){
	val rectangle = Rectangle(2.0, 5.0)
	println(rectangle::class.memberProperties.find { it.name == "width" }) //introspective use with properties

	val testClass = rectangle::class
	println("Class name is ${testClass.qualifiedName}") //introspective use with class

	val constructor = ::Rectangle
	println("Constructor name is ${constructor.name}") //instrospective use with constructor
	for (parameter in constructor.parameters){
		println("Parameter of type ${parameter.type} and name ${parameter.name}")
	}

	fun add(a:Int, b:Int) = a + b
	//reflection used as function type value
	println(calculate(5, 4, ::add)) //::add used as function type (Int, Int) -> Int

	//reflection of property
	println(::z.name) //creates property reference, prints z
	println(::z.get()) //prints Andrew
	::z.set("Madeline") //sets value of property
	println(::z.get()) //prints Madeline

	//reflection of property in class
	println(rectangle::height.get()) //prints 0.0
	rectangle::height.set(3.0) //sets property in class
	println(rectangle::height.get()) //prints 3.0

	//bound function reference
	val example = "Example"
	val isSame = example::compareTo //compareTo function is stored as refernce but bound to its receiver
	println(isSame("Example"))

}

var z = "Andrew"

fun calculate (a:Int, b:Int, calculator: (Int, Int) -> Int): Int{
	return calculator(a,b) //equivalent to calculator.invoke(a,b)
}

class Rectangle(height:Double, width:Double){

	var height = 0.0
	var width = 0.0

	fun printPerimeter(){
		println(2* height + 2 * width)
	}

	fun printArea(){
		println(height * width)
	}
}
```

[Home](../README.md)