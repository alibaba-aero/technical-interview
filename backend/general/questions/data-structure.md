# Data Structure

* Time complexity
  * O(1)     : Constant
  * O(logn)  : Logarithmic
  * O(n)     : linear
  * O(nlogn) : Linear Logarithmic
  * O(n^2)   : Quadratic
  * O(n^3)   : Cubic
  * O(n^k)   : Polynomial
  * O(a^n)   : Exponential
  * O(n!)
* Space complexity
* Array
  * Lookup --> O(1)
  * Insert --> O(1)
    * If need growth --> O(n)
  * Delete --> O(1)
    * If need shift items --> O(n)
* Linked-List
  * Lookup
    * By value --> O(n)
    * By index --> O(n)
  * Insertion
    * At the end --> O(n)
      * With tail node --> O(1)
    * At the beginning --> O(1)
    * In the middle --> O(n)
  * Delete
    * At the beginning --> O(1)
    * At the end
      * If we have to find the node before the last node --> O(n) else O(1)
    * In the middle --> O(n)
  * Problems
    * Find the Kth node form the end
      * hint: use two pointers with `K-1` distance
* Stack
  * All operations run in O(1)
  * Balanced Expression
* Queue
  * All operations run in O(1)
  * Implementation
    * Using a circular array with two pointers for where items to get and where to put
    * Using two stacks, one for enqueue and one for dequeue
  * Problems
    * Reverse items in a queue
      * hint: use a stack
  * Priority queue
    * Use array or heap to implement
* Hash table
  * Hash functions are deterministic
  * Use an array to store items internally
  * All operations run in O(1) unless you iterate over the values. It will be O(n)
  * Collision
    * Chaining
    * Open addressing
      * Linear probing
      * Quadratic probing
      * Double hashing
  * Problems
    * Find first non-repeated char
    * Remove duplicate items in an array or find the first repeated char
      * hint: use a *Set*
* Bubble sort
* Selection sort
  * O(n^2)
* Insertion sort
  * Like cards
  * O(n^2)
* Merge sort
  * Time --> O(nlogn)
  * Space --> O(n)
* Quick sort (definition of pivot, pros, and cons VS merge-sort)
* Linear search
  * O(n)
* Binary search
  * Implementation Types
    * Recursive
    * Iterative
  * Time --> O(logn)
  * Space complexity in case of recursive implementation --> O(logn)
  * Space complexity in case of iterative implementation --> O(1)
    * Number of recursive calls
* Binary search tree
  * The Value of any node is always greater than the left and less than the right child; on the other hand value of each
      node is greater than the left subtree and less than the right subtree
  * Lookup, Insert and Delete --> O(logn)
* Traversing a tree approaches:
  * Breadth first
    * Also called as level order
    * Visit all the nodes at the same level before visiting the nodes at the next level
  * Depth first
    * Pre-order --> Root -> Left -> Right
    * Post-order --> Left -> Right -> Root
    * In-order --> Left -> Root -> Right
      * Is in ascending order
      * If we want descending order swap the left with right --> Right -> Root -> Left
* Binary Tree Problems
  * Find the min value in Binary Tree
  * Validating a Binary Tree if it is a Binary Search Tree
  * Nodes at distance K from the root
* Balanced tree
  * Self Balancing Trees
    * AVL Tree
    * Red-Black Tree
    * B-Tree
* Heaps
  * Is a *Complete Binary Tree* that satisfies the *Heap Property*
  * Insert and Delete --> O(logn) or O(h) (h:height)
  * Because Heaps don't have holes, it is more efficient to implement them with an array
  * Heap sort
  * Priority Queue
    * With *Array* implementation, *Insert* is O(n), and _Delete_ is O(1)
    * With *Heap* implementation, *Insert* is O(logn) and *Delete* is O(logn)
  * Problems
    * Finding the Kth largest item in a list
      * hint: Use a max heap
    * Implement a heapify algorithm
      * Means transforming an array into a heap in place
* Tries
  * Also called Digital or Radix or Prefix tree
  * It's not a binary tree
  * Use Tries to implement autocomplete
  * Lookup, Insert and Delete is O(L), where _L_ is the length of the word we are searching for
  * If we want to print all the words, then use Pre-Order traversal
  * If we want to delete a word, then use Post-Order traversal
* Graphs
  * To represent connected objects
  * A tree is a kind of a graph without a cycle
  * A node is called *Vertex*
  * Adjacent or neighbor
  * Dense Graph
  * Adjacency matrix
    * Two dimensional array
    * Suitable when you know ahead of time how many nodes you need
    * Space --> O(n^2)
    * Add and Remove Node --> O(V^2) (V: vertices)
    * Add and Remove Edge --> O(1)
    * Find all the adjacent nodes of a node --> O(V)
  * Adjacency List
    * Array of Linked-List
    * Suitable if you are dealing with a Dense Graph
    * Space is O(V+E) but in the case of the Dense Graph is O(V^2)
    * Add node is O(1)
    * Remove node is O(V+E), but in the case of Dense Graph is O(V^2)
    * Add and remove edge is O(V)
    * Check to see if two nodes are connected --> O(V)
    * Find adjacent node --> O(K) or O(V)
  * Traverse
    * Depth-First
      * Start from a node and recursively visit all of its neighbors, going really deep in the graph
      * Use hashset to keep track of visited items
      * Use recursion or iteration to implement
    * Breadth-First
      * Visit a node and all its neighbors before going further from that node
      * Implement using a queue or iteration
  * Topological sort
    * Use Depth-First traversal
    * Use a stack
  * Cycle detection
  * Problems
    * Find the shortest path between two nodes
    * Show a node best friend
      * hint: by finding an adjacent with a higher weight
* String Manipulation
  * Count vowels
    * Use a for loop
  * Reverse
    * Iterate from start
    * Iterate from End
    * Use a stack
  * Reverse words in a sentence
    * Use a stack
    * Iterate from ends in words array
  * Remove Duplicates
    * Use a hashset to check whether an item is visited or not before
  * Most repeated char
    * Use a hashmap to count the visitation
    * Use `int[]` and ASCII values
      * Allocate an array with size 256 (ASCII size)
      * `int['a']++`
      * Find the max value in an array
