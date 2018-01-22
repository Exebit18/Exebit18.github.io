---
layout : post
title : 'Python Workshop: Lecture 1'
category : ['Python Workshop',]
---

This is the summary of what was covered during Lecture 1 of the Python Workshop series.

## 1. Programming Languages

Programming languages are generally used to communicate with a machine. The programming languages most commomly used are:
* C
* C++
* Java
* Python
* and many more...


## 2. Comparison among programming languages

Here's a comparison among widely known programming languages:
* Execution Time: `C < C++ < Java < Python`
* Lines of code: `C > C++ > Java > Python`

The fact is that an app which a Python programmer can finish in 2 months, two C++ programmers may not be able to complete in a year.

## 3. Why Python?

The following answer the question of need for python:
* Easy to learn.
* User friendly language.
* Easy syntax.
* Requires less programming efforts.
* The commands are logically derived from spoken English.

## 4. Python vs C

How is python different from C?
* For a C program, you first need to write the entire program. Then the program is compiled to generate an executable. The executable is then run on a computer.
* A Python program is interpreted. This means that you can write the programs one line after another on the fly, and the computer will execute it immediately after a line is written.

**Note:** Even though a program is executed line by line, you can write a complete Python program and execute it.

## 5. Printing a line

**In C:**
```c
#include <stdio.h>

void main(){
    printf(“Hello World”);
}
```

**In Python:**
```python
print “Hello World”
```

## 6. Using Python as a calculator - Arithmetic Operations
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

## 7. Variables

```python
>>> a = 5
>>> b = 4
>>> print a+b
9
>>> b = 10
>>> print a+b
15
```

**Note 1:** Unlike in C, we do not have to declare variables. They are automatically created when a value is assigned for the first time.

**Note 2:** Unlike in C, a variable can take any type.

## 8. Variable Names in Python

The names of variables must follow the below rules:
* Must start with a letter or underscore
* Must consist of only letters, numbers or underscore
* Must not be a reserved word

Words that have fixed meaning in a programming language that cannot be redefined by a programmer as for use in variables or identifiers are called **reserved words** or **keywords**. In Python, examples of keywords are `for`,
`and`, `if` etc.

To list all keywords in Python:
```python
>>> import keyword
>>> keyword.kwlist
['and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'exec', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'not', 'or', 'pass', 'print', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

## 9. Taking User Input

There are two functions in Python that are used to read user input.
* `rawinput()`: This function is used to get the user’s input as a string.
* `input()`: This function is used to get the user’s input as an integer.

Here's an example program:

```python
a = raw_input()
b = raw_input()

print a+b

a = input()
b = input()

print a+b
```

## 10. Comments in Python programs

Comments are used to make the programs more readable.
* Single Line Comments:
```python 
# This is a single line comment.
```

* Multi Line Comments:
```python
“““ 
    This is a
    multiline
    comment 
”””
```

**Note:** Reserved words can be used within comments.

Here's an example program demonstrating usage of comments: 

```python
# This program shows comments and prints the sum of two numbers.
a = 5
b = 6

""" Find the sum
of the two numbers """
print a+b
```

## 11. Comparison Operators

* Comparison operators return one of the two values: `True` or `False`.
* Examples of comparison operators are:
  * `==` : Returns `True` if the left and right side of the operators are equal.
  * `!=` or `<>`: Returns `True` if the left and right side of the operators are not equal.
  * `<`: Returns `True` if the left side is less than the right side.
  * `>`: Returns `True` if the left side is greater than the right side.

**Note:** To check if two values are equal, the operator is `==` and not `=`.

```python
>>> print 1 < 2
True
>>> print 2 > 3
False
>>> print 1 > 2
False
>>> print 2 < 3
True
>>> print 1 == 1
True
>>> print 1 != 1
False
>>> print 1 <> 1
False
>>> print 1 <= 2
True
>>> print 1 <= 1
True
```

## 12. Short hand arithmetic operators

* `x += a` is equivalent to `x = x + a`
* Similarly, it can be extended to other arithmetic operators.

**Note:** Unlike C, there is no `++` operator for incrementing.

## 13. Complex Numbers in Python
Examples of complex arithmetic operations using python:

```python
>>> a = 3+4j
>>> b = 6+8j
>>> a += b
>>> a
(9+12j)
>>> abs(a)
15.0
```

## 14. If statements

Points to remember:
* An `if` statement is followed by a conditional statement and then a `:`.
* The statements are executed if the conditional statement evaluates to
`True`.
* All the statements that must be executed if the condition is true must be indented one level more than the `if` statement.

**Example 1**: Only `if` conditional

```python
number = input("Enter your roll number: ")
branch = raw_input("Enter your branch: ")

if number == 28:
    print "Hello roll number 28"

if branch == "CS":
    print "Hello Coder!"
    if number == 28:
        print "Hello roll number 28 from CS"
        
print "Hello world!"
```

**Example 2**: `if-else` conditional

```python
number = input("Enter your roll number: ")

if number == 28:
    print "Hello roll number 28"    
else:
    print "You are not roll number 28"
```

**Example 3**: `if-elif-else` conditional

```python
number = input("Enter your roll number: ")

if number == 28:
    print "Hello roll number 28"
elif number == 30:
    print "Hello roll number 30"
else:
    print "Hello world"
```

## 15. Compound conditions

You can use the logical operators `and`, `or`, `not` to build compound conditions:
* `<condition1> and <condition2>` evaluates to `True` when both the conditions are true.
* `<condition1> or <condition2>` evaluates to `True` when one of the conditions are true.
* `not <condition>` evaluates to `True` when the condition is false.

```python
marks = input("Enter the marks: ")

if marks > 90:
    print "S grade"
elif marks > 80 and marks <= 90:
    print "A grade"
elif marks > 70 and marks <= 80:
    print "B grade"
else:
    print "C grade"
```