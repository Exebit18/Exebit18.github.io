---
layout : post
title : 'Python Workshop: Lecture 2'
category : ['Python Workshop',]
---

This is the summary of what was covered during Lecture 2 of the Python Workshop series.

## 1. is Operator

Evaluates to `True` if the variables on either side of the operator point to the same object and `False` otherwise. `x is y`, here `is` results in `True` if `id(x)` equals `id(y)`.

__Example:__
```python
a = 10
b = 10
if (a is b):
    print "a is equal to b"
else:
    print "a is not equal to b"
```

## 2. in Operator

Evaluates to `True` if it finds a variable in the specified sequence and `False` otherwise. `x in y`, here `in` results in a `True` if `x` is a member of sequence `y`.

__Example:__
```python
a = 10
list = [11, 30, 10, 22, 15]
if (a in list):
    print "a is in the list"
else:
    print "a is not in the list"
```

## 3. while Loop

![while loop]({{"/images/while.jpg"}})

<br>
__Example:__ Program to print odd numbers less than 10

```python
>>> i = 1
>>> while i < 10:   # execute while the statement is true
...     print i
...     i += 2      # it means i=i+2
...
1
3
5
7
9
```

## 4. for Loop

![for loop]({{"/images/for.jpg"}})

<br>__Example 1:__ 
```python
>>> arr = [ 'a', 'b', 'c', 'd', 'e' ]
>>> for i in range(len(a)):
...     print (i, arr[i])
...
0 a
1 b
2 c
3 d
4 e
```

__Example 2:__ 
```python
>>> words = [ 'Exebit', 'IITM' ]
>>> for w in words: # for each element in the list words
...     print w
...
Exebit
IITM
```

__Example 3:__ 
```python
>>> for w in words:
...     if len(w) > 5:
...         words.insert (1, ‘2018’)
...
>>> words
[ 'Exebit', '2018', 'IITM' ]
```

## 5. Loop Control Statement – ‘break’

* Terminates the current loop and resumes execution at the next statement
* The `break` statement can be used in both `while` and `for` loops.
* In case of nested loops, the `break` statement stops the execution of the innermost loop and start executing the next line of code

__Example 1:__ 
```python
>>> for i in 'kohli':
...     if i=='l':
...         break
...     print i
...
k
o
h
```

__Example 2:__
```python
>>> a = 10
>>> while a > 0:
...     print a
...     a = a-1
...     if a == 5:
...         break
...
10
9
8
7
6
```

## 6. Loop Control Statement – ‘continue’

* The `continue` statement rejects all the remaining statements in the current iteration of the loop and moves the control back to the top of the loop.
* Used in both `while` and `for` loops

__Example 1:__ 
```python
>>> for i in 'kohli':
...     if i=='l':
...         continue
...     print i
...
k
o
h
i
```

__Example 2:__ 
```python
>>> a = 10
>>> while a > 0:
...     a = a-1
...     if a == 5:
...         continue
...     print a
...
9
8
7
6
4
3
2
1
0
```

## Try it Yourself

Write a program to check if a number is prime or not using both `while` and `for` loop.

## 7. Lists

* Versatile datatype available in Python
* Ordered Collection of data
* All items in the list need not have same data type

__Example 1:__ Accessing list elements 
```python
>>> squares = [1, 4, 9, 16, 25]
>>> print squares[0]     # indexing returns the item
1
>>> print squares[-2]
16
>>> print squares[1:4]
[4,9,16]
```

Note: `list[a:b]` returns a list from `list[a]` to `list [b-1]` 

<br>
__Example 2:__ Editing a list

```python
>>> squares = [1, 4, 9, 16, 25]
>>> squares += [36, 48, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 48, 64, 81, 100]
```

<br>
__Example 3:__ Editing a list
```python
>>> squares.extend([36,48,64,81,100])
>>> squares.append(121)
[1, 4, 9, 16, 25, 36, 48, 64, 81, 100, 121]
>>> squares.remove(48)
[1, 4, 9, 16, 25, 36, 64, 81, 100,121]
```

<br>
__Example 4:__ List of strings

```python
>>> a = ["Exebit", "2018", "IIT", "Madras"]
>>> a[0]
Exebit
>>> a[2][2]
T
>>> a[3][1]
a
```

<br>
__Example 5:__ List methods
```python
>>> l = [ 1, 2, 1, 1, 0, 5, 1, 3, 5, 1 ]
>>> print l.count(1), l.count(5)
5 2
>>> l.sort()
>>> print l
[0, 1, 1, 1, 1, 1, 2, 3, 5, 5]
>>> l.reverse()
>>> print l
[5, 5, 3, 2, 1, 1, 1, 1, 1, 0]
```

## 8. List Comprehension vs Loops 

Example to create a list of squares.

1. You can use loops.
```python
>>> squares = []
>>> for i in range(10):
...     squares.append (i*i)
...
```

2. Or you can use list comprehension:
```python
>>> squares = [ i*i for i in range(10) ]
```

<br>
__Example:__

```python
>>> a = [i**3 for i in range(10)]
>>> b = [i for i in a if i%2==0]
>>> b
[0, 8, 64, 216, 512]
>>> a
[0, 1, 8, 27, 64, 125, 216, 343, 512, 729]
```

## 9. List comprehensions with more than 1 loops

__Example:__ 
```python
>>> l = [1, 2, 3]
>>> p = ['Python', 'Perl', 'java']
>>> print [(i,j) for i in l for j in p]
[(1, 'Python'), (1, 'Perl'), (1, 'java'), (2, 'Python'), (2, 'Perl'), (2, 'java'), (3, 'Python'),
(3, 'Perl'), (3, 'java')]
>>> print [(i,j) for i in l for j in p if j[0]=='P']
[(1, 'Python'), (1, 'Perl'), (2, 'Python'), (2, 'Perl'), (3, 'Python'), (3,’Perl’)]
```

## 10. Problem: Print all primes less than 100
```python
>>> primes = [h for h in range(2, 100) if h not in [j for i in range(2, 10) for j in range(i*2, 100, i)]]
>>> print primes
[2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]
```

## 11. Strings

__Example 1:__ 
```python
>>> p = 'Exe'
>>> p[2]
e
>>> p = p + 'bit'
>>> p
Exebit
>>> p[2:5] + p[0]
ebiE
```

<br>
__Example 2:__ 
```python
>>> p*5
ExebitExebitExebitExebitExebit
>>> len(p)
6
>>> string = ','.join(["Apple", "Mango", "Banana"])
>>> print string
Apple,Mango,Banana
>>> print p.upper() # try lower() function too
EXEBIT
```

<br>
__Example 3:__ 
```python
>>> import string
>>> string.atof('437.4876')
437.4876
>>> string.atoi('365')
365
>>> str = 'Exebit 2018 IIT Madras'
>>> str.split(' ')
['Exebit', '2018', 'IIT', 'Madras']
```

## Try it Yourself

1. Write a program that prints the reverse of a string
2. Program to check if a string is a palindrome or not.
3. Write two programs to print the following pattern using `while` loop and `for` loop:
```python
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
1 2 3 4 5 6
```