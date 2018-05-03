## 2. Expresssions

___TODO:___

* this chapter about ... how to compose, evaluate, and name expressions
* expressions are composed of operators and operands ... and expressions, meaning they can be nested
* to construct, build, form, compose, write an expression
* to evaluate an expression, to compute
* to name an expression, which itself is an expression with an operator doing the naming, the name, and the "namee" as operand
* to prevent evaluating an expression, which itself is an expression with an operator telling not to evaluate and the expression as operand
* coding exercises from <http://kids.klipse.tech/>

#### Write arithmetic expressions: [excercise KfK, chapter 1: What is computer programming?](http://kids.klipse.tech/clojure/2016/05/03/programming-kids-1.html).

Excercise | Clojure | Scala
:-------|:------|:------
write a program that calculates 7*8 | `(* 7 8)` | `7 * 8`
write a program that calculates 2\*3\*4\*5 | `(* 2 3 4 5)` | `2*3*4*5`
write a program that calculates 2+3+4+5 | `(+ 2 3 4 5)` | `2+3+4+5`

___Notes:___

* Lisp-based languages (like _Clojure_) use _prefix notation_.
* Fortran-based languages (like _Scala_) allow for _infix notation_.
* Clojure: multiple operands allowed for `+`, `*` ... operator.
* Scala: white-space (blanks etc) between operator and operands are optional.

___TODO:___

* purpose of computer languages: to give computer instructions and receive answers
* symbolic expressions, parens, operator, operands
* conversion between prefix/infix/postfix notations
* what are expressions? how are they written in lisp-like languages?  s-expressions, sexprs or sexps or "symbolic expression"
* <https://en.wikipedia.org/wiki/Expression_(computer_science)>, <https://en.wikipedia.org/wiki/S-expression>

Further Reading: [prefix notation](https://en.wikipedia.org/wiki/Polish_notation), [infix notation](https://en.wikipedia.org/wiki/Infix_notation), [postfix notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation)

#### Write nested arithmetic expressions: [excercise KfK, chapter 2: Expressions inside Expressions inside Expressions](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-2.html).

Excercise | Clojure | Scala
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

___TODO:___

* how to compose nested expressions

Further reading: [operator precedence](https://en.wikipedia.org/wiki/Order_of_operations), [postfix notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation), [pocket calculator with postfix notation without parenthesis](https://en.wikipedia.org/wiki/HP-35)

#### Write and use named expressions: [excercise KfK, chapter 3: Giving Names to Expressions](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-3.html).

Excercise | Clojure | Scala
:-------|:------|:------
calculate (4 + 7 + 8)\*3 + (4 + 7 + 8)\*7 + (4 + 7 + 8)\*9 | `(def a ( + 4 7 8)` | `val a = 4 + 7 + 8`
...     | `(+ (* a 3) (* a 7) (* a 9))` | `a * 3 + a * 7 + a * 9`
calculate (2\*3 + 4)\*3 + (2\*3 + 4)\*7 + (2\*3 + 4)\*9 | `(def b (+ (* 2 3) 4)` | `val b = 2 * 3 + 4`
...     | `(+ (* b 3) (* b 7) (* b 9))` | `b * 3 + b * 7 + b * 9`
calculate 2\*3 + 4\*5; then multiply the result by 4 + 5 | `(def c (* (+ (* 2 3) (* 4 5)) (+ 4 5)))` | `val c = (2 * 3 + 4 * 5) * (4 + 5)`
... | |
calculate 2\*3 + 4\*5; then multiply the result by 4 + 5; then multiply the result by 19 | `(* c 19)` | `c * 19`

___Notes:___

* Operator `def` defines a global variable (the operator for binding a local variable is called `let`).
* In Scala, keyword `val` names a constant value.

___TODO:___

* why to name expressions: common subexpressions
* how to name expressions: `def` is the operation that tells the computer to give a name to an expression. (The word def is a shorthand for define).
* in comparison to Clojure, there is less a need of brackets in Scala calculations

Further reading:

* [language constructs of major Lisp dialects](http://hyperpolyglot.org/lisp)

#### Write list expressions: [excercise KfK, chapter 4: Evaluating Several Expressions](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-4.html).

Excercise | Clojure | Scala
:-------|:------|:------
display 2*3, 2*4 and 2*5 | `(list (* 2 3) (* 2 4) (* 2 5))` | `List(2 * 3, 2 * 4, 2 * 5)`
display the numbers 1, 2, 3, 4 and 9 | `(list 1 2 3 4 9)` | `List(1, 2, 3, 4, 9)`
display the ages of your siblings (or friends) | `(def ages (list 12 7 7))` | `val ages = List(12, 7, 7)`
display a list that contains a list of your siblings' ages... | `(list ages 3 10 10)` | `List(ages, 3, 10, 10)`
...followed by the age differences between them and you | `;   -> ((12 7 7) 3 10 10)` | `//   -> List(List(12, 7, 7), 3, 10, 10)`
display a list that contains _two lists_: the ages of your siblings... | `(list ages (list 3 10 10))` | `List(ages, List(3 10 10))`
...and the age differences between them and you | `;   -> ((12 7 7) (3 10 10))` | `//   -> List(List(12, 7, 7), List(3, 10, 10))`

___Notes:___

* Lists may contain lists.
* In Clojure, a list is constructed as `(list ...)` with elements separated by a space.
* In Scala, a list is constructed as `List(...)` with elements separated by a comma.
* In Scala, functions and operators are usually written in lower case, while data types (eg. Int, Boolean, List...) are written in upper case.

___TODO:___

* motivation: display the result of several expressions
* creating a `list` of expressions, `list` operator, expression operands to evaluate
* list of lists
* Scala `Seq`

___TODO:___ sets & lists

value X | elements, subsets, powersets
:-----|:-----------------------------
{ 1 2 3 } | X has 3 elements: 1 2 3
{ {1} {2 3} } | X has 2 elements: inner set {1}, inner set {2 3}
{ 1 } | X has 2 subsets: {}, {1}
{ 1 2 3 } | the powerset of X is a set with 8 elements: { {} {1} {2} {3} {1 2} {2 3} {1 3} {1 2 3} }
{}  | X has no elements, meaning, X is the empty set
{1}  | X has 1 element: 1
{ {} } | X has 1 element: the empty set {}
{ { {} } } | X has 1 element: a set with 1 element that contains the empty set {}

sets vs lists | example
:-----|:-----------------------------
sets: no order, no multiples |  { 1 2 } = { 2 1 } = { 2 2 1 }
lists: no order, multiples |  (list 2 1) != (list 1 2) != (list 1 2 2)

#### Write expressions without evaluating them: [excercise KfK, chapter 5: Please, tell me "what's your name?"](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-5.html).

Excercise | Clojure | Scala
:-------|:------|:------
form the expression `(+ 3 4)` exactly as it is without evaluating it | `(quote (+ 3 4))` | `() => 3 + 4`
... | `'(+ 3 4)` _(alternative notation)_ |
form and then evaluate the expression `(+ 3 4)` | `(eval (quote (+ 3 4)))` | `(() => 3 + 4)()`
... | `(eval '(+ 3 4))` _(alternative notation)_ |
...

#### Write comparison operator expressions: [excercise KfK, chapter 7: True or False (Pinocchio)](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-7.html).

Excercise | Clojure | Scala
:-------|:------|:------
ask if 7 times 6 equals 40 | `(= (* 7 6) 40)` | ` 7 * 6 == 40 `
ask if 7 times 6 is less/equal than 40 | `(<= (* 7 6) 40)` | ` 7 * 6 <= 40 `
ask if 7 times 6 is greater/equal than 40 | `(>= (* 7 6) 40)` | ` 7 * 6 >= 40 `
ask if 7 times 6 is not equal to 40 | `(not= (* 7 6) 40)` | ` 7 * 6 != 40 `

___TODO:___ explain

* <https://en.wikipedia.org/wiki/Boolean_data_type>, <https://en.wikipedia.org/wiki/Predicate_(mathematical_logic)>

#### Write boolean operator expressions.

___TODO:___ explain, give excercises

* What is a conditional?
* exercise: implement and, or, not in terms of nand, xor, and, or, not

___Notes:___

<https://en.wikipedia.org/wiki/Boolean_algebra>

#### Write conditional operator expressions.

___TODO:___ explain, give excercises

* What is a conditional?
* exercise: implement and, or, not in terms of if-then-else
* not useful: [KfK, Chapter 8: If (Emoji)](http://kids.klipse.tech/clojure/2016/08/05/chapter-8.html)

___Notes:___

* <https://en.wikipedia.org/wiki/Conditional_(computer_programming)>
