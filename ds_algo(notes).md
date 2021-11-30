##### Big O Asymptotic Analysis(Big O) #####

1. Good Code: Should be Readable and Scalable(Big O)

2. Big O Cheat Sheet:
   -Big Os-
   O(1) Constant- no loops
   O(log N) Logarithmic- usually searching algorithms have log n if they are sorted (Binary Search)
   O(n) Linear- for loops, while loops through n items
   O(n*log(n)) Log Linear- usually sorting operations
   O(n^2) Quadratic- every element in a collection needs to be compared to ever other element. Two
   nested loops
   O(2^n) Exponential- recursive algorithms that solves a problem of size N
   O(n!) Factorial- you are adding a loop for every element

   **Iterating through half a collection is still O(n)
   **Two separate collections: O(a * b) or O(a + b)

   -What can cause time in a function?-
   Operations (+, -, *, /)
   Comparisons (<, >, ==)
   Looping (for, while)
   Outside Function call (function())

   -Rule Book-
   Rule 1: Always worst Case
   Rule 2: Remove Constants
   Rule 3: Different inputs should have different variables. O(a+b). A and B arrays nested would be
           O(a*b)
           + for steps in order
           * for nested steps
   Rule 4: Drop Non-dominant terms

   -What causes Space complexity?-
   Variables
   Data Structures
   Function Call
   Allocations

3. Pillars of Programming:
   a) Readable
   b) Speed(Time Complexity or Big O)
   c) Memory(Space Complexity)
   ** Speed and Memory comes under Scalability.
   ** There is a trade-off between saving time and saving memory.

4. Data structure: Collection of Values.
   Algorithm: Steps to manipulate the collection og values.
   DS + Algo = Programs

5. Operations performed in Data structures:
   a) Insertion
   b) Deletion
   c) Traversal
   d) Searching
   e) Sorting
   f) Access

6. Static vs Dynamic Arrays
   In static array, we need to define the number of item the array will hold. If we need
   to add an item later then we need to copy whole array in different location in memory and add.
   This gives more control to the user. (Ex: C++)
   But On the other hand, we can resize dynamic array whenever we want and computer will automatically
   allocate the memory for it.(Ex: python, JS)

7. In an interview Question, treat string questions as an array question only.
   Example: In reverse the string: First change the string into an array, reverse the array then
   change it back to a string and return it.

8. When to use Array:
   Advantage:
   Fast Lookups, Fast push(append)/pop, it is Ordered
   Disadvantage:
   Slow inserts, slow deletes, fixed size(for static array)

9. Hash Tables
   AKA hash maps(ruby), maps(Java), ordered maps, objects(JS) and dictionaries(python)
   depending on the language used.
   In Hash Tables we get to set a key-value pair, this key has a specific index in the
   memory (which is decided by the hash function) and for this index the value is stored.

10. Hash Function
    It is a function which generates a value of fixed length for each input it gets.
    The values returned by a hash function are called hash values or simply hashes.
    These hashes are used to get an index in the memory for the key-value pair.

11. Hash Collisions
    Hash collisions occur when the hashes of any two keys coming out of hash function point out
    to the same address(index) in memory. Now we have a collision and we need to store both key-value
    pair in the same address.
    This usually happens when we have a lot of data and less spaces to store them.
    check out this link to understand better: https://www.cs.usfca.edu/~galles/visualization/OpenHash.html
    Hash collisions slows down our access to values.

12. When to use Hash Tables:
    Advantage:
    Quick Access to values(easy lookup)
    Inserting,deleting and searching is O(1) in most cases(not considering hash collision)
    Disadvantage:
    hash collision, Unordered(from python 3.9 dict are ordered)

13. Linked Lists
    A linked lists is a data structure which links one list to another.
    Inside the list has a set of node, these nodes have two elements which are the value of the
    data we want to store and a pointer(covered later in course) which points to the next node in line.
    The first node is called Head and last node is called Tail.
    Linked lists are null terminated which means the tail node will always points to null and it stops there.
    the nodes can have any sort of data type.
    Linked lists is also used as a solution for hash collision.

14. Why Linked Lists?
    linked lists are sort of loose structure that allows you to insert(or delete) a value in the middle of the list.
    By simply resetting a few pointers and we can insert anything we want just like we did in hash tables(items are not
    next to each other in memory) and the only changes that happen is somewhere in the middle and not throughout
    the list unlike array which used to shift all the item after the insertion point.
    The main difference between arrays and linked lists is that in an array the elements are indexed.
    So if we wanted to go to item at index 5 we can do that easily. But in a linked list we start at the head and
    traverse the list until you get to Item 5 which is O(n) and this idea of traversal is the same as iteration.
    We don't usually know how long the linked list is going to be unlike array.
    Array items are always located right next to each other(in memory), but in linked lists the nodes are scattered
    all over the memory. So it is slower to iterate over the items in linked list as compared to array items even though
    both process is O(n).
    The advantage linked lists has over hash table is that there is some order in link list due to pointers.

15. Pointer
    Pointer is simply a reference to another place in memory.

16. Doubly Linked Lists
    Doubly Linked Lists have two pointers in which one points to the list ahead of the data
    and the other points to all the previous list.
    5 <--> 10 <--> 2 --> null(None)
    This has an advantage when we need to traverse(iterate) our linked list backwards.
    The downside is that we need an additional memory to store the pointer which points backward.

17. Singly Vs Doubly Linked List
    Pros of SLL:
    simple implementation
    less memory
    faster operation
    Cons of SLL:
    Cannot be traversed backwards

    Pros of DLL:
    Can be traversed both from front and back
    Deleting a node is easy(we don't need to start from the head)
    Cons of DLL:
    Complex implementation
    need more memory, slower

18. When to use Linked Lists:
    Advantages:
    Fast Insertion, Fast Deletion, Ordered, Flexible Size
    Disadvantage:
    Slow Lookup, More Memory

19. Stacks and Queues
    Both Stacks and Queues are linear data structures.Linear DS allow us
    to traverse through data elements sequentially, in which only one data
    element can be directly reached.
    Both Stacks and Queues are similar to each other in terms of implementation
    and the only difference is the way data gets access from the DS.

20. Stacks
    Stack is a type of data structure in which data are 'stacked' one over the other
    like a bunch of plate.And we can only access the last data(plate on top) which was
    added in the DS. And one by one we can access the rest of the data.
    Stacks works on LIFO(Last In First Out) i.e, the last data that comes in is the first
    data which will come out and vice versa.
    Uses:
    Most Programming Languages are modelled with Stack Architecture.
    Browser history(going one by one to all the previous pages).
    lookup - O(n) {not used mostly in stacks}
    pop - O(1) {to remove the last data}
    push - O(1) {to add data on top of stack}
    peek - O(1) {to see the last added data}

21. Queues
    Queues can be imagined as an entrance to a roller coaster ride.
    It's the opposite of stacks, the first person(data) who enters gets to go
    to the roller coaster and so the next until the very last.
    Queues works on FIFO(First In First Out) i.e, the first data that comes get the
    first access.
    Uses:
    wait listing app for customer(ex uber, zomato etc)
    lookup - O(n) {not used mostly in queues}
    enqueue - O(1) {to add data at the end}
    dequeue - O(1) {to remove the first data}
    peek - O(1) {to see the first data}
    Arrays are not used to built queues because we remove data in the front
    and we have to shift all the other data as well.

22. Stacks V/s Queues
    Stacks can be implemented by either Arrays or Linked Lists based on the requirement
    we have for it.
    Queues Should only be implemented by Linked List and not by arrays(already mentioned).

23. When to use Stacks and Queues:
    Advantages:
    Fast Operations, Fast Peek, Ordered
    Disadvantage:
    Slow Lookup

24. Trees
    Trees are a type of data structure which has a hierarchical model unlike other data
    structure like arrays and linked lists which have linear ds model.
    A tree starts with a single root node and every child of the tree descends from
    this root node. A leaf node is one which is not pointing to any other node(usually present
    at the last level).
    Then there are leaf nodes which are at the very end of this data structure.
    There are subtrees inside a tree ds.
    Facebook comments work on a tree ds.(comments inside a comment)

    Technically, Linked lists is also a tree but with just one single path (linear.)
    and all the arrows always point forward and not backward in a tree.

25. Binary Tree
    Each node can only have either 0,1 or 2 Children and each child can only have 1
    parent.
               o  root node                              o
             /   \                                     /   \
            o     o                                   o     o
           / \   / \                                 / \
          o   o o   o                               o   o
                                                       / \
                                                      o   o
    Perfect Binary Tree(points to 2 nodes)       Full Binary Tree(points to 0 or 2 nodes)

    Properties of Perfect Binary Tree:
    1. A perfect binary tree doubles itself on each level unlike a full binary tree. This makes a
       PBT more efficient.
    2. The number of node on the last level(4) is equal to number of nodes on all the above level
       added 1(3 + 1).
       N_last = N_above + 1

26. Big O: O(log n)

    In layman terms:
    O(log n) is just like "looking through a phone book".
    For example: say I need to search for name Rocky, then i'll start with 'R'(root node)
    and 'R' can be pointing to multiple node(that means the second alphabet can be anything from A to Z), then we
    choose 'O'(a particular node R is pointing to) and we didn't search in any other node(alphabet) in 2nd layer
    and then go to 'C' in Third layer and so on until we find the whole name 'Rocky'.
    This has better runtime than O(n) because we are not searching through every node and removing the node
    which are not needed while searching.

    In Mathematical Terms:
    In a perfect Binary Tree there is a relation between level and nodes.
    Level 0: 2^0 = 1 node
    Level 1: 2^1 = 2 nodes
    Level 2: 2^2 = 4 nodes
    Level 3: 2^3 = 8 nodes

    Total number of nodes in a PBT = 2^steps - 1 (steps is total level in tree)
    taking log on both side(base 2):
    log nodes = steps
    hence log(n).

27. Binary Search Tree:

    It is a Binary tree with these 2 Rules:
    1. All child nodes in the tree to the right of the root node must be greater than
       the current node i.e keep going to the right and value will increase and vice versa.
       Example:        101
                     /    \
                    33    105
                   / \    / \
                  9  37 104  144
    2. A node can only have up to 2 children.(Since it's a Binary tree)

    Operations in BST:
    Lookup: O(log N)
    insert: O(log N)
    delete: O(log N)

28. Balanced VS Unbalanced BST
    In the Balanced BST, the longest path(either left or right subtree) is only one node longer/one level
    deeper than other nodes on it's comparative sibling subtree. But in the Unbalanced tree, the longest path is
    two nodes/two levels deeper than the other node on its sibling subtree.
    The Unbalanced BST can have higher time complexity in the worst case:
    Lookup: O(n)
    insert: O(n)
    delete: O(n)

29. Pros and Cons of BST:

    Pros:
    Operation better than O(n)
    Ordered
    Flexible Size

    Cons:
    No O(1) operation

30. There are few self-balancing Binary search tree which automatically get
    balanced out if one node is going more than 1 level deep, they are:
    1. AVL Tree (named after inventors Adelson-Velsky and Landis)
    Resources
    Animation: https://www.cs.usfca.edu/~galles/visualization/AVLtree.html
    How it Works: https://medium.com/basecs/the-little-avl-tree-that-could-86a3cae410c7

    2. Red/Black Tree
     Resources
     Animation: https://www.cs.usfca.edu/~galles/visualization/RedBlack.html
     How it Works: https://medium.com/basecs/painting-nodes-black-with-red-black-trees-60eacb2be9a5
     -------
     Comparison of AVL and Red/Black: https://stackoverflow.com/questions/13852870/red-black-tree-over-avl-tree

31. Binary Heap
    A binary Heap is a type of heap in which each node has exactly two child node(except the leaf nodes).
    And a heap is a type of Tree in which the value of parent node is always greater than or
    smaller than the value of child node throughout the Tree.

    A max binary heap:                                     A min binary heap:
    (parent always greater than children)                  (parent always lesser than children)
                101                                                  1
               /    \                                             /    \
              72     33                                         32      4
             / \     / \                                       / \     / \
            2  45   5   1                                     39  45  9   17

    Binary Heap is usually used where ordering is important.
    Because there is no arrangement of node in a particular level like left node is lower than right node (like in BST)
    hence we need to search every node in the heap during lookup.
    Binary heap is really good in comparative operations, for ex: finding all the number
    greater than 33 in the tree. This is easy in Binary heap but not in BST[O(n)].
    Operations in Binary Heap:
    Lookup: O(n)
    insert: O(log N)
    delete: O(log N)

32. Priority Queue
    It is a type of data in which each element has a priority, elements with higher
    priority are served before the element with lower priority unlike a normal queue in which
    first data was served first(First in First Out).
    An emergency room can be used to understand a priority queue, in which severe patient(high priority)
    are treated first and then the patients with less injury.
    A Binary Heap works on priority Queue.

33. Pros and Cons of BST:

    Pros:
    Operation better than O(n)
    Priority
    Flexible Size
    Fast insert

    Cons:
    Slow lookup

34. Trie
    A Trie is a specialised tree used in searching(mostly with text). A Trie allows us to know if
    a word or part of a word exist in a given text. Usually, a trie has an empty root node and from there
    letters are added and a parent node can have multiple children node unlike Binary Tree.
    It is used in search engine, when you type a word and it shows all the options from that word.

35. Graphs
    A Graph is simply a set of values that are related in a pair wise manner.
    In graph each item is called a node(or vertex), these nodes are connected to each other with
    edges.(both -- and | are same,i.e edges).
    Graph is really useful in real life application.
    Facebook uses it to find friends (4 is mutual fried of 5 and 6).
    Amazon uses for it's recommendation.


             6
              \
               4 -- 5
               |    |
               3 -- 2

    ** Linked List is a type of Tree and Tree is a type of Graph. So both linked list and tree comes
       under graphs.

36. Classification of Graphs

    1. Directed and Undirected Graphs
       When there is a direction for the edges it is directed and without it is undirected.

       O --> O --> O(Directed)                             O -- O -- O(Undirected)

       Directed graph is like a one way street and Undirected graph is like a highway.
       Facebook has an undirected Graph(both the friends are connected to each other).
       Instagram,Twitter has a directed Graph(I can follow someone but they may not follow me back).

    2. Weighted and Unweighted Graphs
       In a Weighted Graph, we can store information not only in the node but also in the
       edges. In an Unweighted graph only nodes carry the information.
       (5 and 9 are the data in the edges)

          5       9
       1 ---> 89 ---> 54(Weighted)                        1 ---> 89 ---> 54(Unweighted)

       Google Maps uses a Weighted Graph to find the shortest path to a destination.

    3. Cyclic and Acyclic Graphs
       A cyclic(closed) graph is one in which we can reach to the node from which we started, like
       a cycle. In an acyclic graph, we can't do that.

       4--9                                             4 -- 9
        \ |  (Cyclic)                                        |     (Acyclic)
          5                                                  5

        Cyclic Graphs are also used in Google maps, so that we can get back to the original
        destination.

37. Pros and Cons of Graphs:

    Pros:
    Relationships

    Cons:
    Scaling is hard

38. Algorithms
    Algorithms allow us to take action on the data type and data structure to create a program.
    Algorithms help us to reduce the time complexity.

39. Recursion
    Recursion is when you define something(a function) in terms of itself.
    In simple ways, a function calling itself.
    Recursion is really good for a task which has a repeated sub task to do.

40. Stack Overflow
    Stack overflow can occur when there is no way to stop a function going in recursive loop.
    We need to allocate memory every time the function calls itself and we have a limited memory, hence this
    is one of the drawbacks of recursion.

41. Big O - O(2^n)
    The other drawback of a recursive function is it's time complexity
    which is O(2^n), and that is pretty bad.
    This is a layout of recursive fibonacci function of 5. as we can see the the function
    calls itself multiple times. and as the number increases the operation increases exponentially
    (if f(6) needs to be calculated both f(5) tree and f(4) tree will come under it).

                 Structure:                    Function:
                       f(5)                def fibonacci_recursive(index):
                      /   \                    if index < 2:
                   f(4)    f(3)                    return index
                   /  \     /  \               return fibonacci_recursive(index - 1) + fibonacci_recursive(index - 2)
               f(3)  f(2)  f(2)  f(1)
              /  \                         print(fibonacci_recursive(5))
           f(2)  f(1)

42. Recursive VS Iterative
    "Anything you do with a recursion CAN be done iteratively(loop)", this is an actual theory.
    then why we need recursion??
    Rule: Use Recursion when you don't know how deep a data structure is, like in a tree or
    a graph.

    Pros:
    DRY
    Readable

    Cons:
    Large Stack due to repeatable function call(stack overflow can happen).

43. When To Use Recursion
    Every time you are using a tree or converting Something into a tree, consider recursion.
    Use recursion when you see these patterns in a problem:
    1. When the problem is divided into a number of sub problem that are small instances
       of the same problem.
    2. Each instance of the sub problem is identical in nature.
    3. The solutions of each sub problem can be combined to solve the problem at hand.
    Divide and Conquer using Recursion.

    Specifically Recursion is used in:
    1. Merge Sort
    2. Quick Sort
    3. Tree Traversal
    4. Graph Traversal

44. Sorting Introduction
    Why we need sorting when there is a .sort() method in most languages???
    The problem arrives when the input gets larger and larger(like in a company)
    then we need custom sorted methods based on the data.

45. Bubble Sort
    In this type of sorting algorithm web bubble up the highest value at the end, and again
    go from the beginning to bubble up the 2nd highest value and so on(underscore shows selected value).
    Ex:   _4_, _2_, 7, 5  first take 4 and 2 and swap
          2, _4_, _7_, 5  then move to next value(i.e 7)
          2, 4, _7_, _5_  and again go from beginning(if list is not sorted)
          2, 4, 5, 7  (we did not start from the beginning again, cause list got sorted)

    The time complexity of bubble sort is usually O(n^2), which is bad.
    Space Complexity is O(1), really good.

46. Selection Sort
    This algorithm works by scanning a list for the smallest element and swapping it with the first
    item in the list. And then the second smallest to the 2nd place in list and so on.
    Ex:  4, 7, 2, _0_  find smallest and swap it to first
         0, 7, _2_, 4  then 2nd smallest to 2nd place
         0, 2, 7, _4_  and so on.
         0, ,2, 4, 7

    The time complexity of selection sort is O(n^2), which is bad.
    Space Complexity is O(1), really good.

47. Insertion Sort
    Insertion sort is really helpful when we know that the given data input is almost sorted.Insertion sort
    works by scanning all the previous item in a data and fit a particular data where it is needed.
    (underscore shows all the items each loop has access to.)
    Ex:  _4_, 7, 2, 5
         _4_, _7_, 2, 5
         _2_,_4_ , _7_, 5  # when loop reaches 2, it was smaller than 4 hence placed it there.
         _2_, ,_4_, _5_, _7_  # when loop reaches 5 it was in b/w 4 and 7 hence placed it there.

    The time complexity of selection sort is O(n^2), which is bad.
    Space Complexity is O(1), really good.

48. Merge Sort and O(n log n)
    Merge sort works on the principle of divide and conquer(log n), it breaks down the input data into
    half and half again till we have every single data separated.
    then compare each item and make a small sorted block out of it. then again we compare each item
    in one block to other sorted block and make it bigger and bigger until we get the whole input sorted.
    [9,5,8,3,2,0,1,6]
    9,       5,       8,       3,       2,       0,       1,       6
       5,9               3,8               0,2                1,6
             3,5,8,9                               0,1,2,6
                            0,1,2,3,5,6,8,9

    It is like going back in a tree, we are reaching closer and closer to the root node(sorted array).
    Merge sort has better time complexity than most of the other sorting algorithm.
    It has a Big O of O(n log n). The n comes because after breaking down the data to single input
    we need to operate in every item to make a small sorted blocks, hence n.
    The space complexity is O(n).
    Merge sort is not usually asked in interview because the implementation is tough.

50. Quick Sort
    Quick sort is the fastest sorting algorithm on an average. It also works on the principle of
    divide and conquer(log n). In this method, we pick a RANDOM pivot element from the array and any value
    lower than pivot element will go to it's(pivot element) left and any value higher will go to it's
    right. then we take the array of left and right and again use pivot element until the complete array
    is sorted.(underscore is pivot element)
    ** DO NOT TAKE THE HIGHEST OR LOWEST VALUE AS PIVOT ELEMENT(time complexity will be O(n^2))

                            [9, 7, 12, 3, 2, 0, 1, _6_]
                            [1, 7, 12, 3, 2, 0, _6_, 9]  # 1(left of pivot) goes to 9, 9 goes to 6 and 6 goes to 1
                            [1, 0, 12, 3, 2, _6_, 7, 9]  # 0(left of pivot) goes to 7, 7 goes to 6 and 6 goes to 0
                            [1, 0, 2, 3, _6_, 12, 7, 9]  # 2(left of pivot) goes to 12, 12 goes to 6 and 6 goes to 2
        [1, _0_, 2, 3]               [6]                [12, 7, _9_]
        [_0_, 1, 2, 3] (swapped)      |                [7, _9_, 12]  # 7 to 12, 12 to 9 and 9 to 7
                   \                  |                   /
                    \                 |                  /
                     \                |                 /
                           [0, 1, 2, 3, 6, 7, 9, 12]



    The space complexity of Quick sort is O(log n) and time complexity is O(n log n)(on an average).
    Quick sort is not usually asked in interview because the implementation is tough.

51. Which Sort Is Best?
    1. Insertion sort is good when input is small or input is almost sorted.
    2. Bubble sort is only used for education purposes(to get the basics of sorting),
       it's not very efficient.
    3. Same goes for selection sort as with bubble sort.
    4. Merge sort is really good because of divide and conquer. It's time complexity is
       O(n log n) even in the worst case(i.e IT'S FAST). Hence if you worry about the worst
       case then use this. Not good for less memory(space complexity is O(n)).
    5. Quick sort has the same average time complexity as merge sort(O(n log n)), and on top of that
       it has better space complexity(O(log n)) than Merge sort. Hence it's the best
       on an average(mostly used). But the worst case of Time Complexity is bad(O(n^2)) in this sort.

52. Non-Comparison Sort
    All the above sorting algorithm comes under Comparison sort, which means
    we are comparing each item to other items while sorting. Mathematically, Comparison
    sort can have O(n log n) as the best time complexity.

    But there are Non-Comparison Sort and those are:
      1. Counting Sort
      2. Radix Sort
    Remember that these Non-Comparison sorting algorithm only works with
    numbers(specifically integers) in a restricted range.
    These Sorting algorithm uses the way that numbers and data are stored in our
    computer(in 0s and 1s) to sort, hence these are really fast.

53. Sorting in your language
    Python uses Tim Sort which is the combination of merge sort and insertion sort. It
    performs well in real world data.

54. Searching/Traversal
    We use searching everyday in our computer and online hence this topic is very
    important for interview.

55. Linear search
    aka sequential search is a method in which it sequentially check each element in the
    list until a match is found. For loop is an example of linear search, the best time complexity
    can be O(1) [first item is a match] or in general it is O(n).

56. Binary Search
    If the input data is SORTED then we can use binary search(works on divide and conquer).
    Here, we make a binary search tree out of the sorted input. By taking the middle value in every
    level.(Remember: child < parent then child goes to left node and vice versa)

    Ex: Input: [1, 4, 6, 9, 12, 34, 45]
    take middle:                                   9
    then take middle(from left                   /   \
    and right of root node):                    4     34
    then if can't find middle                 /  \    /  \
    put both as child:                       1    6  12   45
    Now, if we search for 12, then we know 12 > 9 so it will be on right node side.
    we goes to 34, then 12<34 so left node hence we found 12. We don't need to search
    every node in the tree.
    ***Remember storing items in a tree is more efficient than a array.
    ***We covered Binary search in BST lookup method(GO BACK).

57. Graph + Tree Traversal
    There are times when we need to go to every single node in the tree(Ex: if we wanna multiply 2 to
    every node value), then we uses tree traversal.
    There are two ways to traverse in a Tree or Graph.
    The tree may not be BST.

58. Breadth First Search (As wide as possible)
    As the name suggest we search by breath of the tree. That means in a particular level of the tree, we goes
    from left to right completely, then goes to next level and again do the same thing until we searched all the
    node in the tree.
    It has a Time Complexity of O(n), since we are searching every node.
                       9        (btw this tree is Binary Tree not BST)
                    /     \
                   6       12
                  /  \    /  \
                 1    4  34   45
    BFS: 9 -> 6 -> 12 -> 1 -> 4 -> 34 -> 45
    BSF output: [9, 6, 12, 1, 4, 34, 45]
    BFS has a higher memory requirement(we need to keep tack of all node's children in a level).

59. Depth First Search (As deep as possible)
    As the name suggest we search by depth of the tree. That means we search a branch of the tree
    down to it's last node then goes back to the parent node and search for other children.
    It has a Time Complexity of O(n), since we are searching every node.
                       9        (btw this tree is Binary Tree not BST)
                    /     \
                   6       12
                  /  \    /  \
                 1    4  34   45
    DFS: 9 -> 6 -> 1 -> 6(goes back) -> 4 -> 9(Goes back) -> 12 -> 34 ->12(Goes back) -> 45
    DSF output: [9, 6, 1, 4, 12, 34, 45]
    DFS has a lower memory requirement.

60. BFS v/s DFS
    Pros of BFS:
    To find Shortest Path(from source to target)
    Closer Nodes
    Good if we know the target is in higher level of tree
    Cons of BFS:
    More Memory

    Pros of DFS:
    Less Memory
    To find whether path exist?(from source to target)
    Good if we know the target is in lower level of tree
    Cons of DFS:
    Can Get Slow

61. Implementation of BFS and DFS

                       9   (it's a BST)
                    /     \
                   4       34
                  /  \    /  \
                 1    6  12   45

    BFS algorithm can be implemented in two ways:
    1. Using (while)loop
    2. Using Recursion

    The output of both the method is same.
    Output: [9, 4, 34, 1, 6, 12, 45]

    DFS algorithm can be implemented in three ways:
    1. Inorder: Here we go all the way down to the left of the tree and then
                starts counting the node comes back to parent then goes to another child
                of the parent and so on. The output is inorder(sorted).
                **Really useful for a BST.
                Output: [1, 4, 6, 9, 12, 34, 45]
    2. Preorder: Here we start of with parent and grab the child node from left to
                 right.
                 **Really useful if we want to recreate a tree.
                 Output: [9, 4, 1, 6, 34, 12, 45]
                 9 is root, 4 is 9 child(it's lower than 9), 1 is 4 child, 6 is also 4 child
                 but to the right(higher than 4), then 34 is 9 child(since 4 has all child), then
                 12 and 45 are 34 child.
    3. Postorder: Here we go all the way down to the left of the tree and then
                  starts counting the nodes from left to right of the same parent then goes back
                  to parent and do the same thing.
                  Output: [1, 6, 4, 12, 45, 34, 9]


61. Graph Traversal
    We use the same algorithm(bfs and dfs) for graphs as well. The only difference is each node will have
    multiple children and not just 2.
    ** U can solve a MAZE by dfs(it checks the depth so it's good for that)
    check how BFS and DFS works in graph: https://visualgo.net/en/dfsbfs

62. Dijkstra + Bellman-Ford Algorithms
    These algorithm are used to find the shortest path in a Graph.
    bfs is fast but it assumes that all edges(of the graph) has same weight.
    Ex: we have 2 roads(edges) to go from A(source vertex) to B(target vertex), BFS will assume that
        both road has the same amount of traffic(weight). But Dijkstra and Bellman-Ford algorithms
        will consider the traffic in those two roads and tell us where the traffic is less
        hence we reach B faster as compare to BFS.
    Bellman-Ford is faster than Dijkstra algorithm in finding shortest path because it can accommodate
    negative weight as well. But Dijkstra algorithm has better time complexity(runtime) hence it is preferred
    if there is no negative weight in the graph.

63. Dynamic Programming Introduction
    It is just an optimization technique using caching, so if we have some data
    that we can cache, then we can use dynamic programming. It works by breaking down
    a problem into a collection of sub problem and solving each of these sub problem once and
    storing there solution.

64. Memoization(caching)
    Caching is a way to store values so that we can use it later on. Memoization
    is a specific form of caching that involves caching the returned value of a function
    based on it's parameter, if the parameter remains same then it is memoized(stored in cache).

65. Dynamic Programming
    Dynamic programming = divide and conquer + memoization
    To check whether we can use DP in a problem:
    1. Can be divided into sub problems
    2. Recursive solution
    3. **Are there repetitive sub problems?
    4. Memoize sub problems
    5. Demand a raise from your boss

66. For non technical part:
    Re watch the section 16 before an interview.
    Remember some points while watching section 16:
    **Write down the answers for every question
    Leadership and Challenge story: Burnout, Transmission workshop 2019 story
    **Standing out is the key
    Biggest Weakness - whenever I face a (personal or professional)problem i directly start giving the solution without
                       thinking too much but lately I started thinking through the problem and comes with the best
                       solution I can have.
    Handling Rejection - those rejection doesn't even count, that one time you got accepted is what counts.










