### 3.2 Predicates, Assertions, Conditionals, and More Function Exercises

Many functions are not just of arithmetic nature, taking and returning a number, but using some form of a [Boolean](https://en.wikipedia.org/wiki/Boolean_data_type), for example, as a parameter or result type within the definition.

See also exercise [2.0.7 Write boolean operator expressions](ch2_expressions.md#207-write-boolean-operator-expressions) on boolean operators and expressions.

Hence, a few concepts on working with booleans.

#### Predicates.

A function that returns a boolean value is often called a _test_ or [predicate](https://en.wikipedia.org/wiki/Predicate_(mathematical_logic)).

#### Assertions.

An [_assertion_](<https://en.wikipedia.org/wiki/Assertion_(software_development)) is an operator that takes a boolean operand.  If that value is `true`, not much happens. In case of `false`, however, an "error" is raised [AssertionError](https://docs.oracle.com/javase/8/docs/api/java/lang/AssertionError.html), which interrupts the ongoing evaluation:

```scala
    scala> assert(1 == 1)

    scala> assert(1 != 1)
    java.lang.AssertionError: assertion failed
      at scala.Predef$.assert(Predef.scala:204)
      ... 28 elided
```

```closure
    user=> (assert (= 1 1))
    nil
    user=> (assert (not= 1 1))

    AssertionError Assert failed: (not= 1 1)  user$eval1760.invokeStatic (:1)
```

Assertions are therefore a simple tool for _unit-testing_(https://en.wikipedia.org/wiki/Unit_testing) the correctness of a function: placing the function call with the expected result within an `assert`.

#### Conditionals.

Sometimes a different value should be chosen depending upon a boolean condition.  A [_conditional_](<https://en.wikipedia.org/wiki/Conditional_(computer_programming)) or `if-then-else` is a predefined operator that takes 3 arguments: 1) a boolean value, 2) an expression for the "then case", and 3) an expression for the "else case".

The first operand decides whether the "then"- or "else"-value is chosen as a result for the entire conditional expression.  The syntax and behaviour:

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

#### 3.2.2 Define and test a function that squares a number

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

#### 3.2.3 Define and test a function that doubles the square of a number.

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

#### 3.2.4 Define and test a function that squares a number if the 1st operand is true, otherwise doubles the number.

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

#### 3.2.5 Test the language's predefined quotient/remainder operators.

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

#### 3.2.6 Define and test a function that returns a list of the quotient and remainder of the division of 2 integers.

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

#### 3.2.7 Define and test a predicate `is_even` that tells whether an integer number is even.

Hint: also give arity+type(s); how to test whether a number is even: x is even if (x \ 2 = y remainder 0).

```
; arity = 1, type(s) = Integer -> Boolean
(def is-even #(= (rem %1 2) 0))
(is-even 6) ; = true
(is-even 7) ; = false
```

```scala
arity = 1, type(s) = Int -> Boolean
def isEven(p: Int): Boolean = p % 2 == 0
isEven(4) // = true
isEven(5) // = false
```

___Notes:___

* `even?` would be the preferred f in Clojure.

#### 3.2.8 Define and test a predicate `is_odd` that tells whether an integer number is odd in terms of using the "...even..." function.

Hint: also give arity+type(s).

```
; arity = 1, type(s) = Integer -> Boolean
(def is-odd #(not (is-even %1)))
(is-odd 9); = true
(is-odd 8); = false
```

```scala
arity = 1, type(s) = Int -> Boolean
def isOdd(i: Int): Boolean = !isEven(i)
isOdd(3) // = true
isOdd(8) // = false
```

#### 3.2.9 Define predicates `not0` `and0`, `or0`, `nand0`, `xor0`, for the logical operators; use the conditional operator only.

Hints:

* See the operators' [truth tables](https://en.wikipedia.org/wiki/Truth_table).
* For this excercise, define the operators as strict/eager, see [2.0.7 Write boolean operator expressions.](ch2_expressions.md#207-write-boolean-operator-expressions)\


```clojure
(def not0 #(if %1 false true))

(def and0 #(if %1 %2 false)) 

(def or0 #(if %1 true %2))

(def nand0 #(if %1 (if %2 false true) true))

(def xor0 #(if (= %1 %2) false true))
```
___Notes:___

* An even more compact version of the function `xor0` would be: `(def xor0 #(not= %1 %2))`. 

#### 3.2.10 Test the predicates `not0` `and0`, `or0`, `xor0`, `nand0`.

```clojure
(assert (= (not0 true) false))

(assert (= (and0 true false) false))

(assert (= (or0 true false) true))

(assert (= (nand0 true false) true))

(assert (= (xor0 true false) true))
```
--------------------

[<-- previous page](ch3_1_formulas_and_functions.md)

[--> next page](ch3_3_plotting_the_evaluation_of_functions.md)
