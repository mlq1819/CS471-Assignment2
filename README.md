# CS471-Assignment2
Homework Assignment 2
Programming Languages
CS471, Spring 2020
Due Tuesday, Feb 4, 2020

General submission instructions can be found at http://bingweb.binghamton.edu/~head/CS471/requirements.html
Read Chapter 2 - Pages 43 to 56, page 67 (2.2.5) pages 69. 73-78  (2.3.1)
Do CYU chapter 1 - 9, 16-19, 20,27,29,30
Homework 2
Code
You'll need the following files to complete the assignment:
Makefile
arith1.c
arith2.c
Problem 1:
Examine arith1.c: It contains an implementation of a simple arithmatic calculator. The following will compile and run a few test cases.

make arith1
./arith1
1 + 2 + 3
./arith1
1 + 2 * 3

The arith1 language is parsed used a recursive-descent parser: It is fairly straightforward to determine the language's grammar from the parser.

In particular:
(1) Using the code, give the complete grammar in BNF form
(2) Is the grammar left or right recursive? How does that affect the associativity of plus and mult?

Problem 1 Answer:

Problem 2:
Using the grammar you extracted in Problem 1 add two new operators,  exponents, "^",  and minus, "-" , operators to the arith1 language .  Exponent operator, "^", should have the highest precedence and "-" should have the a higher precedence than "+" and lower precedence than "*". but still be able to be overridden using parentheses as defined by the grammar. Both operators should have the same associativity as plus and times.
Give the modified grammar.
Problem 2 Answer:
Problem 3:
Write the left derivation for the following expressions according to the modified grammar from Problem 2 -- It may help to draw the parse tree first.
1 + 2 - 2
1 + 2 - 3 * 5
2 ^ 5 ^ 2
NOTE: You should show only one step at a time -- as we did in class -- but may jump from number to the actual terminal number.

For example:
number '+' expr
'10' '+' expr

Problem 3 Answer:
Problem 4:
Modify arith1.c and add the new operator that you defined in Problem 2. Pay careful attention to the pattern between the original grammar and the associated function calls in arith1.c. If you have properly adjusted the grammar, it should be a straightforward modification of the original functions with the additional of a couple new function for the new operator.  (You may use powI.c to compute "^")

You should pay careful attention to how expressions evaluate; a compile and a correct evaluation of some expressions does not mean you have modified everything correctly. Try the sample cases below. 

./arith
1 + 2 - 2
The result is: 1

./arith
1 + 2 - 3 * 5
The result is: -12

./arith
2 ^ 5 ^ 2
The result is: 33554432
Problem 4 Answer:
(Which file contains the modified code?)
Problem 5:
Examine arith2.c: It contains another implementation of a simple arithmetic calculator. The following will compile and run a few test cases. 

make arith2
./arith2
1 + 2 * 3
./arith2
1 + 2 + 3

The arith2 language is parsed using a slightly different technique, although it is still considered a recursive-descent parser. Pay careful attention to the way while loops are used to parse, instead of pure recursion. Thinking in terms of EBNF (hint: kleene star) may help determine the difference from the previous grammar.

In particular:
(1) Using the code, give the complete grammar in BNF or EBNF form
(2) Is the grammar left or right recursive? How does that affect the associativity of plus and mult?

Problem 5 Answer:

Problem 6:
Using the grammar you extracted in Problem 5 add two new operators to the arith2 language. The first, minus, should have higher precedence than plus,but lower precedence than mult. The second, exponent, ^, should have higher precedence than mult, but still be able to be overridden usingparentheses as defined by the grammar. Both operators should have the same associativity as plus and times.

Give the modified grammar.

Problem 6 Answer:

Problem 7:
Write the left derivation for the following expressions according to the modified grammar from Problem 6 -- It may help to draw the parse tree first.
1 + 2 -2
1 + 2 - 3 * 5
2 ^ 5 ^ 2

NOTE: You should show only one step at a time -- as we did in class -- but may jump from number to the actual terminal number.
For example:
number '+' expr
'10' '+' expr
Problem 7 Answer:

Problem 8:
Modify arith2.c and add the new operators that you defined in Problem 6. Pay careful attention to the pattern between the original grammar and the associated function calls in arith2.c. If you have properly adjusted the grammar, it should be a straightforward modification of the original functions with the additional of a couple new functions for the new operators.

You should pay careful attention to how expressions evaluate; a compile and a correct evaluation of some expressions does not mean you have modified everything correctly. Try the sample cases below. 


./arith
1 + 2 - 2
The result is:
1
./arith
1 + 2 - 3 * 5
The result is: -12

./arith
2 ^ 5 ^ 2
The result is:
1024


Problem 8 Answer:
(Which file contains the modified code?)
Problem 9:
Both _Bool and bool are available in the ISO C standard published in 2011.  Briefly explain:
(1) What are they used for?
(2) Why do both exist?
(3) Is one better than the other? Why?

Problem 9 Answer:

Problem 10:
Page 69 cyu 19:
What are pragmas? Why are they processed by the scanner?  Briefly, if you are a language designer what are the trade offs of providing pragmas in a language?

Problem 10 Answer:

Problem 11:
Operator precedence and associativity are often subtle details that are overlooked when using a language (and require careful treatment when implementing a compiler). One way around this issue is to use prefix or postfix notation. This is not as foreign as you think, every function call is in prefix notation: 2 powI 3 is just as valid as + 2 3.
Rewrite the expressions a-d below in prefix notation. Assume the following precedences  and associativities for the operators:


Binary
Operator
Precedence
(3 highest)
Associativity
^
3
right
-
2
left
*
1
left
+
1
left
The algorithm for rewriting is very straightforward:
Parenthesize the expression fully, using the rules of precedence and associativity.
Within each parenthesized sub-expression, move the operator to left of its left operand.
Remove the parentheses.
The operands will have the same order in the resulting expressions (due to the restriction that the operators are NOT commutative).

a) w ^ x ^ y  -  z
     b)  w - x  ^  y  ^  z
c) w  *  x  *  y  - z
     d)  w + x  *  y  +  z

Problem 11 Answer:

Problem 12:
Repeat Problem 10, but use postfix  notation instead.


Problem 12 Answer:
Problem 13:
[Rosen,Discrete Mathematics and Its Applications 5th ed., pg 273 #48] "Consider the following inductive definition of a version of Ackermann's function.  This function was named after Wilhelm Ackermann, a German mathematician who was a student of the great mathematician David Hilbert.  Ackermann's function plays an important role in the theory of recursive functions and in the study of complexity of certain algorithms involving set unions."  In the early days of  imperative languages, Ackermann's function was used to measure the recursion capability of a compiler.

The Ackermann Number N of the compiler as the largest N for which
          ack (3,N)
gives an answer without a stack overflow.  In earlier decades a variation had been used as one of the benchmarking algorithms.  (There are several different variants of this function.  All are called Ackermann's functions and their values do NOT have to agree!)  

ack( m,n ) =	n + 1
if m = 0
ack( m,n ) =	ack(m - 1, 1)
if n = 0 and m > 0 
ack( m,n ) =	ack( m-1, ack( m, n-1 ) )      	if n >0 and m > 0

What is the value of ack(1,0) ?
What is the value of ack(0,6) ?

Problem 13 Answer:
