---
layout: note
title: Linked List
---
A linked list is a linear collection of data elements whose order isn't given by their physical placement in memory; instead, each element **points** to the next. The benefit of this is that linked lists can store a (hypothetically) indefinite amount of data - as long as your computer has enough memory. This differs from arrays because arrays use contiguous storage. It is a data structure consisting of a collection of nodes which together represents a sequence. In its most basic form, each node contains just two things: **data** and a **reference**.

# Variations
## Singly-linked list
In a singly-linked list each node stores some data and a pointer to the next node.
In its simplest form, it can be implemented as follows:
```cpp
struct Node {
    int data;
    Node* next;
    Node (int data) {
        this -> data = data;
        this -> next = NULL;
    }
};

class SinglyLinkedList {
private:
    Node *head, *tail;
public:
    SinglyLinkedList () { // construct an empty list
        head = NULL;
        tail = NULL;
    }
   
    void add (int x) {  // this should add an item to the end of the linked list
        Node *n = new Node(x);
        if (head == NULL) {
            head = n;
            tail = n;
        }
        else {
            Node *n = new Node(x);
            tail->next = n;
            tail = n;
        }
    }  
};
```
We can additionally add some useful functions to the SinglyLinkedList class to make it better.
#### Display
```cpp
void displayNodes () {
    Node *node_ptr = head;
    while (node_ptr != NULL) {
        cout << node_ptr->data << " --> ";
        node_ptr = node_ptr->next;
    }
}
```
#### Insert at beginning
```cpp
void insertAtBeginning(int newNodeVal) {
    Node *newNode = new Node(newNodeVal);
    newNode->next = head;
    head = newNode;
}
```
#### Insert at position
```cpp
void insertAtPosition(int pos, int newNodeVal) {
    Node *newNode = new Node(newNodeVal);
    Node *prevNodePointer = head;
    for (int i = 1; i < pos - 1; i++) {
        prevNodePointer = prevNodePointer->next;
    }
    newNode->next = prevNodePointer->next;
    prevNodePointer->next = newNode;
}
```
#### Delete at beginning 
```cpp
void deleteAtBeginning() {
    Node *tmp = head;
    head = head->next;
    delete tmp;
}
```
#### Delete at position
```cpp
void removePosition(int pos) {
    Node *prevNodePointer = head;
    for (int i = 1; i < pos - 1; i++) {
        prevNodePointer = prevNodePointer->next;
    }
    prevNodePointer->next = prevNodePointer->next->next;
}
```
## Doubly-linked list 
In a doubly-linked list each node contains some data, and points to the next and previous nodes. The implementation of a doubly-linked list is similar to that of a singly-linked list, except the ```Node``` struct also contains a pointer to the previous node:
```cpp
struct Node {
    int data;
    Node *next, *prev;
    Node (int x) {
        this->data = x;
        next = NULL;
        prev = NULL;
    }
};
```
The insertion/deletion operations now need to account for the ```prev``` pointer to allow for backwards-traversal. For example, to add an item to the end:
```cpp
void add(int x) {
    Node *newNode = new Node(x);
    if (head == NULL) {
        head = newNode;
        tail = newNode;
    }
    else {
        newNode->prev = tail;
        tail->next = newNode;
        tail = newNode;
    }
}
```


## Applications