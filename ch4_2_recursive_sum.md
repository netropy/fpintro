### 4.2 Recursive Function `sum`

#### Continue the sequence in which each number is the sum of all previous numbers starting from 0.

```
0 ->  0 = 0
1 ->  1 = 0 + 1
2 ->  3 = 0 + 1 + 2
3 ->  6 = 0 + 1 + 2 + 3
4 -> 10 = 0 + 1 + 2 + 3 + 4
5 -> 15 = 0 + 1 +  ...  + 4 + 5
...
```

#### Express `sum(n)`, which computes the sum of `0 + ... + n`, in terms of `sum(n-1)`.

```
sum(0) =  0 = 0
sum(1) =  1 = 0 + 1 = sum(0) + 1
sum(2) =  3 = 0 + 1 + 2 = sum(1) + 2
sum(3) =  6 = 0 + 1 + 2 + 3 = sum(2) + 3
sum(4) = 10 = 0 + 1 + 2 + 3 + 4 = sum(3) + 4
sum(5) = 15 = 0 + 1 +  ...  + 4 + 5 = sum(4) + 5
...
sum(n) =  ? = (0 + 1 + ... + n-1) + n = sum(n-1) + n
```

#### Define the function `sum(n)` in terms of `sum(n-1)` and add a simple unit test.

```scala
def sum(n: Int): Int =
  if (n == 0) 0 else sum(n-1) + n

assert(sum(0) == 0)
assert(sum(1) == 1)
assert(sum(2) == 3)
assert(sum(4) == 10)
assert(sum(5) == 15)
```

```clojure
(def sum #(if (= % 0) 0 (+ (sum (- % 1)) %)))

(sum 4) ; = 10
```
___Notes:___

* The [summation](https://en.wikipedia.org/wiki/Summation) can also be computed by a non-recursive, closed formula: `sum(n) = n * (n + 1) / 2`.

#### Plot the evaluation of `sum(4)`.

```
--> sum(n=4)
    --> sum(n=3)
        --> sum(n=2)
	    --> sum(n=1)
	        --> sum(n=0)
		<-- sum(n=0): 0
            <-- sum(n=1): 1
	<-- sum(n=2): 3
    <-- sum(n=3): 6
<-- sum(n=4): 10
```

#### Make `sum` robust by rejecting negative arguments.

```scala
def sum(n: Int): Int = {
  require(n >= 0, "n must be non-negative!")
  if (n == 0) 0 else sum(n - 1) + n
}
```
___Notes:___

* TODO: explain `require` and `assert` in Scala/Clojure.

#### Make `sum` robust by extending it to negative arguments.

Hint: It is evident how to sum up negative numbers:
```
...
-6 = 0 + -1 + -2 + -3
-3 = 0 + -1 + -2
-1 = 0 + -1
 0 = 0
 1 = 0 + 1
 3 = 0 + 1 + 2
 6 = 0 + 1 + 2 + 3
...
```

```scala
def sum(n: Int): Int =
  if (n == 0) 0 else ( if (n < 0) -sum(-n) else sum(n - 1) + n )

assert(sum(0) == 0)
assert(sum(1) == 1)
assert(sum(2) == 3)
assert(sum(4) == 10)
assert(sum(-1) == -1)
assert(sum(-2) == -3)
assert(sum(-4) == -10)
```

```clojure
(def sum #(if (= % 0) 0 (if (< % 0) (- (sum (- %))) (+ (sum (- % 1)) %))))

(sum 4) ; = 10
(sum -4) ; = -10
```

___Notes:___

* If the argument is negative, the calculation "delegates" to a positive argument and adjusts the sign afterwards.
* In Scala, there's no need to wrap the 2nd if-then-else in round brackets, hence, better written as chain: `if ... else if (...) ... else ...`.
