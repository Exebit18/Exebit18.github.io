---
layout : post
title : 'Buffer Overflow Attacks'
category : ['Systems Security',]
---

A Buffer Overflow is a very common software programming mistake. A buffer overflow  occurs when more data is put into a fixed-length buffer than the buffer can handle. Adjacent memory space becomes overwritten and corrupted. This creates an opportunity for an attacker to run arbitrary code.

This blog post will start with the basics of stack structure and Array Accesses, and explain how buffer overflow works.

## Accessing data in an Array

Arrays in C are usually declared in the following format
<br>`<type> <variable_name>[<size>]`<br>
For example, char name[50] or float fltArray[9].

Suppose we have defined an array as `char name[10] = "exebit"` ,
Then we can access individual characters in the array by using its position. name[0] gives us 'e' while name[4] gives us 'i'.

Have you ever though what happens if we access an array beyond it's bounds?

## Structure of the Stack

Let us now look at how the stack is organized when a program is executing.

![Stack Structure]({{"/images/stack.png"}})
<br>

Consider the below program:

```c
void function(int a,int b)
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

![Program Stack]({{"/images/actual_stack.png"}})
<br>

## The Attack

We can see that in the above program, `buffer2[10]	=	buffer1[0]`.
Similarly both `buffer2[19]` and `buffer1[9]` point to the location of the return address on the stack.

If the program does a string copy into the buffer, it does so without checking the size of string. This enables us to overflow the buffer and write into the location of the `return address`.

This can subvert execution to arbitrary code location of the attacker.

## Cracking the password

Let us now use a Buffer Overflow attack to bypass a simple password checking function.

The vulnerable code:(Compile using gcc -fn-stack-protector <filename> and Execute using ./a.out)

```c
#include <stdio.h>
#include <string.h>

int check_password(char* entered_password,char* actual_password)
{

    char* new_pass = (char*)malloc(10*sizeof(char));
    strncpy(new_pass, entered_password,7);
    printf("%s %s\n",new_pass,actual_password);
    if(strcmp(new_pass,actual_password)==0)
        return 1;
    else
        return 0;
}

void main()
{
    printf("Enter password:\n");
    char password[8] = "awesome";
    char buf[8];
    gets(buf);
    if(check_password(buf,password)==1)
        printf("Great work\n");
    else
        printf("Sorry,try again\n");
    return;
}
```
The program should print "Great work" only if we input "awesome". But this is not the case. Any input in the format `<7 letter string>XXXXXXXXX<same string as previous>` will print "Great work".

This is because `gets` doesnot perform a check on the input size. This leads to password variable also getting overwritten with a sufficiently long string. Carefully designing the input string will lead to first 7 characters of `buf` being same as `password`.


## Further References
1. [GeeksForGeeks](https://www.geeksforgeeks.org/buffer-overflow-attack-with-example/)
2. [Wikipedia](https://en.wikipedia.org/wiki/Buffer_overflow)
