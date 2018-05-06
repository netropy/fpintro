## 2.0 Expressions

This chapter contains exercises on how to write [expressions](https://en.wikipedia.org/wiki/Expression_(computer_science)).  Most exercises are from the great tutorial [Klipse for Kids](http://kids.klipse.tech) with some added for boolean operations.

In summary, _expressions_ ...

* _evaluate_ to a value, when computed, for example: `3 + 4` yields `7`,
* consist of _operators_ and _operands_ yielding values, for example: `2 + 3` evaluates to `5`,
* are _well-formed_, for example: `1 +` is illformed as it lacks an operand for the operator,
* may be _nested_, for example: `3 * (4 + 5)` contains the sub-expression `4 + 5`
* may be _given a name_, for example: `a = 3 + 4`,
* may _reference names_, for example: `(a + 2) * (a - 4)` uses a constant or variable `a`,
* may _group_ multiple values as lists (or other collections), for example: `List(1, 3, 1)` contains the numbers 1, 3, 1 in that order,
* may just _describe_ expressions, for example: `"3 + 4"`, `(quote (+ 3 4))` or `() => 3 + 4` constructs but won't perform the calculation `3 + 4`.
* may compare values and combine propositions, for example: `(a > 5) and (b <= 0)` states that both, `a > 5` and `b <= 0`, must be true.

In Lisp-based languages, expressions (or so-called _s-expressions_, _sexprs_, or _sexps_ for [symbolic expressions](https://en.wikipedia.org/wiki/S-expression)) take the form of a _list_, typically, with an operator as the 1st element followed by zero or more operands `( operator operands ... operands )`.

Bonus excercise. Lookup the language constructs learned in this chapter in these "cheat-sheets":

* [Clojure](https://clojure.org/api/cheatsheet), [Clojure and other Lisp dialects](http://hyperpolyglot.org/lisp)
* [Scala](https://docs.scala-lang.org/cheatsheets), [Scala-to-Java](http://rea.tech/java-to-scala-cheatsheet)

After having done the coding excercises in this chapter, this cartoon will become clearer  ;-)

![](https://imgs.xkcd.com/comics/lisp_cycles.png)

#### 2.0.1 Write arithmetic expressions: [exercise KfK, chapter 1: What is computer programming?](http://kids.klipse.tech/clojure/2016/05/03/programming-kids-1.html)

Write an expression that calculates ...

Exercise | Clojure | Scala
:-------|:------|:------
7*8 | `(* 7 8)` | `7 * 8`
2\*3\*4\*5 | `(* 2 3 4 5)` | `2*3*4*5`
2+3+4+5 | `(+ 2 3 4 5)` | `2+3+4+5`

___Notes:___

* Lisp-based languages (like _Clojure_) use _prefix notation_.
* Fortran-based languages (like _Scala_) allow for _infix notation_.
* Clojure: multiple operands allowed for `+`, `*` ... operator.
* Scala: white-space (blanks etc) between operator and operands are optional.

___Further Reading:___

* [Prefix Notation](https://en.wikipedia.org/wiki/Polish_notation), [Infix Notation](https://en.wikipedia.org/wiki/Infix_notation), [Postfix Notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation) 
* The Prefix, Infix, and Postfix Notations can be [converted from one to another](https://en.wikipedia.org/wiki/Shunting-yard_algorithm)

#### 2.0.2 Write nested arithmetic expressions: [exercise KfK, chapter 2: Expressions inside Expressions inside Expressions](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-2.html).

Write this calculation as arithmetic expression ...

Exercise | Clojure | Scala
:-------|:------|:------
add 10 to 12 and multiply the result by 3 | `(* (+ 10 12) 3)` | `(10 + 12) * 3`
add 7 to 9 and multiply the result by 5 | `(* (+ 7 9) 5)` | `(7 + 9) * 5`
multiply 7 and 9 and add 6 to the result | `(+ (* 7 9) 6)` |`(7 * 9) + 6` or `7 * 9 + 6`
multiply 7 and 9 and add 6 and 9 to the result | `(+ (* 7 9) 6 9)` | `(7 * 9) + 6 + 9`
add 7 to 9 and multiply the result by 5 and by 3 | `(* (+ 7 9) 5 3)` | `(7 + 9) * 5 * 3`
add 7 to 9 and multiply the result by (+ 3 8 9) | `(* (+ 7 9) (+ 3 8 9))` | `(7 + 9) * (3 + 8 + 9)`

___Notes:___

* Expressions may contain sub-expressions.
* Parenthesis are sometimes needed to express grouping and order of operations.
* Precedence rules of operators may allow to drop parenthesis.
* Above expression can be written with operators only taking a predetermined amount of operands (like 2 operands for + or \*): for example, `(* (+ 7 9) (+ 3 8 9))` can be rewritten as `(* (+ 7 9) (+ (+ 3 8) 9))`.
* Under a predetermined number of operands, parenthesis may be dropped, since the order of operations is unambigous: `(* (+ 7 9) (+ (+ 3 8) 9))` same as `* + 7 9 + + 3 8 9` (prefix notation) or `3 8 + 9 + 7 9 + *` (postfix notation).

___Further reading:___

* [Operator Precedence](https://en.wikipedia.org/wiki/Order_of_operations), 
* [Postfix Notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation), [pocket calculator with Postfix Notation without Parenthesis](https://en.wikipedia.org/wiki/HP-35)

#### 2.0.3 Write and use named expressions: [exercise KfK, chapter 3: Giving Names to Expressions](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-3.html).

Often, it is useful to give expressions a name.  Not only may a name carry a meaning, it can also be referenced multiple times, giving a single definition for "common subexpressions".

Factor out common subexpressions by a defining a constant ...

Exercise | Clojure | Scala
:-------|:------|:------
(4 + 7 + 8)\*3 + (4 + 7 + 8)\*7 + (4 + 7 + 8)\*9 | `(def a ( + 4 7 8)` | `val a = 4 + 7 + 8`
...     | `(+ (* a 3) (* a 7) (* a 9))` | `a * 3 + a * 7 + a * 9`
(2\*3 + 4)\*3 + (2\*3 + 4)\*7 + (2\*3 + 4)\*9 | `(def b (+ (* 2 3) 4)` | `val b = 2 * 3 + 4`
...     | `(+ (* b 3) (* b 7) (* b 9))` | `b * 3 + b * 7 + b * 9`
2\*3 + 4\*5; then multiply by 4 + 5 | `(def c (* (+ (* 2 3) (* 4 5)) (+ 4 5)))` | `val c = (2 * 3 + 4 * 5) * (4 + 5)`
... | |
2\*3 + 4\*5; then multiply by 4 + 5; then multiply by 19 | `(* c 19)` | `c * 19`

___Notes:___

* In Clojure, the operator `def` defines a global variable.  (There's also an operator for binding a local variable is called `let`).
* In Lisp-based languages, to name an expression is itself an expression with an operator doing the naming and taking as operands the name and the named expression.
* In Scala, keyword `val` names a constant value.  (There's also the keyword `var` to define a variable, which may be re-assigned new values.)
* in comparison to Clojure, there is less a need of brackets in Scala calculations

Further reading:

* Programming languages, developers, and projects have conventions about how to form composite names, like ["kebab case"](https://en.wikipedia.org/wiki/Letter_case#Special_case_styles), ["snake case"](https://en.wikipedia.org/wiki/Snake_case), or ["camel case"](https://en.wikipedia.org/wiki/Camel_case)

#### 2.0.4 Write `list` expressions: [exercise KfK, chapter 4: Evaluating Several Expressions](http://kids.klipse.tech/clojure/2016/06/21/programming-kids-4.html).

Lists define a collection of values.

Compose a list of ...

Exercise | Clojure | Scala
:-------|:------|:------
the numbers 1, 2, 3, 4 and 9 | `(list 1 2 3 4 9)` | `List(1, 2, 3, 4, 9)`
2*3, 2*4 and 2*5 | `(list (* 2 3) (* 2 4) (* 2 5))` | `List(2 * 3, 2 * 4, 2 * 5)`
the ages of your siblings or friends | `(def ages (list 12 7 7))` | `val ages = List(12, 7, 7)`
a list of your siblings' ages... | `(list ages 3 10 10)` | `List(ages, 3, 10, 10)`
...followed by the age differences between them and you | `;   -> ((12 7 7) 3 10 10)` | `//   -> List(List(12, 7, 7), 3, 10, 10)`
a list of the ages of your siblings or friends and... | `(list ages (list 3 10 10))` | `List(ages, List(3 10 10))`
...a list of the age differences between them and you | `;   -> ((12 7 7) (3 10 10))` | `//   -> List(List(12, 7, 7), List(3, 10, 10))`

___Notes:___

* Lists may contain lists.
* In Clojure, a list is constructed as `(list ...)` with elements separated by a space.
* In Scala, a list is constructed as `List(...)` with elements separated by a comma.
* In Scala, functions and operators are usually written in lower case, while data types (eg. Int, Boolean, List...) are written in upper case.
* Creating a list is itself an expression with `list/List` as operator followed by the list elements as operands.

___Further Reading:___

* Scala, Clojure, and most languages predefine other collection types as well, for example: [arrays or vectors](https://en.wikipedia.org/wiki/Array_data_structure), [set](https://en.wikipedia.org/wiki/Set_(abstract_data_type)), or [maps](https://en.wikipedia.org/wiki/Associative_array).

* Refresher: sets vs. lists

:-----|:-----------------------------
sets: no order, no multiples |  `{ 1 2 } = { 2 1 } = { 2 2 1 }`
lists: no order, multiples |  `(list 2 1) != (list 1 2) != (list 1 2 2)`

* Refresher: set operations, sets of sets, subsets, powersets

:-----|:-----------------------------
`{ 1 2 3 }` | has 3 elements: `1`, `2`, and `3`
`{ {1} {2 3} }` | has 2 elements: inner set `{1}`, inner set `{2 3}`
`{ 1 }` | has 2 subsets: `{}`, `{1}`
`{ 1 2 3 }` | has a powerset of 8 elements: `{ {} {1} {2} {3} {1 2} {2 3} {1 3} {1 2 3} }`
`{} ` | has no elements, i.e., is the empty set `{}`
`{1} ` | has 1 element: `1`
`{ {} }` | has 1 element: the empty set `{}`
`{ { {} } }` | has 1 element: a set with 1 element that contains the empty set `{}`

#### 2.0.5 Write expressions without evaluating them: [exercise KfK, chapter 5: Please, tell me "what's your name?"](http://kids.klipse.tech/clojure/2016/07/21/chapter-5.html).

Form the expression as it is (without evaluating it) ...

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
* In Closure (and other Lisp-based languages), an operator `quote` indicates not to evaluate the subsequent expressions.  Often, the short form `'( ...)` for `(quote ...)` is preferred.
* Another language construct, available in both Clojure and Scala, is to describe computations as lambdas or anonymous functions (taking no arguments), see [Formulas and Functions](ch3_1_formulas_and_functions.md).

#### 2.0.6 Write comparison operator expressions: [exercise KfK, chapter 7: True or False (Pinocchio)](http://kids.klipse.tech/clojure/2016/08/05/chapter-7.html).

Ask if 7 times 6 ...

Exercise | Clojure | Scala
:-------|:------|:------
equals 40 | `(= (* 7 6) 40)` | ` 7 * 6 == 40 `
is less than 40 | `(< (* 7 6) 40)` | ` 7 * 6 < 40 `
is less/equal than 40 | `(<= (* 7 6) 40)` | ` 7 * 6 <= 40 `
is greater/equal than 40 | `(>= (* 7 6) 40)` | ` 7 * 6 >= 40 `
is greater than 40 | `(> (* 7 6) 40)` | ` 7 * 6 > 40 `
is not equal to 40 | `(not= (* 7 6) 40)` | ` 7 * 6 != 40 `

#### 2.0.7 Write boolean operator expressions.

* Exercise: implement and, or, not in terms of nand, xor, and, or, not

The [Boolean data type](https://en.wikipedia.org/wiki/Boolean_data_type) consists of just two values `true` and `false`.

Expressions yielding a Boolean value can be combined by the logical operators such as _not_, _and_, _or_ .  How these operators "work" is easily seen by the so-called [_truth tables_](https://en.wikipedia.org/wiki/Truth_table), which shows the 2, respectively 4 combinations of `true`/`false` for their operands.

Form the expressions below and compare them to `true` or `false` so that the result is `true` ...

Exercise | Clojure | Scala
:-------|:------|:------
not true | `(= (not true) false)` | `!true == false`
not false | `(= (not false) false)` | `!false == false`
true and true | `(= (and true true) true)` | `(true && true) == true`
true and false | `(= (and true false) false)` | `(true && false) == false`
false and true | `(= (and false true) false)` | `(false && true) == false`
false and false | `(= (and false false) false)` | `(false && false) == false`
true or true | `(= (or true true) true)` | `(true \|\| true) == true`
true or false | `(= (or true false) false)` | `(true \|\| false) == false`
false or true | `(= (or false true) false)` | `(false \|\| true) == false`
false or false | `(= (or false false) false)`) | `(false \|\| false) == false`

___Notes:___

* The `&&` and `||` operators in Scala (and other languages) have lower precedence than `==` or `!=`. 
The round brackets are therefore needed in the code examples here.  Otherwise, `false && false == false`, for example, would be inferred as `false && (false == false)` yielding `false`. The correct way to code this expression would be as follows: `(false && false) == false`, in this case yielding `true`, 

___Further reading:___

* Scala (and other languages) offer the addititional operators `&` and `|` as logical _and_ and _or_ besides `&&` and `||`.  These operators differ in their so-called [_strictness_](https://en.wikipedia.org/wiki/Strict_function): the "single letter" versions `&` and `|` are [_eager_](https://en.wikipedia.org/wiki/Eager_evaluation) in that they always evaluate _both_ their operands.  If the evaluation of the `op2` in `op1 & op2` or `op1 | op2` yields some error, the entire expression results in an error.
* In contrast, the Scala operators `&&`, `||` and the Clojure operators `and`/`or` are [_lazy_](https://en.wikipedia.org/wiki/Lazy_evaluation): the 2nd operand will not be evaluated once `op1` already decides the outcome.  That is, for `false & (...)` and `true | (...)`, any expression `(...)` will not even be evaluated, and any error there would not be raised.  This is also called [short-circuit_evaluation](https://en.wikipedia.org/wiki/Short-circuit_evaluation).
* Besides logical _and_, _or_, there are more boolean operators called _xor_, _nand_, _nor_, and _implies_ whose semantics is easily seen by their [truth table](https://en.wikipedia.org/wiki/Truth_table) as well.

-------

[<-- previous page](ch1_motivation.md)

[--> next page](ch3_0_functions.md)
