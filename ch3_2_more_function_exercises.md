### 3.2 Predicates, Assertions, Conditionals, and More Function Exercises

Many functions are not just of arithmetic nature, taking and returning a number, but using some form of a
[Boolean](https://en.wikipedia.org/wiki/Boolean_data_type),
for example, as a parameter or result type within the definition.

TODO: truthiness, falsey, if-let, when-first etc

See also exercise [2.0.7 Write boolean operator expressions](ch2_expressions.md#207-write-boolean-operator-expressions) on boolean operators and expressions.

Hence, a few concepts on working with booleans.

#### Predicates.

A function that performs a binary test or that returns a Boolean value is often called a
[_predicate_](https://en.wikipedia.org/wiki/Predicate_(mathematical_logic)).

Usually, languages employ naming conventions for predicates.  A function testing a property `Xyz` holds for an argument is often named:
* `isXyz`/`is_xyz` or `hasXyz`/`has_xyz` (in Java- and C-like languages),
* `xyzp` or `xyz?` (in Lisp-like languages, the trailing `p` stands for "predicate").

TODO: https://github.com/bbatsov/clojure-style-guide#pred-with-question-mark

A predicate that tests whether a property does not hold typically inserts a `not`, for example: `isNotXyz`, `has_not_xyz`, or `not-xyz?` etc.

Note how such a naming convention is especially important in programming languages where the function's return type is not explictely stated or which don't offer a primitive Boolean data type.  See
[2.0.7 Write boolean operator expressions.](ch2_expressions.md#207-write-boolean-operator-expressions)

#### Assertions.

An [_assertion_](<https://en.wikipedia.org/wiki/Assertion_(software_development))
is an operator that takes a boolean operand.  If that value is `true`, not much happens. In case of `false`, however, an "error" is raised
[AssertionError](https://docs.oracle.com/javase/8/docs/api/java/lang/AssertionError.html), which interrupts the ongoing evaluation:

```scala
    scala> assert(1 == 1)

    scala> assert(1 != 1)
    java.lang.AssertionError: assertion failed
      at scala.Predef$.assert(Predef.scala:204)
      ... 28 elided
```

```clojure
    user=> (assert (= 1 1))
    nil
    user=> (assert (not= 1 1))

    AssertionError Assert failed: (not= 1 1)  user$eval1760.invokeStatic (:1)
```

Assertions are therefore a simple tool for
[unit-testing](https://en.wikipedia.org/wiki/Unit_testing)
the correctness of a function: placing the function call with the expected result within an `assert`.

#### Conditionals.

Sometimes, a computation must return a different value depending upon whether a condition is `true`/`false`.  A
[_conditional_](<https://en.wikipedia.org/wiki/Conditional_(computer_programming))
or `if-then-else` is a predefined operator that takes 3 arguments:
1) a boolean value, 2) an expression for the "then case", and 3) an expression for the "else case".

The first operand decides whether the "then"- or "else"-value is chosen as a result for the entire conditional expression.  The syntax and behaviour is:

```scala
    scala> assert((if (true) 1 else 2) == 1)

    scala> assert((if (false) 1 else 2) == 2)

```

```clojure
    user=> (assert (= (if true 1 2) 1))
    nil
    user=> (assert (= (if false 1 2) 2))
    nil
```

-----

#### 3.2.1 Define and test a function `mydouble` that doubles a number.

Hint: Also give arity+type(s).

```clojure
; arity = 1, type(s) = Integer
(def mydouble #(* % 2))
(assert (= (mydouble 3) 6))
```

```scala
// arity = 1, type(s) = Integer
def mydouble(d: Int): Int = d * 2
assert(mydouble(4) == 8)
```

#### 3.2.2 Define and test a function that squares a number

Hint: Also give arity+type(s).

```clojure
; arity = 1, type(s) = Integer
(def squares #(* % %))
(assert (= (squares 3) 9))
```

```scala
// arity = 1, type(s) = Integer
def squares(s: Int): Int = s * s
assert(squares(3) == 9)
```

#### 3.2.3 Define and test a function that doubles the square of a number.

Hint: Also give arity+type(s).

```clojure
; arity = 1, type(s) = Integer
(def doubles-the-square #(* (squares %) mydouble(squares %)))
(assert (= (doubles-the-square 3) 18))
```

```scala
// arity = 1, type(s) = Integer
def doubles_the_square(ds: Int): Int = mydouble(squares(ds))
assert(doubles_the_square(2) == 8)

```

#### 3.2.4 Define and test a function that squares a number if the 1st operand is true, otherwise doubles the number.

Hint: Also give arity+type(s).

```clojure
; arity = 2, type(s) = Boolean, Integer
(def square-or-double #(if %1 (squares %2) (mydouble %2)))
(assert (= (square-or-double true 6) 36))
(assert (= (square-or-double false 6) 12))
```

```scala
// arity = 2, type(s) = Boolean, Int
def square_or_double(o: Boolean, z: Int): Int =
  if (o) squares(z) else mydouble(z)
assert(square_or_double(true, 3) == 9)
assert(square_or_double(false, 3) == 6)
```

#### 3.2.5 Test the language's predefined quotient/remainder operators.

Hint: Also give arity+type(s), <https://en.wikipedia.org/wiki/Remainder>.

```clojure
; arity = 2, type(s) = (Integer, Integer) -> Integer
(assert (= (quot 20 3) 6))
(assert (= (rem 20 3) 2))
```

```scala
// arity = 2 , type(s) = (Int, Int) -> Int
assert(13 / 4 == 3)
assert(13 % 4 == 1)
```

#### 3.2.6 Define and test a function that returns a list of the quotient and remainder of the division of 2 integers.

Hint: Also give arity+type(s).

```clojure
; arity = 2, type(s) = (Integer, Integer) -> list
(def quot-and-rem #(list (quot %1 %2) (rem %1 %2)))
(assert (= (quot-and-rem 10 3) (3 1)))
```

```scala
arity = 2, type(s) = (Int, Int) -> List
def quot_and_rem(k: Int, l: Int) = List(k / l, k % l)
assert(quot_and_rem(8, 3) == List(2, 2))
```

#### 3.2.7 Define and test a predicate `is_even` that tells whether an integer number is even.

Hint: Also give arity+type(s); how to test whether a number is even: x is even if (x \ 2 = y remainder 0).

```
; arity = 1, type(s) = Integer -> Boolean
(def is-even #(= (rem %1 2) 0))
(assert (= (is-even 6) true))
(assert (= (is-even 7) false))
```

```scala
arity = 1, type(s) = Int -> Boolean
def isEven(p: Int): Boolean = p % 2 == 0
assert(isEven(4) == true)
assert(isEven(5) == false)
```

___Notes:___

* In Clojure (and Scheme), `even?` would be the preferred function name.
* The unit tests could be shortened to `assert(isEven(4))` and `assert(!isEven(5))`.

#### 3.2.8 Define and test a predicate `is_odd` that tells whether an integer number is odd in terms of the `is_even` function.

Hint: Also give arity+type(s). For simplicity, disregard strictness, see
[2.0.7 Write boolean operator expressions.](ch2_expressions.md#207-write-boolean-operator-expressions)

```
; arity = 1, type(s) = Integer -> Boolean
(def is-odd #(not (is-even %1)))
(assert (= (is-odd 9) true))
(assert (= (is-odd 8) false))
```

```scala
arity = 1, type(s) = Int -> Boolean
def isOdd(i: Int): Boolean = !isEven(i)
assert(isOdd(3) == true)
assert(isOdd(8) == false)
```

___Notes:___

* In Clojure (and Scheme), `odd?` would be the preferred function name.
* The unit tests could be shortened to `assert(isOdd(3))` and `assert(!isOdd(8))`.

#### 3.2.9 Define predicates for the logical operators `not` `and`, `or`, `xor`, `nand`; only use the conditional operator and equals.

Hints: See the logical operators'
[truth tables](https://en.wikipedia.org/wiki/Truth_table).
Since some of the operators are predefined names, name the predicates `not0` `and0`, `or0`, `xor0`, `nand0`. For simplicity, disregard strictness, see
[2.0.7 Write boolean operator expressions.](ch2_expressions.md#207-write-boolean-operator-expressions)

```clojure
(def not0 #(if %1 false true))

(def and0 #(if %1 %2 false))

(def or0 #(if %1 true %2))

(def nand0 #(if %1 (if %2 false true) true))

(def xor0 #(if (= %1 %2) false true))
```
___Notes:___

* An even more compact version of function `xor0` would be: `(def xor0 #(not= %1 %2))`.

#### 3.2.10 Test the predicates `not0` `and0`, `or0`, `nand0`, `xor0`.

```clojure
(assert (= (not0 true) false))

(assert (= (and0 true false) false))

(assert (= (or0 true false) true))

(assert (= (nand0 true false) true))

(assert (= (xor0 true false) true))
```

___Notes:___

* If preferred, the unit tests can be shortened: `(assert (= ... true))` -> `(assert ...)` and `(assert (= ... false))` -> `(assert !...)`.

--------------------

[<-- previous page](ch3_1_formulas_and_functions.md)

[--> next page](ch3_3_plotting_the_evaluation_of_functions.md)
