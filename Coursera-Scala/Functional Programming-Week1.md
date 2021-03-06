# Functional Programming - Elements

## Substitution Model

    def square (x: Double) = x * x

    def sumOfSquares (x: Double, y: Double) = square(x) + square(y)

## Evaluation Strategy

### call-by-value

    sumOfSquares(3, 2+2)
    sumOfSquares(3, 4)
    square(3) + square(4)
    3 * 3 + square(4)
    9 + square(4)
    9 + 4 * 4
    9 + 16
    25


### call-by-name

    sumOfSquares(3, 2+2)
    square(3) + square(2+2)
    3 * 3 + square(2+2)
    9 + square(2+2)
    9 + (2+2) * (2+2)
    9 + 4 * (2+2)
    9 + 4 * 4
    25

#### Question #1 - Evaluation Strategy : Which is the fastest?
def test(x: Int, y: Int) = x * x

##### test(2,3)
| CBV | CBN |
|--|--|
| `test(2,3)` | `test(2,3)` |
| `2 * 2` | `2 * 2` |
| `4` | `4` |

Ans. CBV = CBN

##### test(3+4, 8)
| CBV | CBN |
|--|--|
| `test(3+4,8)` | `test(3+4,8)` |
| `test(7,8)` | `(3+4) * (3+4)` |
| `7 * 7` | `7 * (3+4)` |
| `49` | `7 * 7` |
|  | `49` |

Ans. CBV is faster than CBN
	
##### test(7, 2*4)
| CBV | CBN |
|--|--|
| `test(7,2*4)` | `test(7,2*4)` |
| `test(7,8)` | `7 * 7` |
| `7 * 7` | `49` |
| `49` |  |

Ans. CBV is slower than CBN

##### test(3+4, 2*4)
| CBV | CBN |
|--|--|
| `test(3+4,2*4)` | `test(3+4,2*4)` |
| `test(7,2*4)` | `(3+4) * (3+4)` |
| `test(7,8)` | `7 * (3+4)` |
| `7 * 7` | `7 * 7` |
| `49` | `49` |

Ans. CBV = CBN	


### Infinite Loop
#### Define

    def first(x: Int, y: Int) = x

#### Expression

| CBV | CBN |
|--|--|
| `first(1, loop)` | `first(1, loop)` |
| loop <-> loop | `1` |

 - [ ] CBN terminates more often
 - [ ] Scala uses CBV over CBN.  It is because CBV is exponentially more beneficial and also due to Imperative Paradigm in Scala.
 - [ ] However, to make Scala use CBN, us the below syntax:

	> **=>**

### CBN
#### Example

    def constOne(x: Int, y: => Int) = 1

#### Evaluations
##### constOne(1+2, loop)
| CBV | CBN |
|--|--|
| `constOne(1+2, loop)` |  |
| `constOne(3, loop)` |  |
|  | 1 |

##### constOne(loop, 1+2)
| CBV | CBN |
|--|--|
| `constOne(loop, 1+2)` |  |
| loop <-> loop |  |


## Conditionals and Value Definitions

### Conditional Expressions
#### if-else

    def abs(x: Int) = if (x >= 0) x else -x

The above is an expression and not a statement.

`x>=0` is a *predicate*, of type Boolean.

### Re-write Rules (short-circuit evaluation)

    !true --> false
    !false --> true
    true && e --> e
    false && e --> false
    true || e --> true
    false || e --> e

### Value Definitions
| def | val |
|--|--|
| by-name | by-value |
| RHS is evaluated on each use | RHS is evaluated at the point of the definition itself |
|  | Thereafter the name refers to the value |
|  | Example: |
|  | `val x = 2` |
|  | `val y = square(x)` |
|  | y above refers to 4, not square(2) |

### Recursive Functions
- In recursive function, RHS calls itself
- Recursive functions need an explicit return type
- For non-recursive functions, the return type is optional

### Blocks and Visibility
- The definitions inside a block are only visible from within the block.
- The definitions inside a block ***shadow*** definitions of the same names outside the block.

#### Lexical Scoping
- Definitions of outer blocks are visible inside a block unless they are shadowed.

#### Nesting
- Name space control
- Reusing outer definitions without passing them explicitly in parameters

### Semicolons
- if there are more than one statements on a line, they need to be separated by semicolons:

    val y = x + 1; y * y

### Semicolons and infix operators
- Write multi-line expression in parentheses:
> (someLongExpression 
> "+" someOtherExpression)

- Write the operator on the first line, because this tells the Scala compiler that the expression is not yet finished:
> someLongExpression +
> someOtherExpression

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE4MjE5OTkzMCwtODA3NzIyNTkxLC0xNz
k5NjMyOTEzLC03MzY3ODI3MzAsLTExOTYxOTgxMTcsNzE0NDUx
ODc4LC0xNTQ0MTE0MzI3LC02MzM1MTYwODUsMTYyOTE5OTQxMy
wxNzU0MTE3MDk1LC00OTg4NTAxMzAsNjMzNTE3NjQyLDE4NjEw
NjY3ODcsMTk4ODE3NzQwMV19
-->