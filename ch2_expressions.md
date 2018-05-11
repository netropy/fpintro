## 2.0 Expressions

This chapter contains exercises on how to write
[expressions](https://en.wikipedia.org/wiki/Expression_(computer_science)).
Most coding exercises are from the tutorial
[Klipse for Kids](http://kids.klipse.tech)
with answers given here in Clojure and Scala; also added is an excercise for boolean operations.

For a summary of Clojure's and Scala's expression syntax, see
[below](#21-summary) or look up these "cheat-sheets":
[Clojure](https://clojure.org/api/cheatsheet),
[Clojure and other Lisp dialects](http://hyperpolyglot.org/lisp),
[Scala](https://docs.scala-lang.org/cheatsheets),
[Scala-to-Java](http://rea.tech/java-to-scala-cheatsheet).

#### 2.0.1 Write arithmetic expressions: [exercise KfK, chapter 1: What is computer programming?](http://kids.klipse.tech/clojure/2016/05/03/programming-kids-1.html)

Write an expression that calculates ...

Exercise | Clojure | Scala
:-------|:------|:------
7*8 | `(* 7 8)` | `7 * 8`
2\*3\*4\*5 | `(* 2 3 4 5)` | `2*3*4*5`
2+3+4+5 | `(+ 2 3 4 5)` | `2+3+4+5`

___Notes:___

* Clojure uses
  [_prefix notation_](https://en.wikipedia.org/wiki/Polish_notation): `(operator operand operand)`
* Scala supports the familiar
  [_infix notation_](https://en.wikipedia.org/wiki/Infix_notation): `operand operator operand`.
* Clojure: multiple operands allowed for `+`, `*` ... operator.
* Scala: a blank (or other
  [white space characters](https://en.wikipedia.org/wiki/Whitespace_character)) between the operator and its operands is optional (but preferred).

___Further Reading:___

* [operator](https://en.wikipedia.org/wiki/Operator_(computer_programming))

#### 2.0.2 Write nested arithmetic expressions: [exercise KfK, chapter 2: Expressions inside Expressions inside Expressions](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-2.html).

Write this calculation as arithmetic expression ...
1. add 10 to 12 and multiply the result by 3
2. add 7 to 9 and multiply the result by 5
3. multiply 7 and 9 and add 6 to the result
4. multiply 7 and 9 and add 6 and 9 to the result
5. add 7 to 9 and multiply the result by 5 and by 3
6. add 7 to 9 and multiply the result by 3 plus 8 plus 9

Exercise | Clojure | Scala
:-------|:------|:------
1\. | `(* (+ 10 12) 3)` | `(10 + 12) * 3`
2\. | `(* (+ 7 9) 5)` | `(7 + 9) * 5`
3\. | `(+ (* 7 9) 6)` |`(7 * 9) + 6` or `7 * 9 + 6`
4\. | `(+ (* 7 9) 6 9)` | `(7 * 9) + 6 + 9`
5\. | `(* (+ 7 9) 5 3)` | `(7 + 9) * 5 * 3`
6\. | `(* (+ 7 9) (+ 3 8 9))` | `(7 + 9) * (3 + 8 + 9)`

___Notes:___

* Expressions may contain sub-expressions.
* [Parentheses or round brackets](https://en.wikipedia.org/wiki/Bracket#Parentheses_.28_.29) are needed to express grouping and order of operations.
* However, precedence rules for operators may mitigate the need for parentheses.

___Further Reading:___

* [Infix notation](https://en.wikipedia.org/wiki/Infix_notation)
  is most common among programming languages (since familiar from mathematics) and comes with rules for
  [operator precedence](https://en.wikipedia.org/wiki/Order_of_operations) and
  [associativity](https://en.wikipedia.org/wiki/Associative_property).
* [Prefix notation](https://en.wikipedia.org/wiki/Polish_notation)
  is characteristic for languages derived from 
  [Lisp](https://en.wikipedia.org/wiki/Lisp).
* [Postfix notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation)
  eliminates the need for parentheses (if the operators'
  [arity](https://en.wikipedia.org/wiki/Arity) is predetermined), which allows for a
  [pocket calculator without keys for round brackets](https://en.wikipedia.org/wiki/HP-35).
* Infix, prefix, and postfix notations can be
  [converted into another](https://en.wikipedia.org/wiki/Shunting-yard_algorithm).

#### 2.0.3 Write and use named expressions: [exercise KfK, chapter 3: Giving Names to Expressions](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-3.html).

It is often useful to assign expressions a name.  A name carries a meaning and it can be referenced multiple times, thus, giving a single definition for a "common subexpression".

Factor out common subexpressions among these examples by assigning them to a constant ...
1. (4 + 7 + 8)\*3 + (4 + 7 + 8)\*7 + (4 + 7 + 8)\*9
2. (2\*3 + 4)\*3 + (2\*3 + 4)\*7 + (2\*3 + 4)\*9
3. (2\*3 + 4\*5) \* (4 + 5)
4. (2\*3 + 4\*5) \* (4 + 5) \* 19

Exercise | Clojure | Scala
:-------|:------|:------
1\. | `(def a (+ 4 7 8))` | `val a = 4 + 7 + 8`
...     | `(+ (* a 3) (* a 7) (* a 9))` | `a * 3 + a * 7 + a * 9`
...     | `(* a (+ 3 7 9))` | `a * (3 + 7 + 9)`
...     | `(def z (+ 3 7 9))` | `val z = (3 + 7 + 9)`
...     | `(* a z)` | `a * z`
2\. | `(def b (+ (* 2 3) 4))` | `val b = 2 * 3 + 4`
...     | `(+ (* b 3) (* b 7) (* b 9))` | `b * 3 + b * 7 + b * 9`
...     | `(* b (+ 3 7 9))` | `b * (3 + 7 + 9)`
...     | `(* b z)` | `b * z`
3\. | `(def c (* (+ (* 2 3) (* 4 5)) (+ 4 5)))` | `val c = (2 * 3 + 4 * 5) * (4 + 5)`
4\. | `(* c 19)` | `c * 19`

___Notes:___

* Compared to Clojure, there is a less of a need for round brackets in Scala (see cartoon below ;-)
* In Clojure, the operator `def` defines a global variable.  (There's also an operator for binding a local variable is called `let`).
* In Lisp-based languages, assigning a name to an expression is itself an expression with an operator doing the naming and taking as operands the name and the named expression.
* In Scala, keyword `val` names a constant value.  (There's also the keyword `var` to define a variable, which may be re-assigned new values.)
* Programming languages typically adopt (more or less strict) conventions about how to form and capitalize composite names, for example:

Example | Informal letter case name | Prevalent in
:-----|:-----|:-----
`no-of-widgets` | [kebab case](https://en.wikipedia.org/wiki/Letter_case#Special_case_styles) | Lisp, Clojure
`no_of_widgets` | [snake case](https://en.wikipedia.org/wiki/Snake_case) | C, C++
`noOfWidgets` | [camel case](https://en.wikipedia.org/wiki/Camel_case) | Java, Scala, C++

___Further Reading:___

* Conventions for names or code formatting are typically captured by general language
  [style guides](https://en.wikipedia.org/wiki/Style_guide),
  which are often overlaid by additional rules specific to projects, companies, or developers.
* Take a peek at these widely used style guides for
  [Clojure](https://github.com/bbatsov/clojure-style-guide) and
  [Scala](https://docs.scala-lang.org/style).

#### 2.0.4 Write `list` expressions: [exercise KfK, chapter 4: Evaluating Several Expressions](http://kids.klipse.tech/clojure/2016/06/21/programming-kids-4.html).

[Lists](https://en.wikipedia.org/wiki/List_(abstract_data_type)) define a collection of values in which the order of elements counts and multiples are allowed.

Compose a list of ...
1. the numbers 1, 2, 3, 4 and 9
2. 2\*3, 2\*4 and 2\*5
3. the ages of your siblings or friends
4. a list of the ages of your siblings or friends followed by the age differences between them and you
5. a list of the ages of your siblings or friends and a list of the age differences between them and you

Exercise | Clojure | Scala
:-------|:------|:------
1\. | `(list 1 2 3 4 9)` | `List(1, 2, 3, 4, 9)`
... | `;; => (1 2 3 4 9)` | `// => List(1, 2, 3, 4, 9)`
2\. | `(list (* 2 3) (* 2 4) (* 2 5))` | `List(2 * 3, 2 * 4, 2 * 5)`
... | `;; => (6 8 10)` | `// => List(6, 8, 10)` |
3\. | `(def ages (list 12 7 7))` | `val ages = List(12, 7, 7)`
... | `;; #'user/ages` | `// => ages: List[Int] = List(12, 7, 7)`
4\. | `(list ages 3 10 10)` | `List(ages, 3, 10, 10)`
... | `;; => ((12 7 7) 3 10 10)` | `// => List(List(12, 7, 7), 3, 10, 10)`
5\. | `(list ages (list 3 10 10))` | `List(ages, List(3, 10, 10))`
... | `;; => ((12 7 7) (3 10 10))` | `// => List(List(12, 7, 7), List(3, 10, 10))`

___Notes:___

* Lists may contain lists.
* In Clojure, a list is constructed as `(list ...)` with elements separated by a space.
* In Scala, a list is constructed as `List(...)` with elements separated by a comma.
* In Scala, functions and operators are usually written in lower case, while data types (eg. `Int`, `Boolean`, `List`...) are written in upper case.
* Creating a list is itself an expression with `list` or `List` as operator followed by the list elements as operands.

___Further Reading:___

* Refresher (mathematics):
  [sets](https://en.wikipedia.org/wiki/Set_(abstract_data_type)) vs.
  [lists](https://en.wikipedia.org/wiki/List_(abstract_data_type)) vs.
  [tuples](https://en.wikipedia.org/wiki/Tuple)
  - sets: homogeneous, no order, no multiples: `{ 1 2 } = { 2 1 } = { 2 2 1 }`
  - lists: homogeneous, order counts, multiples allowed: `(list 2 1) != (list 1 2) != (list 1 2 2)`
  - tuples: heterogeneous, order counts, multiples allowed: `(1, 2, 'a') != ('a', 2, 1) != (2, 2, 1, 'a', 'a')`

* Scala, Clojure, and most languages also provide other, predefined collection types, for example:
  [arrays or vectors](https://en.wikipedia.org/wiki/Array_data_structure) or
  [maps](https://en.wikipedia.org/wiki/Associative_array).

* Refresher (mathematics):
  [elements](https://en.wikipedia.org/wiki/Element_(mathematics)),
  [empty set](https://en.wikipedia.org/wiki/Empty_set),
  [subsets](https://en.wikipedia.org/wiki/Subset),
  [power sets](https://en.wikipedia.org/wiki/Power_set),
  [set operations](https://en.wikipedia.org/wiki/Algebra_of_sets),
  [Cartesian product](https://en.wikipedia.org/wiki/Cartesian_product)

Example | Meaning
:-----|:-----------------------------
`{ 1 2 3 }` | has 3 elements: `1`, `2`, and `3`
`{ {1} {2 3} }` | has 2 elements: inner set `{1}`, inner set `{2 3}`
`{ 1 }` | has 2 subsets: `{}`, `{1}`
`{ 1 2 3 }` | has a power set of 8 elements: `{ {} {1} {2} {3} {1 2} {2 3} {1 3} {1 2 3} }`
`{} ` | has no elements, i.e., is the empty set `{}`
`{1} ` | has 1 element: `1`
`{ {} }` | has 1 element: the empty set `{}`
`{ { {} } }` | has 1 element: a set with 1 element that contains the empty set `{}`
`{ 1 2 } X { 3 4 5 }` | is a Cartesian product of 6 elements: `{ (1,3) (1,4) (1,5) (2,3) (2,4) (2,5) }`

#### 2.0.5 Write expressions without evaluating them: [exercise KfK, chapter 5: Please, tell me "what's your name?"](http://kids.klipse.tech/clojure/2016/07/21/chapter-5.html).

A function of quotes in human languages is to indicate when to take an expression literally instead of by its meaning.
Similarly, programming languages offer constructs to refer to an expression "as it is", that is, without evaluating it.

Form and refer to the expression as it is ...

Exercise | Clojure | Scala
:-------|:------|:------
`3 + 4` as it is | `(quote (+ 3 4))` | |
... | `'(+ 3 4)` _(alternative notation)_ |
... | `#(+ 3 4)` _(as a function)_ | `() => 3 + 4` |
`(+ 3 4)` as it is, then evaluate | `(eval (quote (+ 3 4)))` | |
... | `(eval '(+ 3 4))` _(alternative notation)_ | |
... | `(#(+ 3 4))` _(as a function)_ | `(() => 3 + 4)()` |

___Notes:___

* In Clojure and Scala, preventing the evaluation of an expression is itself an expression.
* In Clojure (and other Lisp-based languages), an operator
  - [`quote`](https://clojuredocs.org/clojure.core/quote)
    indicates not to evaluate the subsequent expressions; often, the short form `'( ...)` for `(quote ...)` is preferred.
  - [`eval`](https://clojuredocs.org/clojure.core/eval) submits form data to the interpreter for evaluation and returns the result.
* Quoting of expressions is not directly applicable to Scala.
  However, a general language construct (available in both Clojure and Scala) is to describe computations as _lambdas_ or _anonymous functions_ taking no arguments, see
  [Formulas and Functions](ch3_1_formulas_and_functions.md) for notes and exercises.

#### 2.0.6 Write comparison operator expressions: [exercise KfK, chapter 7: True or False (Pinocchio)](http://kids.klipse.tech/clojure/2016/08/05/chapter-7.html).

Programming languages offer predefined operators to compare values for whether they are _equal_ and _not equal_.  Numbers (and other data types) can be further compared by _less than_, _less/equal than_, _greater than_, and _greater/equal than_.

Ask if 7 times 6 ...

Exercise | Clojure | Scala
:-------|:------|:------
equals 40 | `(= (* 7 6) 40)` | ` 7 * 6 == 40 `
is less than 40 | `(< (* 7 6) 40)` | ` 7 * 6 < 40 `
is less/equal than 40 | `(<= (* 7 6) 40)` | ` 7 * 6 <= 40 `
is greater/equal than 40 | `(>= (* 7 6) 40)` | ` 7 * 6 >= 40 `
is greater than 40 | `(> (* 7 6) 40)` | ` 7 * 6 > 40 `
is not equal to 40 | `(not= (* 7 6) 40)` | ` 7 * 6 != 40 `

___Further Reading:___

* [relational operator](https://en.wikipedia.org/wiki/Relational_operator)
* (mathematics:) [equality](https://en.wikipedia.org/wiki/Equality_(mathematics)),
  [inequality](https://en.wikipedia.org/wiki/Inequality_(mathematics)), and
  [order relationships](https://en.wikipedia.org/wiki/Order_theory).

#### 2.0.7 Write boolean operator expressions.

The [Boolean data type](https://en.wikipedia.org/wiki/Boolean_data_type)
consists of just two values `true` and `false`.
Expressions yielding a Boolean value can be combined by logical operators such as
[_not_ (negation)](https://en.wikipedia.org/wiki/Negation),
[_and_ (conjunction)](https://en.wikipedia.org/wiki/Logical_conjunction),
[_or_ (disjunction)](https://en.wikipedia.org/wiki/Logical_disjunction).
How these operators "work" can be easily seen by their so-called
[_truth tables_](https://en.wikipedia.org/wiki/Truth_table),
which shows the 2, respectively 4  `true`/`false` combinations for their operands.

Form the expressions below and compare them to `true` or `false` such that the result is `true` ...

Exercise | Clojure | Scala
:-------|:------|:------
not true | `(= (not true) false)` | `!true == false`
not false | `(= (not false) true)` | `!false == true`
true and true | `(= (and true true) true)` | `(true && true) == true`
true and false | `(= (and true false) false)` | `(true && false) == false`
false and true | `(= (and false true) false)` | `(false && true) == false`
false and false | `(= (and false false) false)` | `(false && false) == false`
true or true | `(= (or true true) true)` | `(true \|\| true) == true`
true or false | `(= (or true false) true)` | `(true \|\| false) == true`
false or true | `(= (or false true) true)` | `(false \|\| true) == true`
false or false | `(= (or false false) false)`) | `(false \|\| false) == false`

___Notes:___

* The `&&` and `||` operators in Scala (and other languages) have lower precedence than `==` or `!=`.
  The round brackets are therefore needed in above code answers.
* For example, `false && false == false` is inferred as `false && (false == false)` yielding `false`;
  compare to the intended expression `(false && false) == false` yielding `true`.

___Further reading:___

* Scala (and other languages) offer the addititional operators `&` and `|` as (bitwise) _and_ and _or_ besides the (logical) `&&` and `||`.  The "single" and "double" letter operators differ in their so-called
  [_strictness_](https://en.wikipedia.org/wiki/Strict_function): versions `&` and `|` are
  [_eager_](https://en.wikipedia.org/wiki/Eager_evaluation) in that they always evaluate _both_ their operands.
  If the evaluation of the `op2` in `op1 & op2` or `op1 | op2` yields an error, the entire expression results in an error.
* In contrast, the logical Scala operators `&&`, `||` and the Clojure operators `and`/`or` are
  [_lazy_](https://en.wikipedia.org/wiki/Lazy_evaluation): the 2nd operand will not be evaluated once `op1` already decides the outcome.
  That is, for `false & (...)` and `true | (...)`, any expression `(...)` will not even be evaluated, so, any error there would not be raised.  This is also called
  [short-circuit_evaluation](https://en.wikipedia.org/wiki/Short-circuit_evaluation).
* Besides logical _not_, _and_, _or_, there are more boolean operators called _xor_, _nand_, _nor_, and _implies_, whose behaviour is also easily seen by their
  [truth table](https://en.wikipedia.org/wiki/Truth_table).
* For a general discussion of all boolean operators and their inter-relationship, see
  [Boolean algebra](https://en.wikipedia.org/wiki/Boolean_algebra).

### 2.1 Summary

In programming languages, _expressions_ ...

* _evaluate_ to a value, for example: `3 + 4` or `(+ 3 4)` yield `7`;
* may consist of _primitive values_ (or _atoms_, i.e., non-lists), for example: `3`;
* may consist of _operators_ and _operands_, for example: above, operator `+` with operands `3` and `4`;
* are _well-formed_, for example: `1 +` or `(+ 1 2` are illformed as they lack an operand or a round bracket;
* can be _nested_, for example: `3 * (4 + 5)` or `(* 3 (+ 4 5))` contain the sub-expressions `3` and `4 + 5` or `(+ 4 5)`;
* may be _assigned a name_, for example: `val a = 3 + 4` or `(def a (+ 3 4))` define a constant `a`;
* may _reference names_, for example: `(a + 2) * (a - 4)` or `(* (+ a 2) (- a 4)` use a constant (or variable) `a`;
* may _group_ multiple values as lists (or other collections), for example: `List(1, 3, 1)` or `(list 1 3 1)` contain the numbers 1, 3, 1 in that order;
* may just _construct_ expressions, for example: `() => 3 + 4`, `#(+ 3 4)`, `'(+ 3 4)` or `(quote (+ 3 4))` construct but won't perform the calculation `3 + 4`;
* may call for _evaluating_ a constructed expression, for example: `(() => 3 + 4)()`, `(#(+ 3 4))`, `(eval '(+ 3 4))` or `(eval (quote (+ 3 4)))` evaluate to `7`;
* may compare values and combine _propositions_, for example: `(a > 5) && (b <= 0)` or `(and (> a 5) (<= b 0))` state that both, `a > 5` and `b <= 0`, must be true.

___Further reading:___

* In [Lisp](https://en.wikipedia.org/wiki/Lisp)-based languages, expressions (or so-called _s-expressions_, _sexprs_, or _sexps_ for
  [symbolic expressions](https://en.wikipedia.org/wiki/S-expression)) take the form of a
  [_list_](https://en.wikipedia.org/wiki/List_(abstract_data_type)),
  typically, with an operator as the 1st element followed by zero or more operands.
* Languages in which "code" looks similar to "data" (in general, where code resembles its
  [abstract syntax tree](https://en.wikipedia.org/wiki/Abstract_syntax_tree)) are called
  [homoiconic](https://en.wikipedia.org/wiki/Homoiconicity).

![](https://imgs.xkcd.com/comics/lisp_cycles.png)

-------

[<-- previous page](ch1_motivation.md)

[--> next page](ch3_0_functions.md)
