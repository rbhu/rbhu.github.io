---
layout: note
title: Pointers
---
Pointers are a fundamental part of C, and are one of the features which gices C the power and flexibility it is known for. There are various reasons pointers are used:
- it is the only way to express some computations (e.g. )
- it provides compact and efficient code
- it provides a very powerful tool

Additionally, C uses pointers explicitly with arrays, structures and functions.

#### What is a pointer?
A pointer is a variable which contains the address in memory of another variable. We can have a pointer to any variable type.

To get the address of a variable, we use the ```&``` operator. To declare a pointer to a variable, we do the following:
```c
<data_type> *pointer;
```
To make some more sense of this, lets look at a concrete example.
