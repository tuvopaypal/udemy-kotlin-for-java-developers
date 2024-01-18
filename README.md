# Kotlin Tutorial

## Fun Facts

-   Kotlin is named after a Russian island

## Differences Between Kotlin and Java

-   No semi-colons
-   Kotlin imports a lot of classes from standard library in every file so you do not have to include them (i.e. System, Array)
-   A lot of Kotlin classes are aliases for Java standard library classes, with the exception of String
-   no ternary statements
-   no `new` keyword needed to create classes

## Code Examples

### Variable Declarations

-   `val` is used for immutable declarations
-   `var` is used for mutable declaratons

```kt
val number = 4
val str: String = "hello" // explicit declaration
number = 10 // error!

var any = 5
any = 6 // no error
```

### Strings

-   `.length` is a property, not a method

```kt
val str: String = "hello"
println(str.length)
```

### Equality Operators

-   for `data` classes, `==` compares structural equality, whereas `===` compares referential equality

```kt
fun main() {
    val tu = Person("Tu", 36)
    println(tu) // Person(name=Tu, age=36)
    val tuClone = Person("Tu", 36)

    println(tu == tuClone) // true
    println(tu === tuClone) // false
}

data class Person(val name: String, val age: Int) {
}
```

### Bit Operators

-   Instead of using `&`, `|`, and `^`, Kotlin uses `and`, `or` and `xor`

### String Templates

```kt
val tu = Person("Tu", 36)
println("Hi my name is ${tu.name} and I am ${tu.age} years old")
// Hi my name is Tu and I am 36 years old

val legalDrinkingAge = 21
println("The legal drinking age is $legalDrinkingAge")
// The legal drinking age is 21
```

Multi-line strings

```kt
val longString = """Humpty Dumpty
                   |sat on a wall,
                   |and had a great fall
                 """.trimMargin()
println(longString)

// Humpty Dumpty
// sat on a wall,
// and had a great fall
```

### REPL

In IntelliJ, `Tools` -> `Kotlin` -> `REPL` will open a console to run Kotlin code with compiling.

### Arrays

```kt
val names = arrayOf("Tu", "Brenda")
println(names) // Ljava.lang.String;@85ede7b

for (name in names) {
    println(name)
}

// Tu
// Brenda
```

### Null

```kt
var str: String? = null
str?.uppercase()
```

**Elvis operator**

```kt
fun main() {
    var tu = Person(null, null)
    var name = tu.name ?: "default name"
    println(name)
}

data class Person(val name: String?, val age: Int?) {
}
```

**Safely passing nullable values into functions non-nullable params**

```kt
fun main() {
    var str: String? = "Not NULL"
    printText(str) // error: type mismatch
    str?.let { // safe invocation
        printText(it) // lambda
    }
}

fun printText(str: String) {
    println(str)
}
```

## Classes

- classes are public by default
- classes do not need to match the file name and you can have multiple public classes in one file
- the compiler generates a constructor for each class
- Kotlin generates getters/setters
- data classes come with the `copy` method

## Functions

- Default return is `unit`
- Params must have type annotations
- `vararg` is used for variable arguments

## Inheritance

- Must use `open` class modifier since all classes are `final` by default, with the exception of `abstract` classes
- To override functions from parent class, you must specify `override`


## Singletons

- use `object`

## Loops

```kt
fun main() {
    for (i in 1..5) {
        println(i) // 1 2 3 4 5
    }

    for (i in 5 downTo 1) {
        println(i) // 5 4 3 2 1
    }

    val arr = arrayOf("a", "b", "c")
    for (i in arr.indices) {
        println("$i = ${arr[i]}")
    }
    // 0 = a
    // 1 = b
    // 2 = c

    arr.forEach { println(it) } // a b c
    arr.forEachIndexed {
        i, value -> println("$i = $value")
    }
    // 0 = a
    // 1 = b
    // 2 = c
}
```

## Switch/When

```kt
fun main() {
    val num = 1

    when (num) {
        100 -> println("100")
        200 -> println("200")
        300 -> println("300")
        else -> println("none")
    }
}
```