# Syntax

- Variables

    Read-only local variables are defined using the keyword `val`. They can be assigned a value **only once**.

    ```kotlin
    val a: Int = 1  // immediate assignment
    val b = 2   // `Int` type is inferred
    val c: Int  // Type required when no initializer is provided
    c = 3       // deferred assignment
    ```

    Variables that can be reassigned use the `var` keyword:

    ```kotlin
    var x = 5 // `Int` type is inferred
    x += 1
    ```

- Conditional expressions

    In Kotlin, *if* can also be used as an expression:

    ```kotlin
    fun maxOf(a: Int, b: Int) = if (a > b) a else b
    ```

    

- Type checks and automatic casts

    The *is* operator checks if an expression is an instance of a type. If an immutable local variable or property is checked for a specific type, there's no need to cast it explicitly:

    ```kotlin
    fun getStringLength(obj: Any): Int? {
        if (obj is String) {
            // `obj` is automatically cast to `String` in this branch
            return obj.length
        }
    
        // `obj` is still of type `Any` outside of the type-checked branch
        return null
    }
    ```

- for/while loop

- when expression

    ```kotlin
    fun describe(obj: Any): String =
        when (obj) {
            1          -> "One"
            "Hello"    -> "Greeting"
            is Long    -> "Long"
            !is String -> "Not a string"
            else       -> "Unknown"
        }
    ```

- Ranges

    Iterating over a range:

    ```kotlin
    for (x in 1..5) {
        print(x)
    }
    ```

    Check if a number is out of range:

    ```kotlin
    val list = listOf("a", "b", "c")
    
    if (-1 !in 0..list.lastIndex) {
        println("-1 is out of range")
    }
    if (list.size !in list.indices) {
        println("list size is out of valid list indices range, too")
    }
    ```

- Collections

    Using lambda expressions to filter and map collections:

    ```kotlin
    val fruits = listOf("banana", "avocado", "apple", "kiwifruit")
    fruits
      .filter { it.startsWith("a") }
      .sortedBy { it }
      .map { it.toUpperCase() }
      .forEach { println(it) }
    ```

- Class

    ```kotlin
    fun main() {
        val rectangle = Rectangle(5.0, 2.0)
        val triangle = Triangle(3.0, 4.0, 5.0)
        println("Area of rectangle is ${rectangle.calculateArea()}, its perimeter is ${rectangle.perimeter}")
        println("Area of triangle is ${triangle.calculateArea()}, its perimeter is ${triangle.perimeter}")
    }
    
    abstract class Shape(val sides: List<Double>) {
        val perimeter: Double get() = sides.sum()
        abstract fun calculateArea(): Double
    }
    
    interface RectangleProperties {
        val isSquare: Boolean
    }
    
    class Rectangle(
        var height: Double,
        var length: Double
    ) : Shape(listOf(height, length, height, length)), RectangleProperties {
        override val isSquare: Boolean get() = length == height
        override fun calculateArea(): Double = height * length
    }
    
    class Triangle(
        var sideA: Double,
        var sideB: Double,
        var sideC: Double
    ) : Shape(listOf(sideA, sideB, sideC)) {
        override fun calculateArea(): Double {
            val s = perimeter / 2
            return Math.sqrt(s * (s - sideA) * (s - sideB) * (s - sideC))
        }
    }
    ```

    