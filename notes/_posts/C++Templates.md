---
layout: note
title: C++ Templates
---

### Generic Programming and Templates
Generic programming is a style of computer programming in which algorithms are
written in terms of types *to-be-specified-later* that are *instantiated* when needed
for specific types.

C++ offers a particularly powerful mechanism, Templates, which allow us to write
generic functions and classes that are agnostic to type.

#### Template Functions
Here is an example of a template function:

```
template <typename T>
T min (T a, T b)
{
  return a < b ? a : b;
}
```

#### Template Classes

#### Template Specialisation

#### Multi-parameter Templates
