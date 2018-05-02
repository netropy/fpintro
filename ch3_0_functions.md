## 3.0 Functions

### Formulas and Functions

#### What is a function?

TODO: explain, give example

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

#### Define and apply the sample functions from [excercise KfK, chapter 6: Functions (Happy birthday)](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-6.html).

Excercise | Clojure | Scala
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


#### What is a boolean test?

TODO: explain, give example

___Notes:___

* <https://en.wikipedia.org/wiki/Boolean_data_type>, <https://en.wikipedia.org/wiki/Predicate_(mathematical_logic)>

#### Define and apply the boolean tests from [excercise KfK, chapter 7: True or False (Pinocchio)](http://kids.klipse.tech/clojure/2016/06/18/programming-kids-7.html).

Excercise | Clojure | Scala
:-------|:------|:------
ask if 7 times 6 equals 40 | `(= (* 7 6) 40)` | ` 7 * 6 == 40 `
ask if 7 times 6 is less/equal than 40 | `(<= (* 7 6) 40)` | ` 7 * 6 <= 40 `
ask if 7 times 6 is greater/equal than 40 | `(>= (* 7 6) 40)` | ` 7 * 6 >= 40 `
ask if 7 times 6 is not equal to 40 | `(not= (* 7 6) 40)` | ` 7 * 6 != 40 `


#### What is a conditional?

TODO: explain, give example

___Notes:___

* <https://en.wikipedia.org/wiki/Conditional_(computer_programming)>
* excercise from [KfK, Chapter 8: If (Emoji)](http://kids.klipse.tech/clojure/2016/08/05/chapter-8.html)

#### What is an assertion?

TODO: explain, give example

___Notes:___

* <https://en.wikipedia.org/wiki/Assertion_(software_development)>

### Function excercises with basic artihmetics

#### Define and test a function `mydouble` that doubles a number.

Hint: also give arity+type(s).

```clojure
; arity = 1, type(s) = Integer
(def mydouble #(* % 2))
(mydouble 3) ; = 6
```

```scala
// arity = 1, type(s) = Integer
def mydouble(d: Int): Int = d * 2
mydouble(4) // = 8
```

#### Define and test a function that squares a number

Hint: also give arity+type(s).

```clojure
; arity = 1, type(s) = Integer
(def squares #(* % %))
(squares 3) ; = 9
```

```scala
// arity = 1, type(s) = Integer
def squares(s: Int): Int = s * s
squares(3) // = 9
```

#### Define and test a function that doubles the square of a number.

Hint: also give arity+type(s).

```clojure
; arity = 1, type(s) = Integer
(def doubles-the-square #(* (squares %) mydouble(squares %)))
(doubles-the-square 3) ; = 18
```

```scala
// arity = 1, type(s) = Integer
def doubles_the_square(ds: Int): Int = mydouble(squares(ds))
doubles_the_square(2) // = 8

```

#### Define and test a function that squares a number if the 1st operand is true, otherwise doubles the number.

Hint: also give arity+type(s).

```clojure
; arity = 2, type(s) = Boolean, Integer
(def square-or-double #(if %1 (squares %2) (mydouble %2)))
(square-or-double true 6) ; = 36
(square-or-double false 6) ; = 12
```

```scala
// arity = 2, type(s) = Boolean, Int
def square_or_double(o: Boolean, z: Int): Int =
  if (o) squares(z) else mydouble(z)
square_or_double(true, 3) // = 9
square_or_double(false, 3) //  = 6
```

### Functions excercises with `quot` and `rem`

#### Test the language's predefined quotient/remainder operators.

Hint: also give arity+type(s), <https://en.wikipedia.org/wiki/Remainder>

```clojure
; arity = 2, type(s) = (Integer, Integer) -> Integer
(quot 20 3) ; = 6
(rem 20 3) ; = 2
```

```scala
// arity = 2 , type(s) = (Int, Int) -> Int
13 / 4 // = 3
13 % 4 // = 1
```

#### Define and test a function that returns/gives/yields a list of the quotient and remainder of the division of 2 integers.

Hint: also give arity+type(s).

```clojure
; arity = 2, type(s) = (Integer, Integer) -> list
(def quot-and-rem #(list (quot %1 %2) (rem %1 %2)))
(quot-and-rem 10 3) ; = (3 1)
```

```scala
arity = 2, type(s) = (Int, Int) -> List
def quot_and_rem(k: Int, l: Int) = List(k / l, k % l)
quot_and_rem(8, 3) // = List(2, 2)
```

#### Define and test a function `myeven?` that test/tells/gives whether an integer number is even.

Hint: also give arity+type(s); how to test whether a number is even: x is even if (x \ 2 = y remainder 0).

```
; arity = 1, type(s) = Integer -> Boolean
(def myeven? #(= (rem %1 2) 0))
(myeven? 6) ; = true
(myeven? 7) ; = false
```

```scala
arity = 1, type(s) = Int -> Boolean
def myeven(p: Int): Boolean = p % 2 == 0
myeven(4) // = true
myeven(5) // = false
```

#### Define and test a function `myodd?` that tells whether an integer number is odd in terms of using the "...even..." function.

Hint: also give arity+type(s).

```
; arity = 1, type(s) = Integer -> Boolean
(def myodd? #(not (myeven? %1)))
(myodd? 9); = true
(myodd? 8); = false
```

```scala
arity = 1, type(s) = Int -> Boolean
def myodd(i: Int): Boolean = !myeven(i)
myodd(3) // = true
myodd(8) // = false
```

### Functions excercises with `incr` and `decr`

#### Write functions `incr` and `decr` that increment (+1) respectively decrement (-1) a number `n`.

```scala
def incr(n: Int): Int = n + 1
def decr(n: Int): Int = n - 1

incr(2) // = 3
decr(5) // = 4
```

```clojure
(def incr #(+ % 1))
(def decr #(- % 1))

(incr 2) ; = 3
(decr 9) ; = 8
```

#### Define and test a function that decrements a number `n` if `n` is positive, otherwise returns `n` (use `decr`).

```scala
def decr_if_positive(n: Int): Int =
  if (n > 0) decr(n) else n

decr_if_positive(4) // = 3
decr_if_positive(0) // = 0
decr_if_positive(-4) // = -4
```

```clojure
(def decr-if-positive #(if (> % 0) (decr %) (%)))

```

#### Define and test a function that twice increments a number `n` (use `incr`).

```scala
def incr_twice(n: Int): Int =
  incr(incr(n))

incr_twice(4) // = 6
```

```clojure
(def incr-twice #(incr (incr %)))
(incr-twice 6) ; = 8

```

### Plotting the evaluation of functions

The process of applying a function with an argument value can be rendered in a chart.  Sometimes, this process is also called "to evaluate" or "to call" a function.   The "entry" into a function with argument values (input) and the "return" or "exit" with a result value (output) can be marked with arrows '-->' and '<--'.  The entry and exit of nested functions are then marked with an indentation.

For example, the function application `decr_if_positive(4)` would be plotted like this:
```
--> decr_if_positive(n=4)
    --> decr(n=4)
    <-- decr(n=4): 3
<-- decr_if_positive(n=4): 3
```

#### Plot the evaluation of `decr_if_positive(-1)`.

```
--> decr_if_positive(n=-1)
<-- decr_if_positive(n=-1): -1
```

#### Plot the evaluation of `incr_twice(3)`.

```
--> incr_twice(n=3)
    --> incr(n=3)
    <-- incr(n=3): 4
    --> incr(n=4)
    <-- incr(n=4): 5
<-- incr_twice(n=3): 5
```
