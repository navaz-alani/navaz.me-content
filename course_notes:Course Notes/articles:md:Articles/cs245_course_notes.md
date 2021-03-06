# Intro to Logic and Computation

Navaz Alani
_Spring 2020_

****

## Introduciton

What is logic? For Aristotle, logic was the instrument by means of which we come
to know anything. Aristotelian logic formalizes basic principles of good reasoning
and provides a way to evaluate specific cases of reasoning.

A _syllogism_ is a kind of logical argument in whcih one _proposition_ (the
conclusion) is inferred from two or more others (the premises) of a specific form.
Here is an example of an Aristotelian syllogism:

These are the premises:

1. All humans are mortal
2. Socrates is a human

Here is the inference/conclusion

$\rightarrow$ Socrates is mortal

This is an example of a good reasoning/argument because it is truth perserving
i.e. if the premises 1 and 2 are `true`, then the conclusion must also be
`true`. The correctness of the argument depends purely upon its form, not
content. The form can be viewed as the high-level structure of the argument.
Another one of the Aristotelian syllogisms:

1. All Accords are Hondas
2. All Hondas are Japanese

$\rightarrow$ All Accords are Japanese

As you can see, the high-level structure of this argument is the same, which is
why it holds as long as the propositions are `true`. The general form of these
__hypothetical syllogisms__ is:

1. All $x$ are $y$
2. All $y$ are $z$

$\rightarrow$ All $x$ are $z$

This is an example of a good argument. What about this one?

1. All $x$ are $y$
2. Some $y$ are $z$

$\rightarrow$ Some $x$ are $z$

This is actually a bad argument. It is not truth preserving in that the 2
initial premises could be `true` but the conclusion may not necessarily.
Try find a case under which this argument does not hold i.e. find two
premises which are both `true` but the resulting conclusion is not.

### Significance of Logic (in CS)

* In the heart of all electronic computers, there are logic gates. Digital
circuits are formed of logic gates. The study of logic can help minimize
the number of components in electronic circuits.
* AI- in specific, _expert systems_ which are essentially formed of an
inference engine running on a knowledge base. An example is DENDRAL (by Stanford
University in the 1960s) which was an expert system to aid the identification of
unknown organic molecules.
* Automated theorem proving/automated proof verifiers
* Databases- the core of modern database systems (e.g. SQL) uses first order
logic.
* Programming- program specification, formal verification
* DNA computing
* Synthetic biology

****

## Propositional Logic

* In this context, we define __logic__ to be the analysis and appraisal of
arguments.
* An __argument__ is a set of statements, namely one or several premises and a
and a __conclusion__, usually connected by a "therefore". You can see that this
definition is made with respect to the high-level structure of an argument.
Consider the following argument:

1. No pure water is burnable
2. Some Cuyahoga river water is burnable

$\rightarrow$ Some Cuyahoga river water is not pure

This is a __valid argument__, which is one in which whenever the premises are
`true`, the conclusion is also true. Convince yourself that this argument holds.

* Logic essentially studies the "forms" of reasoning (the high-level structure).
As mentioned before, the content of the arguments may deal with anything.
* Learning logic is learning the tools of reasoning applicable to any discipline.

Have a look at this argument:

1. No pure water is burnable
2. Some Cuyahoga river water is not burnable

$\rightarrow$ Some Cuyahoga river water is pure

This argument is invalid (incorrect/unsound). There could be a case where the
whole river is polluted by non-burnable pollutant- it works under the assumption
that all unburnable water is pure. Here is another one:

1. If demand rises, companies expand
2. If companies expand, companies hire more workers

$\rightarrow$ If demand rises, companies hire more workers.

__NOTE__: One may argue against the conclusion but as soon as the premises are
accepted to be `true`, the conclusion must also be `true`. In such cases, the
conclusion is said to _logically follow from the premises_, or that the
_argument is valid (correct/sound)_.

Another argument:

1. This computer program has a bug or the input is erroneous
2. The input is not erroneous

$\rightarrow$ This computer program has a bug

__Compoud statements__ consist of several parts, each of which is a statement
in its own right.

* "Demand rises" and "companies expand" are connected by `if ..., then ...`
* "This computer program has a bug" and "input is erroneous" are connected by
`... or ...`

### Some Important Logical Arguments

To analyze arguments for correctness we abbreviate the essential statements by
substituting letters $p,q,r$ and so on.

* $p$ may represent "demand rises"
* $q$ may represent "companies expand"
* $r$ may represent "companies hire"

The argument then becomes:

1. If $p$, then $q$
2. If $q$, then $r$

$\rightarrow$ If $p$, then $r$

This kind of argument is called a __hypothetical syllogism__ and it is a valid
argument (it is truth preserving/the reasoning is sound).

The "computer bug" example has this high-level structure:

1. $p$ or $q$
2. $q$

$\rightarrow$ $p$

This kind of argument is called a __disjunctive syllogism__. The word disjunction
and its derivatives refer to something to do with the connector `or`.

Here's another argument which is called __modus ponens__.

1. If $p$, then $q$
2. $p$

$\rightarrow$ $q$

### Concretizing Propositional Logic

__Definition__ A _statement_ that is either `true` or `false` is called a
__proposition__. From the previous series of analysis:

* $p,q,r$ are called __propositional variables__
* True (T) and False (F) (or 0 or 1 respectively) are called
__propositional constants__
* Any propositional variable can be __assigned__ to the value 0 or 1
* Propositional variables are _atomic propositions_ i.e. they annot be further
subdivided
* __Compound statements__ are obtained by combining several atomic propositions.
* The function of the structures `... or ...`, `... and ...`, `not ...`,
`if..., then ...` is to combine propositions and are therefore called
__logical connectives__

Statements formulated in natural language are frequently ambiguous because
the words can have more than one meaning. We want to avoid this so we introduce
_new mathematical symbols_ to take the role of connectives.

__Conventions__: Stating a proposition in English rightarrow that it is True.

"It is true that cats eat fish" = "cats eat fish"

Similarly, if $p$ is a proposition, then "$p$" means "$p$ is True" or "$p$ holds".
This should justify the syntax used in the arguments above.

__NEGATION__ (Definition) Let $p$ be a proposition. The compound proposition
$\lnot p$, pronounced as  "not $p$" is the proposition that is True when $p$ is
False and that is False when $p$ is True.

* $\lnot p$ is called the _logical negation_ $p$
* The connective $\lnot$ can be translated into English as `it is not the case
that ...` or simply $not ...$

Here is the truth table for negation:

| $p$ | ($\lnot p$) |
| --- | :---------: |
| 0   |      1      |
| 1   |      0      |

__CONJUNCTION__: (Definition) Let $p$ and $q$ be two propositions, then $p\wedge q$
is True if and only if both $p$ and $q$ are True.

* $p\wedge q$ is called the _logical conjunction_ of $p$ and $q$
* The connective $\wedge$ is pronounded "and" and may be translated to the English
word "and"

Truth table for conjunction:

| $p$ | $q$ | ($p\wedge q$) |
| --- | --- | :-----------: |
| 1   | 1   |       1       |
| 1   | 0   |       0       |
| 0   | 1   |       0       |
| 0   | 0   |       0       |

_Obeservations_:

* In English, we usually take shortcuts that are not allowed in logic statements.
"He eats and drinks" really means "he eats and he drinks".
* In logic, every statement must have its own subject and its own predicate.
  Taking $p =$ "He eats" and $q =$ "he drinks", our sentence becomes $p\wedge q$
* Sometime, we use words other than "and" to denote a conjunction: "but", "in
addition to" and "moreover"
* Not all instances of "and" are for conjunction: "Jack and Jill are cousins".
In this case "and" is not a conjunction at all.

__DISJUNCTION__: (Definition) Let $p$ and $q$ be propositions. Then, $p \lor q$
is False if and only if both $p$ and $q$ are True. If $p$, $q$ or both are True,
then $p\lor q$ is True.

* $p\lor q$ is the _logical (inclusive) disjunction_ of $p$ and $q$.
* The connective $\lor$ is pronounced as "or" and can be translated to English
by "or".

Truth table for (inclusive) disjunction:

| $p$ | $q$ | ($p\lor q$) |
| --- | --- | :---------: |
| 1   | 1   |      1      |
| 1   | 0   |      1      |
| 0   | 1   |      1      |
| 0   | 0   |      0      |

_Observations_:

The English "or" can have 2 meanings:

* "Exclusive or". "You can have either soup or salad" means you can have
"soup" or "salad", but not both.
* "Inclusive or". "The computer program has a bug or the input is erroneous".
The computer program could have a bug, the input could be erroneous, or both.

_Note_: When performing a disjunction of two sentences, make sure that the
sentences are complete: each should have its own subject and predicate.
The predicate is the part of a sentence which contains the verb and states
something about the subject. This helps avoid any ambiguity.

"There was an error on line 15 or 16" must first be expanded to "There was an
error on line 15 or there was an error on line 16". This helps make sure that
the propositions are valid.

__IMPLICATION__: (Definition) Let $p$ and $q$ be two prepositions. Then
$p\rightarrow q$ is False if $p$ is True and $q$ is False and $p\rightarrow q$ is
True otherwise.

* $p\rightarrow q$ is called the _logical implication_ of $p$ and $q$
* $p\rightarrow q$ may be translated to English using `if ..., then ...` to
"it is not the case that $p$ is True and $q$ is False".
* $p$ is called the _antecedent_
* $q$ is called the _consequent_

Truth table for implication:

| $p$ | $q$ | ($p\rightarrow q$) |
| --- | --- | :----------------: |
| 1   | 1   |         1          |
| 1   | 0   |         0          |
| 0   | 1   |         1          |
| 0   | 0   |         1          |

_Observations_:

* If $p$ is False, then $q$ is _vacuously True_ since in such a case, the
verification of $p\rightarrow q$ does not require anything to deduce $q$ from $p$.
More formally, __vacuous__ truth is when an implication is true, only because
its antecedent cannot be satisfied.

The following are logically equivalent:

* $p\rightarrow q$
* If $p$, then $q$
* Whevener $p$, then $q$
* $p$ is sufficient for $q$
* $p$ only if $q$
* $p$ implies $q$
* $q$ if $p$
* $q$ whenever $p$
* $q$ is necessary for $p$
* $q$ is implied by $p$

__EQUIVALENCE__: (Definition) Let $p$ and $q$ be propositions. Then $p \iff q$
is True whenever $p$ and $q$ have the same truth values.

* $p\iff q$ is called the _logical equivalence/biconditional_ of $p$ and $q$
* It is pronounced "$p$ if and only if $q$". Usually, "if and only if" is
abbreviated as "iff".

| $p$ | $q$ | ($p\iff q$) |
| --- | --- | :---------: |
| 1   | 1   |      1      |
| 1   | 0   |      0      |
| 0   | 1   |      0      |
| 0   | 0   |      1      |

_Sorting out Equivalence and Implication_: There is a difference and it is not
always clear which connective is intended in English. Have a look:

> "Eating hanburgers at a fast food restaurant is equivalent to aiding the
> destruction of the world's rainforests"

This looks like an equivalence, but if you swapped the two propositions,
clearly something is wrong. The intended meaning could have been:

> "If one eats hamburgers at a fast food restaurant, then one is aiding the
> destruction of the world's rainforests"

#### Remarks on Logical Operators

1. $\lnot$ is the only __unary__ connective i.e. it acts on one proposition
2. All other connectives are binary i.e. acting on two propositions
3. $\land, \lor, \iff$ are symmetric. The order of propositions does not matter.
$p\land q$ is an equivalent statement to $q\land p$.
4. $\rightarrow$ is not symmetric. $p\rightarrow q$ and $q\rightarrow p$ have different
truth values.

### Ambiguity and Imprecision

Logic helps clarify the meaning of descriptions e.g. in English. After all, we
even use it to state, precisely, the requirements of computer systems. Natural
language definitions can be ambiguous or imprecise. What's the difference?

* __Ambiguity__ is when a sentence has more than one meaning. 

Take a look at this sentence: "David and John from Toronto are coming for a
visit". Well, who is from Toronto? David, John or both? More information is
needed. This statement is ambiguous. Another one: "I know a much funnier man
than Bill". Could it mean "I know a much funnier man than Bill does" or "I know
a much funnier man than Bill is"- it is ambiguous.

Ambiguity is dealt with by querying the author of the sentence or by examining
context.

* __Imprecision (Vagueness)__ is when a sentence has only one meaning but as a
proposition, the distinction between circumstances where under which it is True
and circumstances under which it is False are not clearly defined.

Take a look at this sentence: "John is tall". But what exactly does this mean?
A more precise sentence could be "John is 2 meters tall". Another one: "This
computer is fast" can be made more precise: "This computer can execute 2
million instructions per second".

Imprecise sentences, caused by qualitative descriptions, can be made precise
by introducing quantitative measures.

****

## Propositional Language

Here's the general idea behind the formal propositional language.

* Using connectives, one can combine propositions (atomic or compound)
* Ambiguity is prevented through fully parenthezised formulae which are parsed
  uniquely
* When possible, parentheses are dropped in favor of _precedence rules_

We shall construct the $L^p$, which is the formal language of propositional
logic. We start off by defining the syntax of $L^p$ in which terminology is
introduced. Then, formulas in $L^p$ are discussed. Equipped with these two,
we work on some proofs in order to demonstrate the uniqueness of the $L^p$
language.

### $L^p$ Language Specifications

$L^p$ is the formal language of propositional logic and it is composed of the
following symbols:

* Propositional variables: $p,q,r,\dots$ (with or without subscripts) represent
  propositions, as previously discussed
* Logical Connectives: $\lnot, \land, \lor, \rightarrow, \iff$ as previously
  discussed

The following are laguage specifications, with introduction of terminology:

* __Expressions__: finite length strings of symbols in $L^p$. All of
  $p, pq, (r), (p\land \rightarrow q)$ are expressions in the $L^p$ language.
* The __Length__ of an expression is defined to be the number of symbols in it
  * An _empty expression_ is one which has length 0. It is denoted by
    $\epsilon$, and is not to be mistaken with the empty set, $\emptyset$.
* Two expressions $U$and $V$ are __equal__ iff they are of the same length and
  have the same symbols in the same order.
* Expressions are scanned from left to right, like reading English.
* __Concatenation__ of two expressions $U$ and $V$ (in that order) is denoted
  by $UV$. Note that $\epsilon U = U \epsilon = U$.
* If $U = W_1VW_2$ where $U, V, W_1, W_2$ are expressions, then we define
  * $V$ is a __segment__ of $U$
  * A __proper segement__ of $U$ is defined to be the case when $V\neq U$ and
    $V$ is non-empty
* If $U=VW$, where $U,V,W$ are expressions, then we define
  * $V$ to be an initial segement (prefix) of $U$
  * $V$ to be an terminal segement (suffix) of $U$

### Syntax: Well-formed Formulae

__Definition__: An __atom (atomic formula)__ is an expression consisting of a
prepositional variable only. The set of atomic formulae in $L^p$ is denoted by
$Atom(L^p)$.

__Definition__: An   expression in $L^p$is called a __formula__ (a well-formed
propositional formula) iff it can be constructed according to the following
_rules of formation_:

1. Every atomic formula is a formula
2. If $A$ is an atomic formula, then so it $(\lnot A)$
3. If $A,B$ are formulae, then so are
   $(A \land B), (A \lor B), (A \rightarrow B), (A \iff B)$

the set of all formulae in $L^p$ is denoted by $Form(L^p)$. It is the smallest
class of expressions of $L^p$ that contains $Atom(L^p)$ and is closed under the
formation rules of formulae.

__Example__: Generating formulae.

Let $F = ((p\lor q) \rightarrow ((\lnot p) \iff (p \land q)))$ be an element in
$Form(L^p)$ and $p,q,r$ are elements in $Atom(L^p)$. How is $F$ generated from
the rules of formation?

By rule 1, the atomic propositional variables are themselves formulae.
With these propositional variables, one can form the formulae $A = (p\lor q)$,
$B = (p\land q)$, using rule 3. Another formula, $C = (\lnot p)$ can be formed
by rule 2 applied to $p$. Then, $D = (C \iff B)$ can be formed by rule 3.
Finally, $F = (A \rightarrow D)$ can be formed using rule 3 yet again.

As you can see, a formula in $L^p$ can be built from the bottom up, using the
rules of formation.

__Example__: Parsing formulae

Take the following complex sentence in the English language

> "If Michelle wins at the olympics, everyone will admire her and she will get
> rich, but if she does not win, all her effort was in vain."

To translate this sentence to the language of propositional logic, we first
isolate the atomic propositions in the sentence (notice how each proposition
is sure to have a subject and an action):

* $p =$ Michelle wins at the Olympics
* $q =$ Everyone admires Michelle
* $r =$ Michelle will get rich
* $s =$ Michelle's effort was in vain

Then, the compound sentence (compound proposition) above can be expressed as
follows:

$((p\rightarrow (q\land r)) \land ((\lnot p) \rightarrow s))$

__Parse Trees__: A parse tree can be used to analyse formulae too. Have a look
at the parse tree of $((p \land (\lnot q)) \rightarrow r)$ (Forgive my directory
structure rendering of a parse tree).

$((p \land (\lnot q)) \rightarrow r)$  
$│$  
$├─ (p\land (\lnot q))$  
$│\hspace{1em} ├─ p$  
$│\hspace{1em} │$  
$│\hspace{1em} \hspace{2px}↳ (\lnot q)$  
$│\hspace{3em} \hspace{2px}↳ q$  
$│$  
$\hspace{2px}↳ r$  

__Question__: Can a formula be of two (or more) kinds?
For example, can a formula be both a conjunction and an implication?
This is important when it comes to understanding the place for ambiguity in
$L^p$.

Here are some claims about $L^p$ that we intend to prove, we shall refer to
them as $(\clubs)$.

* Every formula in $L^p$ has the same number of occurences of left and right
  parentheses.
* Any proper initial segment of a formula in $L^p$ has more occurrences of left
  than right parentheses. Any proper terminal segment of a formula in $L^p$
  has fewer occurrences of left compared to right parentheses.
* Neither a proper initial segment/proper terminal segment can be a formula in
  $L^p$.

$(\clubs)$ are all claims which help one prove an even greater claim- the one
which we are interested in.

__Unique Readability Theorem__ Every formula in $L^p$ is exactly one of the
six forms: an atom, $(\lnot A)$, $(A\land B)$, $(A \lor B)$, $(A\rightarrow B)$
and $(A\iff B)$, and it is so in exactly one way.

This theorem obliterates questions about ambiguity of formulae in $L^p$.
But how can we prove such claims? Let us get some guidance from
_mathematical induction_. But first, a review of the natural numbers.

#### Natural Numbers

The natural numbers are the set of numbers that we use to count, namely
0, 1, 2, 3, 4 and so on. These numbers form an unbounded sequence. They
include 0 because it is the number with which a count actually starts- one
starts counting at 0 and increases it with each object/entity counted.

Suppose $P$ names a property. We write '$P(2)$' to mean that that '2 has the
property $P$' or '$P$ holds for 2'.

A statement 'Every natural number has property $P$' actually corresponds to
a set of statements: $P(0), P(1), P(2), \dots$.

#### Mathematical Induction

Here is the essential principle of mathematical induction. Suppose that we
establish two things:

* the natural number $n$ has property $P$ (__BASIS__)
* when a natural number has property $P$, the next natural number also has
  property $P$ (__INDUCTIVE STEP__)

$\rightarrow$ We may conclude that every natural number greater than or equal to
$n$ has property $P$.

Why does this work? Well, one needs to understand the definition of natural
numbers. The natural numbers are defined recursively (in a self-referential
manner). At a high level: let the $n$-th natural number be denoted by $N_n$.
Define $N_0 = 0$ (let the first natural number be 0), and then for $n \geq 1$,
we define $N_n = 1 + N_{n - 1}$ (define every natural number after the first to
be 1 plus the previous natural number). Now of course, no one would take this
definition seriously as the natural numbers are used to define themselves- the
actual definition of the natural numbers involves sets and an idea similar to
the one presented above.

So, if the first natural number has a property $P$, and for any number that has
the property $P$, the next number has property $P$ too, here's what happens.
Since $P$ holds for 0, it starts a domino effect- the next one, 1, also has
property $P$, and therefore 2 has property $P$ and so on...

__Takeaways__: Here's what we can take away from the above insight into
natural numbers and mathematical induction.

* To talk about something, give it a name e.g. a property $P$, a number $k$
* A formula is a textual object. In this object, we can substitute one symbol
  or expression for another.
* The induction principle describes a method for proof consisting of two parts
  * The basis and inductive steps
  * In the inductive step, hypothesize $P(k)$ (this is called the
    __inductive hypothesis__) and prove $P(k+1)$ using it.

__NOTE__: The process of induction does not specify how to use the inductive
hypothesis to prove the next case, or how to prove the basis. In each problem,
these steps will be different.

#### Induction for $L^p$

Suppose one wants to prove that every formula in $L^p$ property $P$. Well, it
turns out that we cannot use induction above because a formula is not a natural
number. However, we can manipulate the situation to approach the proof
using an induction based solution. We can choose to prove any of the following:

* For all natural numbers $n$, every formula with $n$ or fewer symbols in it has
  property $P$.
* For all natural numbers $n$, every formula with $n$ or fewer connectives has
  property $P$.
* For all natural numbers $n$, every formula whose parse tree has height $n$ or
  less has property $n$.
* For all natural numbers $n$, every formula reproducible with $n$ or less
  applications of the formation rules has property $P$.

Note that the inductive step for each of these would require showing, by cases,
that if $P(A)$ and $P(B)$, then $P((\lnot A))$ and $P((A\star B))$ (where
$\star$ is one of $\land, \lor, \rightarrow, \iff$). Formulae $A,B$ have smaller
$n$ values than $(\lnot A)$ and $(A\star B)$.

We concoct a principle of induction which can be used in this case:

#### Structural Induction

The __Principle of Structural Induction__ says: Suppose $R$ is a property. If:

1. For any atomic formula $p$ in $Atom(L^p)$, $R$ holds for $p$
2. For any formula $A$ in $Form(L^p)$, if $R(A)$, then $(\lnot A)$ has property
   $R$ too
3. For all formulae $A,B$ in $Form(L^p)$, if $R(A)$ and $R(B)$, then
   $(A\star B)$ (where $\star$ is one of $\land, \lor, \rightarrow, \iff$) has
   property $R$ too.

then, any formula in $Form(L^p)$ has property $R$.

Here is an example of structural induction in action. Suppose we want to prove
the following lemma, which is the first of the claims in $(\clubs)$.

__Lemma__: Every well-formed formula has an equal number of left and right
parentheses.

__Proof__: Before starting, for convenience, we define: for all formulae $A$
in $Form(L^p)$, $l(A)$ is the number of left parentheses in $A$ and $r(A)$ is
the number of right parentheses in $A$.
Also, let the property being proven be called property $R$.

_Base Case_: If $A$ is an atom, then it has no parentheses. Therefore,
$l(A) = r(A) = 0$ and so $R(A)$. The base case holds.

_Inductive Step_: In this step, we shall consider three formulae $A,B$ and $C$,
for which it the inductive hypothesis that R holds for $A,B$ and $C$ is
assumed.

* Assume $A$ is of the form $(\lnot B)$. By the inductive hypothesis, $l(B) = r(B)$.
  Therefore:

  $\begin{aligned}
    l((\lnot B)) &= 1 + l(B) \hspace{1em}\text{[By inspection]}\\
    &= 1 + r(B) \hspace{1em}\text{[By inductive hypothesis]}\\
    &= r((\lnot B)) \hspace{1em}\text{[By inspection]}
  \end{aligned}$

* Assume $A$ is of the form $(B\star C)$. By the inductive hypothesis,
  $l(B) = r(B)$ and $l(C) = r(C)$. Therefore:

  $\begin{aligned}
    l((B\star C)) &= 1 + l(B) + l(C) \hspace{1em}\text{[By inspection]}\\
    &= 1 + r(B) + r(C) \hspace{1em}\text{[By inductive hypothesis]}\\
    &= r((B\star C)) \hspace{1em}\text{[By inspection]}
  \end{aligned}$

Therefore, property $R$ holds for all well-formed formulae in $L^p$.

We can now move on and use the tool of structural induction as the proof method
for the unique readability theorem. Before proceeding, a small discussion to
build some intuition about the the proof...

Let us try to see what happens when trying to interpret a well-formed formula
in $L^p$ as something that it is not. Consider the implication
$F=((p\land q) \rightarrow r)$. We want to show that this is an implication and
not a conjunction. Let's do both to see where parsing the formula as a
conjunction fails.

If we parse the formula in $F$ as an implication, it would look something like:
let $A=(p\land q)$ and $B=r$, then $F=(A\rightarrow B)$, where $A$ and $B$ are
well-formed formulae in $L^p$ (one can check by following the rules of
formation until the formula has been constructed from the atoms $p,q,r$).

Now, if we try to parse the formula as a conjunction, here is what it would
look like: let $A'=(p$ and $B'=q) \rightarrow r$, and $F=(A'\land B')$. However,
this is not a valid parse since $A'$ and $B'$ are not valid formulae (by the
lemma just proven above about equal number of left and right parentheses in a
well-formed formula in $L^p$. They also fail to be constructible from the rules
of formation).

What does this show us? We managed to prove that $F$ cannot be parsed as a
conjunction because upon decomposition, one does not end up with two
well-formed formulae as specified by $L^p$. But can we be sure that this holds
all the time?

#### Unique Readability Theorem

Now, let us approach the unique readability theorem by rephrasing it as a
property $P(n)$ which is stated below. Note that the notation $l(x)$ and $r(x)$
for the number of left and right parentheses in expression $x$ will continue to
be used.

__Property $P(n)$__:

Every formula, $A$, containing at most $n$ connectives satisifies all of the
following conditions:

1. The first symbol of $A$ is either a '(' (right parenthesis) or a
   propositional variable
2. A has an equal number of right and left parentheses and every
   _proper initial segment_ of $A$ has more left parentheses than right.
3. A has a unique construction as a formula.

Where a __proper initial segement__ is defined to be a non-empty expression $x$
such that $A$ is $xy$ for some non-empty expression $y$.

__Proof__: (Using structural induction, of course)

_Base case_: The base case is $n=0$, which is a formula with no logical
connectives. This has to be a propositional variable, so condition 1 is
satisfied. Secondly, a propositional variable has no parentheses so the first
part of condition 2 is satisfied. Since $A$, in this case has no proper initial
segments, the second part of condition 2 is vacuously satisfied.

_Inductive step_: (This is going to be a bit longer...) The inductive
hypothesis is that the property $P(k)$ holds for some $0 < k\in \mathbb{N}$,
meaning that it holds for formulae with at most $k$ logical connectives.
We now need to prove, using this hypothesis, that $P$ holds for $k+1$.
So let $A$ be a formula with $k+1$ logical connectives.

_Unary connective_: If $A$ is of the form $(\lnot B)$ for some formula $B$,
which has $k$ connectives and therefore satisfies conditions 1, 2 and 3, by the
inductive hypothesis.

1. Clearly, the first symbol of $A$ is a '(', so condition 1 is fulfilled.
2. Since $B$ satisfies condition 1, $(\lnot B)$ has an equal number of left
   and right parentheses too- $A$ satisfies the first half of the second
   condition. Now to prove the second half, we analyse the possible proper
   initial segments, $x$, of $A$:
   * If $x$ is "$($", then $l(x) > r(x)$
   * If $x$ is "$(\lnot$", then $l(x) > r(x)$
   * If $x$ is "$(\lnot$"$z$, where $z$ is some proper initial segment of $B$,
     since $B$ satisfies condition 2, we have that $l(z) > r(z)$ but
     $l(x) = 1 + l(z)$ and $r(x) = r(z)$ which means that $l(x) > r(x)$.
   * If $x$ is "$(\lnot$"$B$, then since $l(B) = r(B)$, we have that
     $l(x) > r(x)$.
   Together, these cases show that $A$ satisfies condition 2.
3. Since $B$ has a unique construction as a formula, so does $A$- It is the
   negation of the uniquely constructued formula $B$.

_Binary Connectives_: If $A$ is of the form $(B\star C)$ where $\star$
represents a logical binary connective and $B,C$ are formulae with at most $k$
connectives, property $P$ holds for them.

To prevent repetition, it is simply stated that the proof of the conditons 1
and 2 is very similar to the ones done for the proof in the unary connecive
case. What remains is to prove the 3rd condition- let's do it!

To prove the unique construction of $A$, we shall prove that if $A$ can be
decomposed as $(A'\star B')$ for some binary connective $\star$ and formulae
$A',B'$, then it must be the case that $B'=B$ and $C'=C$.
For clarity, we mean that the two decompositions,
$(B'\star C')$ and $(B\star C)$, are of the same formula (same length and
sequence of symbols in the same order).

* _Case 1_: If $B'$ has the same length as $B$, they must be the exact same
  string of symbols as they both begin at the second character of $A$.
* _Case 2_: If $B'$ is a proper prefix of $B$ (i.e. $B'$ has length less than
  the length of $B$). Now, since $B'$ and $B$ are both formulae with at most
  $k$ connectives, the inductive hypothesis holds for them.

  But this would mean that by condition 2, $B'$ has the same number of left and
  right parentheses. However, by the same condition applied to $B$, we see that
  any proper prefix of $B$ (namely $B'$) must have fewer left than right
  parentheses. So assuming that $B'$ is a proper suffix of $B$ clearly
  contradicts itself and therefore must be false.
* _Case 3_: Proven same as case 2 above.

Since case 2 and 3 contradict themselves, the only valid case is case 1, which
rightarrow that $B'=B$ (and also $C'=C$). Therefore, the two decompositions of $A$
are the exact same and this shows that $A$ is uniquely constructed.
$\blacksquare$

_Fun fact_: In mathematical proofs, the black square ($\blacksquare$) indicates
the end of a proof. It is used in the same manner here.

This proof proved the unique readability theorem (condition 3), but conditions
1 and 2 were required to prove it.

##### Consequences

Equipped with the a proven unique readability theorem, we can claim the
following now:

$\dagger$ A propositional variable is called an atom

$\dagger$ $(\lnot B)$ is called a negation formula

$\dagger$ $(A \land B)$ is called a conjunction formula

$\dagger$ $(A \lor B)$ is called a disjunction formula

$\dagger$ $(A \rightarrow B)$ is called a implication formula

$\dagger$ $(A \iff B)$ is called an equivalence formula

... and each is exactly of one kind.

This is important, as stated before, because the meaning of these formulae is
going to be derived from their syntax, so this ensures unambiguity.

#### Connective Precedence

For human beings, the following precedence rules are established:

* $\lnot$ takes precedence over $\land$
* $\land$ takes precedence over $\lor$
* $\lor$ takes precedence over $\rightarrow$
* $\rightarrow$ takes precedence over $\iff$

This allows some parentheses to be elided without loss of meaning or ambiguity:

$p\iff q \rightarrow r$ can be expanded, using these precedence rules, to be
$((p\iff q) \rightarrow r)$.

#### Scope

* If $A$ is of the form $(\lnot B)$, then we say that $B$ is the
  _scope of negation_ in $A$.
* If $A$ is of the form $(B\star C)$ (where $\star$ is a binary logical
  connective), then we say that $B$ is the _left scope_ of the connective
  (disjunction, conjunction, ...) in $A$ and $C$ is the _right scope_ of the
  connective in $A$.

### Semantics

So far, the syntax of the propositional language has been covered through the
structure of well-formed formulae in $L^p$. Now, we want to be able to analyse
the meaning of a syntactically valid/well-formed formula. This is done through
the specifications of semantics (grammar) for propositional language.

Syntax cared about when a formula was valid/invalid. Now, we care about when a
formula is true. We shall develop methods which will allow analysis of formulae
to determine truths, validity of arguments and so on. Let's begin.

The __meaning__ of a formula is defined to be its truth value, which is computed
from the truth values of its constitient atomic formulae/propositions. This
means that one has to first parse the formula into its atoms. Let's look at an
example. Take the following compound sentence: "If you take a class in computer
science and if you do not understand the concept of recursion, you will not
pass". The question is- when exactly is this statement true?

To begin the analysis, we decompose the statement into its atomic propositions.

* $p =$ "You take a class in computer science"
* $q =$ "You understand the concept of recursion"
* $r =$ "You will pass"

Using these atoms, the statement can be expressed as a formula in $L^p$ as
$((p\land \lnot q) \rightarrow \lnot r)$ (note how the rule for precedence of
negation over conjunction and implication applies in this formula). Now, let us
see how this statement evaluates for all possible truth value combinations of
$p,q,r$. Each sub-formula, by the unique readablility theorem, is of one form
only. This form is with respect to some logical operator and the truth table
for that operator is used to evaluate the sub-formula with the sub-formula
already evaluated. As you can see, this is a bottom-up process- starting with
the atomic formulae and building up, through the sub-formulae, all the way to
the compound formula in question.

| $p$ | $q$ |  $r$  | $(\lnot q)$ | $(p\land \lnot q)$ | $(\lnot r)$ | $((p\land \lnot q) \rightarrow \lnot r)$ |
| --- | --- | :---: | ----------- | ------------------ | ----------- | ---------------------------------------- |
| 1   | 1   |   1   | 0           | 0                  | 0           | 1                                        |
| 1   | 1   |   0   | 0           | 0                  | 1           | 1                                        |
| 1   | 0   |   1   | 1           | 1                  | 0           | __0__                                    |
| 1   | 0   |   0   | 1           | 1                  | 1           | 1                                        |
| 0   | 1   |   1   | 0           | 0                  | 0           | 1                                        |
| 0   | 1   |   0   | 0           | 0                  | 1           | 1                                        |
| 0   | 0   |   1   | 1           | 0                  | 0           | 1                                        |
| 0   | 0   |   0   | 1           | 0                  | 1           | 1                                        |

Clearly, the only way that this formula can evaluate to false is when $p,q,r$
have truth values of $1,0,0$ respectively i.e. when "You take a class in
computer science and you do not understand the concept of recuresion but you
pass".

We can now generalise what we just did through _truth valuations_.

****

## Truth Valuations

A __truth table__ is a list of the valiues that a formula takes under all
possible truth valuations. Fix a set $\{0,1\}$. We decide to interpret 0 as
false and 1 as true.

Let $A$ be a formula and $\{p_1,\dots,p_n\}$ be the set of propositional
variables that are contained in $A$.
A __truth valuation__, $t$, is a function from a set of propositional variables
$\{p_1,\dots,p_n\}$ to the set $\{0,1\}$. The action of the valuation $t$ on
the formula $A$ is denoted as $A^t$. More formally, $t$ is a function
$t:\{p_1,\dots,p_n\}\mapsto \{0,1\}$.

It is important to realise that a truth table is a collection of truth
valuations, each for a possible combination of the truth values for the
constituent propositional variables.
In the truth table above, the first three columns $p,q,r$ specify the truth
values for the propositional variables. If there are $n$ propositional
variables, there will be $2^n$ rows in the truth table (convince yourself).
The next few columns are intermediate steps to the final column, which is
the value of the truth valuation, evaluated at the truth values for the
propositional variables on that row.

The beauty of the framework that we have created to do logic within is that
it is compatible with recursion- which is essentially when a definition is
self-referential. This will be useful when defining what a truth valuation for
a general formula in $L^p$ is (_hint_: compare the idea of recursion to the
process performed in the truth table above- the definition of a truth valuation
is essentially that process).

__Definition__: Fix a truth valuation $t$. The
__value of the formula__ $C$ in $Form(L^p)$ under the truth valuation $t$ is
denoted by $C^t$ and is defined recursively as follows:

1. $p^t$ is given by the definition of $t$, for every propositional variable,
   $p$.
2. $(\lnot A)^t = \begin{cases}
  1 &\text{ if } A^t =0\\
  0 &\text{ if } A^t =1\\
\end{cases}$
3. $(A\land B)^t = \begin{cases}
  1 &\text{ if } A^t = B^t = 1\\
  0 &\text{ otherwise }\\
\end{cases}$
4. $(A\lor B)^t = \begin{cases}
  1 &\text{ if } A^t = 1 \text{ or } B^t = 1\\
  0 &\text{ otherwise }\\
\end{cases}$
5. $(A\rightarrow B)^t = \begin{cases}
  1 &\text{ if } A^t = 0 \text{ or } B^t = 1\\
  0 &\text{ otherwise }\\
\end{cases}$
6. $(A\iff B)^t = \begin{cases}
  1 &\text{ if } A^t = B^t\\
  0 &\text{ otherwise }\\
\end{cases}$

Suppose $A$ is $p\lor q \rightarrow q\land r$ and $t$ is a truth valuation under
which $p^t = q^t = r^t = 1$. We follow the precedence rules to work with this
unparenthesized formula: $(p\lor q)^t = 1$ and $(q\land r)^t = 1$, therefore
$A^t = 1$. Another truth valuation, $t_1$ could be such that $p^{t_1} = 1$ and
$q^{t_1} = r^{t_1} = 0$. Then $(p\lor q)^{t_1}=1$ and $(q\land r)^{t_1}=0$
so that $A^t=0$. This shows that different truth valuations can lead to
different truth values for the subformulae and the formula at large.

__Note__: We now know how to form propositional formulae from everyday compound
sentences and evaluate them under specific truth values of the constituent
atoms/propositional variables. Now, we proceed to analyse entities larger than
sentences- __arguments__. We shall see how to relate a collection of
propositional formulae (premises) to another propositional formula (the
conclusion), similar to the discussions at the beginning of this document.
What we do now is to make some definitions which will allow us to analyse
arguments in this $L^p$ framework we have studied.

__Definition__: We say that a truth valuation $t$ __satisfies__ a formula $A$
in $Form(L^p)$ iff $A^t=1$.

The Greek letter $\Sigma$ is used to denote an arbitrary set of formulae.

Define:

$\Sigma^t = \begin{cases}
  1 &\text{ if for each formula } B\in\Sigma, \hspace{.5em} B^t = 1\\
  0 &\text{ otherwise }
\end{cases}$

__Definition__: A set of formulae $\Sigma\subseteq Form(L^p)$ is said to be
satisfiable iff there exists a truth valuation $t$ such that $\Sigma^t = 1$.
When this happens, one says that $\Sigma$ is _satisfied under_ $t$.

* Observe that if $\Sigma^t=1$, then __all formulae__ in $\Sigma$ must evaluate
  to be true under the truth valuation $t$.
* If however, $\Sigma^t =0$, then __at least one formula__ in $\Sigma$ must
  evaluate to be false under the truth valuation $t$. This is important to
  understand because it is easily misunderstood that $\Sigma^t=0$ means that
  every formula in $\Sigma$ evaluates to be false under the truth valuation
  $t$- this is not true!

__Example__: We explore satisfiability through the example of a 4x4 Sudoku game
analysis. In 4x4 Sudoku, each number $1,2,3,4$ must appear once in each row,
once in each column and oncee in each 2x2 block in the partitioned 4x4 grid.

Before we write any formulae, we setup our propositional variables. Let
$p_{i,j,k}$ be the proposition that "the cell in the $i$-th row, $j$-th column
contains a $k$", where $1\leq i,j,k\leq 4$ of course.

To verify that a sudoku game is winnable, we need to verify that the game's
rules can be satisfied. So, given a 4x4 Sudoku grid with $n$ starting values
$\{k_1,\dots,k_n\}$, in positions $\{(i_1,j_1), \dots, (i_n,j_n)\}$ (format
$(row, column)$).

Let's start off with a set $\Sigma_0 = \{\} = \emptyset$ containing all of the
formulae (representing conditions of the game) that have to be satisfied in
order to win. We shall populate it with conditions now:

* To verify that a solution for the given grid is indeed for that given grid,
  one can start by verifying that the starting values match. This can be done
  by satisfying each formula in
  $\Sigma_1 = \{p_{i_1,j_1,k_1}, p_{i_2,j_2,k_2}, \dots, p_{i_n,j_n,k_n}\}$.
  We can now add each formula in $\Sigma_1$ to $\Sigma$ above.
* Next, to ensure that there is at most one digit per position in the grid,
  we can do the following. For each position $(i,j)$ and each pair of non-equal
  possible values $k,k'$, we add the formula
  $p_{i,j,k}\rightarrow \lnot p_{i,j,k'}$ to the set $\Sigma$.
* Next, to verify that each digit appears once in each row. First, we can check
  that for each row, each digit appears at least once. This can be done by
  adding the formula
  $(p_{i,1,k}\land p_{i,2,k}\land p_{i,3,k}\land p_{i,4,k})$ for $i,k$
  both ranging over $\{1,2,3,4\}$.

  Now, to make sure that each number appears once in each row, we look at every
  pair of cells $(i,j)$ and $(i,j')$ in each row and add the following formula
  $p_{i,j,k}\rightarrow \lnot p_{i,j',k}$ for all values of $k$.
* To verify that the columns are properly filled, the same process as the rows
  is performed, with the necessary index changes.
* The same goes for verifying that the 2x2 boxes in the 4x4 grid are also
  properly filled- also with the indexing changes required.

Once all of this has been done, $\Sigma$ contains all of the formulae which all
have to be true in order for the Sudoku grid to be considered solved. This
condition can be checked by forming one large formula by taking the conjunction
of each of the formulae in $\Sigma$.

__Definition__: A formula $A$ is a __tautology__ iff it is true under all
possible truth valuations $t$.

__Definition__: A formula $A$ is a __contradiction__ iff it is false under all
possible truth valuations $t$.

__Definition__: A formula that is neither a tautology nor a contradiction is
said to be __contingent__.

__Example__ This is an important tautology that we have all dealt with in real
life: __the law of the excluded middle__ ("_tertium non datur_") states that
$p\lor \lnot p$ is a tautology. Let us check this by drawing out the truth
table and verifying that it evaluates to be true under all possible truth
values:

| $p$ | $\lnot p$ | $p\lor \lnot p$ |
| --- | --------- | :-------------: |
| 1   | 0         |        1        |
| 0   | 1         |        1        |

Now, you may be thinking of why this is important. Well, tautologies can be
considered to be a method of generating statements that are always true (a way
of bootstrapping towards truth, if you may...). For example, take the formula
$(q\land r)$, which is clearly contingent. However, using the tautology
$(p\land\lnot p)$, one can be sure that the formula obtained by replacing
all instances of $p$ in the tautology with $(q\land r)$, namely
$((q\land r)\lor \lnot (q\land r))$ is also a tautology:

We formalise and generalise this...

__Theorem__: Let $A$ be a tautology and let $p_1,\dots,p_n$ be the
propositional variables of $A$. Suppose that $A_1,\dots,A_n$ are arbitrary
fomulae, then the formula obtained by replacing $p_1$ by $A_1$, $p_2$ by $A_2$,
..., $p_n$ by $A_n$ is a tautology.

__Example__ This is an important contradiction, which presumably, we have all
encountered in one way or another. It is __law of contradiction__ which says
that "Nothing can both be, and not be" i.e. $(p\land \lnot p)$. Again, we check
the truth table for this formula to ensure that it evaluates to false under all
possible truth values.

| $p$ | $\lnot p$ | $p\land \lnot p$ |
| --- | --------- | :--------------: |
| 1   | 0         |        0         |
| 0   | 1         |        0         |

__Note__: Some eagle-eyed readers must have noticed the inherent connection
between tautologies and contradictions- you cannot have one without the other.
$A$ is a tautology iff $\lnot A$ is a contradiction. Can you see why?

These can be summarized through __Plato's three essential laws of thought__:

* __Law of identity__: _"Whatever is, is"_. $p=p$
* __Law of contradiction__: _"Noting can both be, and not be"_.
  $\lnot(p\land \lnot p)$
* __Law of excluded middle__: _"Everything must either be or not be"_.
  $(p\lor \lnot p)$

****

## Argument Validity

As stated in the beginning of this document, the idea is to only analyse the
structure of an argument. That is why propositional language is being used- to
abstract out the content of an argument and narrow focus to the structure. A
typical argument states a series of propositions (called the __premises__) and
using those premises, states a final proposition (called the __conclusion__).
If the argument is correct (valid, sound), the the conclusion is guaranteed to
be correct provided that the content of the premises is correct. We formalize
these ideas now.

__Definition__ Let $\Sigma \subseteq Form(L^p)$ and $A\in Form(L^p)$. $A$ is
said to be a __tautological consequence__ of the formulae in $\Sigma$ iff for
any truth valuation $t$, we have that $\Sigma^t=1$ implies that $A^t=1$. When
this is the case, it is denoted as $\Sigma \models A$.

__Note__ the following:

* "$\models$" is NOT a valid symbol in $L^p$ (as per the specifications above)
  and so $\Sigma\models A$ is not a formula. Instead, it is a statement made
  about $\Sigma$ and $A$.
* When it is not the case that $\Sigma\models A$, this is denoted as
  $\Sigma\not\models A$.
* When $\Sigma \models A$, we say that the formulae in $\Sigma$
  __(tauto)logically imply__ the formula $A$ or that $\Sigma$
  __semantically entails__ $A$.

__Special Case__: What if $\Sigma = \emptyset = \{\}$? By the definitions we
just made, if $\Sigma=\emptyset \models A$, then for every valuation $t$, if
$\emptyset^t =1$ then $A^t = 1$. Now, $\emptyset^t = 1$ means that for every
formula $B$ in $\Sigma$, $B^t=1$. But since there are no formulae in $\Sigma$,
$\Sigma^t = 1$ is vacuously true. As a result, $\Sigma \models A$ is a
tautology.

Arguing intuitively, $\Sigma\models A$ means that the truth of the formule in
$\Sigma$ is enough for $A$ to be true. But since $\Sigma$ has no formulae,
the antecedent of the condition is false and so the truth value of $A$ is
unconditional, therefore it is a tautology,

### Argument Validity and Satisfiability

Let $\Sigma = \{A_1,\dots,A_n\}\subseteq Form(L^p)$ be a set of formulae (premises)
and let $C\in Form(A)$ be a formula (conclusion). The following are equivalent:

* The argument with premises $\{A_1,\dots,A_n\}$ and conclusion $C$ is valid
* $(A_1\land \dots \land A_n)\rightarrow C$ is a tautology
* $(A_1\land \dots \land A_n \land \lnot C)$ is a contradiction
* $(A_1\land \dots \land A_n \land \lnot C)$ is not satisfiable
* The set $\{A_1\land \dots \land A_n \land \lnot C\}$ is not satisfiable
* $C$ is a tautological consequence of $\Sigma$ i.e. $\Sigma\models C$

__Note__: Here are some key points that one ought to remeber about validity:

Consider and argument comprised of the premises
$\{A_1,\dots,A_n\}\subseteq Form(A)$ and conclusion $C\in Form(A)$.

* A valid/sound argument does not guarantee the truth value of the conclusion.
  As mentioned before, there is another requirement for the conclusion to be
  true the truth of all the premises. Formally, the conclusion $C$ is true iff
  * The argument with premises $\{A_1,\dots,A_n\}$ and conclusion $C$ is
    valid and
  * The premises $A_1,\dots,A_n$ are all true
* TLDR: a valid argument (sound reasoning) only guarantees the truth of a
  conclusion if the argument is based on true premises (assumptions).

__Definition__: For two formulae $A,B\in Form(A)$, the notation
$A \models\!\mid B$ is used to denote that $A\models B$ and $B\models A$.
$A$ and $B$ are said to be __tautologically equivalent__ (or just equivalent)
iff $A\models\!\mid B$ holds.

Formulae that are tautologically equivalent have the property that they are
assigned the same truth values under any truth valuation.

__Notes__:

* "(Tauto)logically implies" $A\models B$ is different from the meaning of
  the implication $(A\rightarrow B)$. By its definition, $A\models B$ iff
  $(A\rightarrow B)$ is a tautology.
* "(Tauto)logically equivalent" ($A\models\!\mid B$) is different from the
  meaning of the equivalence $(A\iff B)$. By its definition, $A\models\!\mid B$
  iff $(A\iff B)$ is a tautology.

#### Validity Proofs with Truth Tables

One way to verify the statement $\Sigma\models A$ (prove the validity of the
argument with premises $\Sigma$ and conclusion $A$), it is sufficient to show
that all truth valuations $t$ which satisfy $\Sigma$ also satisfy $A$ (note
that there can exist truth valuations which satisfy $A$ but not $\Sigma$ and
this is fine).

Here's an example showing that
$\{p\rightarrow q,q\rightarrow r\}\models (p\rightarrow r)$ using a truth table.
Letting $A_1=(p\rightarrow q)$ and $A_2=(q\rightarrow r)$ be the premises:

| __ROW #__ | $p$ | $q$ | $r$ | $(p\rightarrow q)$ | $(q\rightarrow r)$ | $(A_1\land A_2)$ | $(p\rightarrow r)$ |
| --------- | --- | --- | --- | ------------------ | ------------------ | ---------------- | ------------------ |
| _1_       | 1   | 1   | 1   | 1                  | 1                  | __1__            | __1__              |
| _2_       | 1   | 1   | 0   | 1                  | 0                  | 0                | 0                  |
| _3_       | 1   | 0   | 1   | 0                  | 1                  | 0                | 1                  |
| _4_       | 1   | 0   | 0   | 0                  | 1                  | 0                | 0                  |
| _5_       | 0   | 1   | 1   | 1                  | 1                  | __1__            | __1__              |
| _6_       | 0   | 1   | 0   | 1                  | 0                  | 0                | 1                  |
| _7_       | 0   | 0   | 1   | 1                  | 1                  | __1__            | __1__              |
| _8_       | 0   | 0   | 0   | 1                  | 1                  | __1__            | __1__              |

The truth valuations represented by rows 1,5,7,8 are the ones under which the
premises evaluate to be true. What is important is what when the premises are
true, the conclusion is also true. This shows that
$\{p\rightarrow q,q\rightarrow r\}\models (p\rightarrow r)$.

Therefore, the argument

1. $(p\rightarrow q)$
2. $(q\rightarrow r)$

__Conclusion__: $(p\rightarrow r)$

is a valid argument. Try it- let $p,q,r$ be any propositions for which the
premises above are true- the conclusion $p\rightarrow r$ will also be true.

Now, to prove that an argument is NOT valid, one has to repeat the same truth
table drawing as above for that argument, and find at least one truth valuation
under under which the premises are satisfied, but not the conclusion. That is
enough to prove the invalidity of the argument.

There's a problem with this method of validating arguments though. For a
formula with $n$ variables and $m$ connectives, the truth table has $2^n$ rows
and at most $n+m$ columns. This gets out of hand quickly when the number of
variables is larger.

#### Validity without Truth Tables

In this case, we can be smart and use the following proof methods.

__Proof by Contradiction__: Remember in logic, a contradiction is a statement
which is never true. In this context, the word contradiction is used
differently. The proof method works by assuming the opposite of what is being
proven and showing the absurdity of that.

Say, again, that we want to show that
$\{A\rightarrow B,B\rightarrow C\}\models A\rightarrow C$.

_Proof by contradiction_: Assume the opposite-
$\{A\rightarrow B,B\rightarrow C\}\not\models A\rightarrow C$.

This means that there exists a truth valuation under which the premises are
true but not the conclusion i.e. there exists a truth valuation $t$ such that:

1. $(A\rightarrow B)^t=1$
2. $(B\rightarrow C)^t=1$
3. $(A\rightarrow C)^t=0$

Here's what one can deduce from this: by the 3rd line, we it must be that
$A^t = 1$ and $C^t = 0$. But if $A^t=1$, this must mean that $B^t=1$ by the 1st
line. But if $B^t=1$, this means that $C^t=1$ to satisfy the 2nd line.
Wait what? By the third line, $C^t = 0$ but by the 2nd line, $C^t = 1$, which
shows that this is an absurd situation. For it to be true, $C^t$ would need to
both be and not be 1- which is never true. Therefore, the assumption that we
made at the beginning, that
$\{A\rightarrow B,B\rightarrow C\}\not\models A\rightarrow C$ is false.
As a result, $\{A\rightarrow B,B\rightarrow C\}\models A\rightarrow C$ is true,
proving that the argument is valid.

__Proof by Counterexample__: This method works by constructing a truth
valuation under which the premises are true, but the conclusion is false.

Suppose we want to show that
$\{(p\rightarrow \lnot q)\lor r, q\land \lnot r, p\iff r\}\not\models (\lnot p\land (q\rightarrow r))$.

_Proof by counterexample_: By any method you can think of, construct a
counterexample such as the truth valuation $t$ under which $p^t = 0$, $q^t = 1$
and $r^t = 0$. Under this:

* _Premise 1_: $((p\rightarrow \lnot q)\lor r)^t = 1$
* _Premise 2_: $(q\land \lnot r)^t = 1$
* _Premise 3_: $(p\iff r)^t = 1$
* _Conclusion_: $(\lnot p\land (q\rightarrow r))^t = 0$

So we have a counterexample- the truth valuation $t$. Therefore, this argument
is not valid.

There are smarter ways however...

#### Important Tautological Equivalences

Consider the following statements:

* "He is either not informed or he is not honest"
* "It is not true that he is informed and honest"

These two statements seem to be logically equivalent. Let's prove this.
Let $p=$ "he is honest" and $q=$ "he is informed". The first statement
translates to $(\lnot p \lor \lnot q)$ and the second one to
$(\lnot (p\land q))$.

We have __De Morgan's Law__:
$(\lnot (p\land q)) \models\!\mid (\lnot p \lor \lnot q)$

| $p$ | $q$ | $\lnot p$ | $\lnot q$ | $p\land q$ | $\lnot p \lor \lnot q$ | $(\lnot (p\land q))$ |
| --- | --- | --------- | --------- | ---------- | ---------------------- | -------------------- |
| 1   | 1   | 0         | 0         | 1          | __0__                  | __0__                |
| 1   | 0   | 0         | 1         | 0          | __1__                  | __1__                |
| 0   | 1   | 1         | 0         | 0          | __1__                  | __1__                |
| 0   | 0   | 1         | 1         | 0          | __1__                  | __1__                |

De Morgan's Laws are used to negate conjunctions and disjunctions. The one
above can be summarized as "To negate a conjunction, take the conjunction of
the negation of the conjuncts".

We also have __Dual De Morgan's Law__:
$(\lnot (p\lor q))\models\!\mid (\lnot p\land \lnot q)$. Again, this can be
readily shown by drawing out a truth table. This one says: "To negate a
disjunction, take the conjunction of the negation of the disjuncts".

Next, consider the following statements:

* "If the goods were not delivered, the customer cannot have paid"
* "If the customer has paid, the goods must have been delivered"

Let $p=$ "the goods were delivered" and $q=$ "the customer has paid", then the
two sentences above translate to $(\lnot p \rightarrow \lnot q)$ and
$(q\rightarrow p)$.

The two $(\lnot p \rightarrow \lnot q)$ and $(q\rightarrow p)$ are called
__contrapositives__ of each other. The table below shows that these are
tautologically equivalent i.e.
$(\lnot p \rightarrow \lnot q) \models\!\mid (q\rightarrow p)$

| $p$ | $q$ | $\lnot p$ | $\lnot q$ | $\lnot p \rightarrow \lnot q$ | $(q\rightarrow p)$ |
| --- | --- | --------- | --------- | ----------------------------- | ------------------ |
| 1   | 1   | 0         | 0         | __1__                         | __1__              |
| 1   | 0   | 0         | 1         | __1__                         | __1__              |
| 0   | 1   | 1         | 0         | __0__                         | __0__              |
| 0   | 0   | 1         | 1         | __1__                         | __1__              |

The contrapositive can be useful in proofs when it is easier to prove
$\lnot q\rightarrow \lnot p$ than $p\rightarrow q$.

__Contrapositive VS Converse__: It is easy to get these two confused and this
leads to logical errors since they are not tautologically equivalent.

* The contrapositive of $(p\rightarrow q)$ is $(\lnot q\rightarrow \lnot p)$
  and it is equivalent to the formula
* The converse of $(p\rightarrow q)$ is $(q\rightarrow p)$ and it is __NOT__
  equivalent to the formula

Another important tautological equivalence is the __biconditional__ which
states that $(p\iff q)\models\!\mid ((p\rightarrow q)\land (q\rightarrow p))$.
We can see this in the following truth table:

| $p$ | $q$ | $p\rightarrow q$ | $q\rightarrow p$ | $(p\rightarrow q)\land (q\rightarrow p)$ | $p\iff q$ |
| --- | --- | ---------------- | ---------------- | ---------------------------------------- | --------- |
| 1   | 1   | 1                | 1                | __1__                                    | __1__     |
| 1   | 0   | 0                | 1                | __0__                                    | __0__     |
| 0   | 1   | 1                | 0                | __0__                                    | __0__     |
| 0   | 0   | 1                | 1                | __1__                                    | __1__     |

The biconditional is important in proofs: when proving $p\iff q$, proving
$p\rightarrow q$ and $q\rightarrow p$ is sufficient.

__Lemma__: If $A\models\!\mid A'$ and $B\models\!\mid B'$

1. $\lnot A \models\!\mid \lnot A'$
2. $A\land B \models\!\mid A'\land B'$
3. $A\lor B \models\!\mid A'\lor B'$
4. $A\rightarrow B \models\!\mid A'\rightarrow B'$
5. $A\iff B \models\!\mid A'\iff B'$

__Theorem \[Replacability of Equivalent Formulae\]__: Let $B\models\!\mid C$.
If $A'$ results from replacing some (not necessarily all) instances of $B$ in
$A$ by $C$, then $A\models\!\mid A'$.

_Proof_: \[An exercise in structural induction\]

__Theorem \[Negating a formula\]__: Suppose $A$ is a formula composed of some
atoms and the connectives $\lnot,\land,\lor$ only, by the formation rules.
Suppose that $\Delta(A)$ results from replacing $\land$ with $\lor$ and $\lor$
with $\land$ in $A$, as well as replacing each propositional variable with its
negation. Then $A\models\!\mid \lnot \Delta(A)$.

_Proof_: \[An exercise in structural induction\]

For example, if we have that $A=(p\land\lnot q)\land(\lnot r\land s)$. The
negation of $A$ by the above theorem is
$\lnot A = (\lnot p\lor q)\lor (r\lor \lnot s)$.

## Formula Simplification, Essential Laws and Normal Forms

Here, we draw a similarity between simple algebraic manipulations and
simplification of formulae in the propositional language. In algrebra, the
expression $(a + b) - b$ is clearly yields $a$. But how do we know this? The
rules that were followed to reach the deduction that the expression evaluated to
$a$ were the associativity of addition, and how zero is defined i.e. $y-y=0$ and
$x+0=x$. In essence, this helped us reach a simplified form of the expression,
which can help to make it easier to understand and work with.

Now, consider the following propositional formula $(p \land q) \land \lnot q$.
When seeking a simplification of this formula, the process is very similar to
the algebraic one above. The difference is that in this case, the algebraic
rules are actually (tauto)logical equivalences. We use the following
equivalences in order to simplify this logical formula:

$\begin{aligned}
  (A\land B) \land C &\models\!\mid A\land (B\land C) \\
  A\land \lnot A &\models\!\mid 0 \\
  A\land 0 &\models\!\mid 0
\end{aligned}$

Using these equivalences above, we can do the following:

$\begin{aligned}
(p\land q) \land\lnot q &\models\!\mid p\land (q\land \lnot q)\\
  &\models\!\mid p\land 0 \\
  &\models\!\mid 0
\end{aligned}$

### Simplification of Conditonals and Biconditionals

Since the symbolic treatment of conditionals and biconditionals is relatively
cumbersome, one usually "substitutes" them using logically equivalent formulae.
In order to remove the conditional from a formula, one pay perform a
substitution using the following equivalence:

$p\rightarrow q \models\!\mid \lnot p \lor q$

To get rid of the biconditional, one may use either of the following forms:

$\begin{aligned}
  p \iff q &\models\!\mid (p\land q)\lor (\lnot p\land \lnot q)\\
  &\models\!\mid (p\rightarrow q) \land (q\rightarrow p) \\
  &\models\!\mid (\lnot p\lor q) \land (p\lor \lnot q)
\end{aligned}$

__Example__:

$\begin{aligned}
  (p\rightarrow q\land r)\lor ((r\iff s) \land (q\lor s))
  \models\!\mid (\lnot p \lor q\land r) \lor (
  ((r\land s)\lor (\lnot q\land \lnot s)) \land (q\lor s))
\end{aligned}$

### Essential Laws of Propositional Calculus

| Name              | Law                                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Excluded Middle   | $p\lor \lnot p \models\!\mid 1$                                                                                          |
| Contradiction Law | $p\land \lnot p \models\!\mid 0$                                                                                         |
| Identity Laws     | $p\lor 0 \models\!\mid p$ and $p\land 1 \models\!\mid p$                                                                 |
| Dominaiton Laws   | $p\lor 1\models\!\mid 1$ and $p\land 0 \models\!\mid 0$                                                                  |
| Idempotent Laws   | $p\lor p\models\!\mid p$ and $p\land p\models\!\mid p$                                                                   |
| Double-negation   | $\lnot(\lnot p) \models\!\mid p$                                                                                         |
| Commutative Laws  | $p\land q\models\!\mid q\land p$ and $p\lor q\models\!\mid q\lor p$                                                      |
| Associative Laws  | $(p\lor q)\lor r \models\!\mid p\lor (q\lor r)$ and $(p\land q)\land r \models\!\mid p\land(q\land r)$                   |
| Distributive Laws | $p\land (q\lor r) \models\!\mid (p\land q)\lor (p\land r)$ and $p\lor (q\land r) \models\!\mid (p\lor q)\land (p\lor r)$ |
| De Morgan's Laws  | $\lnot (p\land q)\models\!\mid \lnot p \lor \lnot q$ and $\lnot (p\lor q) \models\!\mid \lnot p \land \lnot r$           |

* Note that all of these laws can be readily proven using a truth table
* All laws come in pairs (except the double negation law). These pairs are
  called dual pairs: for each formula depending only on the connectives
  $\lnot, \land, \lor$, the dual is obtained by replacing each 1 by a 0 and each
  0 by a 1, all $\land$ with $\lor$ and finally replace all $\lor$ with $\land$.
* The laws help one simplify a formula and should therefore be applied whenever
  they can. There is no point in leaving the formula $\lnot\lnot p\lor
  (q\land\lnot q)$ as it is. It is better simplified as just $p$.
* A __non-perfect__ analogy for the commutative, associative and distributive
  laws is found in the algebraic operators $+,-$. The $\land$ is often treated
  as $+$ and $\lor$ is often treated as $-$ (not always...).

Here are two other laws which can be derived from the laws above. Firstly, here
are the absorption laws:

* $p\land (p\lor q) \models\!\mid p$
* $p\lor (p\land q) \models\!\mid p$

They can be proven using the identity, distributivity and domination laws:

$\begin{aligned}
  p\lor (p\land q) &\models\!\mid (p\land 1) \lor (p\land q) &\text{Identity}\\
  &\models\!\mid p \land (1\lor q) &\text{Distributivity (in reverse)}\\
  &\models\!\mid p \land 1 &\text{Domination}\\
  &\models\!\mid p &\text{Identity}
\end{aligned}$

Here is another important law, with its dual:

* $(p\land q)\lor (\lnot p\land q) \models\!\mid q$
* $(p\lor q) \land (\lnot p \lor q) \models\!\mid q$

These can be proven using distributivity in revserse, followed by the law of the
excluded middle and finally the identity laws.

#### Shortcuts for Simplifying Formulae

__Definition__: A formula is called a literal if it is of the form $p$ or $\lnot
p)$, where $p$ is a propositional variable.
The two $p$ and $\lnot p$ are called _complementary literals_. The following
rules allow one to simplify conjunctions only containing literals:

* If a conjunction contains complementary literals or the propositional constant
  0, then it always yields 0 i.e. it is a contradiction
* All instances of the propositional constant 1 and the duplicate copies of any
  literal may be dropped. If nothing remains, then the formula is a tautology -
  you can keep just a 1 to have a formula.

To simplify disjunctions, the duals of the two rules above are used.

* If a disjunction contains complementary literals or the propositional constant
  1, then it always yields 1 i.e. it is a tautology
* All instances of the propositional constant 0 and all duplicate copies of any
  literal may be dropped. If nothing remains, then the formula is a
  contradiction- you can keep just a 0 to have a formula.

__Example__: Simplifying
$(p_3\land \lnot p_2 \land p_3 \land \lnot p_1)\lor (p_1\land p_3 \land\lnot p_1)$

Using the rules above, this expression can be simplified to:
$p_3\land \lnot p_2 \land \lnot p_1$

### Normal Forms

Just like matrices, formulae can be converted into some standard froms through
which they can become more convenient for symbolic manipulations and
identification and comparision of formulae. In propositional calculus, there are
two such forms: the __Disjunctive Normal Form__ and the __Conjunctive Normal
Form__.

__Definition__: A formula is said to be in disjunctive normal form (DNF) if it
is written as a disjunction, in which all the terms are conjunctions of
literals.

__Example__: The formulae $(p\land q)\lor (p\land \lnot q)$, $p\lor (q\land r)$
and $\lnot p \lor t$ are all in DNF.

The disjunction $\lnot (p\land q) \lor r$ is NOT in DNF. This is because the
term $\lnot (p\land q)$ is a negation, not a conjunction.

__Definition__: A disjunction with literals as disjuncts is called a disjunctive
clause. Similarly, a conjunction with literals as conjuncts is called a
conjunctive clause.

__Examples__: $(p\land q\land \lnot r)$ is a conjunctive clause and
$(p\lor q\lor \lnot r)$ is called a disjunctive clause,

In general, disjunctive and conjunctive clauses are just called clauses,

__Definition__: A conjunction with disjunctive clauses as its conjuncts is said
to be in conjunctive normal form.

__Examples__: Each of $p\land (q\lor r)$, $p\land q$ and $p\land \lnot q$ is in
CNF. However, the formula $p\land (r\lor (p\land q))$ is NOT in CNF- the term
$p\land q$ in the second argumet of the first conjunction is a conjunction, not
a literal, therefore it is not a disjunctive clause.

### Obtaing Normal Forms

How does one compute the normal form of a formula? The following tautological
equivalences can be used to this end.

These help to get rid of implications and equivalences from formulae.

* $A\rightarrow B \models\!\mid \lnot A\lor B$ 
* $A\iff B \models\!\mid (\lnot A \lor B)\land (A\lor \lnot B)$
* $A\iff B \models\!\mid (A\land B)\lor (\lnot A \land \lnot B)$

These equivalences help to eliminate $\lnot, \land, \lor$ from the scope of
$\lnot$ such that every $\lnot$ only has an atom in its scope.

* $\lnot\lnot A \models\!\mid A$
* $\lnot (A_1\land\dots\land A_n) \models\!\mid \lnot A_1\lor\dots\lor\lnot A_n$
* $\lnot (A_1\lor\dots\lor A_n) \models\!\mid \lnot A_1\land\dots\land\lnot A_n$

These equivalences help eliminate $\lor$ from the scope of $\land$.

* $A\land (B_1\lor\dots\lor B_2) \models\!\mid (A\land B_1)\lor\dots\lor(A\land
  B_n)$
* $(B_1\lor\dots\lor B_n)\land A \models\!\mid (B_1\land
  A)\lor\dots\lor(B_n\land A)$

These last equivalences help eliminate $\land$ from the scope of $\lor$.

* $A\lor (B_1\land\dots\land B_n) \models\!\mid (A\lor B_1)\land\dots\land
  (A\lor B_n)$
* $(B_1\land\dots\land B_n)\lor A \models\!\mid (B_1\lor A)\land\dots\land
  (B_n\land A)$

This method will lead to the DNF/CNF of a formula.

__Notes__: The two nomrmal forms that have been discussed thus far are not
mutually exclusive i.e. a formula in CNF can also be a valid formula in DNF.
Have a look at the formula $\lnot p\land q \land \lnot r$, which is a
conjunction with 3 literals. It is in CNF, with three disjunctive clauses.
Alternatively, it is also in DNF, with one conjunctive clause.

On the other hand, the formula $\lnot p \lor (q\land \lnot r)$ is in DNF, with
two conjunctive clauses, but it cannot be considerd to be a formula in CNF at
all. But if $\lor$ is exchanged for $\land$ in this formula, it is a valid
formula in CNF too, just like the example above.

#### Algorithm for CNF

* Eliminate equivalences and implications using $A\rightarrow B \models\!\mid
  \lnot A \lor B$ and $A\iff B \models\!\mid (\lnot A \lor B)\land (A\lor \lnot
  B)$
* Push negation inwards, to the variables using De Morgan's Laws
* Recursively: $CNF(A)$
    * If $A$ is a literal, then return $A$
    * If $A$ is $B\land C$, then return $CNF(B)\land CNF(C)$
    * If $A$ is $B\lor C$,
      * call $CNF(B)$ and $CNF(C)$
      * Suppose $CNF(B) = B_1\land\dots\land B_n$
      * Suppose $CNF(C) = C_1\land\dots\land C_m$
      * Return $\land_{i=1,\dots,n\;\text{ and }\;j=1,\dots,m}(B_i\lor C_j)$
        i.e. the conjunction of $B_i\land C_j$, for all pairs of $i,j$.

__Example__: Consider the formula
$((a\lor b)\land (c\lor \lnot a\lor d))\lor ((\lnot a)\land (c\lor d)\land
(\lnot b \lor \lnot c \lor \lnot d))$. Using the recursive algorithm for CNF in
the last step above, we can expand and simplify into the DNF:
$(a\lor b\lor c\lor d) \land (\lnot a\lor c\lor d)$

__Theorem (Existance of Normal Forms)__: Any formula $A\in Form(L^p)$ is
tautologically equivalent to a formula in DNF.

_Proof_:

* If $A$ is a contradiction, then $A$ is tautologically equivalent to the DNF
  $p\land \lnot p$, where $p$ is any atom occurring in $A$.
* If $A$ is not a contradiction, then the following method can be used (note
  that this is just a demonstration of the method on an example)

  Suppose that $A$ has three atoms, $p,q,r$ and the value of $A$ is 1 iff $1,1,0$
  or $1,0,1$ or $0,0,1$ are assigned to $p,q,r$ respectively.

  For each of these assignments, we have a conjunctive clause with three
  literals, each being either the atom or its negation, depending on the truth
  value that has been assigned to it. We have the following conjunctive clauses:
  $\;p\land q\land\lnot r$, $\;p\land\lnot q\land r$, $\;\lnot p \land\lnot
  q\land r$. We see that the first of these clauses is true iff $p,q,r$ have
  truth values $1,1,0$, the second is true iff $p,q,r$ have truth values $1,0,1$
  respectively and finally the third is true iff $p,q,r$ have truth values
  $0,0,1$.

  Therefore, the follwing formula in DNF is stautologically equivalent to $A$.
  $(p\land q\land\lnot r)\lor (p\land \lnot q\land r)\lor (\lnot p\land\lnot
  q\land r)$.
* If $A$ is a tautology, then the required DNF may simply be the formula
  $p\lor\lnot p$, where $p$ is any atom occurring in $A$.

This completes the "proof".

The following theorem can also be proven using a similar strategy:

__Theorem__: Any formula $A\in Form(A)$ is tautologically equivalent to a
formula in CNF.

##### DNF from Truth Tables

Note that from the example provided in the proof above shows that it can be
possible to construct the DNF of a formula using just its truth table.
Consider the following truth table for the formula $A$ with three propositional
variables $p,q,r$.

| $p$ | $q$ | $r$ | $A$   |
| --- | --- | --- | ----- |
| 1   | 1   | 1   | __1__ |
| 1   | 1   | 0   | 0     |
| 1   | 0   | 1   | __1__ |
| 1   | 0   | 0   | 0     |
| 0   | 1   | 1   | 0     |
| 0   | 1   | 0   | 0     |
| 0   | 0   | 1   | __1__ |
| 0   | 0   | 0   | 0     |

From this table, it can be seen that the truth valuations under which $A$ is
true are $1,1,1$, $1,0,1$ and $0,0,1$ for $p,q,r$ respectively.
Using the same approach as in the theorem above, we get that

$(p\land q\land r)\lor (p\land \lnot q\land r)\lor (\lnot p\land \lnot q\land r)
\models\!\mid A$

##### CNF from Truth Tables

The process of __complementation__ can be used to obtain conjunctive normal
forms from truth tables. If a formula $A$ only contains the connectives $\land,
\lor, \lnot$, then its __complement__ is the formula formed by replacing all
$\lor$ by $\land$, all $\land$ by $\lor$ and all atoms by their negations.

Using complementation, the complement of the formula $A = (p\land q)\lor\lnot r$
is $\lnot A= (\lnot p\lor\lnot q)\land r$

Note that if a formula is in DNF, then its complement, $\lnot A$, is in CNF.
Therefore, the CNF of a formula $A$ can be obtained from a truth table by first
computing the DNF of $\lnot A$, then taking the complement of that.

## Adequate Sets of Connectives

So far, one unary connective ($\lnot$) and four binary connectives
($\land,\lor,\rightarrow,\iff$) have been introduced. However, there exist many
more connectives. In fact, there are $2^4=16$ possible binary connectives.

In general, for any $n$-ary connective (one that takes $n$ arguments), there are
$2^n$ rows in the truth table for such a connective ($2^n$ truth valuations for
the $n$ arguments to the connective. The number of $n$-ary connectives is equal
to the number of rows in the truth table, times the number of binary numbers of
length (equal to the height of the truth table) $2^n$. So there are $2^{(2^n)}$
$n$-ary connectives.

__Definition__: An _adequate set_ of connectives is one that has the capability
to express all truth tables. It can be shown that the set $\{\lnot, \land, \lor,
\rightarrow, \iff\}$ is an adequate set of connectives. This is also known as
the __standard set of connectives__.

The objective now is to devise a method to show that a set of connectives is
adequate.

### Proofs of Adequacy

__Definition__: The __arity__ of a function, $f$, is the number, $n\geq 0$ of
inputs that the function $f$ takes. Functions with 0 inputs are called
__nullary__. Functions with 1 input are called __unary__. Functions with 2
inputs are called __binary__. A propositional connective, $f$, with arity $n$,
is $f:\{0,1\}^n \mapsto \{0,1\}$.

A set, $S$, of propositional connectives is said to be __adequate for
propositional logic__ if __every__ propositional connective (of any arity) can
be implemented using only the connectives in $S$.

__Theorem__: $\{\lnot, \land, \lor\}$ is an adequate set of connectives.

__Proof__: Fix any $n$-ary function $f:\{0,1\}^n \mapsto \{0,1\}$.
Let $p_1,\dots, p_n$ be the arguments to the function $f$. We shall show that
the function $f$ can be implemented using only the connectives in the given set.

We already know of a method which can be used to do this- from the formation of
Disjunctive Normal Forms.

* Write out the truth table for $f$
* For every row in the truth table, write out a conjunction with $n$ literals-
  the $i$-th one being $p_i$ if, for that row, the $i$-th column equals 1 and
  $(\lnot p)$ otherwise
* Construct a formula $A$ that is the disjunction of all of the conjunctions
  formed from the truth table.

By construction, $A$ has the same truth table as $f$ and so we have managed to
implement $f$ using only the connectives in the given set. Therefore, the set
$\{\lnot, \land, \lor\}$ is adequate for propositional logic. $\blacksquare$

Here is a connective that is itself adequate for propositional logic. The
__Pierce arrow__, denoted $\downarrow$, is defined through the following truth
table:

|$p$|$q$|$p\downarrow q$|
|---|---|---------------|
| 1 | 1 | 0             |
| 1 | 0 | 0             |
| 0 | 1 | 0             |
| 0 | 0 | 1             |

Indeed, the standard set of connectives can be implemented using the Pierce
arrow:

* $\lnot p = p\downarrow p$
* $p\land q = (p\downarrow p)\downarrow (q\downarrow q)$
* $p\lor q = (p\downarrow q)\downarrow (p\downarrow q)$

So, to test whether a set of connectives is adeqate for propositional logic, it
suffices to show that the Pierce arrow can be implemented using that set.

Another one of these beastly connectives is the Sheffer stroke, which is denoted
as $|$. It is defined as follows:

|$p$|$q$|$p$\|$q$|
|---|---|---------------|
| 1 | 1 | 0             |
| 1 | 0 | 1             |
| 0 | 1 | 1             |
| 0 | 0 | 1             |

The Sheffer stroke is also known as NAND (negation of $\land$).
The set of connectives $\{|\}$ is also adequate. This can be shown by
implementing the Pierce arrow using the Sheffer stroke:

* $p\downarrow q = ((p|p)|(q|q))|((p|p)|(q|q))$

### Proofs of Indequacy

Similar to how a connective can be proven adequate, a connective can be proven
inadequate by showing that one or more of the standard connectives cannot be
implemented using the connective.

__Example__: Show that the set of connectives $S=\{\land\}$ is inadequate.

We shall show that $\lnot$ cannot be implemented using the set $S$. Note that a
formula of one variable, say $p$, containing only the connectives in $S$ is such
that if a truth valuation sets $p^t = 0$, then the formula itself must evaluate
to 0.

So, for it to be possible to define the standard $\lnot p$ using $S$, there
needs to exist a formula $A$ with the only propositional variable being $p$ and
the only connective being $\land$ such that $\lnot p \models\!\mid A$. But as
mentioned before, if $p^t = 0$, then $A^t = 0$ too, so $\lnot p$ and $A$ cannot
be tautologically equivalent.

## Formal Deducibility

So far, the methods studied for proving arguments are using truth tables and the
semantics (tautological equivalence, $\models\!\mid$). We now desire to replace
these methods with a purely syntactic one, with rules of deduction that are
entirely syntactic.

We now define a relation called __formal deducibility__, denoted by $\vdash$,
which is intuitively the same as tautological equivalence, but has a different
method of proving the validity of an argument which can be done
mechanically/syntactically.

The word "formal" in this context means that the method is only concerned with
the syntactic form of an argument. Proofs do not refer to any semantic
properties and can be verified mechanically.

The system of proof being used in this document is the system of Natural
Deduction, which is far from the only system of formal proof.

__Conventions__: Here are some conventions to be followed to make notation
easier.

* Formal deducibility is a relationship between a set of formulae (called the
  premises) and a formula $A$ (called the conclusion).
* The symbol $\vdash$ denotes the relationship of formal deducibility between a
  set and a formula. So $\Sigma \vdash A$ asserts that $A$ is formally deducible
  from the set $\Sigma$.
* If $\{A_1,\dots,A_n\}$ is a set of formulae, for notational convenience, the
  curly braces may be elided. So saying $A_1,\dots,A_n$ is equivalent.
* If $\Sigma\cup \{A\}$ is a set, where $A$ is a formula, then set-notational
  syntax may be elided. So saying $\Sigma, A$ is equivalent.
* If $\Sigma$ and $\Sigma^*$ are sets of formulae, then set notation syntax can
  be elided from the expression $\Sigma\cup \Sigma^*$. So $\Sigma,\Sigma^*$ is
  equivalent notation.

### Natural Deduction

A __proof__ is a finite sequence of the form $\Sigma_i \vdash A_i$. Such a
statement is called a __sequent__.

A proof is considered to be valid if every sequent in the sequence of sequents
in the proof is created from previous sequents according to a specified proof
rule. These rules shall be introduced soon.

Also, a __theorem__ is a sequent that occurs in a valid proof (usually the last).

Now, here are the rules of natural deduction. Each of $A,B,C$ is any formula and
$\Sigma$ is any set of formulae.

1. $\text{(Ref)}$ is the rule of __Reflexivity__. It says that $A\vdash A$ is a
   theorem.
2. $(+)$ is the rule of __Addition of Premises__. It states that if $\Sigma
   \vdash A$ is a theorem, then so is $\Sigma, \Sigma^* \vdash A$.
3. $(\lnot +)$ is the rule of __$\lnot$ elimination__. It states that if
   $\Sigma, \lnot A \vdash B$ and $\Sigma, \lnot A \vdash \lnot B$ are theorems,
   then $\Sigma \vdash A$ is a theorem.
4. $(\rightarrow -)$ is the rule of __$\rightarrow$ elimination__. It states
   that if $\Sigma \vdash A \rightarrow B$ and $\Sigma \vdash A$ are theorems,
   then $\Sigma \models B$ is a theorem.
5. $(\rightarrow +)$ is the rule of __$\rightarrow$ introduction__. It states
   that if $\Sigma, A\vdash B$ is a theorem, then $\Sigma\vdash A\rightarrow B$
   is a theorem.
6. $(\land -)$ is the rule of __$\land$ elimination__. It states that if $\Sigma
   \vdash A\land B$ is a theorem, then $\Sigma \vdash A$ and $\Sigma \vdash B$
   are theorems.
7. $(\land +)$ is the rule of __$\land$ introduction__. It states that if
   $\Sigma \vdash A$ and $\Sigma \vdash B$ are theorems, them $\Sigma\vdash
   A\land B$ is a theorem.
8. $(\lor -)$ is the rule of __$\lor$ elimination__. It states that if $\Sigma,
   A \vdash C$ and $\Sigma, B \vdash C$ are theorems, then $\Sigma, A\lor B
   \vdash C$ is a theorem.
9. $(\lor +)$ is the rule of __$\lor$ introduction__. It states that if
   $\Sigma\vdash A$ is a theorem, then $\Sigma\models A\lor B$ and $\Sigma\vdash
   B\lor A$ are theorems.
10. a) $(\iff -)$ is the rule of __$\iff$ elimination__. It states that if $\Sigma
    \vdash A\iff B$ and $\Sigma \vdash A$ are theorems, then $\Sigma \vdash B$
    is a theorem.

    b) $(\iff -)$ is the rule of __$\iff$ elimination__. It states that if $\Sigma
    \vdash A\iff B$ and $\Sigma \vdash B$ are theorems, then $\Sigma \vdash A$
    is a theorem.
11. $(\iff +)$ is the rule of __$\iff$ introduction__. It states that if
    $\Sigma, A \vdash B$ and $\Sigma, B \vdash A$ are theorems, then $\Sigma
    \vdash A\iff B$ is a theorem.

__Example__: This is called the __membership rule__. It states that if $A\in
\Sigma$, then $\Sigma\vdash A$ is a theorem.

The membership rule, when used, will now be cited as $(\in)$.
This now shows how to prove a theorem using the method of formal deduction.

__Proof__: Assume that $A\in \Sigma$ and let $\Sigma^* = \Sigma \setminus
\{A\}$. So $\Sigma^*, A = \Sigma^* \cup A = \Sigma$.

$\begin{aligned}
&1.\quad A \vdash A &(\text{Ref})\\
&2.\quad A,\Sigma^* \vdash A &\text{by (+) on 1}\\
\blacksquare
\end{aligned}$

In the above proof, line 1 is generated using the $\text{(Ref)}$ rule and this
is cited to its right. Then, line 2 is generated using line 1, by the $(+)$
rule which is the addition of premises and this is cited to its right again.
These citations are important because they provide justification for each step.
Note that citations can only be made to previous lines in the proof.
These steps provide a _formal proof_ for the statement $\Sigma \vdash A$ and so
it is now a theorem.

__Example__: Prove that $A\rightarrow B, B\rightarrow C \vdash A \rightarrow C$.
Here is a formal proof for this statement.

$\begin{aligned}
&1.\quad A\rightarrow B, B\rightarrow C, A \vdash A\rightarrow B &(\in)\\
&2.\quad A\rightarrow B, B\rightarrow C, A \vdash A &(\in)\\
&3.\quad A\rightarrow B, B\rightarrow C, B \vdash B &(\rightarrow -)\text{ on
1,2}\\
&4.\quad A\rightarrow B, B\rightarrow C, A \vdash B\rightarrow C &(\in)\\
&5.\quad A\rightarrow B, B\rightarrow C, A \vdash C &(\rightarrow -)\text{ on
4,3}\\
&6.\quad A\rightarrow B, B\rightarrow C \vdash A \rightarrow C &(\rightarrow +)
\text{ on 5}
\end{aligned}$

In this proof, the membership rule, $(\in)$, was used as a lemma. This is
possible because the rules of natural deduction and theorems are just schemas
for a proof. So instead of executing each of the steps in the proof of the
lemma, it suffices to cite the lemma, which is a theorem.

Note that in the above proof, it was also possible to reorder the lines, as long
as they all cite previous lines.

#### Some Intuition

* $(\lnot -)$ is the proof schema for an indirect proof/a proof by
  contradiction. If a contradiction, which, in the rules, is $B$ and $\lnot B$
  can be deduced from the set $\Sigma$, with an additional false premise (one
  that does not hold), $\lnot A$, then this proposition is deducible from the
  set: $\Sigma \vdash A$.
* $(\lor -)$ is the proof schema for a proof by cases. If $C$ follows from $A$
  and $C$ also follows from $B$, then $C$ follows from $A\lor B$.
* $(\rightarrow +)$ is the proof schema used to prove an implication. In order
  to prove $A\rightarrow B$ with a certain set of premises i.e. to prove
  $\Sigma \vdash A\rightarrow B$, one should assume $A$ (by adding it to the
  premises) and try to prove $B$ i.e. $\Sigma, A \vdash B$.

__Definition__: Here is a complete formal definition for __formal
deducibility__. A formal deduction system such as Natural Deduction is specified
by a set of deduction rules.

A formula $A$ is __formally deducible__ from $\Sigma$ (denoted as $\Sigma \vdash
A$) iff $\Sigma \vdash A$ is generated by a finite numeber of applications of
the rules of the system. So $\Sigma \vdash A$ holds iff there exists a finite
sequence:

$\begin{aligned}
(1) \Sigma_1 &\vdash A_1\\
&\vdots\\
(n) \Sigma_n &\vdash A_n
\end{aligned}$

such that the following are satisfied:

* Each sequent $\Sigma_i \vdash A_k$ (for $1\leq k \leq n$) is generated by one
  rule of formal deduction from the sequents that preceed it
* The final sequent $\Sigma_n \vdash A_n$ is the desired $\Sigma\vdash A$ i.e.
  $\Sigma_n = \Sigma$ and $A_n = A$.

The above sequence of sequents is called a __formal proof__ of its last sequent
i.e. $\Sigma_n \vdash A_n$.

Both formal deducibility and $Form(L^p)$ are constructed inductively and one can
observe that formulae correspond to schemes of proof and the rules of formation
correspond to the rules of formal deduction.

__$\Sigma \models A$ VS $\Sigma \vdash A$__: There is a difference between
consequence and formal deducibility.

* Tautological consequence is concerned with semantics while formal
  deducibility is concerned with syntax (Remeber: syntax is to form while
  semantics is to meaning).
* The connection between tautological consequence and implications is that
  "$A\models B$ iff $A\rightarrow B$ is a tautology".
* The connection between formal deducibility and implications is that "$A\vdash
  B$ iff $\emptyset\vdash A\rightarrow B$".
