### 3.1 Formulas and Functions

Most of the time, we want to write a calculation not with fixed, "hard-coded" numbers but in a general form using [variables](https://en.wikipedia.org/wiki/Variable_(mathematics)), like `(x + y) * z`.  In computing and other areas of science, this is often called a [formula](https://en.wikipedia.org/wiki/Formula).  Writing computations as formulas has several advantages, but mainly:

1) The abstract form highlights the essence of the computation in a concise way.
2) A formula may be given a name, under which it then can be used (and discussed).
3) A formula can be "applied" by substituting numbers for variable names.

In computing (and mathematics or logic), the corresponding technical terms for working with formulas are:

* formula: [anonymous function](https://en.wikipedia.org/wiki/Anonymous_function), function literal, lambda abstraction, or [lambda expression](https://en.wikipedia.org/wiki/Lambda_calculus)
* writing a formula: [function definition](https://en.wikipedia.org/wiki/Function_(mathematics)), [user-defined operators](https://en.wikipedia.org/wiki/Operator_(computer_programming)), parametrization, or [abstraction](https://en.wikipedia.org/wiki/Abstraction_(computer_science))
* appling a formula: [function application](https://en.wikipedia.org/wiki/Function_application), [function call](https://en.wikipedia.org/wiki/Subroutine), or [function evaluation](https://en.wikipedia.org/wiki/Evaluation_strategy)
* variables: [parameters](https://en.wikipedia.org/wiki/Parameter_(computer_programming)) or formal parameters
* numbers: [arguments](https://en.wikipedia.org/wiki/Argument_of_a_function), [operands](https://en.wikipedia.org/wiki/Operand), actual parameters, or (in general) [values](https://en.wikipedia.org/wiki/Value_(computer_science))

Examples:

definition/application | Math Notation | Clojure (et.al.) | Scala (et.al.)
:----|:----|:----|:----
def | `a = 3`              | `(def a 3)`             | `val a = 3`
def | `f(x) = x + 4`       | `(def f #(+ % 4))`      | `def f(x: Int) = x + 4`
def | `g: x -> x + 5`      | `(defn g [x] (+ x 5))`  | `val g: Int => Int = x => x + 5`
app | `f(a) = 3 + 4 = 7`   | `(f a)         ; => 7`  | `f(a)                    // => 7`
app | `f(2) = 2 + 4 = 6`   | `(f 2)         ; => 6`  | `f(2)                    // => 6`
app | `f(9) = 9 + 4 = 13`  | `(f 9)         ; => 13` | `f(9)                    // => 13`
app | `(x -> x + 4)(2)`    | `(#(* % 3) 2)  ; => 6`  | `((x: Int) => x + 4)(2)  // => 6`
app | `g(a) = 3 + 5 = 8`   | `(g a)         ; => 8`  | `g(a)                    // => 8`

___Notes___:

* Some programming languages offer multiple notations of varying brevity by which an anonymous or named function can be defined.
* Functions should be given a name that's short yet meaningful (chosing a good name can be a task in itself).
* Programming languages, developers, and projects have conventions about how to form composite names, like ["kebab case"](https://en.wikipedia.org/wiki/Letter_case#Special_case_styles), ["snake case"](https://en.wikipedia.org/wiki/Snake_case), or ["camel case"](https://en.wikipedia.org/wiki/Camel_case)
* The [arity](https://en.wikipedia.org/wiki/Arity) of a function (or formula) is the number of its parameters
* The [type signature](https://en.wikipedia.org/wiki/Type_signature) of a function (or formula) lists the [data types](https://en.wikipedia.org/wiki/Data_type) of the parameters and the result.

####  3.1.1 Define and evaluate functions: [exercise KfK, chapter 6: Functions (Happy birthday)](http://kids.klipse.tech/clojure/2016/07/30/chapter-6.html).

Exercise | Clojure | Scala
:-------|:------|:------
A: write a function hours->minutes transforming hours into minutes | `(def hours-to-minutes #(* % 60))` | `val hoursToMinutes = (h :Int) => h * 60`
... | `(def hours-to-minutes (fn [h] (* h 60)))` | `val hoursToMinutes: Int => Int = h => h * 60`
... | `(defn hours-to-minutes [h] (* h 60))` | `def hoursToMinutes(h: Int): Int = h * 60`
B: use hours->minutes to calculate how many minutes there are in 12 hours | `(hours-to-minutes 12)` | `hoursToMinutes(12)`
... | `(apply hours-to-minutes (list 12))` |
C: apply the function you defined in #A to 12 without using its name | `(#(* % 60) 12)` | `((h :Int) => h * 60)(12)`
D: write a function minutes->hours transforming minutes into hours | `(def minutes-to-hours #(/ % 60))` | `val minutesToHours = (m :Int) => m / 60`
... | `(def minutes-to-hours (fn [m] (/ m 60)))` | `val minutesToHours: Int => Int = m => m / 60`
... | `(defn minutes-to-hours [m] (/ m 60))` | `def minutesToHours(m: Int): Int = m / 60`
E: use minutes->hours to calculate how many hours there are in 6000 minutes | `(minutes-to-hours 6000)` | `minutesToHours(6000)`
F: apply the function you defined in #D to 6000, without using its name | `(#(/ % 60) 6000)` | `((m :Int) => m / 60)(6000)`

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

Further reading:
* <https://en.wikipedia.org/wiki/Cartesian_product>, <https://en.wikipedia.org/wiki/Tuple>

-----------------

[<-- previous page](ch3_0_functions.md)

[--> next page](ch3_2_more_function_exercises.md)
