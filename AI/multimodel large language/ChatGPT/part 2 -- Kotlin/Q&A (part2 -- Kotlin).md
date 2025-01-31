# Q&A in chatGPT part2 -- Kotlin
## abstract
I will ask chatGPT from basic to advanced questions in order.

## Q & A
-----------------------------------------------
---------- BASIC CONCEPT AND SYNTAX -----------
-----------------------------------------------
1. Q: How to output 'Hello World!!!' in Kotlin?

A:

In Kotlin, you can output "Hello World!!!" using the `println` function. Here's the code:

```
fun main() { 
    println("Hello World!!!") 
}
```

### Explanation:

1. **`fun main()`**: This is the entry point of a Kotlin application. The `main` function is where the program starts executing.
2. **`println`**: This function is used to print text to the standard output followed by a newline.

When you run this program, it will display:

```
Hello World!!!
```

2. Q: How to define a variable with initial value 'Hello World!!!' in Kotlin?

A:

In Kotlin, you can define a variable with the initial value `"Hello World!!!"` using either `val` or `var`. Here's how:

### Using `val` (Immutable Variable)

```
val greeting = "Hello World!!!"
```

- **`val`**: Declares a read-only (immutable) variable. Once assigned, the value cannot be changed.

### Using `var` (Mutable Variable)

```
var greeting = "Hello World!!!"
```

- **`var`**: Declares a mutable variable. You can reassign a new value to it later.

### Example:

```
fun main() {     
    val greeting = "Hello World!!!"     
    println(greeting) 
}
```

Output:

```
Hello World!!!
```

3. Q: How to define a function named `function1` with zero parameters at top level in Kotlin?

A:

In Kotlin, you can define a top-level function named function1 with zero parameters like this:

```
fun function1() {
    println("This is function1")
}
```

### Explanation:

1. **`fun`**: Declares a function in Kotlin.
2. **`function1`**: The name of the function.
3. **`()`:** Indicates that the function takes no parameters.
4. **Top-Level**: In Kotlin, functions can be defined directly in a file without being inside a class.

### Example Usage:

```
fun function1() {
    println("This is function1")
}

fun main() {
    function1() // Calls the function
}
```

Output:

```
This is function1
```

4. Q: What is entry point in Kotlin?

A:

The **entry point** in a Kotlin program is the function where the program starts executing. In Kotlin, the entry point is the `main` function.

### Syntax of the `main` Function:

```
fun main() {
    // Program execution starts here
}
```

### Key Points:

**Mandatory Name**: The function must be named `main`.
    
**Parameter Options**:
    
    - The `main` function can have no parameters:

    ```
    fun main() {
        println("Hello, Kotlin!")
    }
    ```

    - Or it can have a parameter to accept command-line arguments.

    ```
    fun main(args: Array<String>) {
        for (arg in args) {
            println(arg)
        }
    }
    ```

    Here, args is an array of strings that represents the command-line arguments passed to the program.

**Location**: The `main` function can be placed in any Kotlin file. Kotlin does not require it to be inside a class.

**Execution**: When you run the Kotlin program, the `main` function is invoked, and its code is executed.

5. Q: A parent class of all class in Kotlin is?

A:

In Kotlin, the **parent class of all classes** is the **`Any`** class. It serves as the root of the class hierarchy, similar to `Object` in Java.

### Key Features of `Any`:

**Default Parent**: Every class in Kotlin implicitly inherits from `Any` if no explicit superclass is specified.
**Methods Provided by `Any`**:
    - `equals(other: Any?): Boolean` - Determines equality between objects.
    - `hashCode(): Int` - Returns a hash code value for the object.
    - `toString(): String` - Returns a string representation of the object.

### Example:

```
class MyClass // Implicitly inherits from `Any`

fun main() {
    val obj = MyClass()
    println(obj.toString())  // Default implementation from `Any`
    println(obj.hashCode())  // Default implementation from `Any`
    println(obj.equals(MyClass()))  // Default implementation from `Any`
}
```

Output:

```
MyClass@6e8dacdf
1846274131
false
```

### Notes:

- You can override `Any` methods in your class to provide custom behavior:


```
class MyClass {
    override fun toString(): String {
        return "This is MyClass"
    }
}

fun main() {
    val obj = MyClass()
    println(obj.toString()) // Output: This is MyClass
}
```

- `Any` does not include features like `clone` or `wait/notify`, which are part of Java's `Object` class. These features are available in Kotlin only for classes that directly extend `java.lang.Object`.

4o

-----------------------------------------------
---------- EXCEPTION HANDLING -----------------
-----------------------------------------------

6. Q: A parent class of all class that are related to `Exception` in Kotlin is?

A: 

In Kotlin, the parent class of all exception-related classes is **`Throwable`**.

### Key Points about `Throwable`:

**Root Class for Exceptions and Errors**:
    
    - All exceptions and errors in Kotlin inherit from `Throwable`.
    - It has two main direct subclasses:
        - **`Exception`**: Represents recoverable conditions.
        - **`Error`**: Represents serious errors that usually indicate issues in the environment or JVM.
**Constructors**:
    
    - `Throwable(message: String?)`: Accepts a message describing the exception.
    - `Throwable(cause: Throwable?)`: Accepts a cause (another `Throwable`).
    - `Throwable(message: String?, cause: Throwable?)`: Accepts both a message and a cause.

**Common Methods**:
    
    - `message`: Returns the exception message.
    - `cause`: Returns the cause of the exception.
    - `printStackTrace()`: Prints the stack trace of the exception.

### Hierarchy Example:

```
Throwable
├── Exception
│   ├── IOException
│   ├── RuntimeException
│       ├── NullPointerException
│       ├── IllegalArgumentException
│       └── others...
└── Error
    ├── OutOfMemoryError
    ├── StackOverflowError
    └── others...
```

### Example Usage:

#### Custom Exception

```
class CustomException(message: String) : Exception(message)

fun main() {
    try {
        throw CustomException("This is a custom exception")
    } catch (e: CustomException) {
        println("Caught exception: ${e.message}")
    }
}
```

Output:

```
Caught exception: This is a custom exception
```

### Notes:

- Use `Exception` for conditions you expect to recover from.
- Avoid catching `Error`, as it typically indicates critical issues.


7. Q: How to throw an Exception -- `IllegalFormatException` in Kotlin?

A: 

To throw an `IllegalFormatException` in Kotlin, you can use the `throw` keyword, as `IllegalFormatException` is a part of the Java standard library (under `java.util` package). Here's how you can do it:

### Example:

```
import java.util.IllegalFormatException

fun main() {
    val format = "Hello %s!"
    val arg = null

    try {
        if (arg == null) {
            throw IllegalFormatException() // Manually throwing the exception
        }
        println(String.format(format, arg))
    } catch (e: IllegalFormatException) {
        println("Caught IllegalFormatException: ${e.message}")
    }
}
```

### Key Notes:

**Throwing Exceptions**:
    
    - In Kotlin, exceptions are thrown using the `throw` keyword.
    - An instance of the exception must be created using its constructor.

**IllegalFormatException Details**:
    
    - It is part of the Java library (`java.util.IllegalFormatException`).
    - This exception is usually thrown when a format string is invalid or incompatible with provided arguments in `String.format()`.

**Using a Message or Cause**:
    
    - You can pass a message or cause when creating the exception:
        
    ```
    throw IllegalFormatException("Invalid format string")
    ```
        
4. **When to Use**:
    
    - `IllegalFormatException` is specifically used when dealing with formatting errors in strings, such as with `String.format()` or similar operations.

### Output for the Above Code:

```
Caught IllegalFormatException: null
```

This demonstrates a simple way to throw and handle `IllegalFormatException` in Kotlin.

8. Q: How to catch an Exception -- `IllegalFormatException` in Kotlin?

A:

To catch an `IllegalFormatException` in Kotlin, you use a `try-catch` block. The `catch` block will handle the exception if it is thrown during the execution of the `try` block.

Here’s an example of catching an `IllegalFormatException`:

### Example:

```
import java.util.IllegalFormatException

fun main() {
    val format = "Hello %d!" // Incorrect format specifier for a String
    val name = "World" // Argument is not an integer

    try {
        // This will throw IllegalFormatException because format specifier and argument don't match
        println(String.format(format, name))
    } catch (e: IllegalFormatException) {
        println("Caught IllegalFormatException: ${e.message}")
    }
}

```

### Explanation:

**`try` block**:
    - Contains the code that might throw an exception.

**`catch` block**:
    - Captures the `IllegalFormatException` if it occurs.
    - The exception object (`e` in this case) provides details about the error, like the message and stack trace.

### Output:

```
Caught IllegalFormatException: Conversion = 'd', type = java.lang.String
```

### Key Notes:

**`IllegalFormatException`**:
    - This exception is part of the `java.util` package and is typically thrown when there's a mismatch between the format string and the arguments in `String.format`.

**Handling Other Exceptions**:
    - You can include additional `catch` blocks to handle other exceptions, or a generic `catch` block for all exceptions using `Exception`:
        
        ```
        catch (e: Exception) {     
            println("Caught an exception: ${e.message}") 
        }
        ```
        
**Best Practices**:
    - Always try to catch specific exceptions (like `IllegalFormatException`) rather than generic ones (`Exception`), as it makes error handling more precise.

9. Which block does always be executed in `try`-`catch`-`finally` block in Kotlin, even if there is an Exception thrown? 

A: 

In Kotlin, the **`finally` block** is always executed, regardless of whether an exception is thrown or not. This block is typically used for cleanup activities like closing resources, releasing locks, or other necessary finalization tasks.

### Syntax:

```
try {
    // Code that might throw an exception
} catch (e: Exception) {
    // Code to handle the exception
} finally {
    // Code that will always execute
}
```

### Key Characteristics of `finally`:

**Always Executed**:
    
    - The `finally` block executes after the `try` block and any `catch` blocks, even if an exception is thrown or caught.
    - It also executes if a `return`, `break`, or `continue` statement is used in the `try` or `catch` blocks.

**Optional Block**:
    
    - The `finally` block is optional. You can use `try`\-`catch` without it.

### Example:

```
fun main() {
    try {
        println("Inside try block")
        throw Exception("An exception occurred") // Throwing an exception
    } catch (e: Exception) {
        println("Caught exception: ${e.message}")
    } finally {
        println("This is the finally block, always executed")
    }
}
```

### Output:

```
Inside try block
Caught exception: An exception occurred
This is the finally block, always executed
```

### Example Without Exception:

```
fun main() {
    try {
        println("Inside try block, no exception")
    } catch (e: Exception) {
        println("This will not be executed")
    } finally {
        println("This is the finally block, always executed")
    }
}
```

### Output:

```
Inside try block, no exception
This is the finally block, always executed
```

### Notes:

- If the JVM exits (e.g., `System.exit()` is called) or the thread is interrupted/terminated, the `finally` block might not execute.

10. Q: How to customize an Exception named `CustomizedException` in Kotlin?

A:

In Kotlin, you can create a custom exception class by inheriting from the built-in `Exception` class (or any of its subclasses like `RuntimeException`, `IOException`, etc.). Here's how you can define a custom exception named `CustomizedException`:

### Custom Exception Definition

```
class CustomizedException(message: String) : Exception(message)
```

### Key Points:

1. **Inheriting from `Exception`**:
    - The custom exception class extends `Exception`, giving it all the functionality of a standard exception.
2. **Primary Constructor**:
    - The `message` parameter is passed to the superclass (`Exception`) constructor.
3. **Additional Properties or Methods** (Optional):
    - You can add custom properties or methods to provide more context about the exception.

---

### Example 1: Basic Custom Exception

```
class CustomizedException(message: String) : Exception(message)

fun main() {
    try {
        throw CustomizedException("This is a custom exception")
    } catch (e: CustomizedException) {
        println("Caught CustomizedException: ${e.message}")
    }
}
```

**Output:**

```
Caught CustomizedException: This is a custom exception
```

---

### Example 2: Custom Exception with Additional Details

```
class CustomizedException(
    message: String,
    val errorCode: Int
) : Exception(message)

fun main() {
    try {
        throw CustomizedException("Invalid operation", 404)
    } catch (e: CustomizedException) {
        println("Caught CustomizedException: ${e.message}, Error Code: ${e.errorCode}")
    }
}
```

**Output:**

```
Caught CustomizedException: Invalid operation, Error Code: 404
```

---

### Example 3: Adding Custom Methods

```
class CustomizedException(message: String) : Exception(message) {
    fun logError() {
        println("Logging error: $message")
    }
}

fun main() {
    try {
        throw CustomizedException("Something went wrong")
    } catch (e: CustomizedException) {
        e.logError()
        println("Caught CustomizedException: ${e.message}")
    }
}
```

**Output:**

```
Logging error: Something went wrong
Caught CustomizedException: Something went wrong
```

---

### Notes:

- Always aim to include meaningful messages and properties in your custom exception to make debugging easier.
- Use custom exceptions sparingly and only when a built-in exception type does not adequately represent your error condition.


-----------------------------------------------
---------- HIGH ORDER FUNCTIONS ---------------
-----------------------------------------------

11. Q: What are the use of high order functions in Kotlin?

A:

In Kotlin, **higher-order functions** are functions that either take other functions as parameters, return a function, or both. They are a key feature of Kotlin that supports functional programming and provide several benefits for cleaner and more flexible code.

### Uses of Higher-Order Functions in Kotlin:

#### 1\. **Code Reusability**

Higher-order functions allow you to abstract common logic into reusable components, reducing code duplication.

**Example: Custom Filtering**

```
fun filter(numbers: List<Int>, predicate: (Int) -> Boolean): List<Int> {
    return numbers.filter(predicate)
}

fun main() {
    val numbers = listOf(1, 2, 3, 4, 5)
    val evens = filter(numbers) { it % 2 == 0 }
    println(evens) // Output: [2, 4]
}
```

#### 2\. **Improved Readability**

Higher-order functions enable concise and expressive code by eliminating boilerplate.

**Example: Using `map` for Transformation**

```
fun main() {
    val numbers = listOf(1, 2, 3)
    val squared = numbers.map { it * it }
    println(squared) // Output: [1, 4, 9]
}
```

#### 3\. **Functional Composition**

You can compose functions to define complex behavior more cleanly.

**Example: Combining Functions**

```
fun add(a: Int, b: Int) = a + b
fun multiply(a: Int, b: Int) = a * b

fun performOperation(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

fun main() {
    println(performOperation(5, 3, ::add))      // Output: 8
    println(performOperation(5, 3, ::multiply)) // Output: 15
}
```

#### 4\. **Custom Control Flow**

You can implement your control flow structures using higher-order functions.

**Example: Custom Loop**

```
fun repeatAction(times: Int, action: (Int) -> Unit) {
    for (i in 0 until times) action(i)
}

fun main() {
    repeatAction(3) { println("Iteration: $it") }
    // Output:
    // Iteration: 0
    // Iteration: 1
    // Iteration: 2
}
```

#### 5\. **Encapsulating Behavior**

You can pass behavior as parameters for flexibility in APIs.

**Example: Sorting with Custom Comparator**

```
fun main() {
    val names = listOf("John", "Alice", "Bob")
    val sortedNames = names.sortedWith { a, b -> a.length - b.length }
    println(sortedNames) // Output: [Bob, John, Alice]
}
```

#### 6\. **Asynchronous Programming**

Higher-order functions are often used in APIs for asynchronous programming, like callbacks or coroutines.

**Example: Callback Pattern**

```
fun fetchData(onSuccess: (String) -> Unit, onFailure: (Exception) -> Unit) {
    try {
        val data = "Data fetched successfully"
        onSuccess(data)
    } catch (e: Exception) {
        onFailure(e)
    }
}

fun main() {
    fetchData(
        onSuccess = { println(it) },
        onFailure = { println("Error: ${it.message}") }
    )
}
```

#### 7\. **DSLs and Fluent APIs**

Higher-order functions are heavily used in Kotlin DSLs (Domain Specific Languages), like for building UI or defining rules.

**Example: Kotlin `apply` DSL**

```
data class Person(var name: String, var age: Int)

fun main() {
    val person = Person("John", 30).apply {
        name = "Alice"
        age = 25
    }
    println(person) // Output: Person(name=Alice, age=25)
}
```

### Benefits:

1. **Conciseness**: Simplifies code by reducing boilerplate.
2. **Flexibility**: Enables passing and returning behavior dynamically.
3. **Readability**: Code becomes more declarative and easier to understand.
4. **Modularity**: Helps create reusable components and abstractions.

### Common Higher-Order Functions in Kotlin:

- **`map`**: Transforms a collection.
- **`filter`**: Filters elements based on a condition.
- **`reduce` / `fold`**: Aggregates values.
- **`forEach`**: Iterates through elements.
- **`apply` / `let` / `run`**: Scope functions for object manipulation.

By leveraging higher-order functions, you can write more expressive, modular, and efficient Kotlin code.


12. Q: List three high order functions in Kotlin.

A:

Here are three commonly used higher-order functions in Kotlin:

### 1\. **`map`**

Transforms each element in a collection and returns a new collection containing the results.

**Example:**

```
fun main() {
    val numbers = listOf(1, 2, 3, 4)
    val squared = numbers.map { it * it }
    println(squared) // Output: [1, 4, 9, 16]
}
```

### 2\. **`filter`**

Filters a collection based on a given condition and returns a new collection with only the elements that satisfy the condition.

**Example:**

```
fun main() {
    val numbers = listOf(1, 2, 3, 4, 5)
    val evens = numbers.filter { it % 2 == 0 }
    println(evens) // Output: [2, 4]
}
```

### 3\. **`forEach`**

Performs the specified action on each element in a collection.

**Example:**

```
fun main() {
    val numbers = listOf(1, 2, 3, 4)
    numbers.forEach { println(it) }
    // Output:
    // 1
    // 2
    // 3
    // 4
}
```

These higher-order functions are widely used for concise and expressive manipulation of collections and other iterable data structures in Kotlin.

13. Q: What are high order functions in Kotlin?

A:

**Higher-order functions** in Kotlin are functions that either:

1. Take another function as a parameter, or
2. Return a function as a result, or
3. Both.

Higher-order functions are a key feature of functional programming, enabling concise, flexible, and reusable code.

---

### Defining Higher-Order Functions

1. **Passing Functions as Parameters**:
    - You can pass a function or a lambda expression as an argument to a higher-order function.
2. **Returning Functions**:
    - A higher-order function can return another function.

---

### Example 1: Passing Functions as Parameters

```
fun performOperation(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

fun main() {
    val sum = performOperation(5, 3) { x, y -> x + y }
    println("Sum: $sum") // Output: Sum: 8

    val multiply = performOperation(5, 3) { x, y -> x * y }
    println("Multiply: $multiply") // Output: Multiply: 15
}
```

### Example 2: Returning Functions

```
fun createMultiplier(factor: Int): (Int) -> Int {
    return { number -> number * factor }
}

fun main() {
    val multiplier = createMultiplier(3)
    println(multiplier(5)) // Output: 15
}
```

### Common Built-In Higher-Order Functions in Kotlin

1. **`map`**: Transforms each element in a collection.
2. **`filter`**: Filters elements based on a condition.
3. **`reduce`**: Aggregates values in a collection.
4. **`forEach`**: Executes a block of code for each element.
5. **`apply` / `let` / `run`**: Scope functions for object manipulation.

---

### Benefits of Higher-Order Functions

1. **Conciseness**: Reduce boilerplate code.
2. **Reusability**: Create general-purpose functions by passing behavior as arguments.
3. **Readability**: Makes the code more expressive and easier to understand.
4. **Modularity**: Helps separate logic and behavior.

Higher-order functions are a powerful tool for creating flexible and maintainable code in Kotlin.


-----------------------------------------------
----- CLASS, ABSTRACT CLASS, AND OOP ----------
-----------------------------------------------

14. Q: What is class in Kotlin?

A: 

A **class** in Kotlin is a blueprint for creating objects, representing a combination of state (properties) and behavior (functions). Classes are fundamental to object-oriented programming in Kotlin and are used to define the structure and functionality of an object.

---

### Key Features of a Class in Kotlin

1. **Properties**: Variables that store data (state) of the class.
2. **Functions**: Methods that define behaviors or operations for objects of the class.
3. **Constructors**: Used to initialize objects of the class.
4. **Encapsulation**: Ability to control access to class members using visibility modifiers (`public`, `private`, `protected`, `internal`).
5. **Inheritance**: Ability to derive a class from another class.

---

### Declaring a Class

```
fun main() {
    val obj = MyClass()
    obj.name = "Alice" // Accessing and modifying a property
    obj.display()      // Calling a method
}
```

### Creating an Object

To create an object of a class, use the `className()` syntax:

```
fun main() {
    val obj = MyClass()
    obj.name = "Alice" // Accessing and modifying a property
    obj.display()      // Calling a method
}
```

**Output:**

```
Name is Alice
```

---

### Primary Constructor

Kotlin classes can have a **primary constructor** for initializing properties:

```
class Person(val name: String, var age: Int)

fun main() {
    val person = Person("John", 25)
    println("${person.name} is ${person.age} years old")
}
```

**Output:**

```
John is 25 years old
```

### Secondary Constructors

A class can also have secondary constructors for additional initialization logic.

```
class Person {
    var name: String
    var age: Int

    constructor(name: String, age: Int) {
        this.name = name
        this.age = age
    }
}

fun main() {
    val person = Person("Alice", 30)
    println("${person.name} is ${person.age} years old")
}
```

### Inheritance

A class can inherit another class using the `:` syntax.

```
open class Animal {
    fun sound() = println("Animal makes a sound")
}

class Dog : Animal() {
    fun bark() = println("Dog barks")
}

fun main() {
    val dog = Dog()
    dog.sound() // Inherited method
    dog.bark()  // Method from Dog
}
```

**Output:**

```
Animal makes a sound Dog barks
```

### Visibility Modifiers

1. **`public`** (default): Accessible from anywhere.
2. **`private`**: Accessible only within the class.
3. **`protected`**: Accessible within the class and its subclasses.
4. **`internal`**: Accessible within the same module.

---

### Special Types of Classes

1. **Data Class**: Used to store data with automatically generated methods like `equals`, `hashCode`, and `toString`.
    
    ```
    data class User(val name: String, val age: Int)
    ```
    
2. **Sealed Class**: Used for restricted class hierarchies.
    
    ```
    sealed class Shape{

    }
    ```
    
3. **Abstract Class**: Contains abstract methods and cannot be instantiated directly.
    
    ```
    abstract class Vehicle {     
        abstract fun drive() 
    }
    ```
    
4. **Object Class**: A singleton instance.
    
    ```
    object Singleton
    ```


### Summary

- **Class**: Blueprint for objects.
- **Object**: Instance of a class.
- **Encapsulation**: Controlled access to class members.
- **Inheritance**: Reuse functionality in derived classes.

Classes in Kotlin provide a robust and flexible way to model real-world entities and their behaviors.

15. Q: List all design patterns of OOP (Object-Oriented Programming) design in Kotlin, and simply introduce them.

A: 

Design patterns are standard solutions to common software design problems. In Object-Oriented Programming (OOP), they are categorized into **creational**, **structural**, and **behavioral** patterns. Below is a list of common OOP design patterns in Kotlin, with a brief introduction to each:

---

## **Creational Design Patterns**

These patterns focus on the process of object creation.

1. **Singleton**
    
    - Ensures that a class has only one instance and provides a global access point.
    - **Kotlin Implementation**: Use the `object` keyword.
    
    ```
    object Singleton {
        fun doSomething() = println("Singleton instance")
    }
    ```

2. **Factory Method**
    
    - Defines a method for creating objects but allows subclasses to alter the type of objects created.
    
    ```
    interface Animal {
        fun sound(): String
    }
    class Dog : Animal {
        override fun sound() = "Bark"
    }
    class AnimalFactory {
        fun createAnimal(type: String): Animal = when (type) {
            "dog" -> Dog()
            else -> throw IllegalArgumentException("Unknown type")
        }
    }
    ```
    
3. **Abstract Factory**
    
    - Provides an interface for creating families of related objects without specifying their concrete classes.
    
    ```
    interface FurnitureFactory {
        fun createChair(): Chair
        fun createTable(): Table
    }
    ```
    
4. **Builder**
    
    - Separates the construction of a complex object from its representation.
    
    ```
    class Car(val engine: String, val wheels: Int, val color: String)
    class CarBuilder {
        var engine: String = "Default Engine"
        var wheels: Int = 4
        var color: String = "Black"
        fun build() = Car(engine, wheels, color)
    }
    ```
    
5. **Prototype**
    
    - Creates a new object by copying an existing one.
    
    ```
    data class Prototype(val name: String, val age: Int)
    ```

## **Structural Design Patterns**

These patterns deal with object composition and structure.

1. **Adapter**
    
    - Converts one interface into another that a client expects.
    
    ```
    interface Usb {
        fun connectWithUsbCable()
    }
    class UsbToMicroUsbAdapter : Usb {
        override fun connectWithUsbCable() = println("Connected via USB Adapter")
    }
    ```

2. **Decorator**
    
    - Dynamically adds responsibilities to an object without modifying its structure.
    
    ```
    interface Coffee {
        fun cost(): Double
    }
    class BasicCoffee : Coffee {
        override fun cost() = 5.0
    }
    class MilkDecorator(private val coffee: Coffee) : Coffee {
        override fun cost() = coffee.cost() + 1.5
    }
    ```
    
3. **Proxy**
    
    - Provides a surrogate or placeholder for another object to control access.
    
    ```
    class RealService : Service {
        override fun execute() = println("Executing Real Service")
    }
    class ProxyService(private val service: RealService) : Service {
        override fun execute() = println("Proxy before execution").also { service.execute() }
    }
    ```
    
4. **Composite**
    
    - Composes objects into tree-like structures to represent part-whole hierarchies.
    
    ```
    interface Component {
        fun operation()
    }
    class Leaf : Component {
        override fun operation() = println("Leaf operation")
    }
    class Composite : Component {
        private val children = mutableListOf<Component>()
        override fun operation() {
            println("Composite operation")
            children.forEach { it.operation() }
        }
        fun add(component: Component) = children.add(component)
    }
    ```
    
5. **Bridge**
    
    - Separates an abstraction from its implementation so the two can vary independently.

    ```
    interface Device {
        fun turnOn()
    }
    class TV : Device {
        override fun turnOn() = println("TV turned on")
    }
    ```
    
6. **Flyweight**
    
    - Reduces memory usage by sharing common parts of an object.
    
    ```
    class FlyweightFactory {
        private val cache = mutableMapOf<String, Flyweight>()
        fun getFlyweight(key: String): Flyweight = cache.computeIfAbsent(key) { Flyweight(key) }
    }
    ```
## **Behavioral Design Patterns**

These patterns focus on communication between objects.

1. **Observer**
    
    - Defines a dependency between objects so that one object is notified of state changes in another.
    
    ```
    interface Observer {
        fun update(state: String)
    }
    class Subject {
        private val observers = mutableListOf<Observer>()
        fun attach(observer: Observer) = observers.add(observer)
        fun notifyObservers(state: String) = observers.forEach { it.update(state) }
    }
    ```
    
2. **Strategy**
    
    - Defines a family of algorithms and lets the client choose one at runtime.
    
    ```
    interface Strategy {
        fun execute(): String
    }
    class StrategyA : Strategy {
        override fun execute() = "Executing Strategy A"
    }
    ```
    
3. **Command**
    
    - Encapsulates a request as an object, allowing parameterization of clients with queues or logs.
    
    ```
    interface Command {
        fun execute()
    }
    class PrintCommand : Command {
        override fun execute() = println("Print command executed")
    }
    ```
    
4. **State**
    
    - Allows an object to alter its behavior when its internal state changes.
    
    ```
    class StateContext {
        var state: State = InitialState()
    }
    ```
    
5. **Chain of Responsibility**
    
    - Passes a request along a chain of handlers until one of them handles it.

    ```
    abstract class Handler {
        var next: Handler? = null
        abstract fun handleRequest(request: String)
    }
    ```
    
6. **Mediator**
    
    - Encapsulates object communication within a mediator object.
    
    ```
    interface Mediator {
        fun notify(sender: Component, event: String)
    }
    ```
    
7. **Visitor**
    
    - Separates an algorithm from the structure it operates on.
    
    ```
    interface Visitor {
        fun visit(element: Element)
    }
    ```

### Summary

Design patterns help structure and solve software design problems. Kotlin simplifies many patterns due to its features, like `object` for Singleton or lambdas for Strategy. Adapting these patterns depends on the problem's requirements and Kotlin's language capabilities.

16. Q: What is property in class in Kotlin?

A: 

In Kotlin, a **property** is a key concept in classes that represents a value associated with an object. Properties are essentially fields (variables) within a class, but they are much more powerful because they come with built-in getters and setters for managing their state. Kotlin provides a more concise and flexible way to define and work with properties compared to Java.

### Key Features of Properties in Kotlin:

1. **Automatic Getter and Setter**: By default, Kotlin generates a getter and setter for the property.
2. **Custom Getter and Setter**: You can override the getter and setter to customize their behavior.
3. **Immutable Properties**: Properties can be declared as `val` (read-only) or `var` (mutable).
4. **Backing Fields**: Kotlin allows you to store a property value in a backing field, providing access to the internal value of the property.

---

### Syntax for Declaring Properties

#### 1\. **Read-Write Property (Using `var`)**:

- A property that can be modified.

```
class Person {
    var name: String = "John" // Mutable property
}

fun main() {
    val person = Person()
    println(person.name) // Output: John
    person.name = "Alice" // Changing the value
    println(person.name) // Output: Alice
}
```

#### 2\. **Read-Only Property (Using `val`)**:

- A property that cannot be modified after initialization (similar to `final` fields in Java).

```
class Person {
    val birthYear: Int = 1990 // Immutable property
}

fun main() {
    val person = Person()
    println(person.birthYear) // Output: 1990
    // person.birthYear = 1995 // Error: Val cannot be reassigned
}
```

### Custom Getter and Setter

Kotlin allows you to define **custom** behavior for properties using custom getters and setters.

#### Example of Custom Getter:

```
class Person(private var _age: Int) {
    var age: Int
        get() = _age // Custom getter
        set(value) {
            if (value >= 0) _age = value // Custom setter with validation
            else println("Age cannot be negative")
        }
}

fun main() {
    val person = Person(25)
    println(person.age) // Custom getter
    person.age = 30      // Custom setter
    println(person.age)
    person.age = -5      // Error in setter, no negative values
}
```

**Output:**

```
25
30
Age cannot be negative
```

### Backing Fields

Kotlin uses **backing fields** to store the value of a property when you need custom logic in the getter or setter, but you still want to refer to the actual stored value.

#### Example of Backing Field:

```
class Person(private var _name: String) {
    var name: String
        get() = _name // Access the backing field
        set(value) {
            if (value.isNotEmpty()) _name = value
        }
}

fun main() {
    val person = Person("John")
    println(person.name) // Output: John
    person.name = "Alice" // Setter updates the value
    println(person.name) // Output: Alice
}
```

### Lateinit Properties

For **non-nullable properties** that are initialized later (e.g., dependency injection), Kotlin provides `lateinit` keyword, which ensures the property will be initialized before being accessed, otherwise an exception will be thrown.

#### Example of `lateinit`:

```
class Person {
    lateinit var name: String
    
    fun initializeName(name: String) {
        this.name = name
    }
}

fun main() {
    val person = Person()
    person.initializeName("John")
    println(person.name) // Output: John
}
```

**Note:** `lateinit` can only be used with mutable (`var`) properties of non-primitive types. Trying to access an uninitialized `lateinit` property will throw an `UninitializedPropertyAccessException`.


### Summary

- **`val`**: Read-only property (immutable).
- **`var`**: Read-write property (mutable).
- **Custom Getter and Setter**: Allows you to control how properties are accessed and modified.
- **Backing Fields**: Helps manage internal state when custom logic is needed.
- **`lateinit`**: Allows late initialization for non-null properties.

Properties in Kotlin help encapsulate data, manage access to fields, and provide clean, expressive ways to manipulate object state.

17. Q: What is method in class in Kotlin?

A: 

18. Q: What is the difference between property of class and variable in Kotlin?

A:

19. Q: What is the difference between method of class and function in Kotlin?

A: 

20. Q: How to inherit a base class in Kotlin?

A:

21. Q: How to implement an abstract class in Kotlin?

A:

22. Q: How to override a member of an abstract class in Kotlin?

A:

-----------------------------------------------
----------------- COROUTINES ------------------
-----------------------------------------------

23. Q: What are coroutine in Kotlin?

A: 

24. Q: How to execute a function with asynchronization in Kotlin?

A:

-----------------------------------------------
----------------- FLOW, STATEFLOW -------------
-----------------------------------------------

25. Q: What are flows in Kotlin?

A: 

26. Q: What are cold flows in Kotlin?

A:

27. Q: What are hot flows in Kotlin?

A:
