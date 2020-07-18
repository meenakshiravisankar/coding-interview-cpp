# Introduction
STL is the standard template library which contains C++ template classes. STL is a powerful tool and it reduces programming time with rich implementations of freuently used data structures and algorithms. Important parts of the STL are as follows:
1. Containers - includes container classes to store and manipulate data elements.
2. Algorithms - includes important techniques like sorting, searching.

> Learn STL, save your life

**Table of contents**
* Containers
    1. Vector
    2. Deque
    3. Stack
    4. Queue
    5. Priority Queue
   
* Algorithms
  
## Time complexity cheat sheet for containers

## Containers
Following are the important containers illustrated with example use cases. Some methods support multiple ways of providing arguments which are also presented here.

### Vector
A vector is similar to an array but with dynamic size where elements can be added from the end.
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

// size() - returns size of vector
int vec_size = vec_5.size(); // vec_size contains 2

// empty() - returns 1 if vector is empty, 0 otherwise
bool vec_empty = vec.empty(); // vec_empty contains 1

// access
int value = vec_5[0]; // similar to array, value contains 1

// front() - returns first element
value = vec_5.front(); // value contains 1 

// back() - returns last element
value = vec_5.back(); // value contains 2 

// push_back() - inserts new element at the end
vec_5.push_back(3); // vec_5 contains 1, 2, 3

// pop_back()  - removes last element
vec_5.pop_back(); // vec_5 contains 1, 2

// insert() - inserts elements at desired positions
// insert(position, value)
vec_5.insert(vec_5.begin()+1, 4); // vec_5 contains 1, 4, 3

// insert(position, repetitions, value)
vec_5.insert(vec_5.begin(), 3, 2); // vec_5 contains 2, 2, 2, 1, 4, 3

// insert(position, start, end)
vec_5.insert(vec_5.begin(), vec_2.begin(), vec_2.begin()+2); // vec_5 contains 100, 100, 2, 2, 2, 2, 1, 4, 3

// assign() - overwrites values from the beginning
// assign(repetitions, value)
vec_5.assign(1, 5); // vec_5 contains 5, 100, 2, 2, 2, 2, 1, 4, 3

// assign(start, end)
vec_5.assign(vec_2.begin(), vec_2.begin()+3); // vec_5 contains 100, 100, 100, 2, 2, 2, 1, 4, 3

// erase() - erases elements at desired positions
// erase(position)
vec_5.erase(vec_5.begin()); // vec_5 contains 100, 100, 2, 2, 2, 1, 4, 3

// erase(start, end)
vec_5.erase(vec_5.begin(), vec_5.begin()+3); // vec_5 contains 2, 2, 1, 4, 3

// swap() - swaps the contents of vectors
vec_1.swap(vec_2); // vec_1 contains 100, 100, 100, 100 and vec_2 contains 0, 0, 0, 0, 0

// clear() - delete the vector
vec_5.clear(); // vec_5 is empty

// relational
bool status;
status = (vec_3 == vec_4); // status contains 1
status = (vec_3 != vec_4); // status contains 0
status = (vec_1 < vec_2); // status contains 0, lexicographically compares elements from left
```


### Deque
A deque is double ended queue similar to vector with an additional benefit where elements can be added from start and end.
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

// size() - returns size of deque
int deq_size = deq_5.size(); // deq_size contains 2

// empty() - returns 1 if deque is empty, 0 otherwise
bool deq_empty = deq.empty(); // deq_empty contains 1

// access
int value = deq_5[0]; // similar to array, value contains 1

// front() - returns first element
value = deq_5.front(); // value contains 1 

// back() - returns last element
value = deq_5.back(); // value contains 2 

// assign() - overwrites values from the beginning
// assign(repetitions, value)
deq_5.assign(1, 5); // deq_5 contains 5, 100, 2, 2, 2, 2, 1, 4, 3

// assign(start, end)
deq_5.assign(deq_2.begin(), deq_2.begin()+3); // deq_5 contains 100, 100, 100, 2, 2, 2, 1, 4, 3

// push_front() - inserts new element at the start
deq_5.push_front(3); // deq_5 contains 3, 1, 2

// pop_front()  - removes first element
deq_5.pop_front(); // deq_5 contains 1, 2

// push_back() - inserts new element at the end
deq_5.push_back(3); // deq_5 contains 1, 2, 3

// pop_back()  - removes last element
deq_5.pop_back(); // deq_5 contains 1, 2

// insert() - inserts elements at desired positions
// insert(position, value)
deq_5.insert(deq_5.begin()+1, 4); // deq_5 contains 1, 4, 3

// insert(position, repetitions, value)
deq_5.insert(deq_5.begin(), 3, 2); // deq_5 contains 2, 2, 2, 1, 4, 3

// insert(position, start, end)
deq_5.insert(deq_5.begin(), deq_2.begin(), deq_2.begin()+2); // deq_5 contains 100, 100, 2, 2, 2, 2, 1, 4, 3

// erase() - erases elements at desired positions
// erase(position)
deq_5.erase(deq_5.begin()); // deq_5 contains 100, 100, 2, 2, 2, 1, 4, 3

// erase(start, end)
deq_5.erase(deq_5.begin(), deq_5.begin()+3); // deq_5 contains 2, 2, 1, 4, 3

// swap() - swaps the contents of deques
deq_1.swap(deq_2); // deq_1 contains 100, 100, 100, 100 and deq_2 contains 0, 0, 0, 0, 0

// clear() - delete the deque
deq_5.clear(); // deq_5 is empty

// relational
bool status;
status = (deq_3 == deq_4); // status contains 1
status = (deq_3 != deq_4); // status contains 0
status = (deq_1 < deq_2); // status contains 0, lexicographically compares elements from left

```

### Stack
A stack is a last-in-first-out container where elements are added and removed from one end only. It is similar to stack of papers where recently added is on the top and is considered the first element of stack.

```c++

// declaration and initialization
stack<int> sta; // sta is a stack variable
vector<int> vec (2,100);
stack<int, vector<int>> sta_1 (vec); // sta_1 is a copy of vec

// empty() - returns 1 if stack is empty, 0 otherwise
bool sta_empty = sta.empty(); // sta_empty contains 1

// size() - returns size of stack
int sta_size = sta_1.size(); // sta_size contains 2

// top() - returns reference to top element
int sta_top = sta_1.top(); // sta_top is 100

// push() - pushes new element from the top
sta.push(5); // sta is 5
sta_1.push(5); // sta_1 is 5, 100, 100

// pop() - removes top element
sta_1.pop(); // sta_1 is 100, 100

// swap() - swaps the contents of stacks
sta.swap(sta_1); // sta_1 is 5, sta is 100, 100

// relational
bool status;
status = (sta == sta_1); // status contains 0
status = (sta != sta_1); // status contains 1
status = (sta < sta_1); // status contains 0, lexicographically compares elements from left 

```

### Queue
A queue is a first-in-first-out container where elements are added and removed from one end only. It is similar to a line of people where person who entered first exists first.

```c++

// declaration and initialization
queue<int> que; // que is a queue variable
vector<int> vec (2,100);
queue<int, vector<int>> que_1 (vec); // que_1 is a copy of vec

// empty() - returns 1 if queue is empty, 0 otherwise
bool que_empty = que.empty(); // que_empty contains 1

// size() - returns size of queue
int que_size = que_1.size(); // que_size contains 2

// front() - returns reference to first element
int que_front = que.front(); // que_front is 100

// push() - pushes new element from the end
que.push(5); // que is 5
que_1.push(5); // que_1 is 100, 100, 5

// back() - return reference to last element
int que_back = que.back(); // que_back is 5

// pop() - removes first element
que_1.pop(); // que_1 is 100, 5

// swap() - swaps the contents of stacks
que.swap(que_1); // que_1 is 5, que is 100, 5

// relational
bool status;
status = (que == que_1); // status contains 0
status = (que != que_1); // status contains 1
status = (que < que_1); // status contains 0, lexicographically compares elements from left 
```

### Priority Queue
A priority queue is a sorted container with greatest element first by default.

```c++

// declaration and initialization
priority_queue<int> pq; // pq is a priority_queue variable
int arr[] = {3,6,4};
priority_queue<int> pq_1 (arr, arr+3); // pq_1 is a copy of arr

// empty() - returns 1 if priority_queue is empty, 0 otherwise
bool pq_empty = pq.empty(); // pq_empty contains 1

// size() - returns size of priority_queue
int pq_size = pq_1.size(); // pq_size contains 3

// top() - return reference to first element
int pq_front = pq.top(); // pq_front is 6

// push() - pushes element into priority queue
pq.push(5); // pq is 5
pq_1.push(5); // pq_1 is 6, 5, 4, 3

// pop() - removes first element
pq_1.pop(); // pq_1 is 5, 4, 3

// swap() - swaps the contents of priority queues
pq.swap(pq_1); // pq_1 is 5, pq is 5, 4, 3

// changing order to least element first
priority_queue<int, vector<int>, greater<int>> pq_2;
pq_2.push(5);
pq_2.push(3); // pq_2 is 3, 5
```