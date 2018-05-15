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

* "Formula" -> [anonymous function](https://en.wikipedia.org/wiki/Anonymous_function), function literal, lambda abstraction/expression, or just
  ["lambda"](https://en.wikipedia.org/wiki/Lambda_calculus).
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

definition/application | Math Notation | Clojure | Scala
:----|:----|:----|:----
 1\. def     | `x \|-> x - 2`                | `#(- % 2)`                  | `(x: Int) => x - 2`
 2\. def     | `(x, y) \|-> x - y`           | `#(- %1 %2)`                | `(x: Int, y: Int) => x - y`
 3\. def     | `f: x \|-> x + 4`             | `(def f #(+ % 4))`          | `val f = (x: Int) => x + 4`
 4\. def     | `g(x) := x + 5`               | `(defn g [x] (+ x 5))`      | `def g(x: Int) = x + 5`
 5\. def     | `h: (x, y) \|-> x * y`        | `(defn h [x, y] (* x y))`   | `def h(x: Int, y: Int) = x * y`
 6\. def     | `i: () \|-> 5`                | `(defn i [] 5)`             | `def i(): Int = 5`
 8\. app     | `f(2) = 2 + 4 = 6`            | `(f 2)             ;; => 6` | `f(2)                               // => 6`
 9\. app     | `f(9) = 9 + 4 = 13`           | `(f 9)             ;; => 13`| `f(9)                               // => 13`
10\. app     | `g(3) = 3 + 5 = 8`            | `(g 3)             ;; => 8` | `g(3)                               // => 8`
11\. app     | `h(3, 4) = 12`                | `(h 3 4)           ;; => 12`| `h(3, 4)                            // => 12`
12\. app     | `i() = 5`                     | `(i)               ;; => 5` | `i()                                // => 5`
13\. def+app | `(x \|-> x + 3)(1) = 4`       | `(#(%1 + 3) 1)     ;; => 4` | `((x: Int) => x + 3)(1)             // => 4`
14\. def+app | `(x, y \|-> x - y)(5, 3) = 2` | `(#(- %1 %2) 5 3)  ;; => 2` | `((x: Int, y: Int) => x - y)(5, 3)  // => 2`

___Notes:___

* Clojure and Scala offer multiple notations, short forms, for defining a function (see 3. and 4.) (some variants of definition/application not shown here).
* A function can remain anonymous ("lambda"), that is, just defining the mapping of input to output (1., 2.); or it can be defined with a name, under which it may then be called (4. - 6.).
* The typical use case for lambdas is to pass them as arguments to other functions (which is not shown here), but they can also be assigned a name (3.) and then called later (10.).
* In Clojure, the `defn` form is usually preferred (4. - 6.), except for short lambdas (1., 2.).
* In Scala, the `def` form is usually preferred (4. - 6.), except for short lambdas (1., 2.) (technically, `def` defines a _method_, see _Further Reading_ below, if interested).
* In Scala, the type ascription `: Int` (1. - 6.) on the parameters `(x: Int) => ...` or the result `(...): Int` is not needed when it can be inferred.
* Functions may take one argument (1., 3., 4., 13.), two arguments (2., 5., 14.), zero arguments (6.), or any other positive number.
* Functions should be given a name that's short yet meaningful (sometimes a challenge).
  For example, these two function names, `miles-to-meters` and `meters-to-miles`, make it clear "what goes in" and "what comes out" (though, some might prefer singular units like `meter`).
* Programming languages typically have conventions about how to form composite function names, like
  ["kebab-case"](https://en.wikipedia.org/wiki/Letter_case#Special_case_styles),
  ["snake_case"](https://en.wikipedia.org/wiki/Snake_case), or
  ["CamelCase"](https://en.wikipedia.org/wiki/Camel_case), see
  [exercise 2.0.3](ch2_expressions.md#203-write-and-use-named-expressions-exercise-kfk-chapter-3-giving-names-to-expressions).

___Further Reading:___

* Since names can be assigned to both, data and functions, what happens if there's a name "clash" between them?
  Curiously, both older languages, Lisp and Java, allow for data and a function to be given the same name (the usage/context decides which one is meant).
  Yet, both younger languages forbid such a case, both data and functions "share the same namespace"; see
  Clojure following [Scheme as a Lisp-1 language](https://en.wikipedia.org/w/index.php?title=Common_Lisp&oldid=402600249#The_function_namespace) and
  [namespaces in Scala vs Java](https://quizful.com/theory/447/scala_namespaces_for_definitions).

* In computing, there are a couple of technical terms that refer to functions.  However, there are relevant yet subtle differences, see
  [subroutine](https://en.wikipedia.org/wiki/Subroutine),
  [method](https://en.wikipedia.org/wiki/Method_(computer_programming)),
  [lambda](https://en.wikipedia.org/wiki/Anonymous_function),
  [closure](https://en.wikipedia.org/wiki/Closure_(computer_programming)),
  [function object](https://en.wikipedia.org/wiki/Function_object).

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

* Clojure and Scala offer multiple notations for defining and applying functions (see [above](ch3_1_formulas_and_functions.md)).
  - In Clojure, named functions are often written as `(defn add [x y] (+ x y))` and short lambdas as `#(+ %1 %2)`.
  - In Scala, named functions are often written as `def add(x: Int, y: Int): Int = x + y` and short lambdas as `(x, y) => x + y` or even shorter `_ + _` (when the types can be inferred).
* Clojure also offers an explicit `apply` operator which takes a function name and a list of arguments (for example, `(apply f '(2 3))`).

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

* Many programming languages also support to define
  - multi-arity functions per [overloading](https://en.wikipedia.org/wiki/Function_overloading), which accept a varying but predefined number of arguments,
  - [variadic functions](https://en.wikipedia.org/wiki/Variadic_function), which accept a variable number of arguments.

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

Both, Clojure and Scala, report an error (in form of an exception) if too few or too many arguments are provided.

```clojure
user=> (defn g [x] (+ x 5))
#'user/g

user=> (g)
ArityException Wrong number of args (0) passed to: user/g  clojure.lang.AFn.throwArity (AFn.java:429)

user=> (g 2)
7

user=> (g 2 3)
ArityException Wrong number of args (2) passed to: user/g  clojure.lang.AFn.throwArity (AFn.java:429)
```

```scala
scala> def g(x: Int) = x + 5
g: (x: Int)Int

scala> g()
<console>:13: error: not enough arguments for method g: (x: Int)Int.

scala> g(2)
res18: Int = 7

scala> g(2, 3)
<console>:13: error: too many arguments (2) for method g: (x: Int)Int
```
___Further Reading:___

* Clojure and Scala allow to define functions that take a varying, predefined or unknown, number of arguments.
  - For Scala examples, see multi-arity functions per [overloading](https://www.javatpoint.com/scala-method-overloading),
    [variadic functions](https://alvinalexander.com/scala/how-to-define-methods-variable-arguments-varargs-fields).
  - For Clojure examples, see [multi-arity functions](ahttp://clojure-doc.org/articles/language/functions.html#multi-arity-functions),
    [variadic-functions](http://clojure-doc.org/articles/language/functions.html#variadic-functions).

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
