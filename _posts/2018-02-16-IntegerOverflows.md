---
layout : post
title : 'Integer Overflows'
category : ['System Security',]
---

A basic familiarity with C along with the binary and hexadecimal representation of numbers is assumed.  A knowledge of how integers are stored in memory is also useful, but not essential.

**What is an integer?**

An integer, in the context of computing, is a variable capable of representing a real number with no fractional part. When humans talk about integers, we usually represent them in decimal, as that is the numbering system humans are most used to.  Computers, being digital, cannot
deal with decimal, so internally to the computer integers are stored in binary.  Binary is another system of representing numbers which uses only two numerals, 1 and 0, as opposed to the ten numerals used in decimal.  As well as binary and decimal, hexadecimal (base sixteen) is often used in computing as it is very easy to convert between binary and hexadecimal.

There are two types of integers
1. Signed - The representation determines if a number is negative or not by testing if the Most Significant Bit(MSB) is 1. If the MSB is 1, it is negative, otherwise it is positive.
2. Unsigned - All the numbers are positive irrespective of the value of the MSB.

Since a memory location that stores an integer is of fixed size, there is a fixed maximum value it can store.  When an attempt is made to store a value greater than this maximum value it is known as an integer overflow. We will assume that the fixed size of the memory location is 32 bits.

**Why can they be dangerous?**

Integer overflows cannot be detected after they have happened, so there is not way for an application to tell if a result it has calculated previously is in fact correct.  This can get dangerous if the calculation has to do with the size of a buffer or how far into an array to index.  Of course
most integer overflows are not exploitable because memory is not being directly overwritten, but sometimes they can lead to other classes of bugs, frequently buffer overflows.  As well as this, integer overflows can be difficult to spot, so even well audited code can spring surprises.

When an integer overflow occurs, the result should ideally use more bits for storage. However, the additional bits are ignored, hence giving a result that is reduced modulo the number that is one greater than the largest value that can be represented by the resulting type.

**Example:**

We have two unsigned integers, a and b, both of which are 32 bits long.  We assign to a the maximum value a 32 bit integer can hold, and to b we assign 1.  We add a and b together and store the result in a third unsigned 32 bit integer called r:
```
a = 0xffffffff
b = 0x1
r = a + b
```

Now, since the result of the addition cannot be represented using 32 bits, the result, in accordance with the ISO standard, is reduced modulo 0x100000000.
```
r = (0xffffffff + 0x1) % 0x100000000
r = (0x100000000) % 0x100000000 = 0
```

Reducing the result using modulo arithmetic basically ensures that only the lowest 32 bits of the result are used, so integer overflows cause the result to be truncated to a size that can be represented by the variable. This is often called a "wrap around", as the result appears to wrap around to 0.

**Widthness overflows**

An integer overflow is the result of attempting to store a value in a variable which is too small to hold it.  The simplest example of this can be demonstrated by simply assigning the contents of large variable to a smaller one:

```
<CODE BEGIN>
      #include <stdio.h>

    int main(void){
            int l;
            short s;
            char c;

            l = 0xdeadbeef;
            s = l;
            c = l;

            printf("l = 0x%x (%d bits)\n", l, sizeof(l) * 8);
            printf("s = 0x%x (%d bits)\n", s, sizeof(s) * 8);
            printf("c = 0x%x (%d bits)\n", c, sizeof(c) * 8);

            return 0;
    }
   <CODE END>
```
The output of which looks like this:
```
l = 0xdeadbeef (32 bits)
s = 0xffffbeef (16 bits)
c = 0xffffffef (8 bits)
```

Since each assignment causes the bounds of the values that can be stored in each type to be exceeded, the value is truncated so that it can fit in the variable it is assigned to.

**Arithmetic overflows**

As shown in the previous section, if an attempt is made to store a value in an integer which is greater than the maximum value the integer can hold, the value will be truncated.  If the stored value is the result of an arithmetic operation, any part of the program which later uses the result
will run incorrectly as the result of the arithmetic being incorrect.
Consider this example demonstrating the wrap around shown earlier:

```
<CODE BEGIN>
    #include <stdio.h>

    int main(void){
            unsigned int num = 0xffffffff;

            printf("num is %d bits long\n", sizeof(num) * 8);
            printf("num = 0x%x\n", num);
            printf("num + 1 = 0x%x\n", num + 1);

            return 0;
    }
<CODE END>
```
The output of this program looks like this:
```
num is 32 bits long
num = 0xffffffff
num + 1 = 0x0
```

Since an integer is signed by default, an integer overflow can cause a change in signedness which can often have interesting effects on subsequent code.  Consider the following example:
```
<CODE BEGIN>
      #include <stdio.h>

    int main(void){
            int l;

            l = 0x7fffffff;

            printf("l = %d (0x%x)\n", l, l);
            printf("l + 1 = %d (0x%x)\n", l + 1 , l + 1);

            return 0;
    }
 <CODE END>
```
The output of which is:
```
l = 2147483647 (0x7fffffff)
l + 1 = -2147483648 (0x80000000)
```

Here the integer is initialised with the highest positive value a signed long integer can hold.  When it is incremented, the most significant bit(indicating signedness) is set and the integer is interpreted as being negative.

**Exploiting**

One of the most common ways arithmetic overflows can be exploited is when a calculation is made about how large a buffer must be allocated.  Often a program must allocate space for an array of objects, so it uses the malloc() or calloc() routines to reserve the space and calculates how much space is needed by multiplying the number of elements by the size of an object.  If we are able to control either of these operands (number of elements or object size) we may be able to mis-size the buffer, as the following code fragment shows:

```
<CODE BEGIN>
    int myfunction(int *array, int len){
        int *myarray, i;

        myarray = malloc(len * sizeof(int));    /* [1] */
        if(myarray == NULL){
            return -1;
        }

        for(i = 0; i < len; i++){              /* [2] */
            myarray[i] = array[i];
        }

        return myarray;
    }
<CODE END>
```

This seemingly innocent function could bring about the downfall of a system due to its lack of checking of the len parameter.  The multiplication at [1] can be made to overflow by supplying a high enough value for len, so we can force the buffer to be any length we choose.  By choosing a suitable value for len, we can cause the loop at [2] to write past the end of the myarray buffer, resulting in a heap overflow.  This could be leveraged into executing arbitrary code on certain implementations by overwriting malloc control structures.
To illustrate with an example, suppose the value of ‘len’ is passed as 0x40000001 and suppose sizeof(int) is 4. Then the value of len*sizeof(int) after overflow will be 4.(You can work this out. Note that the value of len is specified in hexadecimal) So, in the loop at [2], we would be writing a lot more values than the memory allocated for the array. We are effectively writing at memory locations which we haven’t allocated. This can be a security issue, since we would be overwriting data to which we actually do not have access to.

**References:**
This post is a summary of the post at [http://phrack.org/issues/60/10.html](http://phrack.org/issues/60/10.html) 












