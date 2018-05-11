### 3.1 Formulas and Functions

Most of the time, we want to write a calculation not with fixed,
["hard-coded"](https://en.wikipedia.org/wiki/Hard_coding) numbers, but in a _general_ form using
[variables](https://en.wikipedia.org/wiki/Variable_(mathematics)) in mathematics, like `(x + y) * z`.
In computing and other areas of science, this is often called a
["formula"](https://en.wikipedia.org/wiki/Formula).
Writing computations as formulas has several advantages, mainly:

1. The abstract form using _variables_ highlights the essence of the computation in a concise way.
2. A formula may be given a _name_, under which it then can be referred to, used, and discussed.
3. A formula can be _applied_ by substituting numbers for its variables and calculating a result.

These so far informally described concepts have corresponding, technical terms in computing (and mathematics or logic).  Take a look:

* "Formula" -> [anonymous function](https://en.wikipedia.org/wiki/Anonymous_function), function literal, lambda abstraction, or
  [lambda expression](https://en.wikipedia.org/wiki/Lambda_calculus).
* "Defining a formula" -> [function definition](https://en.wikipedia.org/wiki/Function_(mathematics)),
  [user-defined operators](https://en.wikipedia.org/wiki/Operator_(computer_programming)),
  parametrization, or
  [abstraction](https://en.wikipedia.org/wiki/Abstraction_(computer_science)).
* "Applying a formula" -> [function application](https://en.wikipedia.org/wiki/Function_application),
  [function call](https://en.wikipedia.org/wiki/Subroutine), or
  [function evaluation](https://en.wikipedia.org/wiki/Evaluation_strategy).
* "Variables" -> [parameters](https://en.wikipedia.org/wiki/Parameter_(computer_programming)), formal parameters, or
  [bound variable](https://en.wikipedia.org/wiki/Free_variables_and_bound_variables).
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

* Some programming languages offer multiple notations (short forms) by which an anonymous or named function can be defined.
* Functions should be given a name that's short yet meaningful (chosing a good name can be a task in itself).
* Programming languages and projects typically have conventions about how to form composite function names, like
  ["kebab-case"](https://en.wikipedia.org/wiki/Letter_case#Special_case_styles),
  ["snake_case"](https://en.wikipedia.org/wiki/Snake_case), or
  ["CamelCase"](https://en.wikipedia.org/wiki/Camel_case), see
  [exercise 2.0.3](ch2_expressions.md#203-write-and-use-named-expressions-exercise-kfk-chapter-3-giving-names-to-expressions).

___Further Reading:___

* The [_arity_](https://en.wikipedia.org/wiki/Arity) of a function (or formula) is the number of its
  [parameters](https://en.wikipedia.org/wiki/Parameter_(computer_programming)).

Arity | Function/Operator is called ...
:-----|:-----
0 | [nullary](https://en.wikipedia.org/wiki/Arity#Nullary)
1 | [unary](https://en.wikipedia.org/wiki/Unary_operation)
2 | [binary](https://en.wikipedia.org/wiki/Binary_function)
3 | [ternary](https://en.wikipedia.org/wiki/Ternary_operation)
n | [_n_-ary]

* As listed, a function may take no
  [arguments](https://en.wikipedia.org/wiki/Argument_of_a_function).
  This often (but not always) means that the function returns a
  [constant](https://en.wikipedia.org/wiki/Constant_(mathematics)) value while deferring the calculation until being called.
  Also see excercise
  [2.0.5 Write expressions without evaluating them](ch2_expressions.md#205-write-expressions-without-evaluating-them-exercise-kfk-chapter-5-please-tell-me-whats-your-name).

* The [_type signature_](https://en.wikipedia.org/wiki/Type_signature) of a function (or formula) lists the
  [data types](https://en.wikipedia.org/wiki/Data_type) of the parameters and the
  [result](https://en.wikipedia.org/wiki/Return_type).
  As values have types, the signature define's the function's
  [type](https://en.wikipedia.org/wiki/Function_type).

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
* In Clojure, named functions are typically  written like this: `(defn add [x y] (+ x y))`
* In Scala, named functions are typically  written like this: `def add(x: Int, y: Int): Int = x + y`
* In Clojure, anonymous functions are typically  written like this: `(def #(+ %1 %2))`
* In Scala, anonymous functions are typically  written like this: `(x: Int, y: Int) => x + y`
* Functions may have 0, 1 or more variables ("parameters"); zero parameters means no input values (nullary function).
* Upon applying a function, a value ("arguments") must be given for each parameter; nullary functions take no value (think of an "empty tuple").
* With a nullary functions one has the control over when a calculation is run.
* Clojure also offers an explicit `apply` operator which takes a list of function arguments (ie. `apply` needs `(list ...)` or ` '(...) ` )

-----------------

[<-- previous page](ch3_0_functions.md)

[--> next page](ch3_2_more_function_exercises.md)
