---


---

<h1 id="functional-programming---elements">Functional Programming - Elements</h1>
<h2 id="substitution-model">Substitution Model</h2>
<p>def square (x: Double) = x * x<br>
def sumOfSquares (x: Double, y: Double) = square(x) + square(y)</p>
<h2 id="evaluation-strategy">Evaluation Strategy</h2>
<h3 id="call-by-value">call-by-value</h3>
<p>sumOfSquares(3, 2+2)<br>
sumOfSquares(3, 4)<br>
square(3) + square(4)<br>
3 * 3 + square(4)<br>
9 + square(4)<br>
9 + 4 * 4<br>
9 + 16<br>
25</p>
<h3 id="call-by-name">call-by-name</h3>
<p>sumOfSquares(3, 2+2)<br>
square(3) + square(2+2)<br>
3 * 3 + square(2+2)<br>
9 + square(2+2)<br>
9 + (2+2) * (2+2)<br>
9 + 4 * (2+2)<br>
9 + 4 * 4<br>
25</p>
<h4 id="question-1---evaluation-strategy--which-is-the-fastest">Question #1 - Evaluation Strategy : Which is the fastest?</h4>
<p>def test(x: Int, y: Int) = x * x</p>
<h5 id="test23">test(2,3)</h5>
<pre><code>|	CBV			|	CBN			|
|	test(2,3)	|	test(2,3)	|
|	2 * 2		|	2 * 2		|
|	4			|	4			|
Ans. CBV = CBN
</code></pre>
<h5 id="test34-8">test(3+4, 8)</h5>
<pre><code>|	CBV				|	CBN				|
|	test(3+4,8)		|	test(3+4,8)		|
|	test(7,8)		|	(3+4) * (3+4)	|
|	7 * 7			|	7 * (3+4)		|
|	49				|	7 * 7			|
|					|	49				|
Ans. CBV is faster than CBN
</code></pre>
<h5 id="test7-24">test(7, 2*4)</h5>
<pre><code>|	CBV				|	CBN				|
|	test(7,2*4)		|	test(7,2*4)		|
|	test(7,8)		|	7 * 7			|
|	7 * 7			|	49				|
|	49				|					|
Ans. CBV is slower than CBN
</code></pre>
<h5 id="test34-24">test(3+4, 2*4)</h5>
<pre><code>|	CBV					|	CBN					|
|	test(3+4,2*4)		|	test(3+4,2*4)		|
|	test(7,2*4)			|	(3+4) * (3+4)		|
|	test(7,8)			|	7 * (3+4)			|
|	7 * 7				|	7 * 7				|
|	49					|	49					|
Ans. CBV = CBN	
</code></pre>
# Test
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MTc1NTg4NThdfQ==
-->