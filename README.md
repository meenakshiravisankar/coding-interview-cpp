# Introduction

This repository contains a collection of resources helpful for coding interviews which involve competitive programming. The content is currently supported in C++ only. Since vast amount of material is already present online, links to the same are given below. However, there is no concise and easy to understand documentation of STL available currently. You will find detailed STL syntax with examples in this repo.

# Contents
1. [Basic Programming](#basic-programming)
2. [Time Complexity](#time-complexity)
3. [Standard Template Library](#standard-template-library)
4. [Data Structures](#data-structures)
5. [Algorithms](#algorithms-1)
6. [Math and Miscellaneous](#math-and-miscellaneous)
7. [Practice](#practice)
8. [Acknowledgements](#acknowledgements)


# Basic Programming
[Tutorial](https://www.tutorialspoint.com/cplusplus/index.htm) - Basic programming introduces the language syntax and related concepts.

# Time Complexity
[Tutorial](https://www.interviewbit.com/courses/programming/topics/time-complexity/) - Understanding computational complexity of your code is important. This is especially significant when choosing an efficient method if there are multiple ways to solve a particular problem.

# Standard Template Library
[Tutorial](#stl-contents) - STL is the standard template library which contains C++ template classes. STL is a powerful tool and it reduces programming time with rich implementations of freuently used data structures and algorithms. Important parts of the STL are as follows:

1. Containers - includes container classes to store and manipulate data elements.
2. Algorithms - includes important techniques like sorting, searching.
3. Miscellaneous - includes string class and other functions.
    
> Learn STL, save your life

Usage of several STL classes are illustrated. For convenience and ease of learning, examples are also provided along with syntax.

## STL Contents
  - [Containers](#containers)
    - [Vector](#vector)
    - [Deque](#deque)
    - [List](#list)
    - [Stack](#stack)
    - [Queue](#queue)
    - [Priority Queue](#priority-queue)
    - [Set](#set)
    - [Multiset](#multiset)
    - [Map](#map)
    - [Multimap](#multimap)
    - [Unordered Set](#unordered-set)
    - [Unordered MultiSet](#unordered-multiset)
    - [Unordered Map](#unordered-map)
    - [Unordered Multimap](#unordered-multimap)
  - [Algorithms](#algorithms)
  - [Miscellaneous](#miscellaneous)

  
## Containers
Following are the important containers provided with example use cases. Some methods support multiple ways of accepting arguments which are also presented. Templates accept both primitive and user-defined data types. For simiplicity, integer data type is used in the below examples.

### Vector
A vector is similar to an array but with dynamic size where elements can be added from one end. 

**Design:** The values are stored consecutively in memory like array for O(1) element access. Costly O(n) for insertion/deletion in the middle of vector.

```c++
// declaration and initialization
vector<int> vec; // vec is a vector variable
vector<int> vec_1 (5); // vec_1 is a vector of 0, 0, 0, 0, 0
vector<int> vec_2 (4,100); // vec_2 is a vector of 100, 100, 100, 100

vector<int>::iterator vec_iter; // vec_iter is an iterator for vector<int>
vec_iter = vec_2.begin(); // vec_2.begin() is the address of its first element, *vec_iter contains 100

vector<int> vec_3 (vec_2.begin(), vec_2.end()); // initializes from another vector
vector<int> vec_4 (vec_3); // copies entire vec_3 vector

int arr[] = {1,2,3};
vector<int> vec_5 (arr, arr+2); // initializes from arr array, vec_5 is a vector of 1, 2

// size() - O(1) - returns size of vector
int vec_size = vec_5.size(); // vec_size contains 2

// empty() - O(1) - returns 1 if vector is empty, 0 otherwise
bool vec_empty = vec.empty(); // vec_empty contains 1

// access - O(1)
int value = vec_5[0]; // similar to array, value contains 1

// front() - O(1) - returns reference to first element
value = vec_5.front(); // value contains 1 

// back() - O(1) - returns reference to last element
value = vec_5.back(); // value contains 2 

// push_back() - O(1) - inserts new element at the end
vec_5.push_back(3); // vec_5 contains 1, 2, 3

// pop_back() - O(1) - removes last element
vec_5.pop_back(); // vec_5 contains 1, 2

// insert() -  inserts elements at desired positions. Moves the elements after "position" accordingly.
// insert(position, value) - O(n-position) - due to moving elements after position
vec_5.insert(vec_5.begin()+1, 4); // vec_5 contains 1, 4, 2

// insert(position, repetitions, value) - O(repetitions+n-position)
vec_5.insert(vec_5.begin(), 3, 2); // vec_5 contains 2, 2, 2, 1, 4, 2

// insert(position, start, end) - O(end-start+n-position)
vec_5.insert(vec_5.begin(), vec_2.begin(), vec_2.begin()+2); // vec_5 contains 100, 100, 2, 2, 2, 1, 4, 2

// assign() - overwrites values from the beginning
// assign(repetitions, value) - O(n') where n' is final size
vec_5.assign(1, 5); // vec_5 contains 5

// assign(start, end) - O(n') - n' is final size
vec_5.assign(vec_2.begin(), vec_2.begin()+3); // vec_5 contains 100, 100, 100

// erase() - erases elements at desired positions
// erase(position) - O(n-position) - due to moving elements after position
vec_5.erase(vec_5.begin()); // vec_5 contains 100, 100

// erase(start, end) - O(end-start+n-end) - due to elements erased and moving 
vec_5.erase(vec_5.begin(), vec_5.begin()+1); // vec_5 is 100

// swap() - O(1) - swaps the contents of vectors
vec_1.swap(vec_2); // vec_1 contains 100, 100, 100, 100 and vec_2 contains 0, 0, 0, 0, 0

// clear() - O(n) delete the vector
vec_5.clear(); // vec_5 is empty

// relational - O(n)
bool status;
status = (vec_3 == vec_4); // status contains 1
status = (vec_3 != vec_4); // status contains 0
status = (vec_1 < vec_2); // status contains 0, lexicographically compares elements from left
```


### Deque
A deque is double ended queue similar to vector with an additional benefit where elements can be added from both start and end.

**Design:** Contiguous memory is not guaranteed unlike vector and insertion/deletion in the middle is costly. However the access is still O(1).

```c++

// declaration and initialization
deque<int> deq; // deq is a deque variable
deque<int> deq_1 (5); // deq_1 is a deque of 0, 0, 0, 0, 0
deque<int> deq_2 (4,100); // deq_2 is a deque of 100, 100, 100, 100

deque<int>::iterator deq_iter; // deq_iter is an iterator for deque<int>
deq_iter = deq_2.begin(); // deq_2.begin() is the address of its first element, *deq_iter contains 100

deque<int> deq_3 (deq_2.begin(), deq_2.end()); // initializes from another deque
deque<int> deq_4 (deq_3); // copies entire deq_3 deque

int arr[] = {1,2,3};
deque<int> deq_5 (arr, arr+2); // initializes from arr array, deq_5 is a deque of 1, 2

// size() - O(1) - returns size of deque
int deq_size = deq_5.size(); // deq_size contains 2

// empty() - O(1) - returns 1 if deque is empty, 0 otherwise
bool deq_empty = deq.empty(); // deq_empty contains 1

// access - O(1)
int value = deq_5[0]; // similar to array, value contains 1

// front() - O(1) - returns reference to first element
value = deq_5.front(); // value contains 1 

// back() - O(1) - returns reference to last element
value = deq_5.back(); // value contains 2 

// insert() - inserts elements at desired positions
// insert(position, value) - O(n-position) due to moving elements after position
deq_5.insert(deq_5.begin()+1, 4); // deq_5 contains 1, 4, 2

// insert(position, repetitions, value) - O(repetitions+n-position)
deq_5.insert(deq_5.begin(), 3, 2); // deq_5 contains 2, 2, 2, 1, 4, 2

// insert(position, start, end) - O(end-start+n-position)
deq_5.insert(deq_5.begin(), deq_2.begin(), deq_2.begin()+2); // deq_5 contains 100, 100, 2, 2, 2, 1, 4, 2

// assign() - overwrites values from the beginning
// assign(repetitions, value) - O(n') - n' is final size
deq_5.assign(1, 5); // deq_5 contains 5

// assign(start, end) - O(n')
deq_5.assign(deq_2.begin(), deq_2.begin()+3); // deq_5 contains 100, 100, 100

// push_front() - O(1) - inserts new element at the start
deq_5.push_front(3); // deq_5 contains 3, 100, 100, 100

// pop_front() - O(1) - removes first element
deq_5.pop_front(); // deq_5 contains 100, 100, 100

// push_back() - O(1) - inserts new element at the end
deq_5.push_back(3); // deq_5 contains 100, 100, 100, 3

// pop_back() - O(1) - removes last element
deq_5.pop_back(); // deq_5 contains 100, 100, 100

// erase() - erases elements at desired positions
// erase(position) - O(n-position)
deq_5.erase(deq_5.begin()); // deq_5 contains 100, 100

// erase(start, end) - O(end-start+n-position)
deq_5.erase(deq_5.begin(), deq_5.begin()+1); // deq_5 contains 100

// swap() - O(1) - swaps the contents of deques
deq_1.swap(deq_2); // deq_1 contains 100, 100, 100, 100 and deq_2 contains 0, 0, 0, 0, 0

// clear() - O(n) - delete the deque
deq_5.clear(); // deq_5 is empty

// relational - O(n)
bool status;
status = (deq_3 == deq_4); // status contains 1
status = (deq_3 != deq_4); // status contains 0
status = (deq_1 < deq_2); // status contains 0, lexicographically compares elements from left
```

### List
A doubly linked list with discontiguous storage. 

**Design:** Allows constant insertion/deletion anywhere. O(position) time for accessing.

```c++
// declaration and initialization
list<int> mylist; // mylist is a list variable
list<int> mylist_1 (4,100); // mylist_1 contains 100, 100, 100, 100
list<int> mylist_2 (mylist_1); // mylist_2 is a copy of mylist_1
int arr[] = {1,4,3};
list<int> mylist_3 (arr, arr+3); // mylist_3 contains 1, 4, 3

// size() - O(1) - returns size of list
int mylist_size = mylist_1.size(); // mylist_size contains 4

// empty() - O(1) - returns 1 if list is empty, 0 otherwise
bool mylist_empty = mylist.empty(); // mylist_empty contains 1

// front() - O(1) - returns reference to first element
int value = mylist_1.front(); // value contains 100

// back() - O(1) - returns reference to last element
value = mylist_1.back(); // value contains 100

// assign() - overwrites values from the beginning
// assign(repetitions, value) - O(n') - n' is final size
mylist_1.assign(1, 5); // mylist_1 contains 5

// assign(start, end) - O(n') - n' is final size
mylist_2.assign(mylist_3.begin(), mylist_3.end()); // mylist_2 contains 1, 4, 3

// push_front() - O(1) - inserts new element at the start
mylist_3.push_front(2); // mylist_3 contains 2, 1, 4, 3

// pop_front() - O(1) - removes first element
mylist_3.pop_front(); // mylist_3 contains 1, 4, 3

// push_back() - O(1) - inserts new element at the end
mylist_3.push_back(2); // mylist_3 contains 1, 4, 3, 2

// pop_back() - O(1) - removes last element
mylist_3.pop_back(); // mylist_3 contains 1, 4, 3

// insert() - inserts elements at desired positions
// insert(position, value) - O(n-position) due to moving elements after position
mylist_3.insert(mylist_3.begin(), 2); // mylist_3 contains 2, 1, 4, 3

// insert(position, repetitions, value) - O(repetitions+n-position)
mylist_3.insert(mylist_3.begin(), 2, 2); // mylist_3 contains 2, 2, 2, 1, 4, 3

// insert(position, start, end) - O(end-start+n-position)
mylist_3.insert(mylist_3.begin(), mylist_1.begin(), mylist_1.end()); // mylist_3 contains 5, 2, 2, 2, 1, 4, 3

// erase() - erases elements at desired positions
// erase(position) - O(n-position)
mylist_3.erase(mylist_3.begin()); // mylist_3 contains 2, 2, 2, 1, 4, 3

// erase(start, end) - O(end-start+n-position)
list<int>::iterator list_iter;
list_iter = mylist_3.begin();
list_iter++; // only unary operator works on this iterator as opposed to mylist_3.begin()+1
mylist_3.erase(mylist_3.begin(), list_iter); // mylist_3 contains 2, 2, 1, 4, 3

// swap() - O(1) - swaps the contents of lists
mylist_1.swap(mylist_2); // mylist_1 contains 1, 4, 3 and mylist_2 contains 5

// clear() - O(n) - delete the list
mylist_3.clear(); // mylist_3 is empty

// relational - O(n)
bool status;
status = (mylist_1 == mylist_2); // status contains 0
status = (mylist_1 != mylist_2); // status contains 1
status = (mylist_1 < mylist_2); // status contains 1, lexicographically compares elements from left
```

### Stack
A stack is a last-in-first-out container where elements are added and removed from one end only. It is similar to stack of papers where recently added is on the top and is considered the first element of stack.

**Design:** Underlying container by default is deque.

```c++

// declaration and initialization
stack<int> sta; // sta is a stack variable
vector<int> vec (2,100);
stack<int, vector<int> > sta_1 (vec); // sta_1 is a copy of vec

// empty() - O(1) - returns 1 if stack is empty, 0 otherwise
bool sta_empty = sta.empty(); // sta_empty contains 1

// size() - O(1) - returns size of stack
int sta_size = sta_1.size(); // sta_size contains 2

// top() - O(1) - returns reference to top element
int sta_top = sta_1.top(); // sta_top is 100

// push() - O(1) - pushes new element from the top
sta.push(5); // sta is 5
sta_1.push(5); // sta_1 is 5, 100, 100

// pop() - O(1) - removes top element
sta_1.pop(); // sta_1 is 100, 100

// swap() - O(1) - swaps the contents of stacks
sta.swap(sta_1); // sta_1 is 5, sta is 100, 100

// relational - O(n)
bool status;
status = (sta == sta_1); // status contains 0
status = (sta != sta_1); // status contains 1
status = (sta < sta_1); // status contains 0, lexicographically compares elements from left 

```

### Queue
A queue is a first-in-first-out container where elements are added and removed from one end only. It is similar to a line of people where person who entered first exists first.

**Design:** Underlying container by default is deque.

```c++

// declaration and initialization
queue<int> que; // que is a queue variable
vector<int> vec (2,100);
queue<int> que_1;
for(int i=0; i<vec.size(); i++)
    que_1.push(vec[i]);

// empty() - O(1) - returns 1 if queue is empty, 0 otherwise
bool que_empty = que.empty(); // que_empty contains 1

// size() - O(1) - returns size of queue
int que_size = que_1.size(); // que_size contains 2

// front() - O(1) - returns reference to first element
int que_front = que.front(); // que_front is 100

// push() - O(1) - pushes new element from the end
que.push(5); // que is 5
que_1.push(5); // que_1 is 100, 100, 5

// back() - O(1) - return reference to last element
int que_back = que.back(); // que_back is 5

// pop() - O(1) - removes first element
que_1.pop(); // que_1 is 100, 5

// swap() - O(1) - swaps the contents of stacks
que.swap(que_1); // que_1 is 5, que is 100, 5

// relational - O(n)
bool status;
status = (que == que_1); // status contains 0
status = (que != que_1); // status contains 1
status = (que < que_1); // status contains 0, lexicographically compares elements from left 
```

### Priority Queue
A priority queue is a sorted container with greatest element first by default.

**Design:** It is implemented as max heap where the root of any sub-tree is the maximum element.

```c++

// declaration and initialization
priority_queue<int> pq; // pq is a priority_queue variable
int arr[] = {3,6,4};
priority_queue<int> pq_1 (arr, arr+3); // pq_1 contains 6, 4, 3

// empty() - O(1) - returns 1 if priority_queue is empty, 0 otherwise
bool pq_empty = pq.empty(); // pq_empty contains 1

// size() - O(1) - returns size of priority_queue
int pq_size = pq_1.size(); // pq_size contains 3

// top() - O(1) - return reference to first element
int pq_front = pq_1.top(); // pq_front is 6

// push() - O(log n) - pushes element into priority queue
pq.push(5); // pq is 5
pq_1.push(5); // pq_1 is 6, 5, 4, 3

// pop() - O(log n) removes first element
pq_1.pop(); // pq_1 is 5, 4, 3

// swap() - O(1) - swaps the contents of priority queues
pq.swap(pq_1); // pq_1 is 5, pq is 5, 4, 3

// changing order to least element first
priority_queue<int, vector<int>, greater<int> > pq_2;
pq_2.push(5);
pq_2.push(3); // pq_2 is 3, 5
```

### Set
A set contains unique elements with least element first by default. 

**Design:** Implemented as binary search trees (Red-black tree).

```c++
// declaration and initialization
set<int> myset; // myset is a set variable
int arr[] = {4,2,1,2};
set<int> myset_1 (arr, arr+4); // myset_1 is a set of 1, 2, 4
set<int> myset_2 (myset_1); // myset_2 is a copy of myset_1

// empty() - O(1) - returns 1 if set is empty, 0 otherwise
bool myset_empty = myset.empty(); // myset_empty contains 1

// size() - O(1) - returns size of set
int myset_size = myset_1.size(); // myset_size contains 3

// insert() - inserts new elements into the set
// insert(value) - O(log n)
myset.insert(3); // myset contains 3

// insert(start, end) - O(N log(N+n)) where N = end-start
int arr_1[] = {4,3,4};
myset_1.insert(arr_1, arr_1+3); // myset_1 contains 1, 2, 3, 4

// clear() - O(n) - delete the set
myset.clear(); // myset is empty

// erase() - erase elements at desired positions
myset.insert(arr_1, arr_1+3); // myset contains 3, 4
// erase(position) - O(1)
set<int>::iterator set_iter;
set_iter = myset.begin();
myset.erase(set_iter); // myset contains 4

// erase(value) - O(log n)
myset.insert(arr_1, arr_1+3); // myset contains 3, 4
myset.erase(4); // myset contains 3

// erase(start, end) - O(end-start)
myset.insert(arr_1, arr_1+3); // myset contains 3, 4
myset.erase(myset.begin(), myset.end()); // myset is empty

// find(value) - O(log n) - returns iterator to element if found, end() otherwise
set_iter = myset_1.find(3); // *set_iter outputs 3
set_iter = myset_1.find(5); // set_iter is myset_1.end()

// count(value) - O(log n) returns 1 if the element is present, 0 otherwise
int set_count = myset_1.count(4); // set_count contains 1
set_count = myset_1.count(10); // set_count contains 0

// lower_bound(value) - O(log n) - returns iterator to element equal to or immediately greater than value. Returns end otherwise
set_iter = myset_1.lower_bound(3); // *set_iter outputs 3
set_iter = myset_2.lower_bound(3); // *set_iter outputs 4

// upper_bound(value) - O(log n) - returns iterator to element immediately greater than value. Returns end otherwise
set_iter = myset_1.upper_bound(3); // *set_iter outputs 4
set_iter = myset_2.upper_bound(3); // *set_iter outputs 4

// equal_range(value) - O(log n) - returns pair of iterators to elements equal to value. In other words, returns lower_bound and upper_bound as a pair.
pair<set<int>::iterator,set<int>::iterator> set_iter_pair;
set_iter_pair = myset_1.equal_range(3); // *(set_iter_pair.first) outputs 3 and *(set_iter_pair.second) outputs 4

// swap() - O(1) - swaps the contents of sets
myset_1.swap(myset_2); // myset_1 contains 1, 2, 4 and myset_2 contains 1, 2, 3, 4

// changing order to greatest element first
set<int, greater<int> > myset_3 (arr, arr+4); // myset_3 contains 4, 2, 1
```

### Multiset
A multiset is similar to set but can contain duplicate elements with least element first by default.

**Design:** Implemented as binary search trees (Red-black tree).

```c++
// declaration and initialization
multiset<int> mulset; // mulset is a multiset variable
int arr[] = {4,2,1,2};
multiset<int> mulset_1 (arr, arr+4); // mulset_1 is a set of 1, 2, 2, 4
multiset<int> mulset_2 (mulset_1); // mulset_2 is a copy of mulset_1

// empty() - O(1) - returns 1 if multiset is empty, 0 otherwise
bool mulset_empty = mulset.empty(); // mulset_empty contains 1

// size() - O(1) - returns size of multiset
int mulset_size = mulset_1.size(); // mulset_size contains 4

// insert() - inserts new elements into the multiset
// insert(value) - O(log n)
mulset.insert(3); // mulset contains 3

// insert(start, end) - O(N log(N+n)) where N = end-start
int arr_1[] = {4,3};
mulset_1.insert(arr_1, arr_1+2); // mulset_1 contains 1, 2, 2, 3, 4, 4

// clear() - O(n) - delete the multiset
mulset.clear(); // mulset is empty

// erase() - erase elements at desired positions
mulset.insert(mulset_1.begin(), mulset_1.end()); // mulset contains 1, 2, 2, 3, 4, 4
// erase(position) - O(1)
multiset<int>::iterator mulset_iter;
mulset_iter = mulset.begin();
mulset.erase(mulset_iter); // mulset contains 2, 2, 3, 4, 4

// erase(value) - O(log n + num) where num is number of occurrences of value 
mulset.erase(4); // mulset contains 2, 2, 3

// erase(start, end) - O(end-start)
mulset.erase(mulset.begin(), mulset.end()); // mulset is empty

// find(value) - O(log n) - returns iterator to element if found, end() otherwise
mulset_iter = mulset_1.find(3); // *mulset_iter outputs 3
mulset_iter = mulset_1.find(5); // mulset_iter is mulset_1.end()

// count(value) - O(log n + num) - returns count of element
int mulset_count = mulset_1.count(4); // mulset_count contains 2
mulset_count = mulset_1.count(10); // mulset_count contains 0

// lower_bound(value) - O(log n) - returns iterator to element equal to or immediately greater than value. Returns end otherwise
mulset_iter = mulset_1.lower_bound(3); // *mulset_iter outputs 3
mulset_iter = mulset_2.lower_bound(3); // *mulset_iter outputs 4

// upper_bound(value) - O(log n) - returns iterator to element immediately greater than value. Returns end otherwise
mulset_iter = mulset_1.upper_bound(3); // *mulset_iter outputs 4
mulset_iter = mulset_2.upper_bound(3); // *mulset_iter outputs 4

// equal_range(value) - O(log n) - returns pair of iterators to elements equal to value. In other words, returns lower_bound and upper_bound as a pair.
pair<multiset<int>::iterator, multiset<int>::iterator> mulset_iter_pair;
mulset_iter_pair = mulset_1.equal_range(3); // *(mulset_iter_pair.first) outputs 3 and *(mulset_iter_pair.second) outputs 4

// swap() - O(1) - swaps the contents of multisets
mulset_1.swap(mulset_2); // mulset_1 contains 1, 2, 2, 4 and mulset_2 contains 1, 2, 2, 3, 4, 4

// changing order to greatest element first
multiset<int, greater<int> > mulset_3 (arr, arr+4); // mulset_3 contains 4, 2, 2, 1
```

### Map
Map is an associative container that stores key-value pairs with least key element first by default. The key is unique i.e value is overwritten in case the key is already present.

**Design:** Implemented as binary search trees (Red-black tree).

```c++
// declaration and initialization
map<int, int> mymap;
int keys[] = {3,1};
int values[] = {4,2};
map<int, int> mymap_1;
mymap_1[keys[0]] = values[0];
mymap_1[keys[1]] = values[1]; // mymap_1 contains {1,2},{3,4} pairs
map<int,int> mymap_2 (mymap_1); // mymap_2 is a copy of mymap_1

// empty() - O(1) - returns 1 if map is empty, 0 otherwise
bool mymap_empty = mymap.empty(); // mymap_empty contains 1

// size() - O(1) - returns size of map
int mymap_size = mymap_1.size(); // mymap_size contains 2

// insert() - inserts new elements into the map
// insert(pair) - O(log n) returns a pair. First is iterator to inserted element or already existing key and second is boolean - true if inserted or false if present already.
pair<map<int,int>::iterator, bool> map_insert;
map_insert = mymap.insert(pair<int, int>(1,6)); // map_insert.second contains true, map_insert.first points to element inserted, mymap contains {1,6}

map_insert = mymap_1.insert(pair<int, int>(1,6)); // map_insert.second contains false, map_intert.first points to the pair {1,2}. mymap_1 contains {1,2},{3,4}

// insert(start, end) - O(N log(N+n)) where N = end-start
mymap.insert(mymap_1.begin(), mymap_1.end()); // mymap contains {1,6}, {3,4}

// clear() - O(n) - delete the map
mymap.clear(); // mymap is empty

// erase() - erase elements at desired positions
mymap_1.insert(pair<int, int>(5,6)); // mymap_1 contains {1,2}, {3, 4}, {5,6}
// erase(position) - O(1)
map<int,int>::iterator map_iter;
map_iter = mymap_1.begin();
mymap_1.erase(map_iter); // mymap_1 contains {3,4}, {5,6}

// erase(key) - O(log n)
mymap_1.insert(pair<int, int>(1,2)); // mymap_1 contains {1,2}, {3, 4}, {5,6}
mymap_1.erase(1); // mymap_1 contains {3, 4}, {5,6}

// erase(start, end) - O(end-start)
mymap.insert(pair<int, int>(1,2)); // mymap contains {1,2}
mymap.erase(mymap.begin(), mymap.end()); // mymap is empty

// find(key) - O(log n) - returns iterator to element if found, end() otherwise
map_iter = mymap_1.find(3); // map_iter->first outputs 3, map_iter->second outputs 4
map_iter = mymap_1.find(1); // map_iter is mymap_1.end()

// count(key) - O(log n) returns 1 if the element is present, 0 otherwise
int map_count = mymap_1.count(3); // map_count contains 1
map_count = mymap_1.count(1); // map_count contains 0

// lower_bound(key) - O(log n) - returns iterator to element equal to or immediately greater than value. Returns end otherwise
map_iter = mymap_1.lower_bound(3); // map_iter->first outputs 3, map_iter->second outputs 4
map_iter = mymap_1.lower_bound(1); // map_iter->first outputs 3, map_iter->second outputs 4

// upper_bound(key) - O(log n) - returns iterator to element immediately greater than value. Returns end otherwise
map_iter = mymap_1.upper_bound(3); // // map_iter->first outputs 5, map_iter->second outputs 6

// equal_range(key) - O(log n) - returns pair of iterators to elements equal to value. In other words, returns lower_bound and upper_bound as a pair.
pair<map<int,int>::iterator,map<int,int>::iterator> map_iter_pair;
map_iter_pair = mymap_1.equal_range(3); // map_iter_pair.first->first outputs 3 and map_iter_pair.second->first outputs 5

// swap() - O(1) - swaps the contents of maps
mymap_1.swap(mymap_2); // mymap_1 contains {1,2}, {3, 4} and mymap_2 contains {3, 4}, {5,6}
```

### Multimap
A multimap is similar to map but can contain multiple values for a key with least key first by default. In case of multiple values for a key, they are not sorted according to value and follows the order of initialization.

**Design:** Implemented as binary search trees (Red-black tree).

```c++
// declaration and initialization
multimap<int, int> mulmap;
int keys[] = {3,1,3};
int values[] = {6,2,4};
multimap<int, int> mulmap_1;
for(int i=0; i<3; i++)
    mulmap_1.insert(pair<int,int>(keys[i],values[i])); 
// mulmap_1 contains {1,2}, {3,6}, {3,4}. Unlike in map, operator [] cannot be used here.
multimap<int,int> mulmap_2 (mulmap_1); // mulmap_2 is a copy of mulmap_1

// empty() - O(1) - returns 1 if multimap is empty, 0 otherwise
bool mulmap_empty = mulmap.empty(); // mulmap_empty contains 1

// size() - O(1) - returns size of multimap
int mulmap_size = mulmap_1.size(); // mulmap_size contains 3

// insert() - inserts new elements into the multimap
// insert(pair) - O(log n)
mulmap.insert(pair<int, int>(1,6)); // mulmap contains {1,6}
mulmap_1.insert(pair<int, int>(1,6)); // mulmap_1 contains {1,2}, {1,6}, {3,6}, {3,4}

// insert(start, end) - O(N log(N+n)) where N = end-start
mulmap.insert(mulmap_1.begin(), mulmap_1.end()); // mulmap contains {1,6}, {1,2}, {1,6}, {3,6}, {3,4}

// clear() - O(n) - delete the multimap
mulmap.clear(); // mulmap is empty

// erase() - erase elements at desired positions
mulmap.insert(pair<int, int>(5,6)); // mulmap contains {5,6}

// erase(position) - O(1)
multimap<int, int>::iterator mulmap_iter;
mulmap_iter = mulmap.begin();
mulmap.erase(mulmap_iter); // mulmap is empty

// erase(key) - O(log n + num) where num is number of occurrences of key
mulmap_1.erase(1); // mulmap_1 contains {3,6}, {3,4}

// erase(start, end) - O(end-start)
mulmap.insert(pair<int, int>(1,2)); // mulmap contains {1,2}
mulmap.erase(mulmap.begin(), mulmap.end()); // mulmap is empty

// find(key) - O(log n) - returns iterator to element if found, end() otherwise
mulmap_iter = mulmap_1.find(3); // mulmap_iter->first outputs 3, mulmap_iter->second outputs 6
mulmap_iter = mulmap_1.find(1); // mulmap_iter is mulmap_1.end()

// count(key) - O(log n + num) returns count of key
int mulmap_count = mulmap_1.count(3); // mulmap_count contains 2
mulmap_count = mulmap_1.count(1); // mulmap_count contains 0

// lower_bound(key) - O(log n) - returns iterator to element equal to or immediately greater than value. Returns end otherwise
mulmap_iter = mulmap_1.lower_bound(3); // mulmap_iter->first outputs 3, mulmap_iter->second outputs 6
mulmap_iter = mulmap_1.lower_bound(1); // mulmap_iter->first outputs 3, mulmap_iter->second outputs 4

// upper_bound(key) - O(log n) - returns iterator to element immediately greater than value. Returns end otherwise
mulmap_iter = mulmap_1.upper_bound(3); // // mulmap_iter is mulmap_1.end()

// equal_range(key) - O(log n) - returns pair of iterators to elements equal to key. In other words, returns lower_bound and upper_bound as a pair.
pair<multimap<int,int>::iterator,multimap<int,int>::iterator> mulmap_iter_pair;
mulmap_iter_pair = mulmap_1.equal_range(3); // mulmap_iter_pair.first->first outputs 3 and mulmap_iter_pair.second is mulmap_1.end()

// swap() - O(1) - swaps the contents of multimaps
mulmap_1.swap(mulmap_2); // mulmap_1 contains {1,2}, {3,6}, {3,4} and mulmap_2 contains {3,6}, {3,4}
```

### Unordered Set
An unordered set contains unique elements with no particular order and allows faster access. 

**Design:** Implemented as hash map.

```c++
// declaration and initialization
unordered_set<int> myset; // myset is an unordered set variable
int arr[] = {4,2,1,2};
unordered_set<int> myset_1 (arr, arr+4); // myset_1 is an unordered set of 2, 1, 4 (random order)
unordered_set<int> myset_2 (myset_1); // myset_2 is a copy of myset_1

// empty() - O(1) - returns 1 if unordered set is empty, 0 otherwise
bool myset_empty = myset.empty(); // myset_empty contains 1

// size() - O(1) - returns size of unordered set
int myset_size = myset_1.size(); // myset_size contains 3

// insert() - inserts new elements into the unordered set
// insert(value) - O(1) on average
myset.insert(3); // myset contains 3

// insert(start, end) - O(N) where N = end-start
int arr_1[] = {4,3,4};
myset_1.insert(arr_1, arr_1+3); // myset_1 contains 4, 2, 1, 3

// clear() - O(n) - delete the unordered set
myset.clear(); // myset is empty

// erase() - erase elements at desired positions
myset.insert(arr_1, arr_1+3); // myset contains 4, 3
// erase(position) - O(1)
unordered_set<int>::iterator set_iter;
set_iter = myset.find(4);
myset.erase(set_iter); // myset contains 3

// erase(value) - O(1)
myset.insert(arr_1, arr_1+3); // myset contains 3, 4
myset.erase(4); // myset contains 3

// erase(start, end) - O(end-start)
myset.insert(arr_1, arr_1+3); // myset contains 3, 4
myset.erase(myset.begin(), myset.end()); // myset is empty

// find(value) - O(1) - returns iterator to element if found, end() otherwise
set_iter = myset_1.find(3); // *set_iter outputs 3
set_iter = myset_1.find(5); // set_iter is myset_1.end()

// count(value) - O(1) returns 1 if the element is present, 0 otherwise
int set_count = myset_1.count(4); // set_count contains 1
set_count = myset_1.count(10); // set_count contains 0

// equal_range(value) - O(1) - returns pair of iterators to elements equal to value. In other words, returns lower_bound and upper_bound as a pair.
pair<unordered_set<int>::iterator,unordered_set<int>::iterator> set_iter_pair;
set_iter_pair = myset_1.equal_range(3); // *(set_iter_pair.first) outputs 3 and *(set_iter_pair.second) outputs 4

// swap() - O(1) - swaps the contents of unordered sets
myset_1.swap(myset_2); // myset_1 contains 4, 2, 1 and myset_2 contains 4, 2, 1, 3
```

### Unordered MultiSet
An unordered multiset is similar to normal multiset with no order and allows faster access.

**Design:** Implemented as hash map.

```c++
// declaration and initialization
unordered_multiset<int> mulset; // mulset is an unordered multiset variable
int arr[] = {4,2,1,2};
unordered_multiset<int> mulset_1 (arr, arr+4); // mulset_1 is a set of 2, 2, 1, 4 (random order)
unordered_multiset<int> mulset_2 (mulset_1); // mulset_2 is a copy of mulset_1

// empty() - O(1) - returns 1 if unordered multiset is empty, 0 otherwise
bool mulset_empty = mulset.empty(); // mulset_empty contains 1

// size() - O(1) - returns size of unordered multiset
int mulset_size = mulset_1.size(); // mulset_size contains 4

// insert() - inserts new elements into the unordered multiset
// insert(value) - O(1)
mulset.insert(3); // mulset contains 3

// insert(start, end) - O(N) where N = end-start
int arr_1[] = {4,3};
mulset_1.insert(arr_1, arr_1+2); // mulset_1 contains 4, 2, 1, 2, 4, 3

// clear() - O(n) - delete the unordered multiset
mulset.clear(); // mulset is empty

// erase() - erase elements at desired positions
mulset.insert(mulset_1.begin(), mulset_1.end()); // mulset contains 4, 2, 1, 2, 4, 3
// erase(position) - O(1)
unordered_multiset<int>::iterator mulset_iter;
mulset_iter = mulset.find(4);
mulset.erase(mulset_iter); // mulset contains 2, 1, 2, 4, 3

// erase(value) - O(num) where num is number of occurrences of value 
mulset.erase(2); // mulset contains 1, 4, 3

// erase(start, end) - O(end-start)
mulset.erase(mulset.begin(), mulset.end()); // mulset is empty

// find(value) - O(1) - returns iterator to element if found, end() otherwise
mulset_iter = mulset_1.find(3); // *mulset_iter outputs 3
mulset_iter = mulset_1.find(5); // mulset_iter is mulset_1.end()

// count(value) - O(num) - returns count of element
int mulset_count = mulset_1.count(4); // mulset_count contains 2
mulset_count = mulset_1.count(10); // mulset_count contains 0

// equal_range(value) - O(1) - returns pair of iterators to elements equal to value. In other words, returns lower_bound and upper_bound as a pair.
pair<unordered_multiset<int>::iterator,unordered_multiset<int>::iterator> mulset_iter_pair;
mulset_iter_pair = mulset_1.equal_range(3); // *(mulset_iter_pair.first) outputs 3 and *(mulset_iter_pair.second) outputs 4

// swap() - O(1) - swaps the contents of unordered multisets
mulset_1.swap(mulset_2); // mulset_1 contains 4, 2, 1, 2 and mulset_2 contains 4, 2, 1, 2, 4, 3
```

### Unordered Map
Unordered map is an associative container that stores key-value pairs with no order. The key is unique i.e value is overwritten in case the key is already present.

**Design:** Implemented as hash map.

```c++
// declaration and initialization
unordered_map<int, int> mymap;
int keys[] = {3,1};
int values[] = {4,2};
unordered_map<int, int> mymap_1;
mymap_1[keys[0]] = values[0];
mymap_1[keys[1]] = values[1]; // mymap_1 contains {3,4}, {1,2} pairs
unordered_map<int,int> mymap_2 (mymap_1); // mymap_2 is a copy of mymap_1

// empty() - O(1) - returns 1 if unordered map is empty, 0 otherwise
bool mymap_empty = mymap.empty(); // mymap_empty contains 1

// size() - O(1) - returns size of unordered map
int mymap_size = mymap_1.size(); // mymap_size contains 2

// insert() - inserts new elements into the unordered map
// insert(pair) - O(1) returns a pair. First is iterator to inserted element or already existing key and second is boolean - true if inserted or false if present already.
pair<unordered_map<int,int>::iterator, bool> map_insert;
map_insert = mymap.insert(pair<int, int>(1,6)); // map_insert.second contains true, map_insert.first points to element inserted, mymap contains {1,6}

map_insert = mymap_1.insert(pair<int, int>(1,6)); // map_insert.second contains false, map_intert.first points to the pair {1,2}. mymap_1 contains {3,4}, {1,2}

// insert(start, end) - O(N) where N = end-start
mymap.insert(mymap_1.begin(), mymap_1.end()); // mymap contains {1,6}, {3,4}

// clear() - O(n) - delete the unordered map
mymap.clear(); // mymap is empty

// erase() - erase elements at desired positions
mymap_1.insert(pair<int, int>(5,6)); // mymap_1 contains {3, 4}, {1,2}, {5,6}
// erase(position) - O(1)
unordered_map<int,int>::iterator map_iter;
map_iter = mymap_1.find(3);
mymap_1.erase(map_iter); // mymap_1 contains {1,2}, {5,6}

// erase(key) - O(1) - where num is number of occurrences of value
mymap_1.insert(pair<int, int>(3,4)); // mymap_1 contains {1,2}, {5,6}, {3, 4}
mymap_1.erase(1); // mymap_1 contains {5,6}, {3, 4}

// erase(start, end) - O(end-start)
mymap.insert(pair<int, int>(1,2)); // mymap contains {1,2}
mymap.erase(mymap.begin(), mymap.end()); // mymap is empty

// find(key) - O(1) - returns iterator to element if found, end() otherwise
map_iter = mymap_1.find(3); // map_iter->first outputs 3, map_iter->second outputs 4
map_iter = mymap_1.find(1); // map_iter is mymap_1.end()

// count(key) - O(1) returns 1 if the element is present, 0 otherwise
int map_count = mymap_1.count(3); // map_count contains 1
map_count = mymap_1.count(1); // map_count contains 0

// equal_range(key) - O(1) - returns pair of iterators to elements equal to value. In other words, returns lower_bound and upper_bound as a pair.
pair<unordered_map<int,int>::iterator,unordered_map<int,int>::iterator> map_iter_pair;
map_iter_pair = mymap_1.equal_range(3); // map_iter_pair.first->first outputs 3 and map_iter_pair.second->first outputs 5

// swap() - O(1) - swaps the contents of unordered maps
mymap_1.swap(mymap_2); // mymap_1 contains {3,4}, {1,2} and mymap_2 contains {5,6}, {3, 4}
```

### Unordered Multimap
Unordered multimap is similar to unordered map but can contain multiple values for a key with no order.

**Design:** Implemented as hash map.

```c++
// declaration and initialization
unordered_multimap<int, int> mulmap;
int keys[] = {3,1,3};
int values[] = {6,2,4};
unordered_multimap<int, int> mulmap_1;
for(int i=0; i<3; i++)
    mulmap_1.insert(pair<int,int>(keys[i],values[i])); 
// mulmap_1 contains {3,6}, {1,2}, {3,4}. Unlike in map, operator [] cannot be used here.
unordered_multimap<int,int> mulmap_2 (mulmap_1); // mulmap_2 is a copy of mulmap_1

// empty() - O(1) - returns 1 if unordered multimap is empty, 0 otherwise
bool mulmap_empty = mulmap.empty(); // mulmap_empty contains 1

// size() - O(1) - returns size of unordered multimap
int mulmap_size = mulmap_1.size(); // mulmap_size contains 3

// insert() - inserts new elements into the unordered multimap
// insert(pair) - O(1)
mulmap.insert(pair<int, int>(1,6)); // mulmap contains {1,6}
mulmap_1.insert(pair<int, int>(1,6)); // mulmap_1 contains {3,6}, {1,2}, {3,4}, {1,6}

// insert(start, end) - O(N) where N = end-start
mulmap.insert(mulmap_1.begin(), mulmap_1.end()); // mulmap contains {1,6}, {3,6}, {1,2}, {3,4}, {1,6}

// clear() - O(n) - delete the unordered multimap
mulmap.clear(); // mulmap is empty

// erase() - erase elements at desired positions
mulmap.insert(pair<int, int>(5,6)); // mulmap contains {5,6}

// erase(position) - O(1)
unordered_multimap<int, int>::iterator mulmap_iter;
mulmap_iter = mulmap.find(5);
mulmap.erase(mulmap_iter); // mulmap is empty

// erase(key) - O(num) where num is number of occurrences of key
mulmap_1.erase(1); // mulmap_1 contains {3,6}, {3,4}

// erase(start, end) - O(end-start)
mulmap.insert(pair<int, int>(1,2)); // mulmap contains {1,2}
mulmap.erase(mulmap.begin(), mulmap.end()); // mulmap is empty

// find(key) - O(1) - returns iterator to element if found, end() otherwise
mulmap_iter = mulmap_1.find(3); // mulmap_iter->first outputs 3, mulmap_iter->second outputs 6
mulmap_iter = mulmap_1.find(1); // mulmap_iter is mulmap_1.end()

// count(key) - O(num) returns count of key
int mulmap_count = mulmap_1.count(3); // mulmap_count contains 2
mulmap_count = mulmap_1.count(1); // mulmap_count contains 0

// equal_range(key) - O(1) - returns pair of iterators to elements equal to key. In other words, returns lower_bound and upper_bound as a pair.
pair<unordered_multimap<int,int>::iterator,unordered_multimap<int,int>::iterator> mulmap_iter_pair;
mulmap_iter_pair = mulmap_1.equal_range(3); // mulmap_iter_pair.first->first outputs 3 and mulmap_iter_pair.second is mulmap_1.end()

// swap() - O(1) - swaps the contents of unordered multimaps
mulmap_1.swap(mulmap_2); // mulmap_1 contains {3,6}, {1,2}, {3,4} and mulmap_2 contains {3,6}, {3,4}
```



## Algorithms
```c++
// comparison function
bool comp(int a, int b)
{
    return a>b; // for descending order
}

// min(a,b), max(a,b) - returns minimum and maximum values respectively
int min_num = min(3,5); // min_num contains 3
int max_num = max(3,5); // max_num contains 5

// min_element(start, end), max_element(start, end) - O(n) - returns iterator to the element
vector<int> vec ({4,5,1});    // vec contains 4, 5, 1
vector<int>::iterator vec_iter;
vec_iter = min_element(vec.begin(), vec.end()); // *vec_iter contains 1
vec_iter = max_element(vec.begin(), vec.end()); // *vec_iter outputs 5

// distance(start, end) - O(n) - returns distance between two iterators
int vec_dist = distance(vec.begin(), vec_iter); // vec_dist is 1

// reverse(start, end) - O(n) - reverse the order of elements
reverse(vec.begin(), vec.end()); // vec contains 1, 5, 4

// next_permutation(start, end), prev_permutation(start, end) - O(n) - rearranges to lexicographically greater/lesser permutation
next_permutation(vec.begin(), vec.end()); // vec contains 4, 1, 5
prev_permutation(vec.begin(), vec.end()); // vec contains 1, 5, 4

// random_shuffle(start, end) - O(n) - rearrange elements randomly
random_shuffle(vec.begin(), vec.end());

// sort(start, end) - O(nlog n)
int arr_1[] = {4,5,1};
int arr_2[] = {2,3,1};

sort(arr_1, arr_1+3);       // arr_1 contains 1, 4, 5 - ascending by default
sort(arr_2, arr_2+3, comp); // arr_2 contains 3, 2, 1 - descending using comp function

// binary_search(start, end, value) - O(log n) - returns true if value found in sorted range
int status;
status = binary_search(arr_1, arr_1+3, 4);  // status contains 1 (ascending range by default)
status = binary_search(arr_2, arr_2+3, 3, comp);  // status contains 1

// merge(start_1, end_1, start_2, end_2, new_iter)
vector<int> vec_1(6); // vec_1 contains 0, 0, 0, 0, 0, 0
sort(arr_2, arr_2+3); // arr_2 contains 1, 2, 3
merge(arr_1, arr_1+3, arr_2, arr_2+3, vec_1.begin()); // vec_1 contains 1, 1, 2, 3, 4, 5

// find(start, end, value) - O(n) returns iterator to element otherwise end()
vec_iter = find(vec_1.begin(), vec_1.end(), 4); // *vec_iter is 4
vec_iter = find(vec_1.begin(), vec_1.end(), 6); // vec_iter is vec_1.end()
```

## Miscellaneous
**Pair**

```c++
pair<int, int> mypair; // declaration
pair<int, int> mypair_1 (3,5); // initialization
mypair = make_pair(2,4); // assign
int first, second;
first = mypair.first; // first contains 2
second = mypair.second; // second contains 4
```

**String**

```c++
// declaration and initialization
string s;
string s_1 = "random string";
string s_2 (s_1.begin(), s_1.begin()+3); // s_2 contains ran
string s_3 (5,'#'); // s_3 contains #####  
string s_4 (s_1); // s_4 is a copy of s_1

// length() - returns length of string
int s_length = s_3.length(); // s_length contains 5

// access
char s_char = s_1[0]; // s_char contains r
s_4[0] = 'f'; // s_4 contains fandom string

// clear() - deletes the string
s_4.clear(); // s_4 is empty

// empty() - returns 1 if empty, 0 otherwise
bool s_empty = s_4.empty(); // s_empty contains 1

// concatenate
s_2 += "d"; // s_2 contains rand

// append() - concatenates string to the end
s_4 = "om";
// append(string)
s_2.append(s_4); // s_2 contains random
// append(start, end)
s_2.append(s_3.begin(), s_3.begin()+1); // s_2 contains random#

// assign() - replaces current string
// assign(string)
s.assign(s_3); // s contains #####
// assign(start, end)
s.assign(s_2.begin(), s_2.end()); // s contains random#

// insert() - inserts string after position
// insert(position, string)
s.insert(0, s_3); // s contains #####random#
// insert(position, start, end)
s.insert(s.end(), s_3.begin(), s_3.end()-1); // s contains #####random#####

// erase() - deletes character at the given position(s)
// erase(position)
s.erase(s.begin()); // s contains ####random#####
// erase(start, end)
s.erase(s.begin(), s.begin()+4); // s contains random#####

// replace() - replaces from start to end with string
// replace(start, end, string)
s.replace(s.begin(), s.begin()+3, s_3); // s contains #####dom#####
// replace(start, end, start_1, end_1)
s.replace(s.begin()+1, s.end(), s_2.begin(), s_2.end()); // s contains #random#

// find() - returns position of occurrence of string, -1 otherwise
// find(string)
int position;
position = s.find("random"); // position contains 1
position = s.find("fandom");   // position contains -1
// find(string, position) - searches for occurrence from position. By default, position is 0 in the above case
position = s.find("random", 2); // position contains -1

// swap(string) - swaps contents of the strings
s.swap(s_2); // s contains random#, s_2 contains #random#

// relational operators
bool status;
status = (s_1==s_4); // status contains 0
status = (s_1!=s_4); // status contains 1
status = (s_1 < s_4); // status contains 0

// conversions
// stoi - convert string to integer
int num = stoi("1998");

// stoll - convert string to long long int
long long int num_1 = stoll("19981998");

// stof - convert string to float
float num_2 = stof("1998.26");

// stod - convert string to double
double num_3 = stod("19981998.26");

// to_string - convert to string
s = to_string(num_3); // s contains 19981998.26
```
You can find detailed documentation on the [official website](http://www.cplusplus.com/reference/).

# Data Structures
[Tutorial](https://www.hackerearth.com/practice/data-structures) - Different ways of storing, accessing and manipulating data according to the requirements. 

# Algorithms
[Tutorial](https://www.hackerearth.com/practice/algorithms/) -  Efficient techniques and paradigms to solve various problems.

# Math and Miscellaneous
[Tutorial](https://www.hackerearth.com/practice/math/) - Math based concepts and ad-hoc problems that involve logic.

# Practice
1. [InterviewBit](https://www.interviewbit.com/courses/programming/) - InterviewBit has topic wise tutorials and good collection of problems.  
2. [Leetcode](https://leetcode.com/problemset/all/) - Leetcode has a great variety of problems with corner and tricky test cases which are beneficial for interviews.
3. [Codeforces](https://codeforces.com/problemset), [HackerEarth](https://www.hackerearth.com/practice/), [HackerRank](https://www.hackerrank.com/) - Competitive programming websites have huge collection of problems.

# Acknowledgements
Thanks to Ethan for being a source of inspiration and the reason behind this work.
