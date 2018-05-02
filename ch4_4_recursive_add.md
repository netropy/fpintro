### 4.4 Recursive Function `add`
Obviously, adding two numbers is not an exciting calculation.  As a primitive operation offered by any CPU, it is "built into hardware".  Thus, it is inefficient to re-define an `add` operation "in software" as a recursive function.  However, it makes a good excercise in thinking recursively :-)

#### Find a recursive definition for the addition of two numbers `m`, `n`.

Hint: Define addition in terms of increment (+1) and decrement (-1).

The following equation (or _invariant_) holds for the addition of 2 numbers:
```
  (m + n) = ((m - 1) + n) + 1
```

#### Define a recursive function `add(m, n)` with a simple unit test.

Hints:

* Use the recursive equation from above.
* Use functions `decr` and `incr` as defined earlier.
* Think about what constitues the "termination condition".
* For simplicity, ignore negative values for `m` and just assume positive arguments.

```scala
def add(m: Int, n: Int): Int =
  if (m == 0) n else incr(add(decr(m), n))

assert(add(2,3) == 5)
assert(add(3,2) == 5)
assert(add(1,2) == 3)
assert(add(0,2) == 2)
assert(add(0,-2) == -2)

assert(add(-1,-2) == -3) // !java.lang.StackOverflowError!
```

___Notes:___

* Conceptually, the addition of natural numbers can be defined in terms of increment and decrement.
* Above code is not _robust_:  for any negative argument `m`, it keeps decrementing `m` resulting in a `StackOverflowError` (or [Integer Overflow](https://en.wikipedia.org/wiki/Integer_overflow)).
* Above code is not _efficient_, meaning it is not tail-recursive, hence, its evaluation consumes much time and memory for large input values.  Annotating the function with `@annotation.tailrec` would raise an error.
* Some Scala style guides prefer to split the `if (...) ... else ...` into two lines before the `else` (which requires to put the entire function body into `{ ... }`).

#### Plot the evaluation of `add(3, 2)`.

```
--> add(m=3, n=2)
    --> add(m=2, n=2)
        --> add(m=1, n=2)
	    --> add(m=0, n=2)
	    <-- add(m=0, n=2): 2
	<-- add(m=1, n=2): 3
    <-- add(m=2, n=2): 4
<-- add(m=3, n=2): 5
```

Or as a more detailed version, also showing the evaluation of `decr` and `incr`:

```
--> add(m=3, n=2)
    --> decr(3)
    <-- decr(3): 2
    --> add(m=2, n=2)
        --> decr(2)
        <-- decr(2): 1
        --> add(m=1, n=2)
            --> decr(1)
            <-- decr(1): 0
	    --> add(m=0, n=2)
	    <-- add(m=0, n=2): 2
            --> incr(2)
            <-- incr(2): 3
	<-- add(m=1, n=2): 3
        --> incr(3)
        <-- incr(3): 4
    <-- add(m=2, n=2): 4
    --> incr(4)
    <-- incr(4): 5
<-- add(m=3, n=2): 5
```

___Notes:___

* The 1st argument `m` is being decremented until the "termination condition" `(m == 0)` holds.
* The 2nd argument `n` remains unchanged  while being "passed through" all recursive calls.
* The result is build up on "result position", which shows that `add` is not tail-recursive.

#### Make `add` robust by extending it to negative arguments.

Hint: Modify above's equation to increment the 1st argument: `(m + n) = ((m + 1) + n) - 1`.

```scala
def add(m: Int, n: Int): Int = {
  if (m == 0) n
  else if (m < 0) decr(add(incr(m), n))
  else incr(add(decr(m), n))
}

assert(add(3,2) == 5)
assert(add(3,-2) == 1)
assert(add(0,2) == 2)
assert(add(0,-2) == -2)
assert(add(-3,2) == -1)
assert(add(-3,-2) == -5)
```

___Notes:___

* The `incr` and `decr` operations are reversed for negative `m` to "count up" to zero.
* Above code is not tail-recursive.  Annotating the function with `@annotation.tailrec` would raise an error.
* The chained expression `if (...) ... else if (...) ... else ...` is split into multiple lines for better readability; no need for additional round brackets `... else (if (...) ... else)`.
* Notation: some Scala style guides prefer if-then-else chains over a value `m` to be writted as `m match { case x if (...) => ... ; case x ... }` :
```scala
def add(m: Int, n: Int): Int = m match {
  case x if (x == 0) => n
  case x if (x < 0) => decr(add(incr(m), n))
  case x => incr(add(decr(m), n))
}
```

#### Make `add` robust by extending it to negative arguments -- alternative version.

Hint: Instead of incrementing `m` towards zero, reduce the case of a negative argument to a positive `m` by this equation: `(m + n) = -(-m - n)`.

```scala
def add(m: Int, n: Int): Int = {
  if (m == 0) n
  else if (m < 0) -add(-m, -n)
  else incr(add(decr(m), n))
}

assert(add(3,2) == 5)
assert(add(3,-2) == 1)
assert(add(0,2) == 2)
assert(add(0,-2) == -2)
assert(add(-3,2) == -1)
assert(add(-3,-2) == -5)
```

___Notes:___

* For a negative argument `m`, the calculation "delegates" to `-add(-m, -n)` turning `m` positive.
* Above code is not tail-recursive.  Annotating the function with `@annotation.tailrec` would raise an error.

#### Plot the evaluation of `add(-2, -1)`.

```
--> add(m=-2, n=-1)
    --> add(m=2, n=1)
        --> add(m=1, n=1)
	    --> add(m=0, n=1)
	    <-- add(m=0, n=1): 1
	<-- add(m=1, n=1): 2
    <-- add(m=2, n=1): 3
<-- add(m=-2, n=1): -3
```

#### Reformulate `add` to make it tail-recursive.

Hints:

* Instead of incrementing the _result_ of the recursive call, increment the 2nd parameter `n` by this equation: `(m + n) = (m - 1) + (n + 1)`.
* For simplicity, ignore the handling of negative `m` and just assume positive arguments, like in the 1st definition of `add` above.

```scala
@annotation.tailrec
def add(m: Int, n: Int): Int = {
  if (m == 0) n
  else add(decr(m), incr(n))
}

assert(add(3,2) == 5)
assert(add(3,-2) == 1)
assert(add(0,2) == 2)
assert(add(0,-2) == -2)
// assert(add(-3,2) == -1)
// assert(add(-3,-2) == -5)
```

___Notes:___

* Above code is tail-recursive, hence, efficient: annotating the function with `@annotation.tailrec` will not raise an error.

#### Plot the evaluation of tail-recursive `add(3, 2)`.

```
--> add(m=3, n=2)
    --> add(m=2, n=3)
        --> add(m=1, n=4)
	    --> add(m=0, n=5)
	    <-- add(m=0, n=5): 5
	<-- add(m=1, n=4): 5
    <-- add(m=2, n=3): 5
<-- add(m=3, n=2): 5
```

___Notes:___

* The result is build up on "parameter position" by incrementing `n`.
* The function's return value remains unchanged and just being "passed through", which shows `add` to be tail-recursive.


#### Make the tail-recursive version of `add` robust by extending it to negative arguments.

Hints:

* A negative sign operation in front of a recursive call, as in `-add(-m, -n)` would no longer make the function tail-recursive.
* Instead, put the tail-recursive code into a "helper" function `add_go(...) = ...` and call it from function `add(...) = ...`.

```scala
@annotation.tailrec
def add_go(m: Int, n: Int): Int = {
  if (m == 0) n
  else add_go(decr(m), incr(n))
}

def add(m: Int, n: Int): Int = {
  if (m < 0) -add_go(-m, -n)
  else add_go(m, n)  
}

assert(add(3,2) == 5)
assert(add(3,-2) == 1)
assert(add(0,2) == 2)
assert(add(0,-2) == -2)
assert(add(-3,2) == -1)
assert(add(-3,-2) == -5)
```
___Notes:___

* Above code is tail-recursive (i.e., efficient) and robust :-)
* Notation: since the "helper" function is not robust and hence to be used from "outside", the preferred style is it make it a _local_ function, typically just called `go` or `loop`, within a "wrapper" function:
```scala
def add(m: Int, n: Int): Int = {
  @annotation.tailrec
  def go(m: Int, n: Int): Int = {
    if (m == 0) n
    else go(decr(m), incr(n))
  }

  if (m < 0) -go(-m, -n)
  else go(m, n)  
}

```
