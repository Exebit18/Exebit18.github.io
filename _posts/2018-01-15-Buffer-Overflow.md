---
layout : post
title : 'Buffer Overflow Attacks'
category : ['Systems Security',]
---

A Buffer Overflow is a very common software programming mistake. A buffer overflow  occurs when more data is put into a fixed-length buffer than the buffer can handle. Adjacent memory space becomes overwritten and corrupted. This creates an opportunity for an attacker to run arbitrary code.

This blog post will start with the basics of stack structure, and explain how buffer overflow works.

## Structure of the Stack

Let us now look at how the stack is organized when a program is executing.

<br>
<div style="text-align: center;">
<img src="/images/stack.png" alt="Stack Structure">
</div>
<br>

Consider the below program:

```c
void function(int a, int b)
{
    char buffer1[5];
    char buffer2[10];
}

void main()
{
    function(1,2);
}
```
<br>
The stack for theabove will be organized in the following way:

<br>
<div style="text-align: center;">
<img src="/images/actual_stack.png" alt="Program Stack">
</div>
<br>

## The Attack

Note that in the above program, `buffer2[10]	=	buffer1[0]`.
Similarly both `buffer2[19]` and `buffer1[9]` point to the location of the return address on the stack.

If the program does a string copy into the buffer, it does so without checking the size of string. This enables us to overflow the buffer and write into the location of the `return address`.

This can subvert execution to arbitrary code location of the attacker.

## Further References
1. [GeeksForGeeks](https://www.geeksforgeeks.org/buffer-overflow-attack-with-example/)
2. [Wikipedia](https://en.wikipedia.org/wiki/Buffer_overflow)
