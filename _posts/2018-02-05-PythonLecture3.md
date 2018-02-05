---
layout : post
title : 'Python Workshop: Lecture 3'
category : ['Python Workshop',]
---

Here's what transpired in the lecture 3 of Python Workshop Series.

<br>
## 1. Dictionaries

* A list supports indexing using integers. Ex: arr[0], arr[1] etc.
* A dictionary maps keys to values.
* A dictionary supports indexing using any immutable type.
* Since the keys can be of any type, there is no concept of order among the elements of a dictionary

Here's an example:

```python
>>> mydict = {}
>>> mydict[‘abc’] = 123
>>> mydict[5] = 24
>>> mydict[(1,2)] = 78
>>> mydict
{(1, 2): 78, ‘abc’: 123, 5: 24}
>>> mydict[(1,2)]
78
>>> z = 5
>>> mydict[z]
24
>>> mydict[‘hello’] = [5,6,7,8]
>>> mydict
{(1, 2): 78, ‘abc’: 123, 5: 24, ‘hello’:[5,6,7,8]}
```

## 1.1 Dictionary operands and methods

```python
>>> mydict.keys() # Gives a list of the keys in the dictionary             
[(1, 2), ‘abc’, 5, ‘hello’]   
>>> mydict.values() # Gives a list of the values in the dictionary
[78, 123, 24, [5,6,7,8]] 
>>> del mydict[5]
>>> mydict
{(1, 2): 78, ‘abc’: 123, ‘hello’:[5,6,7,8]}
>>> mydict.has_key(1)
False
>>> mydict.update({1:2})
{(1, 2): 78, ‘abc’: 123, ‘hello’:[5,6,7,8], 1: 2}
```

<br>
## 2. Files

The commonly used functions in file handling are:

* `open(filename,mode)` : Gives a pointer to the beginning of the file to be used for reading and writing.
* `read()` : to read the whole file as a string
* `readline()` and `readlines()` : to read each line from the file separately
* `write(data)` : writes to file (the file must be opened in a mode that supports writing)
* `close()` : to close the file pointer. The file pointer can no longer be used to access the file.

Here's an example:

```python
fp = open("file.txt","r")
print fp.read()
fp.close()

fp = open("file.txt","r")
lines = fp.readlines()
print lines
fp.close()

fp = open("file.txt","r+")
line = fp.readline()
print line
fp.close()

fp = open("file1.txt","w")
fp.write("New file")
fp.close()

fp = open("file.txt","r")
for line in fp:
   print line.strip()
```

<br>
## 3. Functions

Functions are used for the following reasons:
* **Reusability:** Once a function is defined, it can be used over and over again.
* **Abstraction:** Once the arguments and the behaviour of a function is defined, it can be used without knowing how it works inside.
* Inputs to the function are taken as arguments.
* Output of the function is returned to the caller.
* Since typing is not strict in Python, argument types and return types do not need to be specified. If wrong types are passed/returned, an error will be thrown if it is used wrongly.

Here's an example:

```python
def isprime(n):
   for i in range(2,n/2+1):
      if n%i==0:
         return False
   return True
   
   
n = input("Enter a number: ")
if isprime(n):
   print "The number is prime"
else:
   print "The number is not prime"
```

Here's an example of an **erroneous** function call:

```python
def func(a,b):
   if a == 5:
      print "Hello"
   if b[0] == 6:
      print "Hi"
   
   
func(5,6)
```

<br>
## 4. NumPy and Matplotlib Libraries

* NumPy Provides functions to perform operations on arrays and matrices.
* A quickstart tutorial for NumPy can be found [here](https://docs.scipy.org/doc/numpy-dev/user/quickstart.html)
* Pyplot within Matplotlib can be used to draw plots in Python.
* A tutorial for Matplotlib’s Pytplot can be found [here](https://matplotlib.org/tutorials/introductory/pyplot.html)

<br>
## 5. Do It Yourself

1. Write a program to produce a dictionary B from a list A that initially has
   N strings. The strings in the list A should be the keys of B and the
   corresponding lengths of the strings are the corresponding values.
   <br>
   **Example:**
   `A = [‘hello’, ‘how’, ‘are’]`
   <br>
   **Output:** `{‘hello’: 5, ‘how’: 3, ‘are’: 3}`

2. Do the previous exercise assuming that the strings are stored
   in a file with each string on one line.

3. Write a function that takes an integer as argument and returns a list of all
   the Fibonacci numbers (starting from 1) less than the given integer.
   <br>
   **Example:**
   `n = 10`
   <br>
   **Output:** `[1, 1, 2, 3, 5, 8]`

<br>
