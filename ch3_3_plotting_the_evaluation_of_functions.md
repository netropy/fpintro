### 3.3 Plotting the Evaluation of Functions

The process of applying a function with an argument value can be rendered in a chart.  Sometimes, this process is also called "to evaluate" or "to call" a function.   The "entry" into a function with argument values (input) and the "return" or "exit" with a result value (output) can be marked with arrows '-->' and '<--'.  The entry and exit of nested functions are then marked with an indentation.

#### Define and test functions `incr` and `decr` that increment (+1) respectively decrement (-1) a number `n`.

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

#### Plot the evaluation of `incr(2)` and `decr(-1)`.

```
--> incr(n=2)
<-- incr(n=2): 3
--> decr(n=-1)
<-- decr(n=-1): -2
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

#### Plot the evaluation of `decr_if_positive(-1)`.

```
--> decr_if_positive(n=-1)
<-- decr_if_positive(n=-1): -1
```

#### Plot the evaluation of `decr_if_positive(4)`.

```
--> decr_if_positive(n=4)
    --> decr(n=4)
    <-- decr(n=4): 3
<-- decr_if_positive(n=4): 3
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

#### Plot the evaluation of `incr_twice(3)`.

```
--> incr_twice(n=3)
    --> incr(n=3)
    <-- incr(n=3): 4
    --> incr(n=4)
    <-- incr(n=4): 5
<-- incr_twice(n=3): 5
```
