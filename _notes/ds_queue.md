---
layout: note
title: Queue
---

A queue is a linear data structure which follows a particular order in which operations are performed. The order is __First In First Out__ (FIFO) and is conceptually similar to a queue of people - whoever joined the queue earliest gets served first, and whoever is at the end of the queue has to wait. The difference between stacks and queues is in removing; in a stack, we remove the item most recently added, whereas in a queue we remove the item least recently added.

![test]({{ site.baseurl }}/images/queue.png)

At its simplest, a queue has two operations:
- enqueue (add an item to the tail)
- dequeue (take an item from the head).

Additionally, we can add the following operations:
- peek()
- isEmpty()
- isFull()
- size()