---
layout: note
title: Stack
---

In computer science, a stack is an abstract data type which serves as a collection of elements. It serves two principal operations:
- push, which adds an element to the collection
- pop, which removes an element from the collection

The order in which elements come off a stack give rise to an alternative name: __last in, first out__ (LIFO). There may additionally be some added operations:
- peek, which gives access to the top of the stack without modifying it
- isEmpty, returns true if the stack is empty, else false

Consider a stack to be like a stack of plates - the last plate you place on the pile (at the top), has to be the first one you remove - else the pile of plates may come tumbling down.


#### Implementations
There are two ways a stack can be implemented, by using one of the following underlying data structures:
- Array
- Linked List

##### Array Implementation
```c
#include <stdio.h> // C standard library files included with angle brackets
#include <string.h>
#define STACK_SIZE 100

void push ( int x );
void pop ();
void peek();
void print_stack();

int stack[STACK_SIZE];
int choice, x, top = -1;

int main () {
    do 
    {
        printf("Enter a choice: 0 = push, 1 = pop, 2 = peek, 3 = print, 4 = quit\n");
        scanf("%d", &choice);
        switch (choice) {
            case 0: 
                printf("Enter a value to push: ");
                scanf("%d", &x); 
                push(x);
                break;
            case 1: 
                pop();
                break;
            case 2:
                peek();
                break;
            case 3:
                print_stack();
                break;
            default: 
                printf("Please enter a valid option\n");
                break;
        }
    }
    while (choice != 4);
}

void push ( int x ) {
    if (top + 1 == STACK_SIZE)
        printf("Cannot push - stack full.\n");
    else {
        top++;
        stack[top] = x;
    }
}

void pop () {
    if (top < 0) 
        printf("Cannot pop - stack empty.\n");
    else {
        printf("Popping %d\n", stack[top]);
        top--;
    }
}

void peek () {
    printf("Top of stack: %d\n", stack[top]);
}

void print_stack() {
    printf("Printing the stack: \n\n");
    for (int i = top; i >= 0; i--) 
        printf("| %d |\n-----\n", stack[i]);
}
```


#### Applications
