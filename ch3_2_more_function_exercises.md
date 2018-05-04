### 3.2 More Function Exercises

___TODO:___ explain

* [boolean data type](https://en.wikipedia.org/wiki/Boolean_data_type),
  [predicate](https://en.wikipedia.org/wiki/Predicate_(mathematical_logic)),
   <https://en.wikipedia.org/wiki/De_Morgan%27s_laws>, <https://en.wikipedia.org/wiki/Boolean_algebra>

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

__Notes:__

* Preferred naming in Clojure would be `even?`

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

--------------------

[<-- previous page](ch3_1_formulas_and_functions.md)

[--> next page](ch3_3_plotting_the_evaluation_of_functions.md)
