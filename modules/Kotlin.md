<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [Syntax](#syntax)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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

    `is` 检测一个表达式是否某类型的一个实例。 如果一个不可变的局部变量或属性已经判断出为某类型，那么检测后的分支中可以直接当作该类型使用，无需显式转换

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

- 方法

    ```kotlin
    fun sum(a: Int, b: Int): Int {
        return a + b
    }
    ```

- null检测

    当某个变量的值可以为 *null* 的时候，必须在声明处的类型后添加 `?` 来标识该引用可为空

    [Doc](https://www.kotlincn.net/docs/reference/null-safety.html)

- 习惯用法

    [Refer](https://www.kotlincn.net/docs/reference/idioms.html) 

- 关键字

    - `open`

        kotlin中所有的类默认都是final, 方法也是 final, 增加`open`, 就可以被继承/重写

