
# The Basics

## Declaring Variables
A variable declared with `val` is constant.  A variable declared with `var` can be changed.  In scala, the "go to" option is `val` as this is in the spirit of functional programming.  And believe it or not, most variable values actually don't change.

### Variable Types
You don't have to specify the type of a variable as it is inferred.  There is no distinction between primitives and class types.  All types are actually just classes.  The conversion between primitive and wrapper classes does occur behind the scenes in the JVM.

| Type    | Description |
| ------- | ----------- |
| Byte    |        |
| Char    | RichChar       |
| Short   |        |
| Int     | RichInt, BigInt       |
| Long    |        |
| Float   |        |
| Double  | RichDouble, BigDecimal       |
| Boolean |        |
| Text    |        |
| String  | A java.lang.String object has access to the functionality of the StringOps class. |

### "Varags"
You can specify that a parameter is "varargs" via the asterik character *

```scala
private def count(values: Int*): Int {
   ...
}

```

### Operators
Operators are actually methods.

```scala
scala> val a: Int = 5
a: Int = 5

scala> val b: Int = 6
b: Int = 6

scala> a + b
res0: Int = 11

scala> a.+(b)
res1: Int = 11
```

### Syntax
`[val|var] <variable name>: <type> = <value>`

## Calling Methods
You can call methods in two ways
`a method b`

OR

`a.method(b)`

## The () Syntax
The `()` operator can be called on any object and it is shorthand for the apply method.

`s(4)` === `s.apply(4)`

# Data Types
RichInt


# Control Structures

## If Statements
These function as you would expect from other languages, but something of note is that the expression has a value.

```
val success = 0
val result = if (success == 0) "sucess" else  "failure"
```

What if the type of both branches do not match?  The common supertype is returned (ex: Any).


## While Loops
While loops are similar like in other languages, for example:
```scala
var n: Integer = 10
while (n > 0) {
   println(n)
   n -= 1
}
```

## For Loops
There are two choices.
```scala
for (i <- 1 to 10)
   println(i) 
```

OR

Traversal of elements
```scala
   for (i <- "Hello")
      println(i) 
```

## Expression Blocks
`{...}` take the value of the last expression.

```scala
val result = {
	val success = 0;
	if (success == 0) "sucess" else  "failure"
}
```


# Workspace
What is the difference between -> aNd => in the map function?



# Resources
[<a name="scala-for-the-impatient">1</a>] Horstmann, Cay S. [Scala for the Impatient][scala-for-the-impatient]. Addison-Wesley., 2017.
[<a name="alvinalexander-varargs">2</a>] ["Scala varargs syntax (and examples)"][alvinalexander-varargs]
https://docs.scala-lang.org/tour/implicit-parameters.html
https://alvinalexander.com/scala/how-create-scala-list-range-fill-tabulate-constructors


[scala-for-the-impatient]: https://learning.oreilly.com/library/view/scala-for-the/9780134540627/
[alvinalexander-varargs]: https://alvinalexander.com/scala/scala-varargs-syntax-function-examples