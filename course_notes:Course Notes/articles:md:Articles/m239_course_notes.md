# Intro to Combinatorics

_UWaterloo, Math 239, Spring 2020_

Notes by Navaz Alani

__Instructors__:

* David Gosset (david.gosset@uwaterloo.ca)
* David Jao (djao@uwaterloo.ca)
* Martin Pei (mpei@uwaterloo.ca)
* Douglas Stebila (dstebila@uwaterloo.ca)
* Xiaohong Zhang (xiaohong.zhang@uwaterloo.ca)

"Symmetry is one of the most powerful tools in the mathematics arsenal."
~ [David Jao](https://djao.math.uwaterloo.ca/)

****

## Tools for Enumeration

__Main interest__: counting the size of various sets.

Let us recall the elementary operations that can be performed with sets. Let $A,
B$ be finite sets. We have the following operations:

__UNION__: $A\cup B = \{x | x \in A \text{ or } x \in B\}$

__INTERSECTION__: $A\cap B = \{x | x\in A \text{ and } x \in B\}$

In order to count the size of a set, one of the approaches used is to build that
set using unions of smaller sets, whose sizes are known. It is important,
therefore, to understand the relationship between the cardinality of a set and
the cardinalities of the sets that it is built from.

Most readers should be aware of the following identity: $|A\cup B| = |A| + |B| -
|A\cap B|$ which is of utmost importance when it comes to counting the size of
sets as it provides a relationship between the cardinality of a set $A\cup B$
and the cardinalities $|A|$ and $|B|$. A much simpler case arises when $A\cap B
= \emptyset$ i.e. when $A\cup B$ is a disjoint union- the identity reduces to
$|A\cup B| = |A| + |B|$.

This identity can be extended to a more general one. Given sets $A_1, \dots,
A_n$ with $A_i\cap A_j = \emptyset$ for $1 \leq i < j \leq n$, we have $|A_1\cup
\dots \cup A_n| = \sum_{j=1}^n |A_j|$. This is readily proven by induction on
$n$. In the case of $n=2$, the identity holds, as seen above. Now, assuming that
the identity holds for some $n > 2$, we can verify it for case $n+1$:

$\begin{aligned}
    |A_1\cup \dots \cup A_n \cup A_{n+1}| &= |(A_1\cup \dots \cup A_n)
    \cup A_{n+1}|\\
    &= |(A_1\cup \dots \cup A_n)| + |A_{n+1}| - |(A_1\cup \dots
    \cup A_n)\cap A_{n+1}|\\
    &= \sum_{i=1}^n |A_i| + |A_{n+1}| - |(A_1 \cap A_{n+1})\cup \dots \cup
    (A_n\cap A_{n+1})|\\
    &= \sum_{i=1}^{n+1} |A_i| - |\emptyset| = \sum_{i=1}^{n+1} |A_i|
\end{aligned}$

This allows us to state one of the techniques used for problem solving in this
course: __Recognizing that a set can be expressed as a disjoint union of other
sets__. The general identity derived above proves to be helpful in this
technique. Now, back to set operations:

__CARTESIAN PRODUCT__: $A\times B = \{(a, b) | a \in A, b \in B\}$. This object
has the property that $|A \times B| = |A|\cdot |B|$.

__CARTESIAN POWER__: $A^k = \{(a_1, \dots, a_k) | a_1\in A, \dots, a_k\in A\}$.
This object can be expressed alternatively as the cartesian product of $A$ with
itself, $k$ times and has the property that $|A^k| = |A|^k$.

__Example__: Let $S=\{0,1\}^k = \{(z_1, \dots, z_k) | z_1, \dots, z_k \in
\{0,1\}\}$.  $S$ is called the set of $k$-tuples of bits. Using the property of
the cartesian product outlined above, we see that $|S| =|\{0,1\}^k| =
|\{0,1\}|^k = 2^k$.

__Example__: Let $S=\{(z_1, z_2, z_3)\in \{0,1\}^3 | z_1 + z_2 + z_3 \leq 1\}$.
Find $|S|$.  In this case, it may be easy to write out the elements of $S$ and
count them but we shall use the method of expressing $S$ as a union of 2
disjoint sets to see how it works.

We can write $S=A\cup B$ where $A=\{(z_1,z_2,z_3)\in \{0,1\}^3 | z_1 + z_2 + z_3
= 0\}$ and $B=\{(z_1,z_2,z_3)\in \{0,1\}^3 | z_1 + z_2 + z_3 = 1\}$. So clearly,
$A\cap B = \emptyset$ by the definition of $A$ and $B$. This allows us to say
that $|S| = |A| + |B|$.

Now, we can count: $A = \{(0,0,0)\}$ so $|A| = 1$ and $B = \{(1,0,0), (0,1,0),
(0,0,1)\}$ so that $|B| = 3$. Therefore, $|S| = 1 + 3 = 4$.

### Binomial Coefficients

These come up a lot when it comes to enumeration and counting problems so getting
comfortable with the binomial coefficients is important.

__Definition__: $S_{k,n} := \{\Omega \in \{1, \dots, n\} | |\Omega| = k\}$. This
will prove to be an important set definition once some of its properties have
been uncovered.  $S_{k,n}$ is the set of all subsets of $\{1, \dots, n\}$ of
size $k$.

In general, this set can be used to understand many real-life situations e.g.
the number of 5-card hands from a standard deck of 52 cards is $|S_{5,52}|$.

__THEOREM__: let $0 \leq k \leq n$. Then $|S_{k,n}| = \frac{n(n-1)\cdots(n - k +
1)}{k!}$.

__Proof__: Let $L_{k,n} := \{(a_1,\dots,a_k)\in \{1,\dots,n\}^k | a_i\neq a_j
\text{ for } i\neq j \}$. $L_{k,n}$ is the set of all $k$-tuples of distinct
elements of $\{1,\dots,n\}$.

What is $|L_{k,n}|$? Well, since the elements in the $k$-tuples are distinct,
there are $n$ possibilities for the first one, $n-1$ possibilities for the
second one and so on. In general, for the $j$-th element in the tuple, there
$n-(j-1)$ possibilities. Therefore, we get that $|L_{k,n}| = n(n-1)\cdots
(n-(k-1))$.

Now, we shall analyse a relationship between $L_{k,n}$ and $S_{k,n}$ which will
allow us to compute $|S_{k,n}|$. Observe the following:

* Each $(a_1, a_2, \dots, a_k) \in L_{k,n}$ can be mapped to an element
  $\{a_1,\dots, a_k\} \in S_{k,n}$. This mapping removes the ordering from the
  $k$-tuple.
* Each $\{a_1,\dots, a_k\} \in S_{k,n}$ is then the image of $k!$ different
  elements in $L_{k,n}$.

Using these 2 observations, we may see the following:

$|L_{k,n}| = \sum_{\Omega \in S_{k,n}} k! = |S_{k,n}|\cdot k!$

$\implies |S_{k,n}| = \frac{|L_{k,n}|}{k!}$, as desired.

Now, we may move forward to define the following object:

__Binomial Coefficient__: $\binom{n}{k} := \frac{n(n-1)\cdots(n - k + 1)}{k!}$
for $0\leq k \leq n$. Note that by this defintion, it can also be seen that
$\binom{n}{k} = \frac{n!}{(n-k)!k!}$. This version of the definition
immediately reveals the symmetrical nature of the binomial coeffcient:
$\binom{n}{k} = \binom{n}{n-k}$ because of the commutativity of multiplication
in the denominator. For convenience and convention, we also define
$\binom{n}{k} = 0$ for $k > n$.

Now, let $A_{k,n} = \{(z_1,\dots,z_n)\in \{0,1\}^n | z_1 + \dots + z_n = k\}$
for $0\leq k \leq n$. What is $|A_{k,n}|$? In previous proof, the size of
$S_{k,n}$ was determined by analysing its relationship with $L_{k,n}$ whose
size we could easily determine: we showed $L_{k,n}$ is $k!$ times larger than
$S_{k,n}$, essentially proving a 1 to many mapping $S_{k,n} \mapsto L_{k,n}$.
This strategy can also be used to find $|A_{k,n}|$ with the only difference
being that this time, the relationship is 1-1 with a set of size
$\binom{n}{k}$.  We conveniently already have such a set! - $|S_{k,n}| =
\binom{n}{k}$, as previously shown.

__THEOREM__: $|A_{k,n}| = \binom{n}{k}$

__Proof__: Observe the following:

* Each $(z_1,\dots, z_n) \in A_{k,n}$ has the propery that there must be $k$ positions
which where the element in the $n$-tuple is a 1. So each of these $n$-tuples can be mapped
to a subset $\Omega = \{j\in \{1,\dots,n\} | z_j = 1\} \in S_{k,n}$.
* Each subset $\Omega \in S_{k,n}$ can be mapped to an element $(z_1,\dots, z_k)\in A_{k,n}$
where $z_j = 1 \iff j\in \Omega$

This shows a 1-1 mapping: for each set in $S_{k,n}$, there is one corresponding $n$-tuple
in $A_{k,n}$ and for every $n$-tuple in $A_{k,n}$, there is one corresponding set in
$S_{k,n}$. Therefore, $|S_{k,n}| = |A_{k,n}|$, as desired.

__THEOREM__: _Binomial Theorem_: Let $n$ be a non-negative integer. Then $(1 + x)^n =
\sum_{k=0}^n \binom{n}{k} x^k$.

__Proof__:

We can write $1 + x = \sum_{z\in\{0,1\}}x^z$. Using this, we can do the following:

$\begin{aligned}
    (1 + x)^n &= (\sum_{z\in \{0,1\}} x^z)^n\\
    &= (\sum_{z_1\in \{0,1\}} x^{z_1})\cdots (\sum_{z_n\in \{0,1\}} x^{z_n})\\
    &= \sum_{(z_1,\dots, z_n)\in \{0,1\}^n} x^{z_1+\dots + z_n}
\end{aligned}$

At this point, what may help tie this problem up is the realisation that the set
$\{0,1\}^n = A_{0,n}\cup A_{1,n}\cup \dots \cup A_{n,n}$, a disjoint union. This is
a useful decomposition because we already know about the size of $A_{n,k}$. Then:

$\begin{aligned}
    (1 + x)^n &= \sum_{(z_1,\dots, z_n)\in \{0,1\}^n} x^{z_1+\dots + z_n}\\
    &= \sum_{k=0}^n (\sum_{(z_1,\dots, z_n)\in A_{k,n}} x^{z_1+\dots + z_n})\\
    &= \sum_{k=0}^n (\sum_{(z_1,\dots, z_n)\in A_{k,n}} x^k)\\
    &= \sum_{k=0}^n |A_{k,n}| x^k\\
    &= \sum_{k=0}^n \binom{n}{k} x^k
\end{aligned}$

As desired.

__Example__: This binomial theorem can be useful when simplifying expressions. Here
is a simple example: Simplify $\sum_{k=0}^n \binom{n}{k}$. At first glance, this looks
quite similar to the formula of the binomial theorem, just with $x$ set to 1. Let's
use this observation:

$\sum_{k=1}^n \binom{n}{k} x^k = (1 + x)^n$

Setting $x = 1$:

$\sum_{k=1}^n \binom{n}{k} = 2^n$. And there we have it- a simplified expression.

__Exercise__: Show that $\sum_{0\leq j \leq \frac{n}{2}} \binom{n}{2j} = 2^{n-1}$.
Basically, that the sum of the binomial coefficient $\binom{n}{k}$ where $k$ is even
is half of the sum of all of the terms. Again, we may use the binomial theorem here
to do most of the heavy lifting. Realise, first that

$\sum_{0\leq j\leq \frac{n}{2}} \binom{n}{2j} = \frac{1}{2}\left(\sum_{k=0}^n \binom{n}{k} +
\sum_{k= 0}^n \binom{n}{k}(-1)^k\right)$

Here, the expression in question has been replaced as an average of 2 terms, both
derived from the binomial theorem. The second term in the RHS sum has the job of
cancelling out all of the odd terms in the sum from the first term. Then, since the
even terms will have been doubly added, the sum needs to be halved, making it an
average.

Next, note that the second term in the RHS sum is just the binomial theorem for
$x$ set to $-1$, giving us $(1+(-1))^n = 0$. Therefore, we get:

$\begin{aligned}
    \sum_{0\leq j \leq \frac{n}{2}} \binom{n}{2j} &= \frac{1}{2}\left(2^n + 0 \right)\\
    &= \frac{1}{2} 2^n\\
    &= 2^{n-1}
\end{aligned}$

As desired.

__Pascal's Triangle__: This is an object of interest in mathematics simply because of
the number of properties that emerge from it. It is formed by arranging the binomial
coefficients by $n$ and $k$ into a triangle.

![Pascal's Triangle with binomial coefficients](
https://wikimedia.org/api/rest_v1/media/math/render/svg/1d13b3b68bb6bdda6b7b21001f5e40a84f46db5d)$=$
![Pascal's Triangle with numeric values](
https://wikimedia.org/api/rest_v1/media/math/render/svg/23050fcb53d6083d9e42043bebf2863fa9746043
)

One of the first things that one may notice is that every number in the triangle
is a sum of the 2 numbers above it. For example, 10 is the sum of 4 and 6 above it.
Therefore, it's easy to construct the triangle, row by row but more importantly,
this observation can be conjenctured as follows:

$\binom{n}{k} =? \binom{n-1}{k-1} + \binom{n-1}{k}$

We'll prove this, and similar identities in the next section.

## Combinatorial Proofs

* Essentially, these are the kinds of proofs which rely on counting
* A key method used is establishing identities by counting a set in two different
ways.

__Example__: $\forall 1\leq k \leq n$, $\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k}$.
As conjenctured from Pascal's triangle above.

__Proof__: We want to approach the solution by counting a set in two different ways.
One way will give us the expression on the LHS and the other way will give us the
expression for the RHS. Since these expressions are representing the cardinality of
the same set, they must be equal.

Recall $S_{k,n} = \{\Omega \in \{1,\dots,n\}||\Omega| = k\}$ which has the property
that $|S_{k,n}| = \binom{n}{k}$. This gives us the RHS expression. Now, we need to
count the size of $S_{k,n}$ in a different way which would give us the LHS expression.

Let $A=\{\Omega\in S_{k,n}| n\in \Omega\}$ and $B=\{\Omega\in S_{k,n}| n\notin \Omega\}$.
Clearly, $A\cap B = \emptyset$ and $S_{k,n} = A\cup B$ which, by our findings in the
previous section, conventiently allows us to do $|S_{k,n}| = |A| + |B|$.

_Case $k=1$_: In this case, $A=\{\{n\}\}$ and $B=\{\{1\},\dots, \{n-1\}\}$.
So that $\binom{n}{1} = |S_{1,n}| = |A| + |B| = 1 + (n-1) = \binom{n-1}{0} + \binom{n-1}{1}$.

_Case $k>1$_: In this case, $A$ and $B$ can be viewed as follows:

$\begin{aligned}
    A &= \{\{n\}\cup Q | Q \subseteq \{1,\dots, n\} \text{ and } |Q| = k-1\}\\
    &= \{\{n\}\cup Q | Q\in S_{k-1, n-1}\}
\end{aligned}$

$\begin{aligned}
    B &= \{\Omega\subseteq \{1,\dots, n-1\} | |\Omega| = k\}\\
    &= S_{k,n-1}
\end{aligned}$

Using this representation, we see that

$\begin{aligned}
    |S_{k,n}| &= |A| + |B|\\
    &= |S_{k-1,n-1}| + |S_{k,n-1}|\\
    &= \binom{n-1}{k-1} + \binom{n-1}{k}
\end{aligned}$

As desired.

This identity can also be proven similarly using the set $A_{k,n}$.

__Example__: (Hockey Stick Identity). This is one which also arises from Pascal's triangle.
In this case, for any number in Pascal's Triangle, the "hockey stick" of that number is the
set of numbers formed by moving one row up and to the left, then following the diagonal of
numbers from there to the right end of the triangle. This identity basically says that for
a number in Pascal's triangle, the sum of all other numbers in its "hockey stick" is itself.
Mathematically represented as:

$\binom{n+k}{n} = \sum_{i=0}^k \binom{n+i-1}{n-1}$ for $n,k \geq 0$.

We shall prove this by counting a set in two different ways. Take
$S_{n,n+k} = \{\Omega\subseteq \{1,\dots,n+k\}||\Omega| = n\}$. So that $|S_{n,n+k}| = \binom{n+k}{n}$
giving us the LHS of the identity. Now, we need to count $S_{n,n+k}$ differently to get the
RHS.

To start, we can partition $S_{n,n+k}$ as follows. Let
$W_i = \{\Omega\in S_{n,n+k} | \text{largest element of }W_i\text{ is }n+i\}$ for $0\leq i\leq k$.
So then we can represent $S_{n,n+k} = W_0\cup \dots \cup W_k$, a disjoint union.
Before moving on, it is important to represent $W_i=\{\{n+i\}\cup Q| Q\in S_{n-1, n+i-1}\}$.

$\begin{aligned}
    |S_{n,n+k}| &= \sum_{i=0}^k |W_i|\\
    &= \sum_{i=0}^k |S_{n-1,n+i-1}|\\
    &= \sum_{i=0}^k \binom{n+i-1}{n-1}
\end{aligned}$

As desired.

### Bijections

Bijections are important tools when it comes to combinatorial proof. They
enable one to show that two sets have the same size and do so conveniently.
Let us try to understand bijections. How does one know that two sets have
equal size?

__Example__: Let $S=\{1,\dots,100\}$ be the set of integers between 1 and 100.
Let $T=\{1,4,9,16,\dots,10000\}$ be the set of perfect squares between 1 and
10000.

In this example, clearly, these two sets have the same number of elements.
A pairing of 1 with 1, 2 with 4, 3 with 9, 4 with 16 and so on all the way
to 100 with 10000 should make this clear. There are no uncounted elements and
since there are 100 elements in $S$, the fact that they can be paired uniquely
with elements in $T$ (with none being left unpaired from $T$ or $S$) shows that
$T$ has size 100 too. Let us formalize this notion:

__Definition__: A _bijection_ is a mapping $f:S\mapsto T$ satisfying:

  * $\forall x_1,x_2\in S (f(x_1)=f(x_2)) \iff (x_1 = x_2)$

  This says that "For all $x_1,x_2$ in $S$, $f(x_1)=f(x_2)$ if and only if
  $x_1=x_2$". A function satisfying this property is said to be one-to-one.
  This is because every element of $S$ maps to a unique element in $T$ under
  the action of $f$.

  * $\forall y\in T (\exists x\in S [f(x) = y])$

  This says that "For every $y$ in $T$, there exists an $x$ in $S$ which
  satisfies $f(x) = y$. A function satisfying this property is said to be onto.
  This is because the image of $S$ under the action of $f$ is the whole of $T$
  i.e. every element in $T$ can be obtained as a result of the action of $f$ on
  some value in $S$.

To test that a function is a bijection, it is sufficient to show that it is
both one-to-one and onto as stated in the above 2 bullets.

__Example__ _(Cont'd.)_: We can now formalize the pairing that was discussed in
the example above. Define a function $f:S\mapsto T$ like so: $\forall x\in S$,
we have that $f(x)=x^2$. Let us show that this function satisfies the above two
properties to be called a bijection.

* _Verify one-to-one_: If we have $x_1,x_2\in S$ such that $f(x_1) = f(x_2)$.
  This would mean that $x_1^2 = x_2^2$. But since both $x_1,x_2$ are members of
  $S$, they must be positive. So taking the square root leaves us with
  $x_1 = x_2$. Therefore, $f$ is one-to-one.

* _Verify onto_: If we have $y\in T$, then by definition, it is a perfect
  square between 1 and 10000 therefore, its square root must lie between 1 and
  100, which are the members of $S$. Therefore, we can take $x=\sqrt{y}\in S$
  and then we get that $f(x) = (\sqrt{x})^2 = y$. This shows that $f$ is onto.

Therefore, the function $f$ is a bijection. We still have to prove that this
bijection actually gives us the result that the sets $S$ and $T$ have the same
size.

__THEOREM__: Suppose $S,T$ are two finite sets and $f:S\mapsto T$. Then:

  * If $f$ is one-to-one, then $|S| \leq |T|$
  * If $f$ is onto, then $|S| \geq |T|$
  * If $f$ is a bijection, then $|S| = |T|$

__Proof__:

  1. Suppose that $f$ is one-to-one. This means that every element of $S$ maps
   to a unique element in $T$ under the action of $f$. Therefore, there must be
   at least $|S|$ elements in $|T|$ i.e. $|S| \leq |T|$.
  2. Suppose that $f$ is onto. Then, every element in $T$ is the image of some
   element in $S$. Therefore, by the definition of a function (that an input
   will always produce the same output), this allows us to see that the size of
   $S$ is at least the size of $T$ i.e. $|S| \geq |T|$.
  3. If $f$ is a bijection, it is both one-to-one and onto. Therefore, we see
  that it must be the case that $(|S| \leq |T|)\land (|S| \geq |T|)$, which
  leaves us with one option: $|S| = |T|$.

As desired.

There is another method for showing that a function is a bijection. This one
relies on the inverse of a function, which comes sort of naturally when
speaking of bijective maps- you need a way to reverse the action of the
function. Inverse functions will capture this idea and provide yet another
tool for combinatorial proofs.

#### Inverse Functions

__Definition__ An inverse of a function $f:S\mapsto T$ is a function
$f^{-1}: T \mapsto S$ which satisfies the following properties:

* $\forall x\in S (f^{-1}(f(x)) = x)$.
  This says that for every element in $S$, the action of $f$ on $x$ can be
  undone through the action of $f^{-1}$.
* $\forall y\in T (f(f^{-1}(y)) = y)$.
  This says that for every element in $T$, the action of $f^{-1}$ can be
  undone through the action of $f$.

This definition can be used to verify that a function is an inverse function.
Now, let us the utility of inverse functions through this theorem:

__THEOREM__: A function $f:S\mapsto T$ has an inverse function if and only if
it is a bijection.

__Proof__: (_Forwards_) Assume that $f$ has an inverse function
$f^{-1}:T\mapsto S$. We need to show that $f$ is a bijection.

  * (_Proving that $f$ is one-to-one_) Take $x_1,x_2\in S$ such that
  $f(x_1)=f(x_2)$. Since $f^{-1}$ is the inverse of $f$, it reverses the
  action of $f$, so we get

  $f^{-1}(f(x_1)) = f^{-1}(f(x_2)) \implies x_1 = x_2$

  This shows that $f$ is one-to-one.

  * (_Proving that $f$ is onto_) Pick a $y\in T$. We need to find a value
  $x\in S$ such that $f(x) = y$. Well, take $x = f^{-1}(y)$ and then:

  $f(x) = f(f^{-1}(y)) = y$

  This shows that $f$ is onto and, together with the above, that $f$ is a
  bijection.

(_Backwards_) Now, let us assume that $f$ is a bijection. Need to show that
$f$ has an inverse function.

We can construct one as follows: given a $y\in T$, we can find an $x\in S$
such that $f(x)=y$. This is possible because the assumption of bijection
means that $f$ is onto. Keeping this in mind, we make the following definition:

Let $f^{-1}:T\mapsto S$ be defined for all $y\in T$, $f^{-1}(y) = x$ as stated
in the passage above. To prove that $f^{-1}$ is an inverse:

  * Pick an $x\in S$. Say $y = f(x)$. Then: $f^{-1}(y) = f^{-1}(f(x)) = x$.
  We see that $f^{-1}$ reverses the action of $f$.
  * Now pick a $y\in T$. Say $x=f^{-1}(y)$. Then: $f(x) = f(f^{-1}(y)) = y$

This completes the proof of the backwards direction and finally proves the
theorem above.

### Generating Series

__Context__: Let $S$ be a set. We define a "weight" function as a function
$w:S\mapsto \{0,1,2,3,\dots\}$.

_Question_: How many $\delta \in S$ such that $w(\delta) = k$?

__Examples__:

1. With $S=\{a,b,c\}$ and $w:S\mapsto \{0,1,2,3,\dots\}$ defined by: $w(a) = 1$,
  $w(b) = 1$, $w(c) = 2$. There are two elements of $S$ with weight 1 and one
  element with weight $2$. This is the kind of information that we wish to
  capture.
2. If $S=\{\Omega\subseteq \{0,1,2,\dots, n\}| w(\Omega) = |\Omega|\}$ ($S$ is the
  set of subsets of $\{1,2,\dots,n\}$ with the weight of a subset being defined
  as the size of the subset). The number of elements with weight $k$ is easily
  obtained (from our previous work with $S_{k,n}$) as $\binom{n}{k}$.

__Definition__: A __generating function__ for a set $S$ with respect to a
weight function $w:S\mapsto \{0,1,2,\dots\}$ encodes information regarding the
counts of elements in $S$ with the weights $\{0,1,2,\dots\}$. It is denoted by
$\Phi_{S}(x)$ and is defined as

$\Phi_{S}(x) = \sum_{\delta \in S} x^{w(\delta)}$

When one stares at this definition long enough, one realises that it is a way
of keeping track of the set of weights that occur in $S$, with respect to the
weight function $w$.

We can manipulate the above definition to make this clearer:

$\begin{aligned}
  \Phi_{S}(x) &= \sum_{\delta \in S} x^{w(\delta)}\\
  &= \sum_{k\geq 0}\left( \sum_{(\delta \in S) \land (w(\delta) = k)} \right) x^k\\
  &= \sum_{k\geq 0} a_k x^k
\end{aligned}$

Where $a_k = |\{\delta \in S | w(\delta) = k\}|$.

The coefficient of the $x^n$ term tells us the number of elements in the set
$S$ which have the weight $n$ (of course, with respect to the weight function
that was used to compute the series).

__Examples__:

1. What is the generating series of the corresponding example 1 above?
  We compute: $\Phi_S(x) = x^{w(a)} + x^{w(b)} + x^{w(c)} = x^1+x^1+x^2 =
  2x + x^2$. Note how even if the weight function were defined differently
  (like $w(a) = w(c) = 1$ and $w(b) = 2$). The resulting generating series
  is the same. What this means is that there is information about the weights
  of elements of $S$ that is not preserved.
2. For corresponding example 2 above, we have the generating function

  $\begin{aligned}
    \Phi_S(x) &= \sum_{k\geq 0} |\{\Omega \in S | w(\Omega) = k\}|\cdot x^k\\
    &= \sum_{k\geq 0} \binom{n}{k}x^k\\
    &= \sum_{k=0}^n \binom{n}{k} x^k\\
    &= (1+x)^n
  \end{aligned}$

This may all be nice, but what is the point of encoding this information in a
generating series?

__Theorem__: Suppose that $S$ is a finite set with the weight funtion
$w:S \mapsto \{0,1,2,\dots\}$. Let $\Phi_S$ be the generating series for $S$
with respect to $w$. Then:

1. $|S| = \Phi_S(1)$. This says that the size of the set $S$ is equal to its
   generating series evaluated at $x=1$.
2. $\sum_{\delta \in S} w(\delta) = \left.\frac{d\Phi_s}{dx}\right|_{x=1}$.
   This says that the sum of the weights of the elements in $S$ is exactly
   equal to the first derivative of the generating series, evaluated at $x=1$.

Let's see why this works:

__Proof__:

1. Here is a short proof for statement 1 above

  $\begin{aligned}
    \Phi_S(1) &= \left.\sum_{\delta \in S} x^{w(\delta)}\right|_{x=1}\\
    &= \sum_{\delta\in S} 1^{w(\delta)} = \sum_{\delta \in S} 1 \\
    &= |S|
  \end{aligned}$
2. Similarly, here is a short proof for statement 2

  $\begin{aligned}
    \left.\frac{d\Phi_S}{dx}\right|_{x=1} &= \left.\sum_{\delta \in S}
    w(\delta) x^{w(\delta) - 1}\right|_{x=1}\\
    &= \sum_{\delta \in S} w(\delta) 1^{w(\delta) - 1}\\
    &= \sum_{\delta \in S} w(\delta)\\
  \end{aligned}$

__Example__: Consider a sequence of $n$ coin flips and suppose you win $1 with
each time that you get heads after tails or tails after heads. Compute the
expected winnings using generating series.

The above theorem allows us to get the sum of the weights of the elements in
$S$ as the number of elements. Putting these together, we can get the average
weight of an element in $S$. Contextualizing to this example, we can benefit by
defining a weight function in terms of the rewards and then compute the average
as explained to get the expected winnings. Take a moment to contemplate how
you would solve this before moving on...

We need to get a 'mathematical handle' on the occurrence of tails after heads
and heads after tails. So, for a sequence of $n$ coin flips, we can concoct
$n-1$ binary variables indicating whether the next flip in the sequence differs
from the current one:

$\forall i\in [1,n-1]$ define $z_i = \left\{\begin{array}{lr}
        1, & \text{if }(i+1)\text{th outcome is different from }i\text{th}\\
        0, & \text{otherwise}
        \end{array}\right.$

Using this string of binary variables $z_1,z_2,\dots,z_{n-1}$, one can derive
useful information about the sequence of $n$ coin flips. We can put this all in
a set $S=\{(z_1, z_2, \dots z_{n-1}) | z_j\in \{0,1\}\}$ with the weight
function defined by $w((z_1,\dots,z_{n-1})) = \sum_{i=1}^{n-1} z_i$.

We can now view $S = \{0,1\}^{n-1}$ and the weight function is essentially
computing the number of ones in an entry from $S$- each of which corresponds
to a dollar reward (as per the rules of the game). Then we can compute
$\Phi_S(x) = \sum_{i\geq 0} a_i x^{i}$, where $a_i$ is the number of elements
in $S$ which have weight $i$. Fortunatly, we have alredy done this (see work on
$A_{k,n}$)- we know that $a_i = \binom{n-1}{i}$. Therefore, we finally get
$\Phi_S(x) = (1+x)^{n-1}$, by the binomial theorem.

Now, we use the theorem above:

$|S| = \Phi_S(1) = 2^{n-1}$

$\begin{aligned}
  \sum_{\delta \in S} w(\delta) &= \left.\frac{d\Phi_S}{dx}\right|_{x=1}\\
  &= \left.(n-1)(1+x)^{n-2}\right|_{x=1}\\
  &= (n-1)2^{n-2}
\end{aligned}$

We can readily compute the expected winnings now:

$\begin{aligned}
  \text{Expected winnings} &= \frac{\left.\frac{d\Phi_S}{dx}\right|_{x=1}}{|S|}\\
  &= \frac{(n-1)2^{n-2}}{2^{n-1}}\\
\end{aligned}$

So far, we have only been considering the cases in which the set $S$ is finite.
What happens to $\Phi_S$ when $S$ is an infinite set? In this case, we have to
make the following distinction:

* If $S$ is finite, then $\Phi_S(x)$ is a polynomial
* If $S$ is infinite, then $\Phi_S(s)$ is a formal power series (given that
  the coefficients $a_k$ are finite)

At this point, we introduce the concept of formal power series through which
we shall obtain tools to deal with generating series.

#### Formal Power Series

A formal power series is an expression $c_0 + c_1x^1 + c_2x^2 + \dots$ where
$(c_0, c_1, c_2, \dots)$ is a sequence of rational numbers (for our intents
and purposes, the coefficients are rational numbers, but the important part is
that they are finite). This is to concretize the notion of a generating series
as a formal power series, and to then to apply the properties of formal power
series in the realm of generating series.

Let $C(x)$ be a formal power series (to be abbreviated as f.p.s). We can write
$C(x) = \sum_{i=0}^\infty c_i x^i$ and define $[x^n] = c_n$. So if
$C(x) = \sum_{i=0}^\infty 2^i x^i$, then $[x^0]C(x) = 1$, $[x^1]C(x) = 2$,
$[x^2]C(x) = 4$ and so on. Let us now consider the operations which can be
performed with formal power series.

##### Operations on Formal Power Series

Consider two formal power series $A(x) = \sum_{i=0}^\infty a_i x^i$ and
$B(x) = \sum_{i=0}^\infty b_i x^i$.

__EQUALITY__: $((A(x) = B(x)) \iff (\forall k \in \mathbb{N} (a_k = b_k)))$.
This states that two formal power series are considered to be equal if and only
if the coefficients $a_k$ and $b_k$ are the same for all natural number $k$.

__ADDITION__: $A(x) + B(x) = \sum_{k=0}^\infty (a_k+b_k)x^k$. This is a valid
definition for addition since the resulting series is also a f.p.s- the
coefficients $(a_k+b_k)$ are all finite rational numbers (by the declaration
that $A$ and $B$ are formal power series above).

__MULTIPLICATION__: Defined as follows:

$\begin{aligned}
  A(x)B(x) &= \sum_{j=0}^\infty \sum_{k=0}^\infty a_jb_k x^{j+k}\\
  &= \sum_{n=0}^\infty \left( \sum_{j=0}^n a_j b_{n-j} \right)x^n\\
\end{aligned}$

Note that we can identify the term $[x^n]A(x)B(x) = \sum_{j=0}^n a_j b_{n-j}$
from the last expression above. This term is also a rational number since it
is a finite sum of product of pairs of rational numbers.

_Example_: Let $A(x) = (1+x)^m$ and $B(x) = \sum_{k=0}^m 2^k x^k$. Let us
compute $[x^n]A(x)B(x)$.

We know, from the binomial theorem that $A(x) = \sum_{j=0}^m \binom{m}{j}x^j$.
So $[x^n]A(x) = \binom{m}{j}$.
It is also clear from the summand of $B(x)$ that $[x^n]B(x)=2^n$. Putting these
two together:

$\begin{aligned}
  [x^n]A(x)B(x) &= \sum_{i=0}^n [x^i]A(x)[x^{n-i}]B(x) \\
  &= \sum_{i=0}^n \binom{m}{i}2^{n-i} \\
  &= 2^n \sum_{i=0}^n \binom{m}{i}2^{-i} \\
\end{aligned}$

Now, notice what happens when $n>m$- the term $\binom{m}{i}$ will be zero for values
of $i>m$ sum would effiectively run from 1 to $m$.

$\begin{aligned}
  2^n\sum_{i=0}^m \binom{m}{i} 2^{-i}
    &= 2^n\sum_{i=0}^m \binom{m}{i} \left(\frac{1}{2}\right)^i\\
    &= 2^n \left( 1+\frac{1}{2} \right)^m\\
    &= 2^{n-m}3^m
\end{aligned}$

So we have that $[x^n]A(x)B(x)=2^{n-m}3^m$.

__Example (Multiplicative Shift)__: This example illustrates how for all $k,n\geq 0$,
the term $[x^n]x^k A(x)$, is similar to a shift in indices. Let
$A(x)=\sum_{j\geq 0}a_j x^j$.

$\begin{aligned}
  [x^n] x^k A(x) &= [x^n] x^k \left( \sum_{j\geq 0} a_j x^j \right)\\
  &= [x^n] \sum_{j= 0}^\infty a_j x^{j+k} \;\text{, let }l = k + j\\
  &= [x^n] \sum_{l=k}^\infty a_{l-k} x^l\\
  &= \begin{cases}
    a_{n-k} &\;\text{, if }n-k\geq 0\\
    0 &\;\text{, if }n-k <0
  \end{cases}
\end{aligned}$

This is a rule/identity that will be used time and time again.

__Definition (Formal Power Series Inverses)__: Let $A(x),B(x)$ be formal power
series satisfying $A(x)B(x)=1$, then one says that $B(x)$ is the inverse of
$A(x)$ and writes $B(x)=A(x)^{-1}$ or $B(x)=\frac{1}{A(x)}$.

__Example__: Let $A(x)=1-x$, $B(x)=\sum_{i=\geq 0} x^k$.

We can write $A(x)$, using the binomial theorem, as
$A(x)=(1-x)^1=\sum_{k=0}^1 \binom{1}{k} (-x)^k$. Using this, it can be seen that
$[x^n]A(x) = (-1)^n\binom{1}{n}$ and this forms the sequence
$(1,-1,0,0,0,\dots)$.

Now, using the multiplication rule:

$\begin{aligned}
  a_n = [x^n]A(x)B(x) &= \sum_{j = 0}^n [x^j]A(x) [x^{n-j}]B(x)\\
  &= \sum_{j = 0}^n (-1)^j\binom{1}{j} (1)\\
  &= \begin{cases}
    0 &\text{ if }n\geq 0\\
    1 &\text{ if }n=0
  \end{cases}
\end{aligned}$

The only term with non-zero coefficent in $A(x)B(x)$ is the $x^0$ term (the
constant term), which has coefficent 1. Therfore, we see that $A(x)B(x) =1$
ans as such we can write $\sum_{i=0}^\infty x^i = \frac{1}{1-x}$, using the
notation in the definiton of inverses in formal power series.

__Theorem (Negative Binomial Series)__: As an extension of the example above,
we have the following theorem: for all $k=1,2,3,\dots$ we have that

$\begin{aligned}
  \frac{1}{(1-x)^k} &= \sum_{n=0}^\infty \binom{n+k-1}{k-1} x^n
\end{aligned}$

_Proof_: The proof of this theorem is provided using induction on $k$.

In the base case when $k=1$, we check:

$\begin{aligned}
  [x^n]\frac{1}{(1-x)^1} &= [x^n]\sum_{j=0}^\infty \binom{j+1-1}{1-1} x^j\\
  [x^n]\frac{1}{1-x} &= [x^n]\sum_{j=0}^\infty \binom{j}{0} x^j\\
  [x^n]\sum_{i=0}^\infty x^i &= [x^n]\sum_{j=0}^\infty x^j\\
  1 &= 1
\end{aligned}$

The base case holds. Now, onto the inductive step where it is assumed that
the theorem holds for some $k$. Now, to show that it holds for $k+1$.

$\begin{aligned}
  \frac{1}{(1-x)^{k+1}} &= \frac{1}{(1-x)^k} \frac{1}{(1-x)}\\
  &= \left( \sum_{n=0}^\infty \binom{n+k-1}{k-1} x^n \right)\cdot
  \left( \sum_{i=0}^\infty x^i \right)
\end{aligned}$

Now that we have $\frac{1}{(1-x)^{k+1}}$ expressed as a product of two power
series, we can use the multiplication rule to compute the coefficient for the
$x^n$ term.

$\begin{aligned}
  [x^n]\frac{1}{(1-x)^{k+1}}
  &= [x^n]\left( \sum_{j=0}^\infty \binom{j+k-1}{k-1} x^j \right)\cdot
  \left( \sum_{i=0}^\infty x^i \right)\\
  &= \sum_{j=0}^n \binom{j+k-1}{k-1} \;\text{ by the Multiplication Rule}\\
  &= \binom{n+k}{k} \;\text{ by the Hockey Stick Identity}
\end{aligned}$

The inductive step holds too and therefore so does the theorem for all
$k=1,2,\dots$. This completes the proof. $\blacksquare$

This theorem is also an important one and should be familiarized with as it
can help with quick conversions to and from power series.

__NOTE__: There are conditions under which formal power series have inverses.
Here's an example highlighting a case when the f.p.s. has no inverse. Consider
$A(x)=x$, which is claimed to have no inverse. Let us proove this.

The proof provided here is by contradiction. Suppose $A(x)$ did have an inverse.
Then, there would exist another f.p.s. $B(x)=\sum_{i\geq 0}b_i x^i$ such that
$A(x)B(x)=xB(x)=1$. This looks like a good place to use the "Multiplicative
shift" mentioned before to get:

$\begin{aligned}
  [x^n]A(x)B(x) &= [x^n]xB(x)\\
  &= \begin{cases}
    b_{n-1} &\;\text{ if }n\geq 0\\
    0 &\;\text{ if }n=0
  \end{cases}
\end{aligned}$

Note that if $B(x)$ is an inverse for $A(x)$, then $[x^0]A(x)B(x)=1$, but with
the result above, we see that $[x^0]A(x)B(x)=0$, which is a contradiction.
The starting assumption, that $A(x)$ has an inverse must have been wrong then.
Therefore, $A(x)=x$ has no inverse.

__Theorem (Condition for Inverses)__: An f.p.s. $A(x)$ has an inverse iff
$[x^0]A(x)\neq 0$.

_Proof_: \[Forwards\] First, assume that $[x^0]A(x)=a_n=0$. Now, we need to show
that $A(x)$ has no inverse (This is proving the contrapositive which is
logically equivalent).

Say $B(x)$ is another f.p.s. with $[x^0]B(x)=b_0$.
Let us check $[x^0]A(x)B(x) = a_0b_0 = 0$ since $a_0 = 0$. This means that
$A(x)B(x)$ can never be equal to $1$, no matter the f.p.s. $B(x)$.
Therefore, $A(x)$ has no inverse. This proves that if $A(x)$ has an inverse
then $a_0\neq 0$.

\[Backwards\] Now, suppose that $[x^0]A(x)\neq 0$. We need to show that $A(x)$
has an inverse. To do this, we let $B(x)=\sum_{i\geq 0}b_i x^i$ and show that
$A(x)B(x)=1$ has a single solution. We can equivalenty solve for:

$\begin{aligned}
  [x^n]A(x)B(x) &= \sum_{j=0}^n a_j b_{n-j}
\end{aligned}$

If $n=0$, then $[x^0]A(x)B(x) = a_0b_0$. Comparing this to the $[x^0]$
coefficient on the Right Hand Side (RHS) of the equation $A(x)B(x)=1$, we get
that $a_0b_0 = 1$, therefore $b_0 = \frac{1}{a_0}$. This is a valid quotient
since $a_0$ is non-zero by assumption.

If $n>0$, then $[x^n]A(x)B(x) = a_0b_n + \sum_{j=1}^n a_jb_{n-j}$. All
coefficents on the RHS of the equation are zero (except the constant term) so
we can solve for $b_n$ from above as
$b_n = \frac{-1}{a_0}\sum_{j=1}^n a_jb_{n-j}$, which can be solved iteratively
for some desidered value of $n$.
This completes the proof. $\blacksquare$

The kind of solution obtained for $b_n$ in the above theorem is called a
__linear recurrence__ because $b_n$ is defined as a linear combination of
previous $b_i$ terms (for $0\leq i < n$). We can use this in solving equations
of formal power series using inverses. This is studied now.

__Theorem__: Let $A(x)$ and $C(x)$ be f.p.s. If $[x^0]A(x)\neq 0$ the there is
a formal power series $B(x)$ such that $A(x)B(x) = C(x)$.

_Proof_: This short and simple proof builds off of the conditions for inverses.
Since $[x^0]A(x) \neq 0$, we know that it has an invserse. Say the inverse of
$A(x)$ is $B'(x)$ i.e. $A(x)B'(x)=1$. Now, let $B(x)=B'(x)C(x)$.
This gives us that $A(x)B(x) = (A(x)B'(x))C(x) = C(x)$.
This completes the proof. $\blacksquare$

__Example__: Let $A(x) = \frac{5+x^2}{1-x}$. Compute $[x^n]A(x)$ for all
$n\geq 0$. Note that in this example, if one considers $A(x)$ to be quotient of
polynomials, the one in the denominator has degree lower than the polynomial in
the numerator.

First, start by writing $A(x) = \left(\frac{1}{1-x} \right)\left(5+x^2\right)$.
Then:

$\begin{aligned}
  [x^n]A(x) &= [x^n]\left(\frac{1}{1-x} \right)\left(5+x^2\right)\\
  &= \sum_{k=0}^n \left( [x^k] \frac{1}{1-x}\right)\left([x^{n-k}]5+x^2\right)\\
  &= \sum_{k=0}^n [x^{n-k}]5+x^2\\
  &= \begin{cases}
    5 &\;\text{if }n\in\{0,1\}\\
    6 &\;\text{if }n\geq 2
  \end{cases}
\end{aligned}$

__Example__: Let $A(x) = \frac{2+7x-3x^2}{1-x^2+x^3}$. Note that in this
example, if one considers $A(x)$ to be a quotient of polynomials the the
polynomial in the denominator has higher degree than the one in the numerator.
In this case, we derive a recurrence relationship which can be used to compute
$[x^n]A(x)$ for all $n\geq 0$.

Write $A(x) = \sum_{k\geq 0} a_k x^k$ so that $[x^n]A(x)=a_n$. Now, rewrite
the original expression for $A(x)$ as $(1-x^2+x^3)A(x) = 2+7x-3x^2$.
This process works by essentially comparing coefficients from the Left Hand
Side (LHS) and RHS of the re-arranged expression for $A(x)$.

Starting with the constant term. Since the LHS and RHS are equal, we have that
$[x^0](1-x^2+x^3)A(x) = [x^0]2+7x-3x^2$. When the expressions for the
coefficients are computed, we get that $a_0 = 2$.

Next, the linear term: $[x^1](1-x^2+x^3)A(x) = [x^1]2+7x-3x^2$. Computing the
expressions on each side of the equation, we get $a_1(1) - a_0(0) = 7$.
We get $a_1 = 7$.

Next, the quadratic term: $[x^2](1-x^2+x^3)A(x) = [x^2]2+7x-3x^2$. Computing
the expressions on each side of the equation, we get $a_2+a_1(0)-a_0 = -3$.
Evaluating using the previous computations, we get $a_2 = -1$.

Now, we derive a general recurrence using $x^n$ term, where $n\geq 3$:
$[x^n](1-x^2+x^3)A(x) = [x^n]2+7x-3x^2$. Evaluating each side gives
$a_n - a_{n-2} + a_{n-3} = 0$. This gives us the expression for the general
$a_n$ as $a_n = a_{n-2} - a_{n-3}$ for $n\geq 3$.

The expression $a_n$ as $a_n = a_{n-2} - a_{n-3}$ for $n\geq 3$ is called a
recurrence relation. But note that to compute $a_n$, one needs to know
$a_{n-2}$ and $a_{n-3}$. Therefore, for the recurrence relation to be of any
use, there must be a set of initial conditions provided. In this case, they
were computed to be $a_0 = 2, a_1 = 7$ and $a_2 = -1$. From this, it is
possible to compute any $a_n$ iteratively.

_Notes_: We began to derive a general recurrence relation when we reached the
cubic (or higher) term. This was because the $x^3$ term (and all after it)
for the expression on the RHS have zero coefficient.

Also note how the $a_0$ term is non-zero.

Now, more generally, if there are f.p.s. $A(x)= \sum_{i\geq 0}a_i x^i$ with
$a_0 \neq 0$ and $C(x) = \sum_{i\geq 0}c_i x^i$. By a theorem, we know that
there exists a $B(x)$ such that $A(x)B(x)=C(x)$. We know that
$B(x) = \frac{C(x)}{A'(x)}$, where $\frac{1}{A(x)}$ is the inverse of $A(x)$.
We can now derive a general linear recurrence relation defining the
coefficients of $B(x)$.

__Theorem__: Let $A(x),C(x)$ be formal power series with $a_0 \neq 0$. Let
$B(x)=\frac{C(x)}{A(x)}$. Then, $b_n = [x^n]B(x)$ is determined by the linear
recurrence:

$b_n = \frac{1}{a_0}\left( c_n - \sum_{j=0}^{n-1} a_{n-j}b_j \right)$

_Proof_: Again this proof is short and straight-forward: To prove the
recurrence, we start by comparing coefficients of the LHS and RHS i.e.
checking $[x^n] A(x)B(x) = [x^n]C(x)$. We get:

$\begin{aligned}
  c_n &= \sum_{j=0}^n a_j b_{n-j}\\
  c_n &= \sum_{j=0}^n a_{n-j} b_{j}\\
  c_n &= a_0b_n + \sum_{j=0}^{n-1} a_{n-j} b_{j}\\
\end{aligned}$

Rearranging the last equation reveals the desired recurrence:

$b_n = \frac{1}{a_0}\left( c_n - \sum_{j=0}^{n-1} a_{n-j}b_j \right)$

__COMPOSITION__: This is yet another operation defined on formal power series.
Let $A(x) = \sum_{j\geq 0}a_j x^j$ and $B(x) = \sum_{j\geq 0}b_j x^j$ be formal
power series. If $b_0=0$ then we define:

$\begin{aligned}
  A(B(x)) &= \sum_{j\geq 0} a_j B(x)^j
\end{aligned}$

In order to verify that composition of formal series is well defined, we check
that the result of composing $A(x),B(x)$ as defined above is a formal power
series too.

$\begin{aligned}
   [x^n]A(B(x)) &= \sum_{j\geq 0} a_j [x^n]B(x)^j
\end{aligned}$

At this stage, note that the logic from multiplicative shift can be applied
here to the term $[x^n]B(x)^j = [x^n](b_1x+b_2x^2+\dots)^j$. If $j>n$, then
there are no terms with $x^n$ left (all terms have exponent $x^n$ or higher).
Therefore, the sum can be reduced to run from $0$ to $n$ instead.

$\begin{aligned}
   [x^n]A(B(x)) &= \sum_{j= 0}^n a_j [x^n]B(x)^j\\
   &< \infty
\end{aligned}$

The coefficient in finite because $a_j$ and $[x^n]B(x)^j$ are all rational and
there is a finite count of summands. Therefore, $A(B(x))$ is a formal power
series and the operation of composition is well defined.

_Note_: Here is an example when the condition that $b_0=0$ is necessary.
Consider the composition of $A(x)=\sum_{i\geq 0}x^i$ and $B(x)=1$. Then, we get
that $A(B(x))=\sum_{j\geq 0} 1 \rightarrow \infty$. It can cause such problems.

Now, we shall look at using composition of formal power series to compute
inverses.

__Theorem__: Let $A(x),B(x)$ be formal power series such that $[x^0]A(x)\neq 0$
and $[x^0]B(x)=0$. Then:

$\begin{aligned} [A(B(x))]^{-1} = A^{-1}(B(x)) \end{aligned}$

_Proof_: Write $A(x)=\sum_{i\geq 0}a_i x^i$. Since $a_0=0$, we know that $A(x)$
has an inverse. Let $A^{-1}(x)=\sum_{i\geq 0}\alpha_i x^i$. Since $[x^0]B(x)=0$
we know that it can be composed into other formal power series namely $A(x)$
and $A^{-1}(x)$. Let us now consider the product of $A(x)$ and $A^{-1}(x)$,
when composed with $B(x)$:

$\begin{aligned}
  A(B(x))A^{-1}(B(x)) &= \left( \sum_{j\geq 0}a_j[B(x)]^j \right)
  \left( \sum_{j\geq 0}\alpha_j[B(x)]^j \right)\\
  &= AA^{-1}(B(x)) \;\text{by the Multiplicative Rule}\\
  &= 1
\end{aligned}$

This shows us that $A(B(x))$ is the invserse of $A^{-1}(B(x))$ since their
product is 1. Therefore, we get the desired result. $\blacksquare$

__Example__: Computing $[x^n](1+3x)^{-2}(1-x)^{-1}$. The key idea here is to
first express the term $(1+3x)^{-2}$ as a composition of formal power series,
then use the theorem above.

Let $A(x)=-3x$. So we get that $(1+3x)^{-2}=(1-A(x))^{-2}$. This is good
because the negative binomial series can be used to obtain a series
representation.

$\begin{aligned}
  \frac{1}{(1+3x)^{2}} &=  \frac{1}{(1-A(X))^{2}}\\
  &= \sum_{n\geq 0} \binom{n+1}{1} (A(x))^n \;\text{ by the Negative Binomial Series}\\
  &= \sum_{n\geq 0} (n+1)(-3x)^n\\
  &= \sum_{n\geq 0} (-3)^n(n+1)x^n
\end{aligned}$

This shows us that $[x^n](1+3x)^{-2} = (-3)^n(n+1)$.

$\begin{aligned}
  [x^n] (1+3x)^{-2} (1-x)^{-1} &= \sum_{j=0}^n [x^j](1+3x)^{-2} [x^{n-j}](1-x)^{-1}\\
  &= \sum_{j=0}^n [x^j](1+3x)^{-2}\\
  &= \sum_{j=0}^n (-3)^j(j+1)
\end{aligned}$

We now have a suite of tools related to formal power series which we shall
employ in our study of generating series- to which we return now...

#### ... Back to Generating Series

Now, we study some additional properties of generating series.

__Sum Lemma__ Let $S=A\cup B$ where $A\cap B = \emptyset$.
Let $w:S\mapsto\{0,1,\dots\}$. Then

$\Phi_S(x)=\Phi_A(x)+\Phi_B(x)$

_Proof_:

$\begin{aligned}
  \Phi_S(x) &= \sum_{\delta\in S} x^{w(\delta)}\\
  &= \sum_{\delta\in A}x^{w(\delta)} + \sum_{\delta\in B}x^{w(\delta)}\\
  &= \Phi_A(x) + \Phi_B(x)\\
  \blacksquare
\end{aligned}$
$

The sum lemma for generating series can be generalised to:

__Generalization of Sum Lemma__: Let $S=A_1\cup A_2\cup \dots A_n$ where
$A_i\cap A_j = \emptyset$ for $1\leq i\neq j\leq n$. Also let
$w:S\mapsto \{0,1,2,\dots\}$. Then

$\Phi_S(x) = \sum_{i=0}^n \Phi_{A_i}(x)$

_Proof_: This is proven by induction on $n$. The base case is trivial.
Assume, inductively that the generalization is true for some $n$. Now we have
to show that it holds for $n+1$. So we have
$S=A_1\cup A_2\cup \dots A_n\cup A_{n+1}$ and where $A_i\cap A_j = \emptyset$
for all $1\leq i\neq j \leq n+1$.

$\begin{aligned}
  S &= A_1\cup A_2\cup \dots A_n\cup A_{n+1}\\
  &= (A_1\cup A_2\cup \dots A_n)\cup A_{n+1}
\end{aligned}$

Since $S$ is a disjoint union of $(A_1\cup A_2\cup \dots A_n)$ and $A_{n+1}$,
we can use the sum lemma:

$\begin{aligned}
  \Phi_S(x) &= \Phi_{(A_1\cup A_2\cup \dots A_n)}(x) + \Phi_{A_{n+1}}(x)\\
  &= \sum_{i=0}^n \Phi_{A_i}(x) + \Phi_{A_{n+1}}(x) \;\text{by Inductive Hypothesis for case }n\\
  &=  \sum_{i=0}^{n+1} \Phi_{A_i}(x)\\
  \blacksquare
\end{aligned}$

__Product Lemma__: Let $A,B$ be sets with weight functions
$\alpha:A\mapsto \{0,1,2,\dots\}$ and $\beta:B\mapsto\{0,1,2,\dots\}$
respectively. Define a weight function $w:A\times B\mapsto \{0,1,2,\dots\}$ by:

$w((a,b))=\alpha(a) + \beta(b)$ for all $(a,b)\in A\times B$

Then:

$\Phi_{A\times B}(x) = \Phi_{A}(x)\Phi_B(x)$

_Proof_:

$\begin{aligned}
  \Phi_{A\times B} &= \sum_{\delta=(a,b)\in A\times B} x^{w((a,b))}\\
  &= \sum_{\delta\in A\times B} x^{\alpha(a)+\beta(b)}\\
  &= \sum_{a\in A}\sum_{b\in B} x^{\alpha(a)+\beta(b)}\\
  &= \left( \sum_{a\in A}x^{\alpha(a)} \right)\cdot \left( \sum_{b\in B}x^{\beta(b)} \right)\\
  &= \Phi_A(x)\Phi_B(x)\\
  \blacksquare
\end{aligned}$

## Integer Compositions

__Definition__: A __composition of an integer $n$__ is a tuple of positive
integers $(a_1,\dots, a_k)$ such that $\sum_{i=1}^k a_i = n$. We say that this
composition of $n$ has $k$ parts. Note that a composition is a tuple and
therefore order matters! Furthermore, note that the parts in a integer
composition are strictly positive integers and therefore 0 is not a valid part.

Also, by convention, $n=0$ has one composition- the empty composition $()$.

The goal is to answer questions of the form: "How many integer compositions of
$n$ have some property $P$?" The property $P$ could be anything of interest.
Here are some examples:

* $P=$ the number of parts is $k$
* $P=$ the parts are even
* $P=$ the parts are congruent to 1 modulo 3.

The general strategy to solve such problems is as follows:

1. Define a set, say $S$, which contains all of the intger compositions with the
   property $P$.
2. Define an appropriate weight function $w$, such that the solution to the
   question of interest is given by $[x^n]\Phi_S(x)$.
3. Compute the generating series of $S$, with respect to the weight function
   $w$, $\Phi_S(x)$.
4. Finally, compute $[x^n]\Phi_S(x)$.

The toolbox that will allow us to perform these steps includes the following:

* Sum lemma: if $A\cap B = \emptyset$, then $\Phi_{A\cup B}(x)=\Phi_A(x) +
  \Phi_B(x)$
* Product lemma: with the condition of the weight functions satisfied, one has
  $\Phi_{A\times B}(x) = \Phi_A(x)\Phi_B(x)$
* Power shifts: $[x^n]x^kA(x) = \begin{cases}
    [x^{n-k}]A(x) &\text{ if }n\geq k\\
    0 &\text{ if }n<k
  \end{cases}$
* Geometric series: $\sum_{i=0}^\infty x^i = \frac{1}{1-x}$
* Composition of geometric series: If $[x^0]A(x) = 0$, then $\sum_{i=0}^\infty
  (A(x))^i = \frac{1}{1-A(x)}$
* Negative binomal series: $\frac{1}{(1-x)^k}=\sum_{n=0}^\infty
  \binom{n+k-1}{k-1} x^n$

__Example__: Compute the number of compositions of $n$ with $k$ parts.

First, we need a set which contains all the integer compositions with $k$ parts.
Let $S=N^k$, where $N=\{1,2,3,\dots\}$.

Then, define an appropriate weight function. Let $w:S\mapsto \{0,1,2,\dots\}$ be
defined as follows: for all $X=(x_1,\dots,x_k)\in S$, $w(X)=\sum_{i=0}^k x_i$.

With these definitions in place, the answer to the "number of compositions of
$n$ which have $k$ parts" is just $[x^n]\Phi_S(x)$. We now compute it.

$\begin{aligned}
\Phi_S(x) &= \Phi_{N^k}(x)\\
&= \left( \Phi_N(x) \right)^k &\text{Product Lemma}\\
&= \left( \sum_{j\geq 1} x^j \right)^j\\
&= \frac{x^k}{(1-x)^k}
\end{aligned}$

Now, using the multiplicative shift rule, one sees that:

$\begin{aligned}
[x^n]\Phi_S(x) &= \begin{cases}
  0 &\text{ if } n< k\\
  \binom{n-1}{k-1} &\text{ if } n\geq k
\end{cases}
\end{aligned}$

The last case evaluates to the binomial coefficient given because of the
negative binomial theorem.

## Binary Strings

This is another object which can be studied very interestingly with the concepts
of generating series. First, some definitions regarding binary strings:

__Definition__: A __binary string__ (a.k.a. $\{0,1\}$-string) is a strings
consisting of only ones and zeroes. The __length of a binary string__ is defined
to be the total number of ones and zeroes in the string.

__Definition__: $b$ is a substring of $s$ if $s=abc$ for some binary strings
$a,c$ (which could possibly be empty strings). The expression $abc$ will become
clear when concatenation is defined soon.

__Definition__: A __block__ in a binary string is a _maximal, non-empty_
substring which consists of only ones or only zeroes.

__Definition__: __Concatenation__ of two binary strings $a,b$ is the string
$ab$.

__Definition__: If $A$ and $B$ are sets of binary strings, we define
$AB=\{ab|a\in A \text{ and }b\in B\}$. So $AB$ is the set consisting of all the
concatenations of a string in $A$ with a string in $B$.

Also, $A^k$ is defined to be $A\cdot A\cdot \dots \cdot A$, $k$ times. Note that
this notation is overloaded with the Cartesian product for regular sets.

__Definition__: For any set $A$ of binary strings, define the __star operation__
as follows:

$\begin{aligned}
  A^* &= \{\epsilon\}\cup A \cup A^2 \cup \dots \\
  &= \cup_{k=0}^\infty A^k
\end{aligned}$

where $\epsilon$ is defined to be the empty string (which has length 0).

With this star operation, it is possible to define the set of all binary strings
as $\{0,1\}^*$. It also allows us to create more specific sets of strings
(which, as in the case of integer compositions is the first step in solving a
combinatorial problem involving binary strings). For example, the set
$\{0\}\{00\}^*$ contains all of the strings of odd length containing only
zeroes.

The goal is to be able to answer questions of the form "How many binary strings
of length $n$ have property $P$?". Again, property $P$ could be anything of
interest in the context of binary strings:

* $P=$ no adjacent ones
* $P=$ exactly $k$ occurrences of the substring $110$
* $P=$ no occurrences of the substring $111$.

The strategy is very similar to the one used for integer compositions:

1. Devise a set $S$ of all binary strings which have the desired property $P$
2. Let $w:S\mapsto \{0,1,2,\dots\}$ be a weight function which, for all $\sigma
   \in S$, $w(\sigma)=$ length of $\sigma$.
3. The desired answer will then be $[x^n]\Phi_S(x)$

While the strategy may be the same as the one for integer compositions, binary
strings have some nuances which require that the set of tools (specifically the
product and sum lemmas) to be readjustment to handle the nuances. In particular,
one may not immediately see how the product lemma may be used for binary strings
as there is no operation of Cartesian products, just concatenation and these two
are __not__ the same.

Consider the two sets of binary strings $A = \{ 010, 01 \}$ and $B = \{ 0, 00
\}$. The Cartesian product $A\times B$ has 4 elements. But observe the set of
strings in the set $AB = \{ 0100, 10100, 101 \}$. Note that the product lemma
does not hold in this case: $\Phi_{AB}(x) = x^3 + x^4 + x^5$ and this is not the
product of $\Phi_A(x) = x^2 + x^3$ and $\Phi_B(x) = x + x^2$. In particular, one
cannot draw a bijection between $AB$ and $A\times B$- there are two elements in
$A\times B$, namely $(010, 0)$ and $(01, 00)$ which map to the same string
"0100" in $AB$. To deal with this, we introduce the concept of ambiguity:

__Definition__: Let $A$ and $B$ be sets of binary strings. The expression $AB$
is ambiguous if there exist $a_1,a_2 \in A$ and $b_1, b_2 \in B$ such that
$a_1b_1 = a_2b_2$.

The expression $A\cup B$ is ambiguous if $A\cap B \neq \emptyset$.

An expression involving concatenations and unions of sets of binary strings is
ambiguous if any of the constituent concatenations or unions of sets is
ambiguous.

An expression is said to be unambiguous iff it is not ambiguous.

Using this definition, for example, the set $A^k$ is ambiguous if there exist
$a_1, \dots, a_k, a_1', \dots a_k' \in A$ such that $(a_1,\dots, a_k)\neq (a_1',
\dots, a_k')$ and $a_1\dots a_k = a_1'\dots a_k'$.

__Example__: Show that the expression $\{ 0 \} \{ 00 \}^*$ is unambiguous.

First, we show that the star operation is unambiguous. The set $\{ 00 \} = \{
\epsilon \} \cup \{ 00 \} \cup \{ 00 \}^2 \cup \dots$. Firstly, these are
clearly disjoint unions. Next, note that the set $\{ 00 \}^k$ is unambiguous for
all $k\geq 0$; we have that $\{ 00 \}^k = \{ \underbrace{00\dots 00}_\text{2k
zeros} \}$.

Next, the concatenation with $\{ 0 \}$ is unambiguous. If we have two strings
$0b = 0b'$, then clearly $b = b'$. So the expression $\{ 0 \} \{ 00 \}^*$ is
unambiguous.

Now, here are some very useful unambiguous expressions for the set of all binary
strings. They are important because they can be "refined" to smaller unambiguous
sets.

* $\{ 0, 1 \}$. This one is trivial.
* $\{ 0 \}^* \left( \{ 1 \} \{ 0 \}^* \right)^*$. In this expression, a binary
  string is split by the ones in the string.
* $\{ 0 \}^* \left( \{ 1 \} \{ 1 \}^* \{ 0 \} \{ 0 \}^* \right)^* \{ 1 \}^*$.
  This expression is called the _block decomposition_ of the set of binary
  strings. A binary string here is viewed as a block of ones followed by a block
  of zeros, with a possible starting block of zeros and a possible ending block
  of ones.

__Note__: One may find it important to know that by the laws of symmetry, it is
perfectly acceptable and valid to switch the ones and zeros in the above
ambiguous expressions and end up with a valid unambiguous expression.

Depending on the situation, one of these expressions will be easier to
manipulate to reduce it into a set of binary strings with desired properties.
For example, in a question specifying conditions on the blocks of ones and the
blocks of zeros, the block decomposition may be a good place to start.

__Example__: Derive an expression for the set of all binary strings with no 3
consecutive zeros.

Since this question only deals with the blocks of zeros, we can use the second
one of the unambiguous decompositions and refine it down to an expression for
the set of all binary strings with no 3 consecutive zeros.

In the expression $\{ 0 \}^* \left( \{ 1 \} \{ 0 \}^* \right)^*$, the parts of
concern are the ones with zeros. The set $\{ 0 \}^* = \{ \epsilon, 0, 00,
\dots \}$ needs to be reduced down to the set $\{ \epsilon, 0, 00 \}$.

Replacing $\{ 0 \}^*$ with this reduced set in the unambiguous expression above
results in the following set $\{ \epsilon, 0, 00 \}^* \left( \{ 1 \} \{
\epsilon, 0, 00 \} \right)^*$ which is an unambiguous expression for the set of
all binary strings which have no 3 consecutive zeros.

Equipped with this concept of unambiguity, one modification needs to be made
before computing generating series for sets of binary strings. This is that the
expression for the set $S$ needs to be unambiguous in order to sanely compute
its generating series. Here are some theorems to aid with this goal:

__Theorem__: Let $A$ and $B$ be sets of binary strings.

1. If $AB$ is unambiguous, then $\Phi_{AB}(x) = \Phi_A(x) \Phi_B(x)$. This is
   called the product lemma for binary strings
2. If $A\cup B$ is unabiguous, then $\Phi_{A\cup B}(x) = \Phi_A(x) + \Phi_B(x)$.
   This is called the sum lemma for binary strings.
3. If $A^*$ is unambiguous, then $\Phi_{A^*}(x) = \frac{1}{1 - \Phi_A(x)}$. This
   is called the star rule.

_Proof_:

Let $l(x)$ be the function which returns the length of the binary string $x$.
This is the default weight function for binary strings, unless otherwise
specified.

1. In this case, note that an element $\sigma \in AB$ is unambiguously a
   concatenation of some element $a\in A$ with a $b\in B$.
   $\begin{aligned}
     \Phi_{AB}(x) &= \sum_{\sigma \in AB} x^{l(\sigma)}\\
     &= \sum_{a\in A \text{ and } b\in B} x^{l(ab)}\\
     &= \sum_{a\in A \text{ and } b\in B} x^{l(a) + l(b)}\\
     &= \left( \sum_{a\in A} x^{l(a)} \right) \left( \sum_{b\in B} x^{l(b)}
     \right)\\
     &= \Phi_A(x) \Phi_B(x)
   \end{aligned}$

2. This case is pretty simple as $A\cup B$ is unambiguous iff it is a disjoint
   union. Therefore the sum lemma can be used.

   $\Phi_{A\cup B}(x) = \Phi_A(x) + \Phi_B(x)$

3. We rewrite $A^* = \cup_{k=0}^\infty A^k$. Since $A^i \cap A^j = \emptyset$
   for all $0 \leq i \neq j$, the sum lemma can be applied. Also, since each
   $A^k$ is unambiguous for all $k\geq 0$, the product lemma may be applied.

   $\begin{aligned}
     \Phi_{A^*}(x) &= \sum_{k=0}^\infty \Phi_{A^k}(x) &\text{Sum lemma}\\
     &= \sum_{k=0}^\infty \left[ \Phi_A(x) \right]^k &\text{Product lemma}
   \end{aligned}$

   Now, this last term looks like a composition with the geometric series, but
   to be sure, we have to verify that $[x^0] \Phi_A(x) = 0$. Note that $A^0 = \{
   \epsilon \}$ and that $A^j \cap A^i = \emptyset$ for all $0\leq i\neq j$ by
   the unambiguity of $A^*$. This means that $\epsilon \notin A$ and so there is
   no string in $A$ with length 0, so the constant term of $\Phi_A(x)$ must be
   0- so this is indeed a valid composition. Finally, we get:

   $\begin{aligned}
     \Phi_{A^*}(x) &= \sum_{k=0}^\infty \left[ \Phi_A(x) \right]^k \\
     &= \frac{1}{1-\Phi_A(x)}
   \end{aligned}$

__Example__: Compute the number of binary strings of length $n$ with no
substring $11$.

First, we need an unambiguous expression for the set of all binary strings with
no substring $11$. We can use symmetry and reverse one of the unambiguous
expressions for the set of all binary strings to get a good starting point. We
reverse the ones and zeros in the unambiguous expression $\{ 0 \}^* \left( \{ 1
\} \{ 0 \}^* \right)^*$ to get $\{ 1 \}^* \left( \{ 0 \} \{ 1 \}^* \right)^*$.
Now, we refine this expression down so that every block of ones does not contain
the substring 11. This gives the expression $S = \{ \epsilon, 1 \} \left( \{ 0
\} \{ \epsilon, 1 \} \right)^*$.

Now, proceeding to compute the generating series of the set $S$ with respect to
string length as the weight function. Note that the product and star rules may
be applied because the expression for $S$ above is unambiguous.

$\begin{aligned}
\Phi_{S}(x) &= \Phi_{\{ \epsilon, 1 \}}(x) \Phi_{\left( \{ 0
  \} \{ \epsilon, 1 \} \right)^*}(x) &\text{Product lemma}\\
&= \frac{ \Phi_{\{ \epsilon, 1 \}}(x) }{ 1 - \Phi_{\{ 0 \} \{ \epsilon, 1
  \}}(x)} &\text{Star rule}\\
&= \frac{ \Phi_{\{ \epsilon, 1 \}}(x) }{ 1 - \Phi_{\{ 0 \}}(x) \Phi_{\{
  \epsilon, 1 \}}(x)} &\text{Product rule}\\
&= \frac{ 1 + x }{ 1 - x(1 + x) } \\
&= \frac{ 1 + x }{ 1 - x - x^2 }
\end{aligned}$

With this expression, note that we can do the following simplification:

$\begin{aligned}
[x^n] \Phi_A(x) &= [x^n] \frac{1}{ 1 - x - x^2 } + [x^n] \frac{x}{ 1 - x -
  x^2}\\
  &= [x^n]\frac{1}{ 1 - x - x^2 } + [x^{n-1}]\frac{1}{ 1 - x - x^2 }\\
  &= f_n + f_{n-1}
\end{aligned}$

where $f_n = [x^n]\frac{1}{ 1 - x - x^2 }$. This is actually part of the
Fibonacci sequence. Computing the starting terms of $f_n$ is easy by comparing
coefficients. We get $f_0 = f_1 = 1$. Putting all of this together, we finally
get that:

$\begin{aligned}
[x^n]\Phi_S(x) &= \begin{cases}
  1 &\text{ if } n = 0\\
  f_{n} + f_{n - 1} &\text{ if } n\geq 1
\end{cases}
\end{aligned}$

This makes intutive sense. When $n=0$, there is clearly only one string with
length 0, which does not contain the substring $11$, namely the empty string.
Then, there are two strings of length 1 which do not contain the string $11$ and
so on.

### Recursive Decompositions

Sometimes, recursive definitions can help to make computation of generating
series easier. Note that recursive decompositions are just expressions and the
rules that have so far been used to compute generating series will still be used
with them, just with collection of like terms to get the final series.

Here is an example. Let us derive a recursive decomposition for the set of all
binary strings, say $S$. One way to approach this is by selecting an arbitrary
string in $S$ and analysing it to see what could come next. In this case, any
binary string could start with either a $1$ or a $0$ and it could be followed by
a sequence of ones or zeros i.e. another binary string. Or, the binary string
could simply be the empty string. This gives us the simple recursive definition
for the set of all binary strings as $S = \{ \epsilon \} \cup \{ 0, 1 \}S$.

Now, let us try to compute the generating series of this set $S$ with this
representation. Note that we can still use the product lemma here as the
concatenation is clearly unambiguous and the sum lemma because the union is
disjoint.

$\begin{aligned}
  \Phi_S(x) &= \Phi_{ \{ \epsilon \} }(x) + \Phi_{ \{ 0, 1 \} S }(x) &\text{Sum
  lemma}\\
  &= 1 + \Phi_{ \{ 0, 1 \} }(x) \Phi_S(x) &\text{Product lemma}\\
  &= 1 + 2x \Phi_S(x)
\end{aligned}$

By collecting like terms, one ends up with the generating series: $\Phi_S(x) =
\frac{1}{1-2x}$.

__Example__: Another example is an expression for the set of all binary strings
with no substring $11$. Let the set of all such strings be $S$.

Firstly, a string in $S$ is either the empty string, starts with a one or starts
with a zero. Let $A_0$ be the set of all binary strings which start with a zero.
And let $A_1$ be the set of all binary strings which start with a one.
So $S = \{ \epsilon \} \cup A_0 \cup A_1$. Note that this is a disjoint union of
sets and so the sun lemma is applicable.

Here are some observations that will make life easier. Firstly, an element in
$A_0$ is such that it begins with a $0$ and then a sequence of ones and zeros
follow i.e. another binary string. Therefore, we get the expression $A_0 = \{ 0
\} S$. Similarly, an element in $A_1$ is either the string $1$ or the string $1$
concatenated to the beginning of every string in $A_0$. More precisely, $A_1 =
\{ 1 \} \cup \{ 1 \} A_0$. Now, we can use these expressions in order to compute
the generating series of the set $S$.

$\begin{aligned}
  \Phi_S(x) &= \Phi_{ \{ \epsilon \} }(x) + \Phi_{ \{ 0 \} S }(x) + \Phi_{ \{ 1
  \} }(x) + \Phi_{ \{ 1 \} \{ 0 \} S }(x) &\text{Sum lemma}\\
  &= \Phi_{ \{ \epsilon \} }(x) + \Phi_{ \{ 0 \} }(x) \Phi_S(x) + \Phi_{ \{ 1 \}
  }(x) + \Phi_{ \{ 1 \} }(x) \Phi_{ \{ 0 \} }(x) \Phi_{ S }(x) &\text{Product
  lemma}\\
  &= 1 + x\Phi_S(x) + x + x^2\Phi_S(x)
\end{aligned}$

By collecting like terms and solving for $\Phi_S(x)$ yields

$\begin{aligned}
  \Phi_S(x) &= \frac{ 1 + x }{ 1 - x - x^2 }
\end{aligned}$

This is the same answer as the one obtained when using unambiguous expressions.

## Coefficients of Rational Functions

This is a new tool that can be used when solving combinatorial problems such as
the ones being dealt above. Specifically, these are tools for computing $[x^n]
\frac{ f(x) }{ g(x) }$ where $f,g$ are polynomials.

A starting point will be the method of partial fractions. In specific cases, it
can be used to split a rational polynomial to a form where its coefficients are
easy to compute using composition with geometric series or the negative binomial
series.

The method of partial fractions will be generalized to rational fractions of the
form $\frac{ f(x) }{ g(x) }$ where $f,g$ are polynomials and $\deg( f ) < \deg(
g )$ and $[x^0] g(x) = 0$.

__Notes__: Here are some points before proceeding:

* Without loss of generality (WLOG), we can assume that $[x^n] g(x) = 1$ since
  it is non-zero- this is fine because it can be scaled to 1 anyway by
  multiplying the numerator and denominator by a constant.
* By the fundamental theorem of algebra, $g$ can be factorized over the complex
  numbers as $g(x) = (\alpha_1 - x)^{e_1} \dots (\alpha_k - x)^{e_k}$. Note that
  the multiplicities $e_1, \dots, e_k \geq 1$ and $\sum_{i=0}^k e_i = \deg( g
  )$. Also, the values $\alpha_1, \dots, \alpha_k \in \mathbf{C}\setminus \{ 0
  \}$- they must be non-zero complex numbers since the constant term of $g$ is
  non-zero.

  Furthermore, if we let $r_i = \alpha_i^{-1}$ for $1\leq i \leq k$, Since the
  constant term of $g$ is effectively $1$, we can re-write it as:
  $g(x) = ( 1 - r_1 x )^{e_1} \dots ( 1 - r_k x )^{e_k}$

Now, we generalize the theorem of partial fractions. This will be just the
statement and not the proof (I may include the proof at a later time).

__Theorem \[ Partial Fractions \]__: Suppose $f,g$ are polynomials with $\deg(
f) < \deg( g )$ and $g(x) = ( 1 - r_1 x )^{e_1} \dots ( 1 - r_k x )^{e_k}$ with
$r_1, \dots, r_k$ distinct complex numbers and $e_1, \dots, e_k$ are integers
greater that one which add up to the degree of $g$. Then:

$\begin{aligned}
  \frac{ f(x) }{ g(x) } &= \frac{C_{1,1}}{(1-r_1x)} +
  \frac{C_{1,2}}{(1-r_1x)^2} + \dots + \frac{C_{1,e_1}}{(1-r_1x)^{e_1}} \\
  &+ \frac{C_{2,1}}{(1-r_2x)} + \frac{C_{2,2}}{(1-r_2x)^2} + \dots +
  \frac{C_{1,e_2}}{(1-r_2x)^{e_2}} \\
  &\vdots \\
  &+ \frac{C_{k,1}}{(1-r_kx)} +
  \frac{C_{k,2}}{(1-r_kx)^2} + \dots + \frac{C_{k,e_k}}{(1-r_kx)^{e_k}}
\end{aligned}$

for complex coefficients $\{ C_{1,1}, \dots, C_{k, e_k} \}$.

This is useful because it allows one to reduce a quotient of polynomial to a
state where it can be dealt with using the negative binomial theorem. For
example, the quotient $A(x) = \frac{ 2 + 2x^2 }{ (1-2x)(1-7x) }$ can be reduced
to a much more friendly form:

$\begin{aligned}
  A(x) &= \frac{-1}{ 1 - 2x } - \frac{1}{ ( 1 - 2x )^2 } + \frac{4}{ 1 - 7x }
\end{aligned}$

In this form, one can easily compute the coefficient of the $x^n$ using the
negative binomial series for each individual term. This results in the following
answer: $[x^n] A(x) = 2^n ( -n -2 ) + 4\cdot 7^n$.

__Theorem__: Suppose that $f,g$ are polynomials with $\deg(f) < \deg(g)$ and $g$
is of the form $g(x) = (1-r_1x)^{e_1} \dots (1-r_kx)^{e_k}$. Then, there exist
polynomials $p_1. \dots, p_k$ such that $\deg( p_i ) \leq e_i$ for $1\leq i
\leq k$ and $[x^n] \frac{f(x)}{g(x)} = p_1(x)r_1^n + \dots + p_k(x)r_k^n$.

_Proof_: This comes pretty simply using the following claim, applied to the
generalised partial fractions theorem.

_Claim_: Let $c,r \in \mathbf{C}$ and $j\geq 1$. Then there is a degree $j-1$
polynomial $q$ such that $[x^n] \frac{ c }{ (1-rx)^j } = q(n)r^n$.

_Proof of claim_: We can use the negative binomial series here to expand the
formal power series into a summation and then extract its coefficient as
follows:

$\begin{aligned}
  [x^n] \frac{c}{(1-rx)^j} &= [x^n] c \sum_{k\geq 0} \binom{k + j - 1}{j - 1}
  (rx)^j\\
  &= c \binom{n+j-1}{j-1} r^n\\
  &= cr^n \frac{(n+j-1)(n+j-2)\dots (n+1)}{(j-1)!}
\end{aligned}$

Note that the numerator has the form of a polynomial in $x$ evaluated at a value
$n$ and the denominator is not at all dependent on $n$. This motivates us to
define $q(x) = \frac{c}{(j-1)!}(x+j-1)(x+j-2)\dots (x+1)$, which is indeed a
degree $j-1$ polynomial. This completes the proof of the claim.

Now, using this claim with each row in the generalized form of the partial
fractions expression, the theorem now holds. For a row $i$ in the partial
fractions expression, one has $e_i$ such polynomials from the claim- each of
them will be multiplied by an $r_i^n$ term and these can be factored to get
$r_i$ multiplied by the sum of $e_i$ polynomials, of which the maixmum degree is
$e_i -1$ by the claim above. Let this sum of polynomials be the polynomial
$p_i(x)$. This completes the proof of the theorem.

Now, this theorem gives us another way of quickly computing the coefficient of
the $x^n$ term in a quotient of polynomials. One knows the form that the
quotient will take, so what remains is to plug whatever available information
exists in the context into this theorem and then attempt to compute the
coefficients of the polynomials $p_1, \dots, p_k$.

