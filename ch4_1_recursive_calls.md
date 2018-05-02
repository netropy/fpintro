### 4.1 What happens when a Function calls itself?

#### 4.1.1 Define two functions `ping(n)` and `pong(n)` that call each other with an incremented argument.

Hint: To avoid an error (`not found: value pong`) while defining `ping`, enter the definitions in the Scala REPL in "paste mode" and exit with ctrl-D.

```scala
:paste
// Entering paste mode (ctrl-D to finish)

def ping(n: Int): Int = pong(n + 1)
def pong(n: Int): Int = ping(n + 1)

^D
// Exiting paste mode, now interpreting.
```

___Notes:___

* Above functions are an example of [_mutual recursion_](https://en.wikipedia.org/wiki/Mutual_recursion) (also called _indirect recursion_): two things being defined in terms of each other -- and, hence, by self-reference.

#### 4.1.2 Run and plot the evaluation of `ping(2)`.

```
scala> ping(2)
java.lang.StackOverflowError
  at .pong(<pastie>:13)
  at .ping(<pastie>:14)
  ...
```

Functions `ping` and `pong` keep calling each other while storing their incremented arguments; since neither function ever returns from a call, the execution aborts upon exhaustion of (stack) memory (`StackOverflowError`):

```
--> ping(n=2)
    --> pong(n=3)
        --> ping(n=4)
            --> pong(n=5)
                --> ...
```

#### 4.1.3 Define a function `increase(n)` that calls itself and then returns an incremented result.

```scala
def increase(n: Int): Int = increase(n) + 1
```

___Notes:___

* Function `increase` is an example of [_direct recursion_](https://en.wikipedia.org/wiki/Recursion), an immediate form of [_self-reference_](https://en.wikipedia.org/wiki/Self-reference).
* In contrast to the functions `ping` and `pong`, which increment the argument, the function `increase` increments the recursive call's return value.

#### 4.1.4 Run and plot the evaluation of `increase(2)`.

```
scala> increase(n=2)
java.lang.StackOverflowError
  at .increase(<console>:11)
  ...
```

Function `increase` keeps re-calling itself while reserving space for the call's result (to be later incremented); since the function never returns from a call, the execution aborts when (stack) memory becomes exhausted (`StackOverflowError`):

```
--> increase(n=2)
    --> increase(n=2)
        --> increase(n=2)
            --> ...
```

#### 4.1.5 Define a function `grow(n)` that calls itself with an incremented argument value.

```scala
def grow(n: Int): Int = grow(n + 1)
```

___Notes:___

* Function `grow` is an example of [_tail-recursion_](https://en.wikipedia.org/wiki/Tail_recursion), a special form of direct recursion where the call's result is passed unchanged.
* In contrast to functions `increase`, which increments the recursive call's result, function `grow` modifies the argument's value but "passes back" the recursive call's return value.
* While functions `ping` and `pong` also "pass back" their call's return value, function `grow` is _directly recursive_.
* Tail-recursion is a practically important concept and is further explored below and in chapters [4.4](ch4_4_recursive_add.md) and [4.5](ch4_5_recursive_multiply.md).

#### 4.1.6 Run and plot the evaluation of `grow(2)`.

```
scala> grow(2)
       // ...not returning...
```

Function `grow` keeps calling itself with an incremented argument but without ever returning from its recursive call:

```
--> grow(n=2)
    --> grow(n=3)
        --> grow(n=4)
            --> ...
```

Unlike functions `ping`, `pong`, and `increase`, however, the Scala shell (or Scala _interpreter_) is able to detect this simple form of _tail-recursion_ and can run the evaluation more efficiently in a [_loop_](https://en.wikipedia.org/wiki/Loop_(computing)) without increasing memory demand.

This execution therefore avoids a `StackOverflowError` but results in an [_infinite loop_](https://en.wikipedia.org/wiki/Loop_(computing)#Infinite_loops).

#### 4.1.7 Define a function `count_down(n)` that calls itself with a decremented argument until zero, then returns zero.

```scala
@annotation.tailrec
def countDown(n: Int): Int =
  if (n == 0) 0 else countDown(n - 1)
```

___Notes:___

* The test `(n == 0)` is called a _termination condition_ as it does not effect the recursive call.
* Function `countDown` is _tail-recursive_ as it "passes back" the call's result unchanged.
* To ensure that a function is tail-recursive and, hence, can be implemented efficiently, the function definition can be preceded with [`@annotation.tailrec`](<https://www.scala-lang.org/api/current/scala/annotation/tailrec.html>). This annotation raises an error should the function turn out not to be tail-recursive.

#### 4.1.8 Run and plot the evaluation of `count_down(2)`.

Unlike all recursive functions above, `countDown` properly _terminates_ (with a return value of zero, here):

```
scala> countDown(2)
res0: Int = 0
```

Function `countDown` keeps calling itself with a decremented argument until it reaches zero; the recursive calls then return with a value of zero:

```
--> countDown(n=2)
    --> countDown(n=1)
        --> countDown(n=0)
        <-- countDown(n=0): 0
    <-- countDown(n=1): 0
<-- countDown(n=2): 0
```

___Notes:___

* Unlike [_circular reasoning_](https://en.wikipedia.org/wiki/Circular_reasoning), recursion with termination meaningfully describes computations.
* Subsequent excercises explore how to find a recursive description of a computation, the choice of the termination conditions, and the reformulation as a tail-recursive version.
