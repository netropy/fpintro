### 3.1 Formulas and Functions

___TODO:___ explain, give example

* What is a function, formula, parametrized expression, anonymous function, lambda?

concept | meaning | example
:---|:---|:---
anonymous function ("formula") | a calculation that has one or more variables | `x -> x + 3`
function definition | naming a formula, giving it a name like `f` | `f(x) = x + 3`
application | evaluating a function with a value for each variable(s) | `f(2)`

definition/application  |  Math Notation |  Lisp-like languages
:----|:----|:----
def  | `a = 3`               | `(def a 3)`
def  | `f(x) = x + 4`        | `(def f #(+ % 4))`
def  | `g: x -> x + 5`       | `(def g #(+ % 5))`
appl | `f(a) = 3 + 4 = 7`    | `(f a) => 7`
appl | `f(2) = 2 + 4 = 6`    | `(f 2) => 6`
appl | `f(9) = 9 + 4 = 13`   | `(f 9) => 13`
appl | `(x -> x + 4)(2)`     | `(#(* x 3) 2) => 6`
appl | `g(a) = 3 + 5 = 8`    | `(g a) => 8`

___Notes___:

* the name of a function should capture the meaning of its calculation
* the "arity" of a function (or formula) is the number of its variables (or parameters)
* the parameters of a function (or formula) may have different types, like Boolean, Integer, String
* <https://en.wikipedia.org/wiki/Function_(mathematics)>,
  <https://en.wikipedia.org/wiki/Subroutine>,
  <https://en.wikipedia.org/wiki/Anonymous_function>

* <https://en.wikipedia.org/wiki/Letter_case#Special_case_styles>, <https://en.wikipedia.org/wiki/Camel_case>, <https://en.wikipedia.org/wiki/Snake_case>

___TODO:___ explain, give example

* What is an assertion?
* why useful for testing

___Notes:___

* <https://en.wikipedia.org/wiki/Assertion_(software_development)>

####  3.1.1 Define and evaluate functions: [exercise KfK, chapter 6: Functions (Happy birthday)](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-6.html).

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
