# Intro to Logic and Computation Course Notes

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
| 1   | 0   |        1        |
| 0   | 1   |        0        |
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
