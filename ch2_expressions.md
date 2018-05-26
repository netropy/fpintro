## 2.0 Forms and Expressions

The exercises in this chapter show how to write
[_expressions_](https://en.wikipedia.org/wiki/Expression_(computer_science))
(or [forms](http://www.n-a-n-o.com/lisp/cmucl-tutorials/LISP-tutorial-9.html),
as they are also called in Lisp-like languages).

Most coding exercises are from the tutorial
[Klipse for Kids](http://kids.klipse.tech)
with code given in Clojure and Scala.  Answer notes and "further reading" pointers provide additional information.

For a summary of Clojure's and Scala's expression syntax, see the last exercise
TODO: [below](#21-summary)
or look up these "cheat-sheets":
[Clojure](https://clojure.org/api/cheatsheet),
[Clojure and other Lisp dialects](http://hyperpolyglot.org/lisp),
[Scala](https://docs.scala-lang.org/cheatsheets),
[Scala-to-Java](http://rea.tech/java-to-scala-cheatsheet).

#### 2.0.1 Write arithmetic expressions: [exercise KfK, chapter 1: What is computer programming?](http://kids.klipse.tech/clojure/2016/05/03/programming-kids-1.html)

Write an expression that calculates ...

Exercise | Clojure | Scala
:-------|:------|:------
1\. 7\*8 | `(* 7 8)` | `7 * 8`
2\. 2\*3\*4\*5 | `(* 2 3 4 5)` | `2*3*4*5`
3\. 2+3+4+5 | `(+ 2 3 4 5)` | `2 + 3 + 4 + 5`

___Notes:___

* Clojure uses
  [_prefix notation_](https://en.wikipedia.org/wiki/Polish_notation) `(<operator> <operand> <operand> ...)`,
  (which is a characteristic of all Lisp-like languages).
* Prefix notation has the benefit to allow for multiple operands after arithmetic operators (see exercises 2. and 3).
* Scala generally uses
  [_infix notation_](https://en.wikipedia.org/wiki/Infix_notation) `<operand> <operator> <operand>` for arithmetic expressions
  (which is familiar from mathematics and which is a characteristic of languages derived from Fortran and Algol).
  Unary operators for sign and negation (`+`, `-`, `!`, and `~`), however, form prefix expressions `<operand><operator>`, for example: `-3`.
* Infix notation requires to repeat arithmetic operators between multiple operands (see exercises 2. and 3).
* Scala also has a switch to allow writing expressions in
  [_postfix notation_](https://en.wikipedia.org/wiki/Reverse_Polish_notation) `<operand> <operator>`, for example: `3 toFloat` (yielding `3.0f`).
  However, postfix expressions are not enabled by default but must be switched on per `import` statement.
* Clojure: Operator and operands are separated by a blank (or other
  [white space characters](https://en.wikipedia.org/wiki/Whitespace_character)
  (a comma is also allowed as separator, but rarely used).
* Scala: A blank or other white space character between a binary operator and its operands is optional but preferred; the blank is usually dropped for unary operators.

___Further Reading:___

* For a brief explanation of the structure (syntax) and evaluation (semantics) of arithmetic expressions, see:
  [functional Clojure](https://clojure.org/guides/learn/syntax#_structure_vs_semantics) vs
  [object-oriented Scala](https://docs.scala-lang.org/tutorials/scala-for-java-programmers.html#numbers-are-objects).
* Scala: postfix notation, that is, `<operand> <operator>` as a shorthand for `<operand>.<operator>()`, can be enabled by importing this
  [postix language feature](https://www.scala-lang.org/api/current/scala/language$.html#postfixOps:languageFeature.postfixOps).
* Clojure: Arithmetic operators extend to
  [more than two and even less than two arguments](https://aphyr.com/posts/302-clojure-from-the-ground-up-basic-types).
* Java, Clojure, and Scala share a common set of
  [_data types_](https://en.wikipedia.org/wiki/Data_type)
  for numbers, for example, `Long` for integral numbers or `Double` for floating-point numbers.
  The choice of a data type affects the performance or result of arithmetic and comparison operations, see
  [exercise 2.0.6](...TODO...) and
  [exercise 2.0.9](...TODO...).
* Clojure: In addition to operators (functions)
  ['+'](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/+),
  ['*'](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/*) ..., there are (slower) variants
  ['+\''](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/+\'),
  ['*\''](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/*\') ...
  that check for arithmetic overflow and auto-promote the result.

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

* Expressions may be nested, that is, they may be composed of sub-expressions.
* [Parentheses, parens, or round brackets](https://en.wikipedia.org/wiki/Bracket#Parentheses_.28_.29)
  are required to express grouping and order of operations.
* In infix notation, rules for
  [operator precedence](https://en.wikipedia.org/wiki/Order_of_operations) and
  [associativity](https://en.wikipedia.org/wiki/Associative_property)
  help mitigate the need for parentheses (see exercise 3.).

___Further Reading:___

* Both terms, `<operator>` and `<operand>`, in the notes of
  [exercise 2.0.1](ch2_expressions.md#201-write-arithmetic-expressions-exercise-kfk-chapter-1-what-is-computer-programming)
  may be themselves composite expressions that evaluate to an
  [operator](https://en.wikipedia.org/wiki/Operator_(computer_programming))
  and an
  [operand](https://en.wikipedia.org/wiki/Operand).
* The operator is usually a
  [function](https://en.wikipedia.org/wiki/Function_(mathematics)) and the operands are called
  [arguments](https://en.wikipedia.org/wiki/Argument_of_a_function) of the function.
* If the [arity](https://en.wikipedia.org/wiki/Arity) of operators is fixed (predetermined),
  postfix notation eliminates the need for parentheses, which allows for a
  [pocket calculator without keys for round brackets](https://en.wikipedia.org/wiki/HP-35).
* Infix, prefix, and postfix notations can be
  [converted into another](https://en.wikipedia.org/wiki/Shunting-yard_algorithm).

#### 2.0.3 Write and use named expressions: [exercise KfK, chapter 3: Giving Names to Expressions](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-3.html).

Expressions can be assigned a name.  Such a name introduces a "constant", "variable", or "symbol" whose value is the evaluated expression.  This allows to
* refer to expressions by a short identifier,
* convey a meaning by choosing a suitable name, and
* reference an expression multiple times while maintaining a single definition for it.

Factor out the "common subexpressions" by assigning each of them to a constant ...
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

* Lisp-like languages show many more round brackets compared to Scala code (see cartoon below ;-)
* Scala: Keyword `val` defines a
  [_constant_](https://en.wikipedia.org/wiki/Constant_(computer_programming)),
  which is immutable.
* Scala: Keyword `var` defines a
  [_variable_](https://en.wikipedia.org/wiki/Variable_(computer_science)),
  which may be re-assigned a new value.
* Clojure: The operator (special form)
  [`def`](https://clojure.org/reference/special_forms#def) defines a
  [_global ("interned") variable_](https://clojure.org/reference/vars),
  which is henceforth known to all evaluations.
* Clojure: For defining a set of _local constants_, which are only known to a list of listed expressions, there is operator (special form)
  [`let`](https://clojure.org/reference/special_forms#let).
  (There are additional operators capable of creating thread-local bindings and for setting static/instance variables of Java classes.)
* In Lisp-like languages, assigning a name to an expression is itself an expression with an operator binding a
  [symbol](https://en.wikipedia.org/wiki/Symbol_(programming))
  to the value of the given expression.  In Java-like languages, the definition of a variable or constant is typically not an expression but a
  [statement](https://en.wikipedia.org/wiki/Statement_(computer_science)).
* Programming languages usually adopt conventions about how to form and capitalize composite names, for example:

Example | Informal letter case name | Prevalent in
:-----|:-----|:-----
`no-of-widgets` | [kebab case](https://en.wikipedia.org/wiki/Letter_case#Special_case_styles) | Lisp, Clojure
`no_of_widgets` | [snake case](https://en.wikipedia.org/wiki/Snake_case) | C, C++
`noOfWidgets` | [camel case](https://en.wikipedia.org/wiki/Camel_case) | Java, Scala, C++

___Further Reading:___

* Clojure and Scala also allow to assign a name to an unevaluated expression, see
  [exercise 2.0.5](ch2_expressions.md#205-write-expressions-without-evaluating-them-exercise-kfk-chapter-5-please-tell-me-whats-your-name).
* Scala: See examples and syntax variants of the
  [definition of variables and constants](https://www.tutorialspoint.com/scala/scala_variables.htm).
* Clojure: Besides special forms
  [`def`)](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/def) for global variables and
  [`let`](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/let) for local constants,
  there are additional operators (macros and special forms) for binding names or assigning variables, for example
  - [`as->`](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/as-%3E)
    for rebinding a name to intermediate results,
  - [`binding`](http://clojure.github.io/clojure/clojure.core-api.html#clojure.core/binding)
    for creating local or thread-local bindings,
  - [set!`](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/set!)
    for setting Java class/instance variables.
* See more on the role of
  [threads](https://en.wikipedia.org/wiki/Thread_(computing)) in computing.
* See more on the use of
  [scope](https://en.wikipedia.org/wiki/Scope_(computer_science)) in programming.
* See more on the kinds of variables, classifying their visibility and lifetime (storage class):
  [static](https://en.wikipedia.org/wiki/Static_variable),
  [global](https://en.wikipedia.org/wiki/Global_variable),
  [local, stack-local, or automatic](https://en.wikipedia.org/wiki/Automatic_variable),
  [thread-local](https://en.wikipedia.org/wiki/Thread-local_storage),
  [class variable](https://en.wikipedia.org/wiki/Class_variable), and
  [instance variable or field](https://en.wikipedia.org/wiki/Instance_variable).

#### 2.0.4 Write `list` expressions: [exercise KfK, chapter 4: Evaluating Several Expressions](http://kids.klipse.tech/clojure/2016/06/21/programming-kids-4.html).

The input or output of a calculation can be a collection of data not just be a single value (datum).
_Lists_ are a universal type of data collections in which
* the order of elements matters and
* multiples are allowed.

Compose a list of ...
1. the numbers 1, 2, 3, 4 and 9
2. 2\*3, 2\*4 and 2\*5
3. the ages of your siblings or friends
4. a list of the ages of your siblings or friends followed by the age differences between them and you
5. a list of the ages of your siblings or friends and a list of the age differences between them and you
6. an empty list
7. a list containing the empty list

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
6\. | `(list)` | ``List()`
... | `;; => ()` | `// => List()`
7\. | `(list (list))` | ``List(List())`
... | `;; => (())` | `// => List(List())`

___Notes:___

* [_Lists_](https://en.wikipedia.org/wiki/List_(abstract_data_type)) may be either
  - empty or
  - contain elements, including possibly other lists.
* Clojure: The expression `(list ...)` constructs a list collection of the provided elements (separated by a space or comma).
  Here, `list` is a predefined function.  In Lisp-like languages, functions (and symbols) typically have lower case names.
* Scala: The expression `List(...)` constructs a list collection of the provided elements (separated by comma).
  Here, `List` is a predefined data type (with a companion object).  In Java-like languages, type names typically start upper case.
* Creating a list is itself an expression with `list` or `List` as operator followed by the list elements as operands.

___Further Reading:___

* Clojure:
  [`list` operator](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/list)
  and [list-related functions](https://clojure.org/reference/data_structures#Lists),
  [the empty list `'()` vs `nil`](https://clojure.org/reference/lisps).
* Scala:
  [Five ways to create a List](https://alvinalexander.com/scala/how-create-scala-list-range-fill-tabulate-constructors),
  methods of the [List class](https://www.scala-lang.org/api/current/scala/collection/immutable/List.html) and of its
  [companion object](https://www.scala-lang.org/api/current/scala/collection/immutable/List$.html),
  [the empty List "Nil"](https://www.scala-lang.org/api/current/scala/collection/immutable/Nil$.html).
* Both, Clojure and Scala, also offer "Lisp-style" construction and traversal mimicking
  [linked lists](https://en.wikipedia.org/wiki/Linked_list), that is, lists as a chain of
  [_conses_](https://www.cs.cmu.edu/Groups/AI/html/cltl/clm/node28.html).
  A _cons_ represents a pair (or record) of
  - a value called "first", "head", or "car" and
  - a reference called "rest", "tail", or "cdr" to the next cons (i.e., list element) or the empty list.
  See Closure's
  [`cons` function](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/cons),
  [its differences from Lisp](https://8thlight.com/blog/sarah-sunday/2017/01/24/common-lisp-clojure-cons-cells.html),
  and Scala's
  [`::` class](https://www.scala-lang.org/api/current/scala/collection/immutable/$colon$colon.html).
* Incidentally, both Clojure and Scala, also offer _sequences_ as a more abstract data type (interface) than lists.
  See Clojure's
  [`ISeq`](https://clojure.org/reference/sequences)
  and Scala's
  [`Seq`](https://www.scala-lang.org/api/current/scala/collection/Seq.html)
  interfaces.
* Refresher (mathematics):
  [sets](https://en.wikipedia.org/wiki/Set_(abstract_data_type)) vs.
  [lists](https://en.wikipedia.org/wiki/List_(abstract_data_type)) vs.
  [tuples](https://en.wikipedia.org/wiki/Tuple)
  - sets: homogeneous, no order, no multiples: `{ 1 2 } = { 2 1 } = { 2 2 1 }`
  - lists: homogeneous, order counts, multiples allowed: `(list 2 1) != (list 1 2) != (list 1 2 2)`
  - tuples: heterogeneous, order counts, multiples allowed: `(1, 2, 'a') != ('a', 2, 1) != (2, 2, 1, 'a', 'a')`
* Clojure and Scala, like most programming languages, provide a variety of other collection types, like
  [arrays/vectors](https://en.wikipedia.org/wiki/Array_data_structure),
  [maps](https://en.wikipedia.org/wiki/Associative_array), or
  [sets](https://en.wikipedia.org/wiki/Set_(abstract_data_type)).
  See
  - [Collections in Clojure](https://clojure.org/reference/data_structures#Collections),
  - [Collections in Scala](https://docs.scala-lang.org/overviews/collections/introduction.html).

* Refresher (mathematics):
  [elements](https://en.wikipedia.org/wiki/Element_(mathematics)),
  [empty set](https://en.wikipedia.org/wiki/Empty_set),
  [subsets](https://en.wikipedia.org/wiki/Subset),
  [power sets](https://en.wikipedia.org/wiki/Power_set),
  [set operations](https://en.wikipedia.org/wiki/Algebra_of_sets),
  [Cartesian product](https://en.wikipedia.org/wiki/Cartesian_product)

Example | Meaning
:-----|:-----------------------------
`{1 2 3}` | has 3 elements: `1`, `2`, and `3`
`{ {1} {2 3} }` | has 2 elements: inner set `{1}`, inner set `{2 3}`
`{1}` | has 2 subsets: `{}`, `{1}`
`{1 2 3}` | has a power set of 8 elements: `{ {} {1} {2} {3} {1 2} {2 3} {1 3} {1 2 3} }`
`{}` | has no elements, i.e., is the empty set `{}`
`{1}` | has 1 element: `1`
`{ {} }` | has 1 element: the empty set `{}`
`{ { {} } }` | has 1 element: a set with 1 element that contains the empty set `{}`
`{1 2} X {3 4 5}` | is a Cartesian product of 6 elements: `{ (1,3) (1,4) (1,5) (2,3) (2,4) (2,5) }`

* Incidentally, the concept of sets of sets that ultimately only contain the
  [empty set](https://en.wikipedia.org/wiki/Von_Neumann_definition_of_ordinals) can be used as a foundational definition of
  [ordinal numbers](https://en.wikipedia.org/wiki/Von_Neumann_definition_of_ordinals).

#### 2.0.5 Write expressions without evaluating them: [exercise KfK, chapter 5: Please, tell me "what's your name?"](http://kids.klipse.tech/clojure/2016/07/21/chapter-5.html).

In human languages, one use of quotes is to indicate when to take an expression literally instead of by its meaning.
Similarly, programming languages offer constructs to refer to an expression "as it is", that is, without evaluating it.

Form and refer to the expression as it is ...

Exercise | Clojure | Scala
:-------|:------|:------
`+ 3 4` as is | `(quote (+ 3 4))` | |
... | `'(+ 3 4)` _(preferred notation)_ |
... | `;; => (+ 3 4)` |
`+ 3 4` as is, then evaluate | `(eval (quote (+ 3 4)))` | |
... | `(eval '(+ 3 4))` _(preferred notation)_ | |
... | `;; => 7` |
`3, 4` as is | `(quote (3 4))` | |
... | `'(3 4)` _(preferred notation)_ |
... | `;; => (3 4)` |
`3, 4` as is, then try evaluate | `(eval (quote (3 4)))` | |
... | `(eval '(3 4))` _(preferred notation)_ | |
... | `;; => error: ClassCastException ...` |

___Notes:___

* Clojure: Preventing the evaluation of an expression is itself an expression.  The operator (special form)
  [`quote`](https://clojure.org/reference/special_forms#quote),
  [clojure.core/quote](https://clojuredocs.org/clojure.core/quote)
  indicates not to evaluate the subsequent expressions.  Usually, the short form (reader macro)
  [`'( ...)`](https://clojure.org/reference/reader#_quote)
  is preferred.
* Clojure: Conversely, calling the evaluation of an expression is itself also an expression.  The operator (function)
  [`eval`](https://clojuredocs.org/clojure.core/eval)
  submits an expression (form data) to the interpreter for evaluation and returns the result.
* Clojure: When the operator symbol `+` is dropped from the quote expression `'(+ 3 4)`, the list is formed as just `(3 4)`.
  So, _quoting is convenient to form lists of values_ (or expressions) without use of operators like `list` or `cons`.
* Clojure: However, any such list of just values cannot be further evaluated, since `eval` expects lists to begin with an operator expression (prefix notation).
  The result is an error (ClassCastException) when the first list element is treated as an operator.
* Scala: Quoting of expressions is not directly supported.  However, see next for related features.

___Further Reading:___

* Clojure and Scala: Another language feature that allows to construct (but not execute) computations are _lambdas_ or _anonymous functions_, see
  [Type Signature, Arity, and Nullary Functions](ch3_1_formulas_and_functions#type-signature-arity-and-nullary-functions)
  for notes and exercises.
TODO: fix check link
* Scala: While quoting of expressions is not supported, there is an experimental feature of
  [quasiquotes](https://docs.scala-lang.org/overviews/quasiquotes/intro.html), mostly for use with
  [macros](https://docs.scala-lang.org/overviews/macros/usecases.html).
  Note, though, that macros have not been standard Scala yet and the
  [plan for macros in Scala 3](https://www.scala-lang.org/blog/2018/04/30/in-a-nutshell.html) is under discussion.
* Clojure: Another variety of quote `\`` and `unquote` operators (primarily of interest to macro-programming) are
  [syntax-quote](https://clojure.org/reference/reader#syntax-quote),
  which allow for selective evaluation of expressions; see
  [Quoting Without Confusion](https://8thlight.com/blog/colin-jones/2012/05/22/quoting-without-confusion.html).
* Clojure: Function `eval` has a related operator (function)
  [`apply`](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/apply),
  which invokes a function on a list of arguments, for example: `(apply (eval '+) '(3 4))` or `(apply + '(3 4))`.
  For more on the general concept, see
  [eval](https://en.wikipedia.org/wiki/Eval) and
  [apply](https://en.wikipedia.org/wiki/Apply).

#### 2.0.6 Write comparison operator expressions: [exercise KfK, chapter 7: True or False (Pinocchio)](http://kids.klipse.tech/clojure/2016/08/05/chapter-7.html).

Numbers can be compared for being _equal_, _not equal_, _less than_, _less/equal than_, _greater than_, and _greater/equal than_.

Ask if 7 times 6 is ... 40

Exercise | Clojure | Scala
:-------|:------|:------
equal to | `(== (* 7 6) 40)` | `7 * 6 == 40`
less than | `(< (* 7 6) 40)` | `7 * 6 < 40`
less/equal than | `(<= (* 7 6) 40)` | `7 * 6 <= 40`
greater/equal than | `(>= (* 7 6) 40)` | `7 * 6 >= 40`
greater than | `(> (* 7 6) 40)` | `7 * 6 > 40`
not equal to | `(not (== (* 7 6) 40))` | `7 * 6 != 40`

___Notes:___

* Scala's infix expressions look simpler and cleaner than the prefix forms in Clojure.
* But then, prefix notation allows for multiple arguments, whereas infix notation requires the use of boolean operators
  (see [exercise 2.0.7](...TODO...)),
  for example:
  - Clojure: `(< 1 2 3)`
  - Scala: `1 < 2 && 2 < 3`
* Java, Clojure, and Scala share a common set of
  [_data types_](https://en.wikipedia.org/wiki/Data_type)
  for numbers, for example, `Long` for integral numbers or `Double` for floating-point numbers.
  The choice of a data type affects the performance or result of arithmetic and comparison operations, see
  [exercise 2.0.9](...TODO...).
* Equality of value, regardless of the numeric data type, is tested by operator `==`, for example:
  - Clojure: `(== 3 3.0)` yields `true`, `(== 2 3)` yields `false`;
  - Scala: `3 == 3.0` yields `true`, `2 == 3` yields `false`.
* All relational operators extend to different numeric data types (by type conversion), for example, all these comparisons yield `true`:
  - Clojure: `(== 3 3.0)`, `(< 2.2 3)`, `(> 2.2 1.1)` (extends also to `BigDecimal`, `BigInt`)
  - Scala: `3 == 3.0`, `2.2 < 3`, `2.2 > 1.1` (extends also to `BigDecimal`, but no automatic type conversions for `BigInt`)
* Scala: Numerical (value) inequality is tested by operator `!=`, for example:
  - `3 != 3.0` yields `false` (and is equivalent to `!(3 == 3.0)`).
* Clojure: Numerical (value) inequality must be tested by boolean
  [`not`](https://clojuredocs.org/clojure.core/not)
  and `==`, for example:
  - `(not (== 3 3.0))` yields `false`,
  - while `(not= 3 3.0)` yields `true` (since equivalent to `(not (= 3 3.0))`, see below).

___Further Reading:___

* Values and objects can be tested for
  [_identity_ or _equality_](https://en.wikipedia.org/wiki/Relational_operator#Sameness_(object_identity)_vs._content_equality).
  - Identity or _sameness_ is typically tested by comparing
    [references](https://en.wikipedia.org/wiki/Reference_(computer_science)) or
    [memory addresses](https://en.wikipedia.org/wiki/Memory_address) of objects.
  - For _non-addressable_ values, like
    [r-values](https://en.wikipedia.org/wiki/Value_(computer_science)#R-values_and_addresses)
    in C-like languages or
    [primitive types](https://docs.oracle.com/javase/specs/jls/se8/html/jls-4.html#jls-4.2)
    in Java-like languages, the notion of identity is either seen as not to apply or as being the same as value equality.
  - Value equality is tested by comparing the data content of objects.  Typically, the objects'
    [data types](https://en.wikipedia.org/wiki/Data_type)
    are examend first, since structurally disparate objects cannot be equal.
    When types are different yet similar enough to allow for comparison of content, an object's type might be adjusted by
    [conversion](https://en.wikipedia.org/wiki/Type_conversion)
    or "upcasting" to a common
    [abstract data type](https://en.wikipedia.org/wiki/Abstract_data_type).

* Test for _identity_:
  - Clojure: function
    [`identical?`](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/identical?)
    tests two objects of any type if they are the same.
  - Scala: method
    [`eq`](https://www.scala-lang.org/api/current/scala/AnyRef.html#eq(x$1:AnyRef):Boolean)
    tests objects of reference type (`scala.AnyRef`) if they are the same.
  - Scala: `eq` cannot be applied to value types (`scala.AnyVal`); instead, use operator `==` to compare for value equality.

* Test for _equality_:
  - Clojure: for numbers, function
    [`==`](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/==)
    compares for value equality across different types.  It cannot be applied to non-numbers (instances not implementing `java.lang.Number`).
  - Clojure: for non-numbers, function
    [`=`](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/=)
    compares for value equality across different types (and delegates to `java.lang.Object.equals`).
    Function `=` should _not_ be used for numbers as some type combinations yield `false` despite precisely equal value.
  - Scala: operator
    [`==`](https://www.scala-lang.org/api/current/scala/Any.html#==(x$1:Any):Boolean)
    compares two arguments of any type for value equality (and delegates to
    [`scala.Any.equals`](https://www.scala-lang.org/api/current/scala/Any.html#equals(x$1:Any):Boolean)).

* Test for _non-identity_:
  - Clojure: no predefined function, use `(not (identical? ...))`.
  - Scala: method
    [`ne`](https://www.scala-lang.org/api/current/scala/AnyRef.html#ne(x$1:AnyRef):Boolean)
    is the negation of `eq` on `AnyRef`s.

* Test for _non-equality_:
  - Clojure: for numbers, no predefined function, use `(not (== ...))`.
  - Clojure: for non-numbers, function
    [`not=`](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/not=)
    is the negation of `=`.
  - Scala: operator
    [`!=`](https://www.scala-lang.org/api/current/scala/AnyRef.html#ne(x$1:AnyRef):Boolean)
    is the negation of `==` on `Any` type.

* Data types for which there is an _ordering_ may also offer
  [relational operators](https://en.wikipedia.org/wiki/Relational_operator)
  and allow for the sorting of values.  See
  - Clojure: function
    [compare](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/compare)
  - Scala: functions and types
    [Ordered.compare](https://www.scala-lang.org/api/current/scala/math/Ordered.html#compare(that:A):Int)
    [Ordering.compare](https://www.scala-lang.org/api/current/scala/math/Ordering.html#compare(x:T,y:T):Int)

* Refresher (mathematics):
  [equality](https://en.wikipedia.org/wiki/Equality_(mathematics)),
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

Not required for this exercise, but note the _Further Reading_ section for fine points on Booleans in Clojure and Scala.

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

___Further Reading:___

TODO: fine points...

* Lisp or older language versions of C did not introduce a primitive data type for Booleans.
  Instead, a test for a boolean outcome is done in
  - Lisp as: A value of `nil` or `'()` means `false`; any non-`nil` value means `true`; often, the keyword symbol `t` is predefined for convenience.
  - C (prior ISO C99) as: An `int` value `0` means `false`; any non-zero value means `true`; often, predefined macros (or `typedef`) provide for a type and values `bool`, `false`, `true` (or an all-caps version thereof).

http://c-faq.com/bool/index.html

* In Clojure, some operators (conditionals) also treat
  [`nil`](https://clojure.org/reference/data_structures#nil) as `false` (note, however, that the empty list `'()` differs from `nil`,
  [unlike in other Lisps](https://clojure.org/reference/lisps)).

* Java offers two related types: the primitive data type `boolean` and the reference type
  [`java.lang.Boolean`](https://docs.oracle.com/javase/8/docs/api/java/lang/Boolean.html),
  also called "boxed" or "wrapper" type.  While the reference type has the
  [`null` reference](https://en.wikipedia.org/wiki/Null_pointer) as valid value,
  there's never an implicit conversion from `null` to `false` (despite
  [auto\[un\]boxing](https://docs.oracle.com/javase/tutorial/java/data/autoboxing.html)).

* Scala just defines a single type `Boolean`, which is a
  [value type](https://docs.scala-lang.org/tour/unified-types.html), so the
  [`null` reference](https://www.scala-lang.org/api/current/scala/Null.html) is not a value of it.

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

TODO:

https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/bit-and
https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/bit-or
https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/bit-not

#### 2.0.8 Write string operator expressions.

#### 2.0.9 Write numerical type expressions.

* numbers can be of different data types, for example
  - `3` is an [integral number](https://en.wikipedia.org/wiki/Integer_(computer_science)) of type `Int`, `Integer`, or `Long`;
  - `3.0` is a [floating point number](https://en.wikipedia.org/wiki/Floating-point_arithmetic) of type `Float` or `Double`;
  - `3M` or `BigDecimal(3)` is an [arbitrary-precision number](https://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic)


  [_data types_](https://en.wikipedia.org/wiki/Data_type)

* Clojure: In addition to operators (functions)
  ['+'](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/+),
  ['*'](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/*) ..., there are (slower) variants
  ['+\''](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/+\'),
  ['*\''](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/*\') ...
  that check for arithmetic overflow and auto-promote the result.


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

___Further Reading:___

* Typical for [Lisp](https://en.wikipedia.org/wiki/Lisp)-like languages is their very "light" syntax, which can be described
  [in a few sentences](http://lisp-lang.org/learn/first-steps#syntax).
* At

expressions (or so-called _S-expressions_, _sexprs_, or

* Lisp-like languages
  typically, with an operator as the 1st element followed by zero or more operands.

* In [Lisp](https://en.wikipedia.org/wiki/Lisp)-like languages, expressions (or so-called _S-expressions_, _sexprs_, or
  [symbolic expressions](https://en.wikipedia.org/wiki/S-expression)) take the form of a
  [_list_](https://en.wikipedia.org/wiki/List_(abstract_data_type)),
  typically, with an operator (or function) as the 1st element followed by zero or more operands (or arguments).
* Languages in which "code" looks similar to "data" (in general, where code resembles its
  [abstract syntax tree](https://en.wikipedia.org/wiki/Abstract_syntax_tree)) are called
  [homoiconic](https://en.wikipedia.org/wiki/Homoiconicity).

----------------------------------------------------------------------

TODO:

https://docs.scala-lang.org/overviews/core/string-interpolation.html

https://clojure.org/reference/other_functions#creating-functions

https://clojure.org/reference/special_forms#fn
https://clojure.org/reference/special_forms#if

https://8thlight.com/blog/aaron-lahey/2016/07/20/relationship-between-clojure-functions-symbols-vars-namespaces.html
https://clojure.org/reference/compilation#directlinking

https://clojure.org/reference/compilation

* Conventions for names or code formatting are typically captured by general language
  [_style guides_](https://en.wikipedia.org/wiki/Style_guide),
  which are often overlaid by additional rules specific to projects, companies, or developers.
* See major style guides for
  [Clojure](https://github.com/bbatsov/clojure-style-guide) and
  [Scala](https://docs.scala-lang.org/style).

----------------------------------------------------------------------



![](https://imgs.xkcd.com/comics/lisp_cycles.png)

-------

[<-- previous page](ch1_motivation.md)

[--> next page](ch3_0_functions.md)
