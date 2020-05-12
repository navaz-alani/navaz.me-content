# Intro to Combinatorics Course Notes

Navaz Alani
_Spring 2020_

****

## Tools for Enumeration

__Main interest__: counting the size of various sets.

Let us recall the elementary operations that can be performed with sets. Let $A, B$
be finite sets. We have the following operations:

__UNION__: $A\cup B = \{x | x \in A \text{ or } x \in B\}$

__INTERSECTION__: $A\cap B = \{x | x\in A \text{ and } x \in B\}$

In order to count the size of a set, one of the approaches used is to build that
set using unions of smaller sets, whose sizes are known. It is important, therefore,
to understand the relationship between the cardinality of a set and the cardinalities
of the sets that it is built from.

Most readers should be aware of the following identity: $|A\cup B| = |A| + |B| - |A\cap B|$
which is of utmost importance when it comes to counting the size of sets as it provides
a relationship between the cardinality of a set $A\cup B$ and the cardinalities $|A|$ and
$|B|$. A much simpler case arises when $A\cap B = \emptyset$ i.e. when $A\cup B$ is a disjoint union- the identity reduces to $|A\cup B| = |A| + |B|$.

This identity can be extended to a more general one. Given sets $A_1, \dots, A_n$ with
$A_i\cap A_j = \emptyset$ for $1 \leq i < j \leq n$, we have
$|A_1\cup \dots \cup A_n| = \sum_{j=1}^n |A_j|$. This is readily proven by induction
on $n$. In the case of $n=2$, the identity holds, as seen above. Now, assuming that the
identity holds for some $n > 2$, we can verify it for case $n+1$:

$\begin{aligned}
    |A_1\cup \dots \cup A_n \cup A_{n+1}| &= |(A_1\cup \dots \cup A_n) \cup A_{n+1}|\\
    &= |(A_1\cup \dots \cup A_n)| + |A_{n+1}| - |(A_1\cup \dots \cup A_n)\cap A_{n+1}|\\
    &= \sum_{i=1}^n |A_i| + |A_{n+1}| - |(A_1 \cap A_{n+1})\cup \dots \cup (A_n\cap A_{n+1})|\\
    &= \sum_{i=1}^{n+1} |A_i| - |\emptyset|
    = \sum_{i=1}^{n+1} |A_i|
\end{aligned}$

This allows us to state one of the techniques used for problem solving in this course:
__Recognizing that a set can be expressed as a disjoint union of other sets__. The general
identity derived above proves to be helpful in this technique. Now, back to set operations:

__CARTESIAN PRODUCT__: $A\times B = \{(a, b) | a \in A, b \in B\}$. This object has the
property that $|A \times B| = |A|\cdot |B|$.

__CARTESIAN POWER__: $A^k = \{(a_1, \dots, a_k) | a_1\in A, \dots, a_k\in A\}$. This object
can be expressed alternatively as the cartesian product of $A$ with itself, $k$ times and has
the property that $|A^k| = |A|^k$.

__Example__: Let $S=\{0,1\}^k = \{(z_1, \dots, z_k) | z_1, \dots, z_k \in \{0,1\}\}$.
$S$ is called the set of $k$-tuples of bits. Using the property of the cartesian product
outlined above, we see that $|S| =|\{0,1\}^k| = |\{0,1\}|^k = 2^k$.

__Example__: Let $S=\{(z_1, z_2, z_3)\in \{0,1\}^3 | z_1 + z_2 + z_3 \leq 1\}$. Find $|S|$.
In this case, it may be easy to write out the elements of $S$ and count them but we shall
use the method of expressing $S$ as a union of 2 disjoint sets to see how it works.

We can write $S=A\cup B$ where $A=\{(z_1,z_2,z_3)\in \{0,1\}^3 | z_1 + z_2 + z_3 = 0\}$
and $B=\{(z_1,z_2,z_3)\in \{0,1\}^3 | z_1 + z_2 + z_3 = 1\}$. So clearly,
$A\cap B = \emptyset$ by the definition of $A$ and $B$. This allows us to say that
$|S| = |A| + |B|$.

Now, we can count: $A = \{(0,0,0)\}$ so $|A| = 1$ and $B = \{(1,0,0), (0,1,0), (0,0,1)\}$
so that $|B| = 3$. Therefore, $|S| = 1 + 3 = 4$.

### Binomial Coefficients

These come up a lot when it comes to enumeration and counting problems so getting
comfortable with the binomial coefficients is important.

__Definition__: $S_{k,n} := \{\Omega \in \{1, \dots, n\} | |\Omega| = k\}$. This will
prove to be an important set definition once some of its properties have been uncovered.
$S_{k,n}$ is the set of all subsets of $\{1, \dots, n\}$ of size $k$.

In general, this set can be used to understand many real-life situations e.g. the number of
5-card hands from a standard deck of 52 cards is $|S_{5,52}|$.

__THEOREM__: let $0 \leq k \leq n$. Then $|S_{k,n}| = \frac{n(n-1)\cdots(n - k + 1)}{k!}$.

__Proof__: Let $L_{k,n} := \{(a_1,\dots,a_k)\in \{1,\dots,n\}^k | a_i\neq a_j \text{ for }
i\neq j \}$. $L_{k,n}$ is the set of all $k$-tuples of distinct elements of $\{1,\dots,n\}$.

What is $|L_{k,n}|$? Well, since the elements in the $k$-tuples are distinct, there are
$n$ possibilities for the first one, $n-1$ possibilities for the second one and so on. In
general, for the $j$-th element in the tuple, there $n-(j-1)$ possibilities. Therefore,
we get that $|L_{k,n}| = n(n-1)\cdots (n-(k-1))$.

Now, we shall analyse a relationship between $L_{k,n}$ and $S_{k,n}$ which will allow us
to compute $|S_{k,n}|$. Observe the following:

* Each $(a_1, a_2, \dots, a_k) \in L_{k,n}$ can be mapped to an element $\{a_1,\dots, a_k\}
\in S_{k,n}$. This mapping removes the ordering from the $k$-tuple.
* Each $\{a_1,\dots, a_k\} \in S_{k,n}$ is then the image of $k!$ different elements in
$L_{k,n}$.

Using these 2 observations, we may see the following:

$|L_{k,n}| = \sum_{\Omega \in S_{k,n}} k! = |S_{k,n}|\cdot k!$

$\implies |S_{k,n}| = \frac{|L_{k,n}|}{k!}$, as desired.

Now, we may move forward to define the following object:

__Binomial Coefficient__: $\binom{n}{k} := \frac{n(n-1)\cdots(n - k + 1)}{k!}$ for $0\leq k
\leq n$. Note that by this defintion, it can also be seen that
$\binom{n}{k} = \frac{n!}{(n-k)!k!}$. This version of the definition immediately reveals the
symmetrical nature of the binomial coeffcient: $\binom{n}{k} = \binom{n}{n-k}$ because of the
commutativity of multiplication in the denominator. For convenience and convention, we also
define $\binom{n}{k} = 0$ for $k > n$.

Now, let $A_{k,n} = \{(z_1,\dots,z_n)\in \{0,1\}^n | z_1 + \dots + z_n = k\}$ for $0\leq k
\leq n$. What is $|A_{k,n}|$? In previous proof, the size of $S_{k,n}$ was determined by
analysing its relationship with $L_{k,n}$ whose size we could easily determine: we showed
$L_{k,n}$ is $k!$ times larger than $S_{k,n}$, essentially proving a 1 to many mapping
$S_{k,n} \mapsto L_{k,n}$. This strategy can also be used to find $|A_{k,n}|$ with the only
difference being that this time, the relationship is 1-1 with a set of size $\binom{n}{k}$.
We conveniently already have such a set! - $|S_{k,n}| = \binom{n}{k}$, as previously shown.

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
