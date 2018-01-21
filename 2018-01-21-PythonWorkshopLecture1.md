---
layout : post
title : 'Python Workshop : Lecture 1'
category : ['Python Workshop',]
---

## Programming Languages

The programming languages most commomly used are :
* C
* C++
* Java
* Python
* and many more...

Programming languages are generally used to communicate with a machine.

## Comparison among programming languages

Here's a comparison among widely known programming languages.
* Execution Time: C < C++ < Java < Python
* Lines of code: C > C++ > Java > Python

The fact is that an app which a Python programmer can finish in 2 months, two C++ programmers may not be able to complete in a year.

## Why Python?

The following answer the question of need for python:
* Easy to learn.
* User friendly language.
* Easy syntax.
* Requires less programming efforts.
* The commands are logically derived from spoken English.

## Python vs C

How is python different from C?
* For a C program, you first need to write the entire program. Then the program is compiled to generate an executable. The executable is then run on a computer.
* A Python program is interpreted. This means that you can write the programs one line after another on the fly, and the computer will execute it immediately after a line is written.

**Note:** Even though a program is executed line by line, you can write a complete Python program and execute it.

## Printing a line

Comparison of codes to print a line.
**In C:**
```
#include <stdio.h>
void main()
{
printf(“Hello World”);
}
```

**In Python:**
```python
print “Hello World”
```

## Using Python as a calculator - Arithmetic Operations
Some examples of arithmetic operations on python:
```python
>>> 5+4
9
>>> 5-4
1
>>> 5*4
20
>>> 5/4
1
>>> 5.0/4
1.25
>>> 5.0//4
1.0
>>> 5**4
625
```
## Variables

```python
	a = 5
	b = 4
	print a+b
	b = 10
	print a+b
```

**Note 1:** Unlike in C, we do not have to declare variables. They are automatically created when a value is assigned for the first time.
**Note 2:** Unlike in C, a variable can take any type.

## Variable Names in Python

The names of variables must follow the below rules:
* Must start with a letter or underscore
* Must consist of only letters, numbers or underscore
* Must not be a reserved word

Words that have fixed meaning in a programming language that cannot be redefined by a programmer as for use in variables or identifiers are called **reserved words** or **keywords**. In Python, examples of keywords are ’for’,
’and’, ’if’ etc.
To list all keywords in Python:
```python
>>> import keyword
>>> keyword.kwlist
```

## Taking User Input

There are two functions in Python that are used to read user input.
* rawinput(): This function is used to get the user’s input as a string.
* input(): This function is used to get the user’s input as an integer.

## Comments in Python programs

Comments are used to make the programs more readable.
* # This is a single line comment.
* “““ This is a<br>
 multiline<br>
 comment ”””

**Note:** Reserved words can be used within comments.

## Comparison Operators

* Comparison operators return one of the two values: ‘True’ or ‘False’.
* Examples of comparison operators are:
  * == : Returns ‘True’ if the left and right side of the operators are equal.
  * != or <>: Returns ‘True’ if the left and right side of the operators are not equal.
  * <: Returns ‘True’ if the left side is less than the right side.
  * >: Returns ‘True’ if the left side is greater than the right side.

**Note:** To check if two values are equal, the operator is ‘==’ and not ‘=’.

## Short hand arithmetic operators

* x += a ≡ x = x + a
* Similarly, it can be extended to other arithmetic operators.

**Note:** Unlike C, there is no ‘++’ operator for incrementing.

## Complex Numbers in Python
Examples of complex arithmetic operations using python:

```python
>>> a = 3+4j
>>> b = 6+8j
>>> a+=b
>>> a
(9+12j)
>>> abs(a)
15.0
```

## If statements

Points to remember:
* An ‘if’ statement is followed by a conditional statement and then a ‘:’.
* The statements are executed if the conditional statement evaluates to
‘True’.
* All the statements that must be executed if the condition is True must be indented one level more than the ‘if’ statement.

## Compound conditions

You can use the logical operators ‘and’, ‘or’, ‘not’ to build compound conditions:
* <condition1> **and** <condition2> evaluates to True when both the conditions are True.
* <condition1> **or** <condition2> evaluates to True when one of the conditions are True.
* **not** <condition> evaluates to True when the condition is False.
