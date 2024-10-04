# C++ Data Types and STL Reference

## Table of Contents
1. [Data Types](#data-types)
   - [Fundamental Data Types](#fundamental-data-types)
   - [Derived Data Types](#derived-data-types)
   - [User-Defined Data Types](#user-defined-data-types)
   - [Standard Library Types](#standard-library-types)
2. [Standard Template Library (STL)](#standard-template-library-stl)
   - [Containers](#containers)
   - [Iterators](#iterators)
   - [Algorithms](#algorithms)
   - [Function Objects](#function-objects)

## Data Types

### Fundamental Data Types

1. **Integer Types:**
   - `char`: 8 bits
   - `signed char`: 8 bits
   - `unsigned char`: 8 bits
   - `short`: 16 bits
   - `unsigned short`: 16 bits
   - `int`: At least 16 bits, typically 32 bits
   - `unsigned int`: At least 16 bits, typically 32 bits
   - `long`: At least 32 bits
   - `unsigned long`: At least 32 bits
   - `long long`: At least 64 bits
   - `unsigned long long`: At least 64 bits

2. **Floating-Point Types:**
   - `float`: Single precision, typically 32 bits
   - `double`: Double precision, typically 64 bits
   - `long double`: Extended precision, typically 80 bits or more

3. **Character Types:**
   - `char`: 8 bits
   - `wchar_t`: Wide character, size is implementation-defined
   - `char16_t`: UTF-16 character, at least 16 bits
   - `char32_t`: UTF-32 character, at least 32 bits

4. **Boolean Type:**
   - `bool`: `true` or `false`

5. **Void Type:**
   - `void`: Represents the absence of type

6. **Null Pointer:**
   - `nullptr`: Represents a null pointer (C++11 and later)

7. **Fixed-Width Integer Types (C++11 and later):**
   - `int8_t`, `int16_t`, `int32_t`, `int64_t`: Signed integers
   - `uint8_t`, `uint16_t`, `uint32_t`, `uint64_t`: Unsigned integers

8. **Size-Specific Types:**
   - `size_t`: Unsigned integer type for sizes
   - `ptrdiff_t`: Signed integer type for pointer arithmetic

### Derived Data Types

1. **Arrays:**
   ```cpp
   int numbers[5] = {1, 2, 3, 4, 5};
   ```

2. **Pointers:**
   ```cpp
   int* ptr = nullptr;
   ```

3. **References:**
   ```cpp
   int& ref = someVariable;
   ```

4. **Functions:**
   ```cpp
   int add(int a, int b);
   ```

5. **Pointers to Functions:**
   ```cpp
   int (*funcPtr)(int, int);
   ```

### User-Defined Data Types

1. **Structures:**
   ```cpp
   struct Person {
       std::string name;
       int age;
   };
   ```

2. **Classes:**
   ```cpp
   class Rectangle {
   private:
       double width, height;
   public:
       double area() { return width * height; }
   };
   ```

3. **Unions:**
   ```cpp
   union Data {
       int i;
       float f;
       char str[20];
   };
   ```

4. **Enumerations:**
   - Unscoped enumeration:
     ```cpp
     enum Color { RED, GREEN, BLUE };
     ```
   - Scoped enumeration (C++11 and later):
     ```cpp
     enum class Fruit { APPLE, BANANA, ORANGE };
     ```

5. **Type Aliases:**
   ```cpp
   using Integer = int;
   typedef double Real;
   ```

### Standard Library Types

1. **String Types:**
   - `std::string`: Sequence of characters
   - `std::wstring`: Sequence of wide characters
   - `std::u16string`: Sequence of 16-bit characters (C++11)
   - `std::u32string`: Sequence of 32-bit characters (C++11)

2. **Smart Pointers (C++11):**
   - `std::unique_ptr`: Exclusive ownership
   - `std::shared_ptr`: Shared ownership
   - `std::weak_ptr`: Non-owning reference

3. **Other Utility Types:**
   - `std::pair`: Holds two values of potentially different types
   - `std::tuple`: Holds a fixed number of elements of potentially different types (C++11)
   - `std::optional`: May or may not contain a value (C++17)
   - `std::variant`: Type-safe union (C++17)
   - `std::any`: Can store any type (C++17)

4. **Thread Support Types (C++11):**
   - `std::thread`: Represents a single thread of execution
   - `std::mutex`: Provides mutual exclusion facility
   - `std::condition_variable`: Synchronization primitive for threads

5. **Time-Related Types (C++11):**
   - `std::chrono::duration`: Represents a time duration
   - `std::chrono::time_point`: Represents a point in time

## Standard Template Library (STL)

### Containers

#### 1. Sequence Containers

a. `std::vector`
```cpp
#include <vector>
std::vector<int> vec = {1, 2, 3, 4, 5};

// Common methods
vec.push_back(6);           // Add element at the end
vec.pop_back();             // Remove last element
vec.size();                 // Get size
vec.clear();                // Remove all elements
vec.front();                // Access first element
vec.back();                 // Access last element
vec.at(2);                  // Access element at index 2
vec[2];                     // Access element at index 2 (no bounds checking)
vec.empty();                // Check if empty
vec.resize(10);             // Resize vector
vec.reserve(20);            // Reserve capacity
```

b. `std::list` (Doubly Linked List)
```cpp
#include <list>
std::list<int> lst = {1, 2, 3, 4, 5};

// Common methods
lst.push_back(6);           // Add element at the end
lst.push_front(0);          // Add element at the beginning
lst.pop_back();             // Remove last element
lst.pop_front();            // Remove first element
lst.size();                 // Get size
lst.clear();                // Remove all elements
lst.front();                // Access first element
lst.back();                 // Access last element
lst.empty();                // Check if empty
lst.remove(3);              // Remove all elements with value 3
lst.unique();               // Remove consecutive duplicate elements
lst.sort();                 // Sort the list
lst.reverse();              // Reverse the list
```

c. `std::deque` (Double-ended Queue)
```cpp
#include <deque>
std::deque<int> deq = {1, 2, 3, 4, 5};

// Common methods (similar to vector, with additional front operations)
deq.push_back(6);           // Add element at the end
deq.push_front(0);          // Add element at the beginning
deq.pop_back();             // Remove last element
deq.pop_front();            // Remove first element
// ... other methods similar to vector
```

#### 2. Associative Containers

a. `std::set`
```cpp
#include <set>
std::set<int> s = {3, 1, 4, 1, 5, 9};

// Common methods
s.insert(2);                // Insert element
s.erase(1);                 // Remove element
s.find(4);                  // Find element
s.count(5);                 // Count occurrences (0 or 1 for set)
s.size();                   // Get size
s.empty();                  // Check if empty
s.clear();                  // Remove all elements
```

b. `std::map`
```cpp
#include <map>
std::map<std::string, int> m = {{"apple", 1}, {"banana", 2}};

// Common methods
m["cherry"] = 3;            // Insert or update element
m.erase("banana");          // Remove element
m.find("apple");            // Find element
m.count("cherry");          // Count occurrences (0 or 1 for map)
m.size();                   // Get size
m.empty();                  // Check if empty
m.clear();                  // Remove all elements
```

#### 3. Unordered Associative Containers

a. `std::unordered_set`
```cpp
#include <unordered_set>
std::unordered_set<int> us = {3, 1, 4, 1, 5, 9};

// Methods similar to std::set, but with constant average time complexity
```

b. `std::unordered_map`
```cpp
#include <unordered_map>
std::unordered_map<std::string, int> um = {{"apple", 1}, {"banana", 2}};

// Methods similar to std::map, but with constant average time complexity
```

#### 4. Container Adapters

a. `std::stack`
```cpp
#include <stack>
std::stack<int> stk;

stk.push(1);                // Add element
stk.pop();                  // Remove top element
stk.top();                  // Access top element
stk.size();                 // Get size
stk.empty();                // Check if empty
```

b. `std::queue`
```cpp
#include <queue>
std::queue<int> q;

q.push(1);                  // Add element
q.pop();                    // Remove front element
q.front();                  // Access front element
q.back();                   // Access back element
q.size();                   // Get size
q.empty();                  // Check if empty
```

c. `std::priority_queue`
```cpp
#include <queue>
std::priority_queue<int> pq;

pq.push(3);                 // Add element
pq.pop();                   // Remove top (highest priority) element
pq.top();                   // Access top element
pq.size();                  // Get size
pq.empty();                 // Check if empty
```

### Iterators

```cpp
std::vector<int> vec = {1, 2, 3, 4, 5};

// Using iterators
for (auto it = vec.begin(); it != vec.end(); ++it) {
    std::cout << *it << " ";
}

// Reverse iterators
for (auto rit = vec.rbegin(); rit != vec.rend(); ++rit) {
    std::cout << *rit << " ";
}

// Const iterators
for (auto cit = vec.cbegin(); cit != vec.cend(); ++cit) {
    std::cout << *cit << " ";
}
```

### Algorithms

STL provides a rich set of algorithms in the `<algorithm>` header. Here are some common ones:

```cpp
#include <algorithm>
#include <vector>

std::vector<int> vec = {3, 1, 4, 1, 5, 9, 2, 6};

// Sorting
std::sort(vec.begin(), vec.end());

// Binary search (on sorted range)
bool found = std::binary_search(vec.begin(), vec.end(), 4);

// Finding elements
auto it = std::find(vec.begin(), vec.end(), 5);

// Counting elements
int count = std::count(vec.begin(), vec.end(), 1);

// Minimum and maximum elements
auto [min, max] = std::minmax_element(vec.begin(), vec.end());

// Reversing a range
std::reverse(vec.begin(), vec.end());

// Removing elements
vec.erase(std::remove(vec.begin(), vec.end(), 1), vec.end());

// Transforming elements
std::transform(vec.begin(), vec.end(), vec.begin(), [](int n) { return n * 2; });

// Generating sequences
std::vector<int> sequence(10);
std::iota(sequence.begin(), sequence.end(), 0);  // Fills with 0, 1, 2, ..., 9

// Permutations
std::next_permutation(vec.begin(), vec.end());

// Heap operations
std::make_heap(vec.begin(), vec.end());
std::pop_heap(vec.begin(), vec.end());
```

### Function Objects

STL provides several function objects in the `<functional>` header:

```cpp
#include <functional>

// Arithmetic operations
std::plus<int> add;
int sum = add(5, 3);  // sum = 8

std::minus<int> subtract;
std::multiplies<int> multiply;
std::divides<int> divide;
std::modulus<int> modulo;
std::negate<int> negate;

// Comparison operations
std::equal_to<int> equal;
std::not_equal_to<int> not_equal;
std::greater<int> greater;
std::less<int> less;
std::greater_equal<int> greater_equal;
std::less_equal<int> less_equal;

// Logical operations
std::logical_and<bool> logical_and;
std::logical_or<bool> logical_or;
std::logical_not<bool> logical_not;

// Binding arguments
auto add_five = std::bind(std::plus<int>(), std::placeholders::_1, 5);
int result = add_five(10);  // result = 15
```

This reference guide combines the comprehensive coverage of C++ data types with the Standard Template Library (STL) components, providing a concise yet thorough overview of these essential aspects of C++ programming.
