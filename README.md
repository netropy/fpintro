# fpintro
Learning How to Program -- with Examples in Clojure and Scala

This tutorial contains the notes and coding exercises of an introductory session on programming with a high school student.

Many websites about ["getting kids excited about programming"](https://www.makeuseof.com/tag/10-tools-to-get-kids-excited-about-programming) employ coding with visual feedback (for example, moving around objects using directional commands, loops, and branches).  Our interest, however, was to get to understand the core concepts of _abstraction_ and _application_, that is, to start with [Functional Programming](https://en.wikipedia.org/wiki/Functional_programming).  Happily, this tutorial, whose coding examples are basic arithmetics in a Lisp-based language, came our way: [_Klipse for Kids_](http://kids.klipse.tech).

The _Klipse for Kids_ tutorial worked well for us.  It does not assume prior coding experience, quickly enables to write calculations and functions, and offers many, small coding excercises, which run locally in the browser's script engine and, thus, invite to experiment with language concepts just learned.  Due to rapid progress, we added exercises ourselves on working with [Booleans](https://en.wikipedia.org/wiki/Boolean_data_type), composing [functions](https://en.wikipedia.org/wiki/Function_(mathematics)), and added an entire chapter on [_recursion_](https://en.wikipedia.org/wiki/Recursion).  As a self-directed study on programming, this document also carries many links to technical terms and concepts on [Wikipedia](https://www.wikipedia.org/) for further reading.

Moreover, we did most coding excercises in two languages, [Clojure](https://clojure.org) and [Scala](https://www.scala-lang.org).  Clojure, as a modern descendant of LISP, is the language used in _Klipse for Kids_.  Scala makes it easier to later incorporate [Object-oriented Programming](https://en.wikipedia.org/wiki/Object-oriented_programming) concepts (or add [Java](https://java.com) as another language).  Starting with two programming languages turned out not delaying the learning progress but came naturally to the student who happened to grow up bilingually :-)

See the [LICENSE](License.txt) file for license rights and limitations (CC0-1.0).

## Table of Content

[0. Preliminaries: Writing Text](ch0_preliminaries.md)

[1. Motivation: An Ever-Changing World of Languages?](ch1_motivation.md)

[2. Expressions](ch2_expressions.md)

[3. Functions](ch3_0_functions.md)

[4. Recursive Functions](ch4_0_recursive_functions.md)

[5. Miscellaneous](ch5_miscellaneous.md)

## Coding Exercises

[2.0.1 Write arithmetic expressions: exercise KfK, chapter 1: What is computer programming?](ch2_expressions.md#201-write-arithmetic-expressions-exercise-kfk-chapter-1-what-is-computer-programming)\
[2.0.2 Write nested arithmetic expressions: exercise KfK, chapter 2: Expressions inside Expressions inside Expressions.](ch2_expressions.md#202-write-nested-arithmetic-expressions-exercise-kfk-chapter-2-expressions-inside-expressions-inside-expressions)\
[2.0.3 Write and use named expressions: exercise KfK, chapter 3: Giving Names to Expressions.](ch2_expressions.md#203-write-and-use-named-expressions-exercise-kfk-chapter-3-giving-names-to-expressions)\
[2.0.4 Write `list` expressions: exercise KfK, chapter 4: Evaluating Several Expressions.](ch2_expressions.md#204-write-list-expressions-exercise-kfk-chapter-4-evaluating-several-expressions)\
[2.0.5 Write expressions without evaluating them: exercise KfK, chapter 5: Please, tell me "what's your name?".](ch2_expressions.md#205-write-expressions-without-evaluating-them-exercise-kfk-chapter-5-please-tell-me-whats-your-name)\
[2.0.6 Write comparison operator expressions: exercise KfK, chapter 7: True or False (Pinocchio).](ch2_expressions.md#206-write-comparison-operator-expressions-exercise-kfk-chapter-7-true-or-false-pinocchio)\
[2.0.7 Write boolean operator expressions.](ch2_expressions.md#207-write-boolean-operator-expressions)

[ 3.1.1 Define and evaluate functions: exercise KfK, chapter 6: Functions (Happy birthday).](ch3_1_formulas_and_functions.md#311-define-and-evaluate-functions-exercise-kfk-chapter-6-functions-happy-birthday)

[3.2.1 Define and test a function `mydouble` that doubles a number.](ch3_2_more_function_exercises.md#321-define-and-test-a-function-mydouble-that-doubles-a-number)\
[3.2.2 Define and test a function that squares a number](ch3_2_more_function_exercises.md#322-define-and-test-a-function-that-squares-a-number)\
[3.2.3 Define and test a function that doubles the square of a number.](ch3_2_more_function_exercises.md#323-define-and-test-a-function-that-doubles-the-square-of-a-number)\
[3.2.4 Define and test a function that squares a number if the 1st operand is true, otherwise doubles the number.](ch3_2_more_function_exercises.md#324-define-and-test-a-function-that-squares-a-number-if-the-1st-operand-is-true-otherwise-doubles-the-number)\
[3.2.5 Test the language's predefined quotient/remainder operators.](ch3_2_more_function_exercises.md#325-test-the-languages-predefined-quotientremainder-operators)\
[3.2.6 Define and test a function that returns a list of the quotient and remainder of the division of 2 integers.](ch3_2_more_function_exercises.md#326-define-and-test-a-function-that-returns-a-list-of-the-quotient-and-remainder-of-the-division-of-2-integers)\
[3.2.7 Define and test a function `is_even` that tells whether an integer number is even.](ch3_2_more_function_exercises.md#327-define-and-test-a-function-iseven-that-tells-whether-an-integer-number-is-even)\
[3.2.8 Define and test a function `is_odd` that tells whether an integer number is odd in terms of using the "...even..." function.](ch3_2_more_function_exercises.md#328-define-and-test-a-function-isodd-that-tells-whether-an-integer-number-is-odd-in-terms-of-using-the-even-function)\
[3.2.9 Define predicates `not0` `and0`, `or0`, `nand0`, `xor0`, for the logical operators; use the conditional operator only.](ch3_2_more_function_exercises.md#329-define-predicates-not0-and0-or0-nand0-xor0-for-the-logical-operators-use-the-conditional-operator-only)\
[3.2.10 Test the predicates `not0` `and0`, `or0`, `xor0`, `nand0`.](ch3_2_more_function_exercises.md#3210-test-the-predicates-not0-and0-or0-xor0-nand0)

[3.3.1 Define and test functions `incr` and `decr` that increment (+1) respectively decrement (-1) a number `n`.](ch3_3_plotting_the_evaluation_of_functions.md#331-define-and-test-functions-incr-and-decr-that-increment-1-respectively-decrement--1-a-number-n)\
[3.3.2 Plot the evaluation of `incr(2)` and `decr(-1)`.](ch3_3_plotting_the_evaluation_of_functions.md#332-plot-the-evaluation-of-incr2-and-decr-1)\
[3.3.3 Define and test a function that decrements a number `n` if `n` is positive, otherwise returns `n` (use `decr`).](ch3_3_plotting_the_evaluation_of_functions.md#333-define-and-test-a-function-that-decrements-a-number-n-if-n-is-positive-otherwise-returns-n-use-decr)\
[3.3.4 Plot the evaluation of `decr_if_positive(-1)`.](ch3_3_plotting_the_evaluation_of_functions.md#334-plot-the-evaluation-of-decr_if_positive-1)\
[3.3.5 Plot the evaluation of `decr_if_positive(4)`.](ch3_3_plotting_the_evaluation_of_functions.md#335-plot-the-evaluation-of-decr_if_positive4)\
[3.3.6 Define and test a function that twice increments a number `n` (use `incr`).](ch3_3_plotting_the_evaluation_of_functions.md#336-define-and-test-a-function-that-twice-increments-a-number-n-use-incr)\
[3.3.7 Plot the evaluation of `incr_twice(3)`.](ch3_3_plotting_the_evaluation_of_functions.md#337-plot-the-evaluation-of-incr_twice3)

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

[4.4.1 Find a recursive definition for the addition of two numbers m, n.](ch4_4_recursive_add.md#441-find-a-recursive-definition-for-the-addition-of-two-numbers-m-n)\
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
[4.5.4 Make multiply robust by extending it to negative arguments.](ch4_5_recursive_multiply.md#454-make-multiply-robust-by-extending-it-to-negative-arguments)\
[4.5.5 Reformulate multiply to make it tail-recursive and handling negative arguments.](ch4_5_recursive_multiply.md#455-reformulate-multiply-to-make-it-tail-recursive-and-handling-negative-arguments)\
[4.5.6 Plot the evaluation of tail-recursive multiply(2,5).](ch4_5_recursive_multiply.md#456-plot-the-evaluation-of-tail-recursive-multiply25)

... and now we understand:

![](https://imgs.xkcd.com/comics/functional_2x.png)

-------------------

[--> next page](ch0_preliminaries.md)
