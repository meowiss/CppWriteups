# Vectors and Standard Template Library

---


## What is Standard Template Library ?

The `Standard Template Library (STL)` is a set of C++ template classes to provide common programming data structures and functions such as lists, stacks, arrays, etc. It is a library of container classes, algorithms, and iterators. C++ vector is a template class in the Standard Template Library (STL) that functions as a more refined array. Unlike arrays, vectors can resize themselves automatically when you insert or delete elements.

### Standard Template Library (STL) Components


| Components | Description                                                                                                                                                                                                                                                                                                                                   |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Containers | Containers are used to manage collections of objects of a certain kind. There are in total seven standard “first-class” container classes and three container adaptor classes and only seven header files that provide access to these  container adaptors. There are several different types of containers like deque, list, vector, map etc |
| Algorithms | It defines a collection of functions specially designed to be used on ranges of elements. They provide the means by which you will perform initialization, sorting, searching, and transforming of the contents of containers. Examples are sorting, searching, etc.                                                                          |
| Iterators  | It is used for working upon a sequence of values.It provides generiality in STL.                                                                                                                                                                                                                                                              |
| Function   | STL includes classes which overload the function call operator. Instances of such classes are called functors. Functors allow the working of the associated function to be customized with the help of parameters to be passed.     |


![](https://i.imgur.com/tk4oWMl.png)


## What is a vector ?
`vectors` (AKA `std::vector`) are sequence containers that represent arrays that can change in size. They’re used to work with dynamic data, and they use contiguous storage locations for their elements. They use adjacent storage locations for their elements just as efficiently as in arrays, which means that their elements can also be accessed using offsets on regular pointers to its elements. In `vectors`, data is inserted at the end. Inserting at the end takes differential time, as sometimes the array may need to be extended. Removing the last element takes only constant time because no resizing happens. Inserting and erasing at the beginning or in the middle is linear in time , sounds like similar to queue :), Vector containers may allocate additional storage space to accommodate for potential growth, so the container may have a larger capacity than what’s actually being stored inside of it. You can use libraries to apply different growth strategies to strike a balance between reallocations and memory usage, but reallocations should only happen lo(g) growing intervals of size. This allows you to use amortized constant time complexity when inserting individual elements at the end of the vector.


## How are vectors actually stored ?

For each time you create a variable in C++, the compiler will work out how to allocate memory in your computer and produce the corresponding machine code to do so. For example, when creating an int, the corresponding machine code will “ask” the computer to reserve a few bytes in RAM to store your integer. Not surprisingly, this same “memory allocation” pattern is used for vectors.

Under the hood, an `vector<T>` just shows us to reference to the starting place in memory where the first value is and where the last value of the vector. All the elements in a vector are stored contiguously / adjacently, meaning that the bytes used to represent the next element is stored directly after the previous one as adjacently (just like train cars, one placed after one another). 

![](https://i.imgur.com/QtGVPRi.png)



On the left is the data stored for a vector (the start and end positions of the memory). On the right is an example of the contents of computer memory, with the vector data in there.


```cpp
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main()
{
    std::vector<int> days = {
      1,  // Monday 
      2,  // Tuesday
      3,  // Wednesday
      4,  // Thursday
      5,  // Friday
      6,  // Saturday
      7,  // Sunday
    };

    for (int i = 1; i <= 5; i++) // printing out the days in a week
        cout << to_string(days[i]);
}
```


## Vector Functions

In C++, a vector is a dynamic list of items, that can shrink and grow in size. It can only store values of the same type. To use vectors, it is necessary to `#include<vector>` the vector library. Let’s take a look at some of the functions and what they do, but first, let's have a look how to initialize or create a vector.

```cpp
vector<int> vector1 = {1, 2, 3, 4, 5};
```


### Indexing

An index refers to an element’s position within an ordered list, like a vector or an array. The first element has an index of 0. A specific element in a vector or an array can be accessed using its index, like `name[index]`.

```cpp
std::vector<double> order = {3.99, 12.99, 2.49};

// What's the first element?
std::cout << order[0];

// What's the last element?
std::cout << order[2];
```

### push_back()


* To add a single element into a vector, we use the `push_back(`) function. It inserts an element into the end of the vector. All the elements that need to be stored in the vector are pushed back one-by-one in the vector using the `push_back()` method. 

* `.push_back()` to add an element to the “end” of a vector

`vector_name.push_back(element_value);`


```cpp
std::vector<std::string> employees;

employees.push_back("michael");
employees.push_back("jim");
employees.push_back("pam");
employees.push_back("dwight");
```
The code above, `push_back` adds elements to the `vector emoplyees`.

### .pop_back()

* To delete a single element from a vector by using the`pop_back()` function.

* `pop_back()` to remove an element from the “end” of a vector

```cpp
std::vector<std::string> wishlist;

wishlist.push_back("Oculus");
wishlist.push_back("Telecaster");

wishlist.pop_back();

std::cout << wishlist.size(); 
```


**output**
```
1
```

## .size()

The `.size()` function can be used to return the number of elements in a vector, like `name.size()`.

```cpp
std::vector<std::string> employees;

employees.push_back("michael");
employees.push_back("jim");
employees.push_back("pam");
employees.push_back("dwight");

std::cout << employees.size();
```

**output**
```
4
```



here are some other functions that can be used by vectors

- `begin()`  returns an iterator pointing to the first element in the vector.
- `end()`  returns an iterator pointing to the last element in the vector.
- `rbegin()` returns a reverse iterator pointing to the last element in the vector.
- `rend()`  returns a reverse iterator pointing to the element preceding the first element in the vector. Basically considered as a reverse end.
- `cbegin()` returns a constant iterator pointing to the first element in the vector.
- `cend()`  returns a constant iterator pointing to the element that follows the last element in the vector.
- `crbegin()` returns a constant reverse iterator pointing to the last element in the vector.
- `crend()` returns a constant reverse iterator pointing to the element preceding the first element in the vector.
- `max_size()`  returns the maximum number of elements that a vector can hold.
- `capacity()`  returns the storage capacity currently allocated to the vector.
- `resize(n)`  resizes the container to store ‘n’ elements.
- `empty()` returns whether the container is empty or not (boolean).


sample code using functions;

```cpp
#include <iostream>
#include <vector> 
using namespace std; 
int main() 
{ 
   //Declaring vector ‘a’ of integer type 
   vector<int> a; 
   
   //Initializing vector ‘a’ with values from 1 to 5
    for (int i = 1; i <= 5; i++) 
        a.push_back(i); 
  
    //Printing size of the vector ‘a’
    cout << "Size : " << a.size(); 
   
    //Printing the Capacity of the vector ‘a’
    cout << "\nCapacity : " << a.capacity(); 
    
    //Printing the maximum size of the vector ‘a’
    cout << "\nMax_Size : " << a.max_size(); 
  
    // resizing  the vector ‘a’ to  size  4 
    a.resize(4); 
  
    // printing the vector ‘a’ size after resize() function
    cout << "\nSize : " << a.size(); 
  
    // checks if the vector is empty or not 
    if (a.empty() == false) 
        cout << "\nVector is not empty"; 
    else
        cout << "\nVector is empty"; 
  
  
    return 0; 
} 
```

**output**

```
Size : 5
Capacity : 6
Max_Size : 4611686018427387903
Size : 4
Vector is not empty
```
