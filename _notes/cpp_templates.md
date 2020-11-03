---
layout: note
title: Templates
---

### Generic Programming and Templates
Generic programming is a style of computer programming in which algorithms are written in terms of types *to-be-specified-later* that are *instantiated* when needed for specific types.

C++ offers a particularly powerful mechanism, templates, which allow us to write generic functions and classes. The simple idea is to pass the data type as a parameter so that we don't need to write the same code for different data types.

For example, we may need ement a ```sort()``` function for a range of data types. Rather than writing and maintaing multiple implementations, we can write one ```sort()``` function and pass the data type.

#### How it works
Templates are expanded at compiler time, similar to macros. The compiler does type-checking before template expansion, and then generates a compiled version of the function for each type that the template function is instantiated with. So whilst there is a single copy of the template function in the source code, the compiled code will have many versions.

#### Function Templates
Here is an example of a basic template function, which calculates the minimum of two different objects (e.g. ```int, double, float, ...```):

```c++
template <typename T>
T min (T a, T b)
{
  return a < b ? a : b;
}
```
To call this function, we use ```<...>``` notation:
```c++
cout << min<int>(3, 7) << endl;
cout << min<char>('a', 'g') << endl;
```
Bear in mind that the above function only works for data types which support the ```<``` operator. This can include user defined types (i.e. classes, structs) as long as the ```<``` has been appropriately overloaded.

#### Class Templates
Similarly to function templates, we can use class templates when a class defines something which is independent of the data type. This is particularly useful for classes such as Array, LinkedList, Queue, Stack, etc.
```c++
template <typename T>
class Array {
private:
  T *ptr;
  int size;
public:
  Array(T arr[], int s) {
    ptr = new T[s];
    size = s;
    for (int i = 0; i < size; i++)
      ptr[i] = arr[i];
  }
  void print() {
    // some code here
  }
};
```
#### Template Specialisation
It is possible to create a special behaviour of a template for a particular data type. This is useful in situations where a certain data type needs to be treated differently to most other data types.
```c++
template <class T>
void sort(T arr[], int size) {
  // code to implement sort for array of type T
}

template <>
void sort<char>(char arr[], int size) {
  // code to implement sort for chars only
}
```
In the second block above, we have used template specialisation to implement the template function for arrays of ```char```s.
#### Multi-parameter Templates
Like with normal parameters, it is possible to pass more than one data type as an argumnet to a template. The following example demonstrates this:
```c++
template<class T, class U>
class A {
  T x;
  U y;
public:
  A() { cout << "Constructor called" << endl; }
};

int main () {
  A<char, char> a;
  A<int, double> b;
}
```

#### Default values
Like normal parameters, we can specify default arguments to templates. The following demonstrates this:
```c++
template<class T, class U = char>
class A {
public:
  T x; 
  U y;
  A() { cout << "Constructor called" << endl; }
};

int main () {
  A<char> a; // This calls A<char, char>
  return 0;
}
```


#### Non-type parameters


#### Difference to function overloading

