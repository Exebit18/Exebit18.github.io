---
layout : post
title : 'Python Workshop: Lecture 2'
category : ['Python Workshop',]
---

What we learnt about in session 1:

## Overview

* Printing
* Python as a calculator
* Variables
* User Input
* Comparison Operators
* Conditional Statements

## Overview of session 2:

* ‘is’ and ‘in’ operator
* ‘while’ and ‘for’ loops
* ‘break’ and ‘continue’ statements
* Lists
* Strings
* Problems

## ‘IS’ OPERATOR

Evaluates to true if the variables on either side of the operator point to the same object and false otherwise.
x is y, here is results in 1 if id(x) equals id(y).

Example:
```python
a = 10
b = 10
if (a is b):
print “a is equal to b”
else
print “a is not equal to b”
```

## ‘IN’ OPERATOR

Evaluates to true if it finds a variable in the specified sequence and false otherwise. x in y, here in results in a 1 if x is a member of sequence y.

Example:
```python
a = 10
list = [11, 30, 10, 22, 15]
if (a in list):
print “a is in the list”
else
print “a is not in the list”
```

## FOR LOOP

![while loop]({{"/images/while.jpg"}})

## WHILE STATEMENT

To print odd numbers less than a

```python
>>> i=1
>>> while i<10:     #execute while the statement is true
. . .
print i
. . .
i+=2                # it means i=i+2
1
3
5
7
9
```

## FOR LOOP

![for loop]({{"/images/for.jpg"}})

## FOR STATEMENT
```python
>>> arr = [ ‘a’, ‘b’, ‘c’, ‘d’, ‘e’ ]
>>> for i in range (len (a)):
...
print (i, arr[i])
...
0 a
1 b
2 c
3 d
4 e
```

```python
>>> words = [ ‘Exebit’, ‘IITM’ ]
>>> for w in words: # for each element in the list words
. . .
print w
```
Exebit
IITM
```python
>>> for w in words:
. . .
if len(w) > 5:
. . .
words.insert (1, ‘2018’)
>>> words
[ ‘Exebit’, ‘2018’, ‘IITM’ ]
```

## LOOP CONTROL STATEMENT – ‘BREAK’

* Terminates the current loop and resumes execution at the next statement
* The break statement can be used in both while and for loops.
* In case of nested loops, the break statement stops the execution of the innermost loop and start executing the next line of code

## BREAK STATEMENT

```python
>>> for i in 'kohli':
if i=='l':
break
print i
>>> a=10
>>> while(a>0):
print a
a=a-1
if a==5:
break
```

## LOOP CONTROL STATEMENT – ‘CONTINUE’

* The continue statement rejects all the remaining statements in the current iteration of the loop and moves the control back to the top of the loop.
* Used in both while and for loops

## CONTINUE STATEMENT

```python
>>> for i in 'kohli':
if i=='l':
continue
print i
>>> a=10
>>> while(a>0):
a=a-1
if a==5:
continue
print a
```

## PROBLEM

Here's a problem to try:

Write a program to check if a number is Prime or not using both 'While' and 'For' loop.

## LISTS INTRODUCTION

* Versatile datatype available in Python
* Ordered Collection of data
* All items in the list need not have same data type

## ACCESSING LIST ELEMENTS
```python
>>> squares = [1, 4, 9, 16, 25]
>>> print squares[0]     # indexing returns the item
1
>>> print squares[-2]
16
>>> print squares[1:4]
[4,9,16]
```
list[a:b] returns a list from list[a] to list [b-1] 

## EDITING A LIST

```python
>>> squares = [1, 4, 9, 16, 25]
>>> squares += [36, 48, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 48, 64, 81, 100]
```
Or
```python
>>> squares.extend([36,48,64,81,100])
>>> squares.append(121)
[1, 4, 9, 16, 25, 36, 48, 64, 81, 100,121]
>>> squares.remove(48)
[1, 4, 9, 16, 25, 36, 64, 81, 100,121]
```

## LIST OF STRINGS

```python
>>> a = [“Exebit”, ”2018”, ”IIT”, “Madras”]
>>> a[0]
‘Exebit’
>>> a[2][2]
‘T’
>>> a[3][1]
‘a’
```

## MORE ON LISTS
```python
>>> l = [ 1, 2, 1, 1, 0, 5, 1, 3, 5, 1 ]
>>> print l.count (1), l.count (5)
5 2
>>> l.sort ()
>>> print l
0 1 1 1 1 1 2 3 5 5
>>> l.reverse ()
>>> print l
5 5 3 2 1 1 1 1 1 0
```

## LIST COMPREHENSION

Example to create a list of squares.
1) You can use loops.
```python
>>> squares = [ ]
>>> for i in range(10):
squares.append (i*i)
```

2) Or you can use list comprehension:
```python
>>> squares = [ i*i for i in range(10) ]
```

```python
>>> a=[i**3 for i in range(10)]
>>> b=[i for i in a if i%2==0]
>>> b
[0, 8, 64, 216, 512]
>>> a
[0, 1, 8, 27, 64, 125, 216, 343, 512, 729]
```

## LIST COMPREHENSION WITH MORE THAN 1 LOOPS


```python
>>> l=[1,2,3]
>>> p=['Python','Perl','java']
>>> print [(i,j) for i in l for j in p]
[(1, 'Python'), (1, 'Perl'), (1, 'java'), (2, 'Python'), (2, 'Perl'), (2, 'java'), (3, 'Python'),
(3, 'Perl'), (3, 'java')]
>>> print [(i,j) for i in l for j in p if j[0]=='P']
[(1, 'Python'), (1, 'Perl'), (2, 'Python'), (2, 'Perl'), (3, 'Python'), (3,’Perl’)]
```

## PRINT ALL PRIMES LESS THAN N
```python
>>> primes = [h for h in range(2, 100) if h not in [j for i in range(2, 10) for j in
range(i*2, 100, i)]]
>>> print primes
. . . [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71,
73, 79, 83, 89, 97]
```

## STRINGS
```python
>>> p = “Exe”
>>> p[2]
‘e’
>>> p = p + “bit”
>>> p
“Exebit”
>>> p[2:5] + p[0]
“ebiE”
```

## STRINGS CONT.

```python
>>> p*5
“ExebitExebitExebitExebitExebit”
>>> len(p)
6
>>> string = ‘, ‘.join([“Apple”,”Mango”,”Banana”])
>>> print string
‘Apple, Mango, Banana’
>>> print p.upper()
“EXEBIT”             # try lower() function too
```

```python
>>> import string
>>> string.atof(‘437.4876’)
437.4876
>>> string.atoi(‘365’)
365
>>> str = ‘Exebit 2018 IIT Madras’
>>> str.split (‘ ‘)
[‘Exebit’, ‘2018’, ‘IIT’, ‘Madras’]
```
## PROBLEM

Here are a few problems to try out.
* Write a program that prints the reverse of a string
* Program to check if a string is a palindrome or not.
* Write two programs to print the following pattern using while loop and for loop
1<br>
1 2<br>
1 2 3<br>
1 2 3 4<br>
1 2 3 4 5<br>
1 2 3 4 5 6<br>