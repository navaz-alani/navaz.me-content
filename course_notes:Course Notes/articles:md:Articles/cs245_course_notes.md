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

$\implies$ Socrates is mortal

This is an example of a good reasoning/argument because it is truth perserving
i.e. if the premises 1 and 2 are `true`, then the conclusion must also be
`true`. The correctness of the argument depends purely upon its form, not
content. The form can be viewed as the high-level structure of the argument.
Another one of the Aristotelian syllogisms:

1. All Accords are Hondas
2. All Hondas are Japanese

$\implies$ All Accords are Japanese

As you can see, the high-level structure of this argument is the same, which is
why it holds as long as the propositions are `true`. The general form of these
__hypothetical syllogisms__ is:

1. All $x$ are $y$
2. All $y$ are $z$

$\implies$ All $x$ are $z$

This is an example of a good argument. What about this one?

1. All $x$ are $y$
2. Some $y$ are $z$

$\implies$ Some $x$ are $z$

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

$\implies$ Some Cuyahoga river water is not pure

This is a __valid argument__, which is one in which whenever the premises are
`true`, the conclusion is also true. Convince yourself that this argument holds.

* Logic essentially studies the "forms" of reasoning (the high-level structure).
As mentioned before, the content of the arguments may deal with anything.
* Learning logic is learning the tools of reasoning applicable to any discipline.

Have a look at this argument:

1. No pure water is burnable
2. Some Cuyahoga river water is not burnable

$\implies$ Some Cuyahoga river water is pure

This argument is invalid (incorrect/unsound). There could be a case where the
whole river is polluted by non-burnable pollutant- it works under the assumption
that all unburnable water is pure. Here is another one:

1. If demand rises, companies expand
2. If companies expand, companies hire more workers

$\implies$ If demand rises, companies hire more workers.

__NOTE__: One may argue against the conclusion but as soon as the premises are
accepted to be `true`, the conclusion must also be `true`. In such cases, the
conclusion is said to _logically follow from the premises_, or that the
_argument is valid (correct/sound)_.

Another argument:

1. This computer program has a bug or the input is erroneous
2. The input is not erroneous

$\implies$ This computer program has a bug

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

$\implies$ If $p$, then $r$

This kind of argument is called a __hypothetical syllogism__ and it is a valid
argument (it is truth preserving/the reasoning is sound).

The "computer bug" example has this high-level structure:

1. $p$ or $q$
2. $q$

$\implies$ $p$

This kind of argument is called a __disjunctive syllogism__. The word disjunction
and its derivatives refer to something to do with the connector `or`.

Here's another argument which is called __modus ponens__.

1. If $p$, then $q$
2. $p$

$\implies$ $q$

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

__Conventions__: Stating a proposition in English implies that it is True.

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
* In logic, every statement must have its own subject and its own predicate
* .
Now taking $p =$ "He eats" and $q =$ "he drinks", our sentence becomes $p\wedge q$
* Sometime, we use words other than "and" to denote a conjunction: "but", "in
addition to" and "moreover"
* Not all instances of "and" are for conjunction: "Jack and Jill are cousins".
In this case "and" is not a conjunction at all.

__DISJUNCTION__: (Definition) Let $p$ and $q$ be propositions. Then, $p lor q$
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
$p\implies q$ is False if $p$ is True and $q$ is False and $p\implies q$ is
True otherwise.

* $p\implies q$ is called the _logical implication_ of $p$ and $q$
* $p\implies q$ may be translated to English using `if ..., then ...` to
"it is not the case that $p$ is True and $q$ is False".
* $p$ is called the _antecedent_
* $q$ is called the _consequent_

Truth table for implication:

| $p$ | $q$ | ($p\implies q$) |
| --- | --- | :-------------: |
| 1   | 1   |        1        |
| 1   | 0   |        0        |
| 0   | 1   |        1        |
| 0   | 0   |        1        |

_Observations_:

* If $p$ is False, then $q$ is _vacuously True_ since in such a case, the
verification of $p\implies q$ does not require anything to deduce $q$ from $p$.
Although this may seem unusual, this does not yield any inconsistency with
everyday speech:

> "If the sun will rise from the West, then I will eat my hat"

This statement will never be contradicted and in that sense, it is True. A
contradiction is not possible because "The sun will rise from the West" is
False. The following are logically equivalent:

* $p\implies q$
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
4. $\implies$ is not symmetric. $p\implies q$ and $q\implies p$ have different
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

### Syntax of $L^p$

$L^p$ is the formal language of propositional logic and it is composed of the
following symbols:

* Propositional variables: $p,q,r,\dots$ (with or without subscripts) represent
  propositions, as previously discussed
* Logical Connectives: $\lnot, \land, \lor, \implies, \iff$ as previously
  discussed

The following are laguage specifications, with introduction of terminology:

* __Expressions__: finite length strings of symbols in $L^p$. All of
  $p, pq, (r), (p\land \implies q)$ are expressions in the $L^p$ language.
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

### Well-formed Formulae

__Definition__: An __atom (atomic formula)__ is an expression consisting of a
prepositional variable only. The set of atomic formulae in $L^p$ is denoted by
$Atom(L^p)$.

__Definition__: An   expression in $L^p$is called a __formula__ (a well-formed
propositional formula) iff it can be constructed according to the following
_rules of formation_:

1. Every atomic formula is a formula
2. If $A$ is an atomic formula, then so it $(\lnot A)$
3. If $A,B$ are formulae, then so are
   $(A \land B), (A \lor B), (A \implies B), (A \iff B)$

the set of all formulae in $L^p$ is denoted by $Form(L^p)$. It is the smallest
class of expressions of $L^p$ that contains $Atom(L^p)$ and is closed under the
formation rules of formulae.

__Example__: Generating formulae.

Let $F = ((p\lor q) \implies ((\lnot p) \iff (p \land q)))$ be an element in
$Form(L^p)$ and $p,q,r$ are elements in $Atom(L^p)$. How is $F$ generated from
the rules of formation?

By rule 1, the atomic propositional variables are themselves formulae.
With these propositional variables, one can form the formulae $A = (p\lor q)$,
$B = (p\land q)$, using rule 3. Another formula, $C = (\lnot p)$ can be formed
by rule 2 applied to $p$. Then, $D = (C \iff B)$ can be formed by rule 3.
Finally, $F = (A \implies D)$ can be formed using rule 3 yet again.

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

$((p\implies (q\land r)) \land ((\lnot p) \implies s))$

__Parse Trees__: A parse tree can be used to analyse formulae too. Have a look
at the parse tree of $((p \land (\lnot q)) \implies r)$ (Forgive my directory
structure rendering of a parse tree).

$((p \land (\lnot q)) \implies r)$  
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
six forms: an atom, $(\lnot A)$, $(A\land B)$, $(A \lor B)$, $(A\implies B)$
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

$\implies$ We may conclude that every natural number greater than or equal to
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
$\star$ is one of $\land, \lor, \implies, \iff$). Formulae $A,B$ have smaller
$n$ values than $(\lnot A)$ and $(A\star B)$.

We concoct a principle of induction which can be used in this case:

#### Structural Induction

The __Principle of Structural Induction__ says: Suppose $R$ is a property. If:

1. For any atomic formula $p$ in $Atom(L^p)$, $R$ holds for $p$
2. For any formula $A$ in $Form(L^p)$, if $R(A)$, then $(\lnot A)$ has property
   $R$ too
3. For all formulae $A,B$ in $Form(L^p)$, if $R(A)$ and $R(B)$, then
   $(A\star B)$ (where $\star$ is one of $\land, \lor, \implies, \iff$) has
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
$F=((p\land q) \implies r)$. We want to show that this is an implication and
not a conjunction. Let's do both to see where parsing the formula as a
conjunction fails.

If we parse the formula in $F$ as an implication, it would look something like:
let $A=(p\land q)$ and $B=r$, then $F=(A\implies B)$, where $A$ and $B$ are
well-formed formulae in $L^p$ (one can check by following the rules of
formation until the formula has been constructed from the atoms $p,q,r$).

Now, if we try to parse the formula as a conjunction, here is what it would
look like: let $A'=(p$ and $B'=q) \implies r$, and $F=(A'\land B')$. However,
this is not a valid parse since $A'$ and $B'$ are not valid formulae (by the
lemma just proven above about equal number of left and right parentheses in a
well-formed formula in $L^p. They also fail to be constructible from the rules
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
implies that $B'=B$ (and also $C'=C$). Therefore, the two decompositions of $A$
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

$\dagger$ $(A \implies B)$ is called a implication formula

$\dagger$ $(A \iff B)$ is called an equivalence formula

... and each is exactly of one kind.

This is important, as stated before, because the meaning of these formulae is
going to be derived from their syntax, so this ensures unambiguity.

#### Connective Precedence

For human beings, the following precedence rules are established:

* $\lnot$ takes precedence over $\land$
* $\land$ takes precedence over $\lor$
* $\lor$ takes precedence over $\implies$
* $\implies$ takes precedence over $\iff$

This allows some parentheses to be elided without loss of meaning or ambiguity:

$p\iff q \implies r$ can be expanded, using these precedence rules, to be
$((p\iff q) \implies r)$.

#### Scope

* If $A$ is of the form $(\lnot B)$, then we say that $B$ is the
  _scope of negation_ in $A$.
* If $A$ is of the form $(B\star C)$ (where $\star$ is a binary logical
  connective), then we say that $B$ is the _left scope_ of the connective
  (disjunction/conjunction/...) in $A$ and $C$ is the _right scope_ of the
  connective in $A$.
