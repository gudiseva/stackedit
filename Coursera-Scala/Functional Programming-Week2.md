# Higher-Order Functions

- Treat functions as first-class values.
- It means like any other value, a function can be passed as a parameter and returned as a result.

> Functions that take other functions as parameters or that return functions as results are called ***higher order functions***.

## Function Types
- The type `A => B` is the type of a ***function*** that takes an argument of type A and returns a result of type B.
- `Int => Int` is the type of functions that map integers to integers.

## Anonymous Functions
~~Motivation~~: Passing functions as parameters leads to the creation of many small functions.  It becomes tedious to define and name these functions using def.

Example:
`(x: Int, y: Int) => x * x * x`
--- `(x: Int, y: Int)` is the ***parameter*** of the function
--- `x * x * x` is the ***body*** of the function

An Anonymous function can always be expressed using def as follows:
`def f(x: Int, y: Int) = x * x * x; f`

where ***f*** is an 

### String Literals
- We do not define a String using def.
Instead of
	`def str = "abc"; println(str)`
We can write
	`println("abc")`
- This is because Strings exist as literals.

### Function Literals
- Lets us write a function without giving it a name,
-  These are called *Anonymous Functions*.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU1NTg1MzkxNiw5MjEyMzMxNTldfQ==
-->