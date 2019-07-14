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
	|	CBV			|	CBN			|
	|	test(2,3)	|	test(2,3)	|
	|	2 * 2		|	2 * 2		|
	|	4			|	4			|
	Ans. CBV = CBN

##### test(3+4, 8)
	|	CBV				|	CBN				|
	|	test(3+4,8)		|	test(3+4,8)		|
	|	test(7,8)		|	(3+4) * (3+4)	|
	|	7 * 7			|	7 * (3+4)		|
	|	49				|	7 * 7			|
	|					|	49				|
	Ans. CBV is faster than CBN
	
##### test(7, 2*4)
	|	CBV				|	CBN				|
	|	test(7,2*4)		|	test(7,2*4)		|
	|	test(7,8)		|	7 * 7			|
	|	7 * 7			|	49				|
	|	49				|					|
	Ans. CBV is slower than CBN

##### test(3+4, 2*4)
	|	CBV					|	CBN					|
	|	test(3+4,2*4)		|	test(3+4,2*4)		|
	|	test(7,2*4)			|	(3+4) * (3+4)		|
	|	test(7,8)			|	7 * (3+4)			|
	|	7 * 7				|	7 * 7				|
	|	49					|	49					|
	Ans. CBV = CBN	


> Nag Arvind Gudiseva

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzU4OTkyOTcsLTY3NjUxODE4M119
-->