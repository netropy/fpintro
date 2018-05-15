### 3.1 Formulas and Functions

Most of the time, we want to write a calculation not with fixed,
["hard-coded"](https://en.wikipedia.org/wiki/Hard_coding) numbers, but in a _general_ form using
[variables](https://en.wikipedia.org/wiki/Variable_(mathematics)) in mathematics, like `(x + y) * z`.
In computing and other areas of science, this is often called a
["formula"](https://en.wikipedia.org/wiki/Formula).
Writing computations as formulas has several advantages, mainly:

1. The abstract form using _variables_ highlights the essence of the computation in a concise way.
2. A formula may be given a _name_, under which it then can be referred to.
3. A formula can be _applied_ by substituting numbers for its variables and calculating a result.

These informal notions have corresponding, technical terms in computing (and mathematics or logic):

* "Formula" -> [anonymous function](https://en.wikipedia.org/wiki/Anonymous_function), function literal, lambda abstraction, or
  [lambda expression](https://en.wikipedia.org/wiki/Lambda_calculus).
* "Defining a formula" -> [function definition](https://en.wikipedia.org/wiki/Function_(mathematics)),
  [user-defined operators](https://en.wikipedia.org/wiki/Operator_(computer_programming)), or
  parametrization as some form of
  [abstraction](https://en.wikipedia.org/wiki/Abstraction_(computer_science)).
* "Applying a formula" -> [function application](https://en.wikipedia.org/wiki/Function_application),
  [function call](https://en.wikipedia.org/wiki/Subroutine), or
  [function evaluation](https://en.wikipedia.org/wiki/Evaluation_strategy).
* "Variables" -> [parameters](https://en.wikipedia.org/wiki/Parameter_(computer_programming)), formal parameters, or
  [bound variables](https://en.wikipedia.org/wiki/Free_variables_and_bound_variables).
* "Numbers" -> [arguments](https://en.wikipedia.org/wiki/Argument_of_a_function),
  [operands](https://en.wikipedia.org/wiki/Operand), actual parameters, or
  [values](https://en.wikipedia.org/wiki/Value_(computer_science)) (in general).

Examples:

definition/application | Math Notation | Clojure (et.al.) | Scala (et.al.)
:----|:----|:----|:----
def | `a = 3`              | `(def a 3)`             | `val a = 3`
def | `f(x) = x + 4`       | `(def f #(+ % 4))`      | `def f(x: Int) = x + 4`
def | `g: x -> x + 5`      | `(defn g [x] (+ x 5))`  | `val g: Int => Int = x => x + 5`
app | `f(a) = 3 + 4 = 7`   | `(f a)        ;; => 7`  | `f(a)                    // => 7`
app | `f(2) = 2 + 4 = 6`   | `(f 2)        ;; => 6`  | `f(2)                    // => 6`
app | `f(9) = 9 + 4 = 13`  | `(f 9)        ;; => 13` | `f(9)                    // => 13`
app | `(x -> x + 4)(2)`    | `(#(* % 3) 2) ;; => 6`  | `((x: Int) => x + 4)(2)  // => 6`
app | `g(a) = 3 + 5 = 8`   | `(g a)        ;; => 8`  | `g(a)                    // => 8`

___Notes:___

* Clojure and Scala offer multiple notations (short forms) by which an anonymous or named function can be defined.
* Functions should be given a name that's short yet meaningful (chosing a good name can be a task in itself).
* Programming languages and projects typically have conventions about how to form composite function names, like
  ["kebab-case"](https://en.wikipedia.org/wiki/Letter_case#Special_case_styles),
  ["snake_case"](https://en.wikipedia.org/wiki/Snake_case), or
  ["CamelCase"](https://en.wikipedia.org/wiki/Camel_case), see
  [exercise 2.0.3](ch2_expressions.md#203-write-and-use-named-expressions-exercise-kfk-chapter-3-giving-names-to-expressions).

___Further Reading:___

* If names can be assigned to both, data and functions, what happens if there's a name "clash" between them?
  It's a curiosity that both older languages, Lisp and Java, allow for data and a function to be given the same name (the usage/context decides which one is meant).  In contrast, both younger languages forbid such a case, both data and functions "share the same namespace"; see
  Clojure following [Scheme as a Lisp-1 language](https://en.wikipedia.org/w/index.php?title=Common_Lisp&oldid=402600249#The_function_namespace) and
  namespaces in [Scala vs Java](https://quizful.com/theory/447/scala_namespaces_for_definitions).

####  3.1.1 Define and evaluate functions: [exercise KfK, chapter 6: Functions (Happy birthday)](http://kids.klipse.tech/clojure/2016/07/30/chapter-6.html).

Define and apply a _named_ or _anonymous_ function ("formula") ...
1. write a function hours->minutes transforming hours into minutes
2. use hours->minutes to calculate how many minutes there are in `12` hours
3. apply just the formula in 1\. (without a function name) to argument `12`
4. write a function minutes->hours transforming minutes into hours
5. use minutes->hours to calculate how many hours there are in `6000` minutes
6. apply just the formula in 4\. (without a function name) to argument `6000`

Exercise | Clojure | Scala
:-------|:------|:------
1\. | `(def hours-to-minutes #(* % 60))` | `val hoursToMinutes = (h :Int) => h * 60`
... | `(def hours-to-minutes (fn [h] (* h 60)))` | `val hoursToMinutes: Int => Int = h => h * 60`
... | `(defn hours-to-minutes [h] (* h 60))` | `def hoursToMinutes(h: Int): Int = h * 60`
2\. | `(hours-to-minutes 12)` | `hoursToMinutes(12)`
... | `(apply hours-to-minutes (list 12))` |
3\. | `(#(* % 60) 12)` | `((h :Int) => h * 60)(12)`
4\. | `(def minutes-to-hours #(/ % 60))` | `val minutesToHours = (m :Int) => m / 60`
... | `(def minutes-to-hours (fn [m] (/ m 60)))` | `val minutesToHours: Int => Int = m => m / 60`
... | `(defn minutes-to-hours [m] (/ m 60))` | `def minutesToHours(m: Int): Int = m / 60`
5\. | `(minutes-to-hours 6000)` | `minutesToHours(6000)`
6\. | `(#(/ % 60) 6000)` | `((m :Int) => m / 60)(6000)`

___Notes:___

* Clojure as well as Scala offer multiple notations for defining and applying functions.
* In Clojure, named functions are typically  written like this: `(defn add [x y] (+ x y))`.
* In Scala, named functions are typically  written like this: `def add(x: Int, y: Int): Int = x + y`.
* In Clojure, short anonymous functions are typically  written like this: `#(+ %1 %2)`.
* In Scala, short anonymous functions are typically  written like this: `(x: Int, y: Int) => x + y` (often, the type ascription can be dropped).
* Clojure also offers an explicit `apply` operator which takes a list of function arguments (ie. `apply` needs `(list ...)` or ` '(...) ` )

### 3.2 Type Signature, Arity, and Nullary Functions

#### Type Signatures

The [_type signature_](https://en.wikipedia.org/wiki/Type_signature) of a function (or formula) lists the
[data types](https://en.wikipedia.org/wiki/Data_type) of the parameters and the result.
Similar as to data values having (simple) types, the signature defines a
[function type](https://en.wikipedia.org/wiki/Function_type).

#### Arity

The [_arity_](https://en.wikipedia.org/wiki/Arity) of a function (or formula) is the number of its
[parameters](https://en.wikipedia.org/wiki/Parameter_(computer_programming)).

Arity | Function/Operator is called ...
:-----|:-----
0 | [nullary](https://en.wikipedia.org/wiki/Arity#Nullary)
1 | [unary](https://en.wikipedia.org/wiki/Unary_operation)
2 | [binary](https://en.wikipedia.org/wiki/Binary_function)
3 | [ternary](https://en.wikipedia.org/wiki/Ternary_operation)
n | [_n_-ary]

Nullary functions present an interesting
[edge case](https://en.wikipedia.org/wiki/Edge_case).
Since a nullary function takes no
[arguments](https://en.wikipedia.org/wiki/Argument_of_a_function),
the result (if any) cannot depend upon input values.
The possibilities for a nullary function are:
1. Any call raises an error, similarly to situations where there's no defined result, for example,
  [integer division by zero](https://en.wikipedia.org/wiki/Division_by_zero).
  Mathematically, this corresponds to the
  [empty function](https://en.wikipedia.org/wiki/Empty_function), whose
  [domain](https://en.wikipedia.org/wiki/Domain_of_a_function) and
  [image](https://en.wikipedia.org/wiki/Image_(mathematics)) are the
  [empty set](https://en.wikipedia.org/wiki/Empty_set).
2. A call always returns the same result, that is, it behaves like a
  [constant function](https://en.wikipedia.org/wiki/Constant_function);
3. A call returns a value that involves the current
  [state](https://en.wikipedia.org/wiki/State_(computer_science)) of "external" (also called "free" or "unbound")
  [variables](https://en.wikipedia.org/wiki/Variable_(computer_science));
  if the state of such variables changes between function calls, different results may occur each time.
  Such behaviour would not represent a mathematical function, as the uniqueness of the result is no longer given.

An interesting use case of nullary functions is to _provide_ a computation that is to be executed at a later time.
The constant function defines a computation (case 2\.), which is only evaluated when called (in case of a nullary function, with no arguments).
Note that this use case is somewhat similar to the `quote` operator in Lisp-based languages from
[excercise 2.0.5](ch2_expressions.md#205-write-expressions-without-evaluating-them-exercise-kfk-chapter-5-please-tell-me-whats-your-name).
Unlike `quote`, however, the ability to define, pass as argument, and later call functions (or
[function objects](https://en.wikipedia.org/wiki/Function_object)) is supported by most programming languages.

A case 3\. example of a function returning different results is a "random number generator".  Upon each call, a new
[pseudorandom number](https://en.wikipedia.org/wiki/Pseudorandomness) is generated (from internal machine state) and returned, for example, Scala's
[util.Random.nextInt](https://www.scala-lang.org/api/2.12.0/scala/util/Random.html#nextInt(\):Int):
```scala
scala> util.Random.nextInt() // => 977507952
scala> util.Random.nextInt() // => -1115536553
scala> util.Random.nextInt() // => 1950804395
```

___Further Reading:___

* The curious case of nullary functions highlights a difference between mathematics and computing:
  - A [mathematical function](https://en.wikipedia.org/wiki/Function_(mathematics)) `f` is defined by its
    set of ordered pairs `(x, f(x))`, also called its
    [graph](https://en.wikipedia.org/wiki/Graph_of_a_function);
    [domain](https://en.wikipedia.org/wiki/Domain_of_a_function) and
    [codomain](https://en.wikipedia.org/wiki/Codomain) may be
    [infinite sets](https://en.wikipedia.org/wiki/Infinite_set).
  - In computing, a function, procedure, or
    [subroutine](https://en.wikipedia.org/wiki/Subroutine) implements an
    [algorithm](https://en.wikipedia.org/wiki/Algorithm), which specifies to some degree the "how" of a calculation;
    this allows for algorithms to be
    [nondeterministic](https://en.wikipedia.org/wiki/Nondeterministic_algorithm),
    [probabilistic](https://en.wikipedia.org/wiki/Randomized_algorithm), or even
    [failing to produce a result](https://en.wikipedia.org/wiki/Divergence_(computer_science)) for certain inputs;
    all [data values and ranges](https://en.wikipedia.org/wiki/Value_(computer_science)) are finite;
    the physical resources of time, space, and energy, required for any computation, are limited.

* To further illustrate the last point, some programming languages (like C++) provide fine-grained control over:
  - if and when arguments expressions are evaluated,
  - how argument values are passed into a function call,
  - when and how the values of "unbound" or "free" variables are captured,
  - in what order subexpressions are evaluated,
  - how the result is returned, or
  - how an error is signalled.

#### 3.2.1 Try out what happens if a function call's number of arguments does not match the arity.

__TODO__: example...

#### 3.2.2 Try out what happens if a function call's argument type does not match the signature.

__TODO__: example...

#### 3.2.3 Write the computation of [excercise 2.0.5](ch2_expressions.md#205-write-expressions-without-evaluating-them-exercise-kfk-chapter-5-please-tell-me-whats-your-name) as an anonymous, nullary function.

Exercise | Clojure | Scala
:-------|:------|:------
`3 + 4` as it is | `#(+ 3 4)` | `() => 3 + 4` |
... | `;; => #object[user$eval1853$fn_..."]` | `// => $$Lambda$1070...` |
`3 + 4` as it is, then evaluate | `(#(+ 3 4))` | `(() => 3 + 4)()` |
... | `;; => 7` | `// => 7` |

#### 3.2.4 Draw some pseudorandom numbers between `0 .. 1000`.

Hint: See the documentation of Clojure's function
[rand-int](https://clojuredocs.org/clojure.core/rand-int)
and Scala's function
[nextInt](https://www.scala-lang.org/api/current/scala/util/Random$.html#nextInt(n:Int\):Int)

Clojure | Scala
:-------|:------
`(rand-int 1000) ;; => 271` | `util.Random.nextInt(1000) // => 808`
`(rand-int 1000) ;; => 979` | `util.Random.nextInt(1000) // => 340`
`(rand-int 1000) ;; => 6`   | `util.Random.nextInt(1000) // => 967`

-----------------

[<-- previous page](ch3_0_functions.md)

[--> next page](ch3_2_more_function_exercises.md)
