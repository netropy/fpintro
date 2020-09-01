## 2.0 Forms and Expressions

The subsequent exercises teach how to write
[_expressions_](https://en.wikipedia.org/wiki/Expression_(computer_science))
(or [forms](http://www.n-a-n-o.com/lisp/cmucl-tutorials/LISP-tutorial-9.html),
as they are also called in Lisp-like languages).

Most coding exercises are from the tutorial
[Klipse for Kids](http://kids.klipse.tech)
with code given in Clojure and Scala.  Answer notes and "further reading"
pointers provide additional information.

For a summary of Clojure's and Scala's syntax for forming expression, see the
last exercise
TODO: [below](#21-summary)
and these "cheat-sheets":
[Clojure](https://clojure.org/api/cheatsheet),
[Clojure and other Lisp dialects](http://hyperpolyglot.org/lisp),
[Scala](https://docs.scala-lang.org/cheatsheets),
[Scala-to-Java](http://rea.tech/java-to-scala-cheatsheet).

#### 2.0.1 Write arithmetic expressions: [exercise KfK, chapter 1: What is computer programming?](http://kids.klipse.tech/clojure/2016/05/03/programming-kids-1.html)

TODO: HOWTO

Write an expression that calculates ...

Exercise | Clojure | Scala
:-------|:------|:------
1\. 7\*8 | `(* 7 8)` | `7 * 8`
2\. 2\*3\*4\*5 | `(* 2 3 4 5)` | `2 * 3 * 4 * 5`
3\. 2+3+4+5 | `(+ 2 3 4 5)` | `2 + 3 + 4 + 5`

___Notes:___

* Clojure uses
  [_prefix notation_](https://en.wikipedia.org/wiki/Polish_notation)
  in round brackets: `(<operator> <operand> <operand> ...)`;
  (this is a characteristic of all Lisp-like languages).
* Prefix notation allows for multiple operands after arithmetic operators (see
  exercises 2. and 3).
* For arithmetic expressions, Scala generally uses
  [_infix notation_](https://en.wikipedia.org/wiki/Infix_notation)
  as familiar from mathematics: `<operand> <operator> <operand>`
  (which is a characteristic of languages derived from Fortran and Algol).
  Additionally, prefix expressions `<operand><operator>` are used for unary
  operators such as sign and negation (`+`, `-`, `!`, and `~`), for example:
  `-3`.
* Infix notation requires to repeat arithmetic operators between multiple
  operands (see exercises 2. and 3).
* Scala also has a switch to allow writing expressions in
  [_postfix notation_](https://en.wikipedia.org/wiki/Reverse_Polish_notation) of
  the form `<operand> <operator>`, for example: `3 toFloat` (yielding `3.0f`).
  However, postfix expression syntax is not enabled by default.
* Clojure: Operator and operands are separated by a blank (or other
  [white space characters](https://en.wikipedia.org/wiki/Whitespace_character)
  (a comma is also allowed as separator, but rarely used).
* Scala: A blank or other white space character between a binary operator and
  its operands is preferred but optional; for unary operators, the blank
  character is usually dropped.

___Further Reading:___

* For an overview of the structure and evaluation of arithmetic expressions,
  see:
  [functional Clojure](https://clojure.org/guides/learn/syntax#_structure_vs_semantics) vs
  [object-oriented Scala](https://docs.scala-lang.org/tutorials/scala-for-java-programmers.html#numbers-are-objects).

* Scala: postfix notation, that is, `<operand> <operator>` as a shorthand for
  `<operand>.<operator>()`, can be enabled by importing this
  [postix language feature](https://www.scala-lang.org/api/current/scala/language$.html#postfixOps:languageFeature.postfixOps).

* Clojure: Arithmetic operators extend to
  [more than two and even less than two arguments](https://aphyr.com/posts/302-clojure-from-the-ground-up-basic-types).

* Java, Clojure, and Scala share a common set of numeric
  [_data types_](https://en.wikipedia.org/wiki/Data_type),
  for example, `Long` for integral numbers or `Double` for floating-point
  numbers.  The choice of a data type affects the performance or result of
  arithmetic and comparison operations, see
  [exercise 2.0.7](ch2_expressions.md#207-write-comparison-operator-expressions-exercise-kfk-chapter-7-true-or-false-pinocchio) and
  [exercise 2.0.9](TODO).

* Clojure: In addition to operators (functions)
  ['+'](https://clojuredocs.org/clojure.core/+),
  ['*'](https://clojuredocs.org/clojure.core/*) ...,
  there are (slower) variants
  ['+\''](https://clojuredocs.org/clojure.core/+\'),
  ['*\''](https://clojuredocs.org/clojure.core/*\') ...
  that check for arithmetic overflow and auto-promote the result when needed.

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
  greatly reduce the need to use parentheses (see exercise 3.).

___Further Reading:___

* Both, the `<operator>` and `<operand>`s, may themselve be composite
  expressions that evaluate to an
  [operator](https://en.wikipedia.org/wiki/Operator_(computer_programming))
  and an
  [operand](https://en.wikipedia.org/wiki/Operand),
  respectively.

* The operator is usually a
  [function](https://en.wikipedia.org/wiki/Function_(mathematics));
  the operands are called
  [arguments](https://en.wikipedia.org/wiki/Argument_of_a_function)
  of the function.

* Curiously, if the
  [arity](https://en.wikipedia.org/wiki/Arity)
  of operators is fixed (predetermined), then postfix notation eliminates the
  need for parentheses, which allows for a
  [pocket calculator without keys for round brackets](https://en.wikipedia.org/wiki/HP-35).

* Infix, prefix, and postfix notations can be
  [converted into another](https://en.wikipedia.org/wiki/Shunting-yard_algorithm).

#### 2.0.3 Write and use named expressions: [exercise KfK, chapter 3: Giving Names to Expressions](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-3.html).

Expressions can be given a name.  The name is an _identifier_ or a _symbol_ that
refers to the value of the evaluated expression.  Each occurence of the
indentifier is then replaced with the referred value.  A named _constant_ always
yields the same value; a _variable_ can be assigned a different value.

Referring to an expression by a name can be quite useful:
* the name may convey information about the meaning of a value,
* names make it easier to comprehend composite expressions consisting of
  subexpressions,
* a name allows to reference an expression multiple times while maintaining a
  single definition for it.

Identifiers, such as constants and variables have a _scope_, in which code
regions that identifier is visible, and a _duration_, for how long that binding
of a name to a value is maintained.  So-called _global_ identifiers are
accessible anywhere and anytime after their _initialization_.  Yet, programming
languages also offer means to limit the scope or duration to a "local" context.

In Clojure, global constants (and variables) are defined by the form
`(def <name> <expression>)`.

In Scala, constants are declared by `val <name> = expression>`.

Factor out the "common subexpressions" among these forms by assigning them to a
constant ...
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

* Program code of Lisp-like languages shows many more round brackets compared to
  Scala code (see cartoon below [in summary](#21-summary) ;-)
* Clojure: The operator (special form)
  [`def`](https://clojure.org/reference/special_forms#def)
  defines a
  [_global variable_](https://clojure.org/reference/vars):
  - _global_ (or "interned"), because the variable is henceforth known to all
    evaluations anywhere in the code;
  - _variable_, because its value could be changed in a subsequent `def` call.
* Clojure: Practically, however, `def` is used to define a global _constant_.
  Per
  [style guide](https://github.com/bbatsov/clojure-style-guide#dont-flag-constants),
  global variables that are bound to values (and not otherwise marked) are
  by convention _not_ expected to change.
* Clojure: A set of _local constants_ can be defined by operator (special form)
  [`let`](https://clojure.org/reference/special_forms#let):
  - _local_, because the constants (bindings) are only known to a given,
    lexically contained list of expressions;
  - there are additional operators for creating so-called dynamic or
    thread-local bindings (see below).
* Clojure: There are no restrictions to the kind of values to which a constant
  or a variable can be bound; for example, a variable may be first assigned a
  number and then a letter or character sequence.
* Scala: Keyword `val` defines a _constant_, whereas `var` defines a _variable_
  (mnemonic).
* Scala: A constant's or variable's _scope_ is largely determined by _where_ it
  is defined (rather than _how_, as in Clojure).
  For example:
  - The local binding `{ ... { val x = 3 ... } ... }` has `x` only available
    within the nested
    [code block](https://en.wikipedia.org/wiki/Block_(programming))
    between the most inner curly brackets `{ }`.
  - In contrast, a definition `object Test { val y = 4 }` creates a global
    constant that is anywhere accessible as `Test.y`, which is declared part of
    a unique, global object named `Test`.
* Scala: Identifiers, such as variables and constants, have a fixed ("static")
  [_data type_](https://en.wikipedia.org/wiki/Data_type),
  which cannot change; for example, a variable may be defined to only hold
  integral numbers (unlike Clojure, where a variable can be bound to a value of
  any data type).
* Scala: The identifier's data type may be declared with the initial value; for
  example, `var x: Int = 3` defines a variable of type `Int` (for integral
  numbers).  The type information ("ascription") is optional, and hence often
  left out, if it can be inferred from the value.
* Programming languages usually adopt conventions about how to capitalize and
  form composite names, for example:

Example | Informal letter case name | Prevalent in
:-----|:-----|:-----
`noOfWidgets` | ["CamelCase"](https://en.wikipedia.org/wiki/Camel_case) | Java, Scala, C++, (Clojure for certain data types)
`no_of_widgets` | ["snake_case"](https://en.wikipedia.org/wiki/Snake_case) | C, C++
`no-of-widgets` | ["kebab-case"](https://en.wikipedia.org/wiki/Letter_case#Special_case_styles) | Lisp, Clojure
`*no-of-widgets*` | ["*earmuffs*"](https://clojure.org/guides/weird_characters#__code_var_name_code_earmuffs) | Lisp et al for variables with dynamic scope

___Further Reading:___

* Clojure and Scala allow to bind a name to an _unevaluated_ expression, instead
  of its final value, see
  [exercise 2.0.5](ch2_expressions.md#205-write-expressions-without-evaluating-them-exercise-kfk-chapter-5-please-tell-me-whats-your-name).

* Scala: The visibility of a constant or variable definition (that is part of an
  object) can be further restricted by so-called
  [_access modifiers_](http://www.jesperdj.com/2016/01/08/scala-access-modifiers-and-qualifiers-in-detail).

* Scala: For more examples and syntax variants, see
  [definition of variables and constants](https://www.tutorialspoint.com/scala/scala_variables.htm).

* Clojure: Besides special forms
  [`def`)](https://clojuredocs.org/clojure.core/def) for global variables and
  [`let`](https://clojuredocs.org/clojure.core/let) for local constants,
  there are many more operators (macros and special forms) for creating name
  bindings or for assigning variables, for example:
  - [if-let](https://clojuredocs.org/clojure.core/if-let),
    [if-some](https://clojuredocs.org/clojure.core/if-some),
    [when-let](https://clojuredocs.org/clojure.core/when-let),
    [when-some](https://clojuredocs.org/clojure.core/when-some),
    [when-first](https://clojuredocs.org/clojure.core/when-first)
    for conditional bindings that are predicated on a test;
  - [dotimes](https://clojuredocs.org/clojure.core/dotimes)
    for repeated evaluations (loops) with a name bound to integers from 0
    through n-1;
  - [`as->`](https://clojuredocs.org/clojure.core/as-%3E)
    for rebinding a name to intermediate results of listed evaluations;
  - [with-open](https://clojuredocs.org/clojure.core/with-open)
    for binding of names to resources, which are automatically opened before and
    closed after an evaluation;
  - [`binding`](https://clojuredocs.org/clojure.core/binding)
    [with-bindings](https://clojuredocs.org/clojure.core/with-bindings)
    [with-bindings*](https://clojuredocs.org/clojure.core/with-bindings*)
    for creating thread-local, dynamic bindings;
  - [set!`](https://clojuredocs.org/clojure.core/set!),
    [var-set](https://clojuredocs.org/clojure.core/var-set)
    for changing thread-local bindings;
  - [`alter-var-root`](https://clojuredocs.org/clojure.core/alter-var-root)
    for updating global variables in a
    [thread-safe (atomic) manner](https://github.com/bbatsov/clojure-style-guide#alter-var).

* Programming languages differ in how they treat the creation of name bindings:
  - In Clojure and all Lisp-like languages, binding a symbol to a value of an
    expression is itself an expression; the value of that binding expressions
	is usually  a reference to the created variable or constant.
  - In Java-like languages, the definition of a variable or constant is not an
    expression but a
    [statement](https://en.wikipedia.org/wiki/Statement_(computer_science)),
	which yields no value.
  - In Scala, assignments (and initializations) are technically an expression
    yielding a singular and uninteresting value
    ([`Unit`](https://www.scala-lang.org/api/current/scala/Unit.html));
    this information-free return value makes an assignment behave like a
    statement.

* A rich _terminology_ has developed about various aspects of name bindings:
  - a [_constant_](https://en.wikipedia.org/wiki/Constant_(computer_programming))
    is _defined_ or _initialized_ with a value;
  - a [_variable_](https://en.wikipedia.org/wiki/Variable_(computer_science))
    can _hold_ a value and be _assigned_ a new value;
  - a [_symbol_](https://en.wikipedia.org/wiki/Symbol_(programming))
    can be _bound_ to a value or to a variable or another entity;
  - a [_namespace_](https://en.wikipedia.org/wiki/Namespace)
    _groups_ identifiers and helps avoid _name collisions_ by separation from
    other namespaces;
  - an [_identifier_](https://en.wikipedia.org/wiki/Identifier)
    is the _name_ of a constant, variable, symbol, namespace, or other entity;
  - a [_name binding_](https://en.wikipedia.org/wiki/Name_binding)
    is the _current association_ of an identifier or a symbol with a value or
    other entity;
  - a [_scope_](https://en.wikipedia.org/wiki/Scope_(computer_science))
    describes the _visibility_ (code region) and _duration_ (in time) of a name
    binding;
  - [_lexical or static scoping_](https://en.wikipedia.org/wiki/Scope_(computer_science)#Lexical_scoping)
    establishes a name binding for a given code region;
  - [_dynamic scoping_](https://en.wikipedia.org/wiki/Scope_(computer_science)#Dynamic_scoping)
    creates and destroys a name binding based on instructions at runtime;
  - a [_thread_](https://en.wikipedia.org/wiki/Thread_(computing))
    is an execution context that can host its own set of statically and
    dynamically scoped name bindings (automatic and thread-local variables, see
    next).

* The scope (visibility) and duration (storage class) of identifiers can be
  further classified:
  [static](https://en.wikipedia.org/wiki/Static_variable),
  [global](https://en.wikipedia.org/wiki/Global_variable),
  [local or automatic (stack)](https://en.wikipedia.org/wiki/Automatic_variable),
  [thread-local](https://en.wikipedia.org/wiki/Thread-local_storage),
  [class variable](https://en.wikipedia.org/wiki/Class_variable), and
  [instance variable or field](https://en.wikipedia.org/wiki/Instance_variable).

* Programming languages can be loosely grouped by their _type system_:
  - [_Static_ typing](https://en.wikipedia.org/wiki/Type_system#Static_type_checking),
    like Scala: identifiers are declared with a fixed data type that determines
    the set of values that can be held in a variable or constant; for each
    reading or writing of data, the compatibility of types is checked at
    compile-time.
  - [_Dynamic_ typing](https://en.wikipedia.org/wiki/Type_system#Dynamic_type_checking_and_runtime_type_information),
    like clojure: values have a data type in the sense that illegal operations
    are checked and prohibited at runtime; but identifiers such as constants or
    variables do not carry type information, they can bind to values of any
    type.
  - [_Gradual_ typing](https://en.wikipedia.org/wiki/Gradual_typing),
    like [_Typed Clojure_](https://github.com/clojure/core.typed/wiki/User-Guide):
	variables may be optionally given types and the correctness of the typing is
    then checked at compile-time where available.

#### 2.0.4 Write `list` expressions: [exercise KfK, chapter 4: Evaluating Several Expressions](http://kids.klipse.tech/clojure/2016/06/21/programming-kids-4.html).

The input or output of a calculation may be a collection of data, and not just
be a single value (datum).

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

* A [_list_](https://en.wikipedia.org/wiki/List_(abstract_data_type))
  may be either
  - empty or
  - contain elements, including possibly other lists.
* Clojure: The expression `(list ...)` constructs a list collection of the
  provided elements (separated by a space or comma):
  - `list` is a predefined function.  In Lisp-like languages, functions (and
    symbols) typically have lower case names.
  - For essential usage information, see
    [`list` operator](https://clojuredocs.org/clojure.core/list) and
    [list-related functions](https://clojure.org/reference/data_structures#Lists),
    [the empty list `'()` vs `nil`](https://clojure.org/reference/lisps).
* Scala: The expression `List(...)` constructs a list collection of the provided
  elements (separated by comma):
  - `List` is a predefined data type (with a companion object).  In Java-like
    languages, type names typically start upper case.
  - For essential usage information, see
    [Five ways to create a List](https://alvinalexander.com/scala/how-create-scala-list-range-fill-tabulate-constructors),
    methods of the
    [List class](https://www.scala-lang.org/api/current/scala/collection/immutable/List.html)
    and of its
    [companion object](https://www.scala-lang.org/api/current/scala/collection/immutable/List$.html),
    [the empty List "Nil"](https://www.scala-lang.org/api/current/scala/collection/immutable/Nil$.html).
* Clojure and Scala: Creating a list is itself an expression with `list` or
  `List`, respectively, as operator followed by the elements as operands;
  the expression's value is the constructed list.

___Further Reading:___

* Clojure and Scala also offer "Lisp-style" construction and traversal mimicking
  [linked lists](https://en.wikipedia.org/wiki/Linked_list),
  that is, lists as a chain of
  [_conses_](https://www.cs.cmu.edu/Groups/AI/html/cltl/clm/node28.html).
  A _cons_ represents a pair (or record) of
  - a value called "first", "head", or "car" and
  - a reference called "rest", "tail", or "cdr" to the next cons (i.e., list
    element) or the empty list.  Compare Clojure's
    [`cons` function](https://clojuredocs.org/clojure.core/cons),
    [its differences from Lisp](https://8thlight.com/blog/sarah-sunday/2017/01/24/common-lisp-clojure-cons-cells.html),
    and Scala's
    [`::` class](https://www.scala-lang.org/api/current/scala/collection/immutable/$colon$colon.html).

* Incidentally, both Clojure and Scala, also offer _sequences_ as a more
  abstract data type (interface) than lists.  Compare Clojure's
  [`ISeq`](https://clojure.org/reference/sequences)
  with Scala's
  [`Seq`](https://www.scala-lang.org/api/current/scala/collection/Seq.html)
  interface.

* Refresher (mathematics):
  [sets](https://en.wikipedia.org/wiki/Set_(abstract_data_type)) vs.
  [lists](https://en.wikipedia.org/wiki/List_(abstract_data_type)) vs.
  [tuples](https://en.wikipedia.org/wiki/Tuple)
  - sets: variable size, no order, no multiples, homogeneous (if typed):
    `{ 1 2 } = { 2 1 } = { 2 2 1 }`
  - lists: variable size, order counts, multiples allowed, homogeneous (if typed):
    `(list 2 1) != (list 1 2) != (list 1 2 2)`
  - tuples: fixed size, order counts, multiples allowed, heterogeneous (if typed):
    `(1, 2, 'a') != ('a', 2, 1) != ('a', 2, 1, 1)`

* Clojure and Scala, like most programming languages, provide a variety of other
  collection types, like
  [arrays/vectors](https://en.wikipedia.org/wiki/Array_data_structure),
  [maps](https://en.wikipedia.org/wiki/Associative_array), or
  [sets](https://en.wikipedia.org/wiki/Set_(abstract_data_type)).
  Compare
  - [Collections in Clojure](https://clojure.org/reference/data_structures#Collections),
  - [Collections in Scala](https://docs.scala-lang.org/overviews/collections/introduction.html).

* Refresher (mathematics):
  [elements](https://en.wikipedia.org/wiki/Element_(mathematics)),
  [empty set](https://en.wikipedia.org/wiki/Empty_set),
  [subsets](https://en.wikipedia.org/wiki/Subset),
  [power sets](https://en.wikipedia.org/wiki/Power_set),
  [set operations](https://en.wikipedia.org/wiki/Algebra_of_sets),
  [Cartesian product](https://en.wikipedia.org/wiki/Cartesian_product).

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
  empty set can be used as a foundational definition of
  [ordinal numbers](https://en.wikipedia.org/wiki/Von_Neumann_definition_of_ordinals).

#### 2.0.5 Write expressions without evaluating them: [exercise KfK, chapter 5: Please, tell me "what's your name?"](http://kids.klipse.tech/clojure/2016/07/21/chapter-5.html).

In human languages, quotes are used to indicate when to take a word or text
literally and not by its meaning.  For similar purposes, Lisp-like programming
languages offer a `quote` operator, which allows to refer to an expression
itself instead of its evaluated result.  While `quote` renders an expression as
a list of symbols, the `eval` operator does the inverse by taking a list and
evaluating it as an expression, yielding its result.

compute the result of a list expressions whose first element
is an operator symbol may be further manipulated or evaluated at
a later time.

In Lisp-like languages, quoting and evaluation are core concepts with an
extension called quasi-quotes or syntax quotes.  Scala

.  The closest
equivalent in Scala 

For Lisp-like languages, quoting, that is, rendering expressions as lists,
and evaluation, that is, interpreting lists as expressions, are core concepts.


While "quotes" 

without evaluating it.  This allows for passing and
changing that data and some possible evaluation later.


TODO: Clojure `(quote ...)`, `'( ...)`, `(eval ...)`, preferred notation
TODO: Scala anonymous `() =>`, `def <name> = `, call, preferred notation
TODO: Scala: use quasiquotes? NO! inline? PERHAPS.
TODO: Scala side shaky

* Scala: While quoting of expressions is not supported, there is an experimental feature of
  [quasiquotes](https://docs.scala-lang.org/overviews/quasiquotes/intro.html), mostly for use with
  [macros](https://docs.scala-lang.org/overviews/macros/usecases.html).


Form and refer to the expression as it is ...

Exercise | Clojure | Scala
:-------|:------|:------
`+ 3 4` as is | `(quote (+ 3 4))` | `() => 3 + 4`|
... | `'(+ 3 4)` _(preferred)_ | `def x = 3 + 4` _(preferred)_ |
... | `;; => (+ 3 4)` | `// => x: Int` |
`+ 3 4` as is, then evaluate | `(eval (quote (+ 3 4)))` | `(() => 3 + 4)()` |
... | `(eval '(+ 3 4))` _(preferred)_ | `def x = 3 + 4 ; x` _(preferred)_ |
... | `;; => 7` | `// => res0: Int = 7` |
`3, 4` as is | `(quote (3 4))` | `3 -> 4` |
... | `'(3 4)` _(preferred)_ | `(3, 4)` _(preferred)_ |
... | `;; => (3 4)` | `` // => res1: (Int, Int) = (3,4)` |
`3, 4` as is, then try evaluate | `(eval (quote (3 4)))` | |
... | `(eval '(3 4))` _(preferred)_ |`(3, 4)()` _(preferred)_ |
... | `;; => error: ClassCastException ...` | `// =>  error: (Int, Int) does not take parameters` |

___Notes:___

* Clojure: Preventing the immediate evaluation of an expression is itself an
  expression.  The operator (special form)
  [`quote`](https://clojure.org/reference/special_forms#quote) or
  [clojure.core/quote](https://clojuredocs.org/clojure.core/quote)
  indicates not to evaluate the subsequent expressions.
  - Usually, the short form (reader macro)
    [`'( ...)`](https://clojure.org/reference/reader#_quote)
    is preferred.
* Clojure: Conversely, calling the evaluation of an expression is itself also an
  expression.  The operator (function)
  [`eval`](https://clojuredocs.org/clojure.core/eval)
  submits an expression (form data) to the interpreter for evaluation and
  returns the result.

TODO: unclear

* Clojure: When the operator symbol `+` is dropped from the quote expression
  `'(+ 3 4)`, the list is formed as `(3 4)`.
  Therefore, _quoting is convenient to form lists of values_ (or expressions)
  without use of operators like `list` or `cons`.
* Clojure: However, any such list of just values cannot be further evaluated,
  since `eval` expects lists to begin with an operator expression (prefix
  notation).  The result is an error (ClassCastException) when the first list
  element is tried to be interpreted as an operator.

TODO: WRONG

* Scala: Quoting of expressions is not directly supported.  However, see next
  for related features.

___Further Reading:___

TODO: check link

* Clojure and Scala: Another language feature that allows to construct (but not execute) computations are _lambdas_ or _anonymous functions_, see
  [Type Signature, Arity, and Nullary Functions](ch3_1_formulas_and_functions#type-signature-arity-and-nullary-functions)
  for notes and exercises.

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
  [`apply`](https://clojuredocs.org/clojure.core/apply),
  which invokes a function on a list of arguments, for example: `(apply (eval '+) '(3 4))` or `(apply + '(3 4))`.
  For more on the general concept, see
  [eval](https://en.wikipedia.org/wiki/Eval) and
  [apply](https://en.wikipedia.org/wiki/Apply).



* Languages in which "code" looks similar to "data" (in general, where code resembles its
  [abstract syntax tree](https://en.wikipedia.org/wiki/Abstract_syntax_tree)) are called
  [homoiconic](https://en.wikipedia.org/wiki/Homoiconicity).

#### 2.0.6 Write boolean operator expressions.

TODO: avoid links here?

The [Boolean data type](https://en.wikipedia.org/wiki/Boolean_data_type)
consists of just two values `true` and `false`.
Expressions yielding a Boolean value can be combined by logical operators such as _not_ (negation), _and_ (conjunction), _or_ (disjunction).
How these operators "work" can be seen by their so-called
[_truth table_](https://en.wikipedia.org/wiki/Truth_table),
which shows the respective result for each `true`/`false` combination of their operands.

Form the not/and/or-expressions below and compare them to `true` or `false` such that the entire result is `true` ...

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

* In Scala, The `&&` and `||` operators (and other languages) have lower precedence than `==` or `!=`.
  Hence, round brackets are needed to group operations.  For example,
  - `false && false == false` is inferred as `false && (false == false)` yielding `false`;
  - `(false && false) == false` is the intended expression yielding `true`.

TODO: and or lazy returning last/first value

___Further Reading:___

* A look at how other languages model Boolean values helps understanding Clojure's and Scala's design:
  - Lisp originally did not introduce constants or a data type for true/false (but some Lisp-dialects have, for example, _Scheme_).
    Instead, any test for a boolean outcome (`cond`, `and`, `or`, and other conditionals) counts the value
    [`nil` or `'()` as `false`](http://www.n-a-n-o.com/lisp/cmucl-tutorials/LISP-tutorial-17.html).
    While the commonly predefined symbol `t` is often used to indicate `true`, any non-`nil` value counts as `true`, in fact.
  - C prior ISO C99 also did not have a primitive (or built-in) data type for Booleans.
    In conditionals and loops (`if`, `while`, `for`), a boolean test treats an
    [integral value `0` as `false`](http://c-faq.com/bool/index.html),
    while any non-zero value means `true`.
    Library header files often provided some macro/`typedef` aliases `BOOL`, `FALSE`, `TRUE`.
  - Java defines a primitive data type
    [`boolean`](https://docs.oracle.com/javase/specs/jls/se8/html/jls-4.html#jls-4.2.5)
    for use in conditionals, loops, or as variables/parameters/results/fields etc.
    However, each primitive type `xyz` is also mirrored by a
    [reference type](https://docs.oracle.com/javase/specs/jls/se8/html/jls-4.html#jls-4.3),
    its so-called "boxed" or "wrapper" class `\[java.lang.\]Xyz`, which encapsulates values as
    [instances or objects](https://docs.oracle.com/javase/specs/jls/se8/html/jls-4.html#jls-4.3.1).
    Hence, the standard class
    [`\[java.lang.\]Boolean`](https://docs.oracle.com/javase/8/docs/api/java/lang/Boolean.html)
    substitutes for primitive type `boolean` where objects are required, for example, for use in collections.
  - Note, however, that (unlike Clojure's `nil` value) Java does not treat the
    [`null` reference](https://docs.oracle.com/javase/specs/jls/se8/html/jls-4.html#jls-4.1)
    of wrapper class `Boolean` as `false`.
    Despite the automatic conversion between primitive and wrapper types, so-called
    [autoboxing](https://docs.oracle.com/javase/tutorial/java/data/autoboxing.html),
    there is no implicit conversion from `null` to `false` (an attempt to unbox `null` raises a `NullPointerException`).

TODO:...

* Clojure defines literals `true`, `false`, and `nil`.

(which map to Java's wrapper type `java.lang.Boolean`).

* Clojure defines symbols uses Java's wrapper type `java.lang.Boolean, the value

* In Clojure, like in other Lisps, the value
  [`nil`](https://clojure.org/reference/data_structures#nil)
  also means `false` in the context of _conditionals_ (variants of
  [`if`](https://clojure.org/reference/special_forms#if),
  [`when`](https://clojuredocs.org/clojure.core/when)
  [`cond`](https://clojuredocs.org/clojure.core/cond)).
  Conversely, any value that is not `nil` and not `false` is treated as `true`.
*

Unlike in other Lisps, however,
  [`nil` differs from the empty list `'()`](https://clojure.org/reference/lisps),
  which is a
  [list-specific singleton](https://clojuredocs.org/clojure.core/empty)
  in Clojure.

* In Clojure, where `nil` is not to be conflated with `false`, the boolean functions
  [`nil?`](https://clojuredocs.org/clojure.core/nil?),
  [`false?`](https://clojuredocs.org/clojure.core/false?), and
  [`true?`](https://clojuredocs.org/clojure.core/true?)
  only test

^bad TODO

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

[_not_ (negation)](https://en.wikipedia.org/wiki/Negation),
[_and_ (conjunction)](https://en.wikipedia.org/wiki/Logical_conjunction),
[_or_ (disjunction)](https://en.wikipedia.org/wiki/Logical_disjunction).

https://clojuredocs.org/clojure.core/bit-and
https://clojuredocs.org/clojure.core/bit-or
https://clojuredocs.org/clojure.core/bit-not

#### 2.0.7 Write comparison operator expressions: [exercise KfK, chapter 7: True or False (Pinocchio)](http://kids.klipse.tech/clojure/2016/08/05/chapter-7.html).

Numbers can be compared for being _equal_, _not equal_, _less than_, _less/equal than_, _greater than_, and _greater/equal than_.
These [relational operators](https://en.wikipedia.org/wiki/Relational_operator) return `true` or `false`.

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

TODO: check link

* Scala's infix expressions look simpler and cleaner than the prefix forms in Clojure.
* But then, prefix notation allows for multiple arguments, whereas infix notation requires the use of boolean operators
  (see [exercise 2.0.6](ch2_expressions.md#207-write-boolean-operator-expressions)),
  for example:
  - Clojure: `(< 1 2 3)`
  - Scala: `1 < 2 && 2 < 3`
* Java, Clojure, and Scala share a common set of
  [_data types_](https://en.wikipedia.org/wiki/Data_type)
  for numbers, for example, `Long` for integral numbers or `Double` for floating-point numbers.
  The choice of a data type affects the performance or result of arithmetic and comparison operations, see
  [exercise 2.0.9](TODO).
* Equality of numeric values is tested by operator `==`, for example:
  - Clojure: `(== 3 3.0)` yields `true`, `(== 2 3)` yields `false`;
  - ... _however_: `(= 3 3.0)` yields `false`, function '=' (unlike `==`) does not extend equality to different numeric types!
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
  - ... _however_: `(not= 3 3.0)` yields `true`, function `not=` is equivalent to `(not (= 3 3.0))`.

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
    [`identical?`](https://clojuredocs.org/clojure.core/identical?)
    tests two objects of any type if they are the same.
  - Scala: method
    [`eq`](https://www.scala-lang.org/api/current/scala/AnyRef.html#eq(x$1:AnyRef):Boolean)
    tests objects of reference type (`scala.AnyRef`) if they are the same.
  - Scala: `eq` cannot be applied to value types (`scala.AnyVal`); instead, use operator `==` to compare for value equality.

* Test for _equality_:
  - Clojure: for numbers, function
    [`==`](https://clojuredocs.org/clojure.core/==)
    compares for value equality across different types.  It cannot be applied to non-numbers (instances not implementing `java.lang.Number`).
  - Clojure: for non-numbers, function
    [`=`](https://clojuredocs.org/clojure.core/=)
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
    [`not=`](https://clojuredocs.org/clojure.core/not=)
    is the negation of `=`.
  - Scala: operator
    [`!=`](https://www.scala-lang.org/api/current/scala/AnyRef.html#ne(x$1:AnyRef):Boolean)
    is the negation of `==` on `Any` type.

* Data types for which there is an _ordering_ may also offer the relational operators and allow for the sorting of values.  See
  - Clojure: function
    [compare](https://clojuredocs.org/clojure.core/compare)
  - Scala: methods and types
    [Ordered.compare](https://www.scala-lang.org/api/current/scala/math/Ordered.html#compare(that:A):Int)
    [Ordering.compare](https://www.scala-lang.org/api/current/scala/math/Ordering.html#compare(x:T,y:T):Int)

* Refresher (mathematics):
  [equality](https://en.wikipedia.org/wiki/Equality_(mathematics)),
  [inequality](https://en.wikipedia.org/wiki/Inequality_(mathematics)), and
  [order relationships](https://en.wikipedia.org/wiki/Order_theory).

#### 2.0.8 Write string operator expressions.

#### 2.0.9 Write numerical type expressions.

* numbers can be of different data types, for example
  - `3` is an [integral number](https://en.wikipedia.org/wiki/Integer_(computer_science)) of type `Int`, `Integer`, or `Long`;
  - `3.0` is a [floating point number](https://en.wikipedia.org/wiki/Floating-point_arithmetic) of type `Float` or `Double`;
  - `3M` or `BigDecimal(3)` is an [arbitrary-precision number](https://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic)


  [_data types_](https://en.wikipedia.org/wiki/Data_type)

* Clojure: In addition to operators (functions)
  ['+'](https://clojuredocs.org/clojure.core/+),
  ['*'](https://clojuredocs.org/clojure.core/*) ..., there are (slower) variants
  ['+\''](https://clojuredocs.org/clojure.core/+\'),
  ['*\''](https://clojuredocs.org/clojure.core/*\') ...
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

can remove 'ch2_expressions.md'#... ?

----------------------------------------------------------------------


![](https://imgs.xkcd.com/comics/lisp_cycles.png)

-------

[<-- previous page](ch1_motivation.md)

[--> next page](ch3_0_functions.md)
