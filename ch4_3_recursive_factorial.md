### 4.3 Recursive Function `factorial`

#### Continue the sequence in which each number is the product of all previous numbers starting with 1.

```
0 ->   1 
1 ->   1 = 1 * 1
2 ->   2 = 1 * 1 * 2
3 ->   6 = 1 * 1 * 2 * 3
4 ->  24 = 1 * 1 * 2 * 3 * 4
5 -> 120 = 1 * 1 *  ...  * 4 * 5
...
```

#### Express `factorial(n)`, which computes the product of `1 * 1 * ... * n`, in terms of `factorial(n-1)`.

```
factorial(0) = 	 1
factorial(1) = 	 1 = 1 * 1 factorial(0) * 1
factorial(2) = 	 2 = 1 * 1 * 2 = factorial(1) * 2
factorial(3) = 	 6 = 1 * 1 * 2 * 3 = factorial(2) * 3
factorial(4) =  24 = 1 * 1 * 2 * 3 * 4 = factorial(3) * 4
factorial(5) = 120 = 1 * 1 *  ...  * 4 * 5 = factorial(4) * 5
...
factorial(n) = ... = (0 * 1 * ... * n-1) * n = factorial(n-1) * n
```

#### Define the function `factorial(n)` in terms of `factorial(n-1)` and add a simple unit test.

Hint: Also reject negative arguments.

```scala
def factorial(n: Int): Int = {
  require(n >= 0, "n must be non-negative!")
  if (n == 0) 1 else factorial(n - 1) * n
}
```

___Notes:___

* Not used here, but the mathematical function [factorial](https://en.wikipedia.org/wiki/Factorial) has an extension to negative arguments.

#### Plot the evaluation of `factorial(5)`.

```
--> factorial(n=5)
    --> factorial(n=4)
        --> factorial(n=3)
	    --> factorial(n=2)
	        --> factorial(n=1)
		    --> factorial(n=0)
		    <-- factorial(n=0): 1
		<-- factorial(n=1): 1
	    <-- factorial(n=2): 2
	 <-- factorial(n=3): 6
    <-- factorial(n=4): 24
<-- factorial(n=5): 120
```

