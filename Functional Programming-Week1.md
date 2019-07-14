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

#### Question #1 - Evaluation Strategy : Which is the fastest?</h4>
<p>
def test(x: Int, y: Int) = x * x</p>
<h5 id="test23">test(2,3)</h5>
<pre><code>

##### test(2,3)
	|	CBV			|	CBN			|
	|	test(2,3)	|	test(2,3)	|
	|	2 * 2		|	2 * 2		|
	|	4			|	4			|
	Ans. CBV = CBN
</code></pre>
<h5 id="test34-8">test(3+4, 8)</h5>
<pre><code>
##### test(3+4, 8)
	|	CBV				|	CBN				|
	|	test(3+4,8)		|	test(3+4,8)		|
	|	test(7,8)		|	(3+4) * (3+4)	|
	|	7 * 7			|	7 * (3+4)		|
	|	49				|	7 * 7			|
	|					|	49				|
	Ans. CBV is faster than CBN
</code></pre>
<h5 id="test7-24">test(7, 2*4)</h5>
<pre><code>	
##### test(7, 2*4)
	|	CBV				|	CBN				|
	|	test(7,2*4)		|	test(7,2*4)		|
	|	test(7,8)		|	7 * 7			|
	|	7 * 7			|	49				|
	|	49				|					|
	Ans. CBV is slower than CBN
</code></pre>
<h5 id="test34-24">test(3+4, 2*4)</h5>
<pre><code>
##### test(3+4, 2*4)
	|	CBV					|	CBN					|
	|	test(3+4,2*4)		|	test(3+4,2*4)		|
	|	test(7,2*4)			|	(3+4) * (3+4)		|
	|	test(7,8)			|	7 * (3+4)			|
	|	7 * 7				|	7 * 7				|
	|	49					|	49					|
	Ans. CBV = CBN	
</code></pre>


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNzk5NDIxNzhdfQ==
-->