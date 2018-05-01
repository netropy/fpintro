## 4.4 Recursive Function `multiply`

#### Find a recursive definition (or "invariant") for the addition of two numbers `m`, `n`.

Hint: define multiplication in terms of `n-1` and `+`

The following equation holds for the multiplication of 2 numbers:
```
  m * n = ((m - 1) * n) + n
```

#### Define a recursive function `multiply(m, n)`.

```scala
def multiply(m: Int, n: Int): Int =
  if (m == 0) 0 else (
    if (m == 1) n else add(multiply(decr(m), n), n)
  )

multiply(2,5) // = 10
multiply(6,3) // = 18
multiply(2,-1) // = -2
multiply(1,5) // = 5
multiply(0,5) // = 0
multiply(-1,5) // !!!endless loop!!!
multiply(-1,-5) // !!!endless loop!!!
```

__Notes:__

* Above code is not _robust_: it goes into an endless loop for any negative `m`.
* Above function is not tail-recursive (see chapter 4.3).  Annotating it with '@annotation.tailrec' would raise an error.

#### Plot the evaluation of `multiply(3,5)`.

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

#### Make `multiply` robust to accept negative arguments.

```scala
def multiply(m: Int, n: Int): Int =
  if (m < 0) -(multiply(-m, n)) else (
    if (m == 0) 0 else (
      if (m == 1) n else add(multiply(decr(m), n), n)
    )
  )

multiply(-1,5) // = -5
multiply(-1,-5) // = 5
multiply(2,-5) // = -10
multiply(0,-5) // = 0

multiply(10000, -5) // = -50000
multiply(100000, -5) // java.lang.StackOverflowError for 100 thousand * -5
```

__Notes:__

* We can use this equation `m * n = -(-m * n)` to _reduce_ a negative `m` to the case of a positive `m`, which we've seen work.

#### Reformulate `multiply` to make it tail-recursive.

Hint: see chapter 4.3 for definition of tail-recursion.

```scala
@annotation.tailrec
def multiply_v0(m: Int, n: Int, acc: Int): Int =
  if (m == 0) 0 else (
    if (m == 1) acc else multiply_v0(decr(m), n, add(acc, n))
  )

def multiply(m: Int, n: Int): Int =
  multiply_v0(m, n, n)

multiply(10000, -5) // = -50000
multiply(100000, -5) // = -500000
multiply(1000000, -5) // = -5000000
multiply(10000000, -5) // = -50000000
multiply(100000000, -5) // = -500000000  = 100 million * -5
```

#### Plot the evaluation of tail-recursive `multiply(2,5)`.

```
--> multiply(m=2, n=5)
    --> multiply_v0(m=2, n=5, acc=5)
        --> multiply_v0(m=1, n=5, acc=10)
        <-- multiply_v0(m=1, n=5, acc=10): 10
    <-- multiply_v0(m=2, n=5, acc=5): 10
<-- multiply(m=2, n=5): 10
```
