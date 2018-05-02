# fpintro
Learning How to Program with Examples in Clojure and Scala

This tutorial contains the excercises and notes of an introductory programming session with a high school student.

While there are many websites and tools for ["getting kids excited about programming"](https://www.makeuseof.com/tag/10-tools-to-get-kids-excited-about-programming), we choose to try out this great tutorial: [Klipse for Kids](http://kids.klipse.tech).  Since this was a self-directed study on programming, this document carries many links to helpful articles from [Wikipedia](https://www.wikipedia.org/).

We chose [Clojure](https://clojure.org) and [Scala](https://www.scala-lang.org) as the two languages to begin the learning process with a [Functional Programming](https://en.wikipedia.org/wiki/Functional_programming) paradigm.  Starting with two languages has come quite naturally, since the student grew up bilingually ;-)  Clojure, as a modern LISP, is the language used on the "Klipse for Kids" website.  Doing the same coding excercises also in Scala, will later allow for a smooth incorporation of [Object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming) concepts.

See the [LICENSE](License.txt) file for license rights and limitations (CC0-1.0).

## Table of Content

[0. Preliminaries: Writing Text](ch0_preliminaries.md)

[1. Motivation: An Ever-Changing World of Languages?](ch1_motivation.md)

// TODO: [2. Expressions](ch2_expressions.md)

[3. Functions](ch3_0_functions.md)

[4. Recursive Functions](ch4_0_recursive_functions.md)

[5. Miscellaneous](ch5_miscellaneous.md)

## Coding Exercises

[4.1.1 Define two functions ping(n) and pong(n) that call each other with an incremented argument.](ch4_1_recursive_calls.md#411-define-two-functions-pingn-and-pongn-that-call-each-other-with-an-incremented-argument)\
[4.1.2 Run and plot the evaluation of ping(2).](ch4_1_recursive_calls.md#412-run-and-plot-the-evaluation-of-ping2)\
[4.1.3 Define a function increase(n) that calls itself and then returns an incremented result.](ch4_1_recursive_calls.md#413-define-a-function-increasen-that-calls-itself-and-then-returns-an-incremented-result)\
[4.1.4 Run and plot the evaluation of increase(2).](ch4_1_recursive_calls.md#414-run-and-plot-the-evaluation-of-increase2)\
[4.1.5 Define a function grow(n) that calls itself with an incremented argument value.](ch4_1_recursive_calls.md#415-define-a-function-grown-that-calls-itself-with-an-incremented-argument-value)\
[4.1.6 Run and plot the evaluation of grow(2).](ch4_1_recursive_calls.md#416-run-and-plot-the-evaluation-of-grow2)\
[4.1.7 Define a function count_down(n) that calls itself with a decremented argument until zero, then returns zero.](ch4_1_recursive_calls.md#417-define-a-function-count_downn-that-calls-itself-with-a-decremented-argument-until-zero-then-returns-zero)\
[4.1.8 Run and plot the evaluation of count_down(2).](ch4_1_recursive_calls.md#418-run-and-plot-the-evaluation-of-count_down2)


[4.2.1 Continue the sequence in which each number is the sum of all previous numbers starting from 0.](ch4_2_recursive_sum.md#421-continue-the-sequence-in-which-each-number-is-the-sum-of-all-previous-numbers-starting-from-0)\
[4.2.2 Express sum(n), which computes the sum of 0 + ... + n, in terms of sum(n-1).](ch4_2_recursive_sum.md#422-express-sumn-which-computes-the-sum-of-0----n-in-terms-of-sumn-1)\
[4.2.3 Define the function sum(n) in terms of sum(n-1) and add a simple unit test.](ch4_2_recursive_sum.md#423-define-the-function-sumn-in-terms-of-sumn-1-and-add-a-simple-unit-test)\
[4.2.4 Plot the evaluation of sum(4).](ch4_2_recursive_sum.md#424-plot-the-evaluation-of-sum4)\
[4.2.5 Make sum robust by rejecting negative arguments.](ch4_2_recursive_sum.md#425-make-sum-robust-by-rejecting-negative-arguments)\
[4.2.6 Make sum robust by extending it to negative arguments.](ch4_2_recursive_sum.md#426-make-sum-robust-by-extending-it-to-negative-arguments)

[4.3.1 Continue the sequence in which each number is the product of all previous numbers starting with 1.](ch4_3_recursive_factorial.md#431-continue-the-sequence-in-which-each-number-is-the-product-of-all-previous-numbers-starting-with-1)\
[4.3.2 Express factorial(n), which computes the product of 1 * 1 * ... * n, in terms of factorial(n-1).](ch4_3_recursive_factorial.md#432-express-factorialn-which-computes-the-product-of-1--1----n-in-terms-of-factorialn-1)\
[4.3.3 Define the function factorial(n) in terms of factorial(n-1) and add a simple unit test.](ch4_3_recursive_factorial.md#433-define-the-function-factorialn-in-terms-of-factorialn-1-and-add-a-simple-unit-test)\
[4.3.4 Plot the evaluation of factorial(5).](ch4_3_recursive_factorial.md#434-plot-the-evaluation-of-factorial5)

[4.4.1 Find a recursive definition for the addition of two numbers m, n.](https://github.com/netropy/fpintro/blob/master/ch4_4_recursive_add.md#441-find-a-recursive-definition-for-the-addition-of-two-numbers-m-n)\
[4.4.2 Define a recursive function add(m, n) with a simple unit test.](ch4_4_recursive_add.md#442-define-a-recursive-function-addm-n-with-a-simple-unit-test)\
[4.4.3 Plot the evaluation of add(3, 2).](ch4_4_recursive_add.md#443-plot-the-evaluation-of-add3-2)\
[4.4.4 Make add robust by extending it to negative arguments.](ch4_4_recursive_add.md#444-make-add-robust-by-extending-it-to-negative-arguments)\
[4.4.5 Make add robust by extending it to negative arguments -- alternative version.](ch4_4_recursive_add.md#445-make-add-robust-by-extending-it-to-negative-arguments----alternative-version)\
[4.4.6 Plot the evaluation of add(-2, -1).](ch4_4_recursive_add.md#446-plot-the-evaluation-of-add-2--1)\
[4.4.7 Reformulate add to make it tail-recursive.](ch4_4_recursive_add.md#447-reformulate-add-to-make-it-tail-recursive)\
[4.4.8 Plot the evaluation of tail-recursive add(3, 2).](ch4_4_recursive_add.md#448-plot-the-evaluation-of-tail-recursive-add3-2)\
[4.4.9 Make the tail-recursive version of add robust by extending it to negative arguments.](ch4_4_recursive_add.md#449-make-the-tail-recursive-version-of-add-robust-by-extending-it-to-negative-arguments)


[4.5.1 Find a recursive definition for the addition of two numbers m, n.](ch4_5_recursive_multiply.md#451-find-a-recursive-definition-for-the-addition-of-two-numbers-m-n)\
[4.5.2 Define a recursive function multiply(m, n) with a simple unit test.](ch4_5_recursive_multiply.md#452-define-a-recursive-function-multiplym-n-with-a-simple-unit-test)\
[4.5.3 Plot the evaluation of multiply(3,5).](ch4_5_recursive_multiply.md#453-plot-the-evaluation-of-multiply35)\
[4.5.4 Make multiply robust by extending it to negative arguments.](https://github.com/netropy/fpintro/blob/master/ch4_5_recursive_multiply.md#454-make-multiply-robust-by-extending-it-to-negative-arguments)\
[4.5.5 Reformulate multiply to make it tail-recursive and handling negative arguments.](ch4_5_recursive_multiply.md#455-reformulate-multiply-to-make-it-tail-recursive-and-handling-negative-arguments)\
[4.5.6 Plot the evaluation of tail-recursive multiply(2,5).](ch4_5_recursive_multiply.md#456-plot-the-evaluation-of-tail-recursive-multiply25)

