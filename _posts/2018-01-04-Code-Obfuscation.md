---
layout : post
title : 'Code Obfuscation'
category : ['Obfuscation',]
---

This blogpost introduces code obfuscation with an example.

## What?

Obfuscation? Uhhh!! Difficult to pronounce?

This is how its pronounced /ɒbfʌsˈkeɪʃ(ə)n/ HaHaHa I know how you’re feeling now! Ok let’s try once more pronounce it as Ob-fas-kay-sion. Hope you did well this time!

Code obfuscation is a method of hiding the intension of the program/code by indirect codes, unusual symbols, confusing names and comments. At first glance it looks like some gibberish program and obviously you think the program will not compile or it won’t run properly, but when you compile and try to run it, gives the desired output. Advantage of Obfuscation is that you can hide your code for trade secrecy. It will be too difficult for others to read and understand the source code. But with great feature comes in great flaw, you will be unable to read your own code after sometime if you forget what you had written. Antivirus software can detect your program as malware because one of the purposes of obfuscation is to hide malicious code.

## Techniques of Obfuscation

Obfuscation actually depends on your creativity and grip over that particular language in which the program is developed. To consider common practice of obfuscation five important steps has to be followed.

1. Changing the variable names to irrelevant things.
Ex: int sum, var1, var2 as int a,b,c
2. Change function names as well!
Ex: void adder(), void multiplier() to void jiiingalala(), void jiingalala()
3. Use indirect method of representation of string, int and float.
4. Use unnecessary loops and decision conditions.
5. Remove unnecessary space and indentation.

## Tutorial

Before we get our hands on reverse engineering the obfuscated code it’s essential to understand the obfuscation of the original code.

Consider a simple program of adding two numbers.

#### Original code:

```c
#include <stdio.h>

void adder(int var1, int var2){
    int sum = var1 + var2;
    printf(“%d”, sum);
}

void main(){
    adder(8, 17);
}
```
<br>

Let’s obfuscate the above code with the simple important steps from above.
<br><br>
#### Step 1: Change variable names.
```c
#include <stdio.h>

void adder(int divider, int dividend){
    int quotient = divider + dividend;
    printf(“%d”, quotient);
}

void main(){
    adder(8, 17);
}
```
<br>

#### Step 2: Change function name

```c
#include <stdio.h>

void divide(int divider, int dividend){
    int quotient = divider + dividend;
    printf(“%d”, quotient);
}

void main(){
    divide(8, 17);
}
```
<br>

#### Step 3: Represent 8 and 17 in other format.

```c
#include <stdio.h>

void divide(int divider, int dividend){
    int quotient = divider + dividend;
    printf(“%d”, quotient);
}

void main(){
    divide(010, 021);
}
```
<br>

#### Step 4: Add irrelevant contents.
```c  
#include <stdio.h>

void divide(int divider, int dividend){
    int quotient = 000;
    divider ? (quotient += divider + dividend) : (quotient = divider + dividend);
    printf(“%d”, divider + dividend);
}

void main(){
    divide(010, 021);
}
```
<br>

#### Step 5: Now remove indentation and white spaces.
```c
#include<stdio.h>divide(intdivider,intdividend)
{intquotient=000;divider?(quotient+=divider+dividend):(quotient=
divider+dividend);printf(“%d”,divider+dividend);}main(){divide(010,021);}
```
<br>

#### Obfuscated code:
```c
#include<stdio.h>divide(intdivider,intdividend)
{intquotient=000;divider?(quotient+=divider+dividend):(quotient=
divider+dividend);printf(“%d”,divider+dividend);}main(){divide(010,021);}
```

So now you’re good to go, reverse everything you have done in each step, starting from step 5 (preferably).

Remember what we have explained here is just an example to make it easy. Real obfuscation will be far away from this example, from representation of the data to the exploiting the features of the native language, one can create the obfuscated code which might cost you years together to decipher. I recommend you to go through the goExpert example given below to feel the depth of the obfuscation.

## Further reading:

1. [Wikipedia](https://en.wikipedia.org/wiki/Obfuscation_(software))
2. [goExpert example](https://www.go4expert.com/articles/create-obfuscated-code-c-t27261/)
