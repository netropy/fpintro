### 4.5 Recursive Function `multiply`

Similar to what was remarked about addition could be said about multiplication.  Yet, it makes another good excercise in thinking recursively :-)

#### 4.5.1 Find a recursive definition for the addition of two numbers `m`, `n`.

Hint: Define multiplication in terms of decrement (-1) and `+`.

The following equation (or _invariant_) holds for the multiplication of 2 numbers:
```
  m * n = ((m - 1) * n) + n
```

#### 4.5.2 Define a recursive function `multiply(m, n)` with a simple unit test.

Hints:

* Use the recursive equation from above.
* Use functions `decr` and `add` as defined earlier.
* Think about what constitues the "termination condition".
* For simplicity, ignore negative values for `m` and just assume positive arguments.

```scala
def multiply(m: Int, n: Int): Int = {
  if (m == 0) 0
  else if (m == 1) n
  else add(multiply(decr(m), n), n)
}

assert(multiply(3,5) == 15)
assert(multiply(6,3) == 18)
assert(multiply(2,-1) == -2)
assert(multiply(1,5) == 5)
assert(multiply(0,5) == 0)

assert(multiply(-1,5) == -5) // !java.lang.StackOverflowError!
assert(multiply(-1,-5) == 5) // !java.lang.StackOverflowError!
```

___Notes:___

* Conceptually, the multiplication of natural numbers can be defined in terms of increment and decrement (via addition).
* Above code is not _robust_:  for any negative argument `m`, it keeps decrementing `m` resulting in a `StackOverflowError` (or [Integer Overflow](https://en.wikipedia.org/wiki/Integer_overflow)).
* Above code is not _efficient_: it is not tail-recursive, hence, its evaluation consumes much time and memory for large input values.  Annotating the function with `@annotation.tailrec` would raise an error.

#### 4.5.3 Plot the evaluation of `multiply(3,5)`.

```
--> multiply(m=3, n=5)
    --> multiply(m=2, n=5)
       --> multiply(m=1, n=5)
       <-- multiply(m=1, n=5): 5
    <-- multiply(m=2, n=5): 10
<-- multiply(m=3, n= 5): 15
```

Or as a more detailed version, also showing the evaluation of `add` and `decr`:

```
--> multiply(m=3, n=5)
    --> decr(3)
    <-- decr(3): 2
    --> multiply(m=2, n=5)
    	--> decr(2)
    	<-- decr(2): 1
        --> multiply(m=1, n=5)
        <-- multiply(m=1, n=5): 5
    	--> add(5, 5)
    	<-- add(5, 5): 10
    <-- multiply(m=2, n=5): 10
    --> add(10, 5)
    <-- add(10, 5): 15
<-- multiply(m=3, n= 5): 15
```

___Notes:___

* The 1st argument `m` is being decremented until the "termination condition" `(m == 1)` holds.
* The 2nd argument `n` remains unchanged  while being "passed through" all recursive calls.
* The result is build up on "result position", which shows that `multiply` is not tail-recursive.

#### 4.5.4 Make `multiply` robust by extending it to negative arguments.

Hint: reduce the case of a negative argument to a positive `m` by this equation: `m * n = -(-m * n)`.

```scala
def multiply(m: Int, n: Int): Int = {
  if (m < 0) -(multiply(-m, n))
  else if (m == 0) 0
  else if (m == 1) n
  else add(multiply(decr(m), n), n)
}

assert(multiply(3,5) == 15)
assert(multiply(6,3) == 18)
assert(multiply(2,-1) == -2)
assert(multiply(1,5) == 5)
assert(multiply(0,5) == 0)

assert(multiply(-1,5) == -5)
assert(multiply(-1,-5) == 5)

assert(multiply(1000, 5) == 5000)
assert(multiply(100000, 5) == 500000) // !java.lang.StackOverflowError!
```

___Notes:___

* For a negative argument `m`, the calculation "delegates" to `-(multiply(-m, n))` turning `m` positive.
* Above code is not tail-recursive.  Annotating the function with `@annotation.tailrec` would raise an error.
* For "large" input values (here `m=100k` at current JVM settings), he above calculation results in a `StackOverflowError` since its not tail-recursive.

#### 4.5.5 Reformulate `multiply` to make it tail-recursive and handling negative arguments.

Hints:

* Instead of modifying the _result_ of the recursive call, add another _parameter_ accumulating the intermediate results.
* Make the 3-parameter function version a _local_ function within the 2-parameter "wrapper" function.
* Delegate the calculation for negative `m` like in the 2nd definition of `multiply` above.

```scala
def multiply(m: Int, n: Int): Int = {
  @annotation.tailrec
  def go(m: Int, n: Int, acc: Int): Int = {
    if (m == 1) acc
    else go(decr(m), n, add(acc, n))
  }

  if (m == 0) 0
  else if (m < 0) -(go(-m, n, n))
  else go(m, n, n)
}

assert(multiply(3,5) == 15)
assert(multiply(6,3) == 18)
assert(multiply(2,-1) == -2)
assert(multiply(1,5) == 5)
assert(multiply(0,5) == 0)

assert(multiply(-1,5) == -5)
assert(multiply(-1,-5) == 5)

assert(multiply(1000, -5) == -5000)
assert(multiply(10000, -5) == -50000)
assert(multiply(100000, -5) == -500000)
assert(multiply(1000000, -5) == -5000000)
assert(multiply(10000000, -5) == -50000000)
assert(multiply(100000000, -5) == -500000000) // no java.lang.StackOverflowError
```

___Notes:___

* The handling of the "zero" case `if (m == 0) 0` can be done in either the "helper" or "wrapper" function.
* Above code is tail-recursive: annotating the function with `@annotation.tailrec` won't raise an error.
* Above code is also robust in accepting negative arguments :-)

#### 4.5.6 Plot the evaluation of tail-recursive `multiply(2,5)`.

```
--> multiply(m=2, n=5)
    --> go(m=2, n=5, acc=5)
        --> go(m=1, n=5, acc=10)
        <-- go(m=1, n=5, acc=10): 10
    <-- go(m=2, n=5, acc=5): 10
<-- multiply(m=2, n=5): 10
```
