# Big O and Scalability :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

import time
"""Just because the runtime of code of someone else is faster than yours doesn't mean that
  his code is more efficient because it(runtime) also depends upon the System we are running it into.
  Big O notation is the language we use to see how long an algorithm takes to run irrespective of the
  system we are using.
  We need to see that When we grow bigger and bigger with our input, how much does the algorithm slow down.
  The SLOWER it slows down the better it is and vice versa."""

var = ['nemo', 'Dorry']
large = ['nemo' for i in range(1, 100001)]

start_time = time.time()
def find_nemo(array):
    for i in array:
        if i == 'nemo':
            print(f'found {i}')
find_nemo(large)
end_time = time.time()

print(f'total runtime: {end_time - start_time} sec')


# O(n) ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""The find_nemo function has a Big O notation of O(n) or Linear Time.
   That means when number of operations(looping here) is proportional to number of elements(items in array here)
    given to the function.(In find_nemo y is same as x and hence also proportional)
   In Big O graph y-axis is number of operation and x-axis is number of elements, and for find_nemo function
   the plot we will get is linear(hence the name Linear Time), n stands for number of input(elements) in O(n)"""

var = ['nemo', 'Dorry']
large = ['nemo' for i in range(1, 100001)]

def find_nemo(array):
    for i in array:
        if i == 'nemo':
            print(f'found {i}')
find_nemo(large)


# O(1) :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""The find_nemo2 function has a Big O notation of O(1) or Constant Time.
   That means when number of operations is same irrespective of the number of elements
    given to the function.(In find_nemo2 y = 1 irrespective of x value)
   In Big O graph for find_nemo2 function the plot will be horizontal(hence the name Constant Time)
   Even if we are doing 2(or even 100) operations we give O(1) as a notation not O(2) or O(100)."""

var = ['nemo', 'Dorry']
large = ['nemo' for i in range(1, 100001)]

def find_nemo2(array):
    if array[0] == 'nemo':
        print(f'found {array[0]}')
find_nemo2(large)


# Exercise: Big O Calculation :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

This is a .js code don't try to run this, just for Big O calculation.

// What is the Big O of the below function? (Hint, you may want to go line by line)

function funChallenge(input) {
  let a = 10;  // O(1)
  a = 50 + 3;  // O(1)

  for (let i = 0; i < input.length; i++) {  // you may or may not count the loop(i didn't)
    anotherFunction();  // O(n)
    let stranger = true;  // O(n)
    a++; // O(n)
  }
  return a; // O(1)
}
So Big O: O(3+3n), Which will be simplified to O(n) later.


---# Big O Rule 1(Worst Case) ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

everyone = ['dory', 'bruce', 'marlin', 'nemo', 'gill'
            , 'bloat', 'nigel', 'squirt', 'darla', 'hank']

"""As we can see the loop runs even after finding nemo(=+), so we use
'break' to make it efficient. But in the Worst case scenario ('nemo' at end of list)
the loop will run 10 times.
Rule 1: We always care about what is the worst case scenario because when we
talk about scalability we can't just assume things are going well.
So if 'nemo' was at first position we will get O(1) but as we said the worst
case will make it O(n)."""

def find_nemo(array):
    for i in array:
        # print('something')   # (=+)
        if i == 'nemo':
            print(f'Found {i.upper()}')
            break

find_nemo(everyone)


# Big O Rule 2(Remove Constants) :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

""" We need to drop the constants while calculating Big O:
    Big O: O(1 + n/2 + 20)
    Big O: O(n/2) [same as O(n) because no. of operation(5) is PROPORTIONAL(1/2) to inputs given(10)]
    Big O: O(n)- The notation we saw on the Graph are only Important """

lst1 = [12, 23, 35, 46, 54, 62, 77, 85, 89, 910]

def random_func(array):
    print(f"first item: {array[0]}")  # O(1)

    for i in range(len(array)//2):  # O(n/2)
        print(array[i])

    for j in range(20):  # O(20)- this loop is independent of input given
        print('Hui')

random_func(lst1)


# Big O Rule 3(Different terms for inputs) ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""If there are two different inputs then the Big O notation depends
 on the size of both of them so we need to use different term to define
 the input.
 Right: O(n + m)
 Wrong: O(2n)
        O(n) [using Rule 2 here, but still Wrong] """

box1 = [12, 23, 35, 46, 54, 62, 77, 85, 89, 910]
box2 = [2, 234, 5, 4, 354]

def boxes(box_1, box_2):
    for i in box_1:  # O(n)
        print(i)

    for j in box_2:  # O(m) because input size for this loop is different
        print(j)

boxes(box1, box2)


# O(n^2) ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""For nested loop the notation is:
   Big O: O(n*n)
   Big O: O(n^2) or Quadratic Time [operation = input^2]
   This has 'horrible' runtime.
   if 2nd loop(j) was for another input then:
   Big O: O(n*m) """

boxes = [1, 2, 3, 4, 5]

def array_pair(array):
    for i in boxes:
        for j in boxes:
            print(i, j)

array_pair(boxes)


# Big O Rule 4(Drop Non Dominants) :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""We need to drop the Non Dominant Terms from the notation:
    Non Dominant terms are those terms(operations) which increases
    SLOWLY as the inputs increases.
   Big O: O(n + n^2)
   Big O: O(n^2)--> this is the notation for below function."""

boxes = [1, 2, 3, 4, 5]

def array_pair_sum(array):
    print('These are the numbers')
    for i in array:  # O(n)
        print(i)

    print('These are pair sums')
    for i in boxes:  # O(n^2)
        for j in boxes:
            print(i+j)

array_pair_sum(boxes)


---# Exercise: Space Complexity :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""In Space Complexity we do not consider the memory taken by the input, rather
we are only concerned about the memory taken by our function to get the output.
Remember: Variables, Data Structures, Function Call and Allocations effects Space Complexity."""

"The notations below denotes Space Complexity and not Time Complexity(Big O) of the function."

def boooo(n):  # O(1) - Here we are not creating any new Variable or DS, rather changing the input
    for i in n:
        print('boooo!')

boooo([1, 2, 3, 4, 5])

def hi(n):  # O(n) - Here we created a new list and we filled it with items.
    hi_Array = []
    for i in range(n):
        hi_Array.append('Hi!')
    return hi_Array

print(hi(5))


---# Exercise: Interview Question :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""Given 2 arrays, create a function that let's a user know(True/False)
whether these two arrays contain any common items:
Sample Input 1:                     Sample Input 2:
Arr1 = ['a', 'b', 'c', 'x']         Arr1 = ['a', 'x', 'c']
Arr2 = ['z', 'y', 'i']              Arr2 = ['z', 'y', 'x']
Sample Output 1:                    Sample Output 2:
False                               True"""


# Brute force solution(not the best but which comes to mind first)
def common_items(lst1, lst2):
    for i in lst1:  # Time O: O(n*m) - nested loop
        for j in lst2:  # Space O: O(1) - no new var,ds
            if i == j:
                return True
    return False

print(common_items(['a', 'b', 'c', 'x'], ['z', 'x', 'i']))


# Improved Solution
def common_items2(lst1, lst2):
    for i in lst1:  # Time O: O(n) - 1 loop
        if i in lst2:  # Space O: O(1) - no new var,ds
            return True
    return False

print(common_items2(['a', 'b', 'c', 'x'], ['z', 'x', 'i']))


# Much Better Solution
def common_items3(lst1, lst2):  # Time O: O(n) - 1 loop
    return any([i in lst2 for i in lst1])  # Space O: O(1) - no new var,ds

print(common_items3(['a', 'b', 'c', 'x'], ['z', 'x', 'i']))


---# Exercise: Google Interview video :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""Given an arrays and an integer create a function that let's a user know(True/False)
whether the sum of any two item inside the array equals to the integer:
Sample Input 1:                     Sample Input 2:
Arr1 = [1, 2, 3, 9]                 Arr1 = [1, 2, 3, 7]
sum1 = 8                            sum2 = 5
Sample Output 1:                    Sample Output 2:
False                               True """


# Brute force solution - Time O: O(n^2), Space O: O(1)
def has_Sum(lst, total):
    for i in range(len(lst)):
        for j in range(i+1, len(lst)):
            if lst[i] + lst[j] == total:
                return True
    return False

print(has_Sum([1, 2, 3, 7], 5))

# Improved Solution- Time O: O(n), Space O: O(n)
def has_Sum2(lst, total):
    my_set = set()  # my_set = {} will make my_set a dict not a set, can't use add method then
    for i in lst:
        if i in my_set:
            return True
        my_set.add(total - i)
    return False

print(has_Sum2([1, 2, 4, 7], 5))


---# Arrays Introduction :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

string = ['a', 'b', 'c', 'd']
print(string[2])

"""If we are in a 32bit system then we need 4 shelves[each of 8bit(1 byte) which makes up to 32bit]
to store each item in the array.
hence, 4 shelves(or 4 bytes) * 4 items = 16 bytes of storage.
The computer knows exactly where each and every item is in memory."""

string.append('e')  # Big O: O(1)
print(string)

string.pop()  # Big O: O(1)
string.pop()
print(string)

string.insert(0, 'x')  # Big O: O(n) because we changed the index of every item in memory(hence more operation).
print(string)

string.insert(2, 'alien')  # Big O: O(n)
print(string)


# Static vs Dynamic Arrays ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

# Only Dynamic Array are in python
string = ['a', 'b', 'c', 'd']
print(string[2])

"""When we appended 'e', the arrays was copied and moved to different
 memory location because it is full, and then the array doubles it size(i.e, 8)
 but this does not occur frequently.
 Now when we append 'f' it has memory for it and simply add it at the end."""

string.append('e')  # Big O: O(n), because every item was copied and moved
string.append('f')  # Big O: O(1)
print(string)


# Implementing An Array ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

class MyArray:
    def __init__(self):
        self.length = 0
        self.data = {}

    def __str__(self):  # this is very important, can't use print(arr) without this
        return str(self.__dict__)

    def index(self, index):
        return self.data[index]

    def push(self, item):
        self.data[self.length] = item
        self.length += 1

    def pop(self):
        last_item = self.data[self.length - 1]
        del self.data[self.length - 1]
        self.length -= 1
        return last_item  # to get this use : print(arr.pop())

    def delete(self, index):
        delete_item = self.data[index]
        for i in range(index, self.length - 1):
            self.data[i] = self.data[i + 1]  # shifting items to the left
        del self.data[self.length - 1]
        self.length -= 1
        return delete_item


arr = MyArray()
arr.push('hi')
arr.push('how')
arr.push('are')
arr.push('you')
arr.push('!')
print(arr.index(0))

arr.pop()
print(arr)

arr.delete(2)
print(arr)
# print(arr.delete(2))  # to get removed item


---# Exercise: Reverse A String :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

# my method
def reverse(string):
    return string[::-1]

print(reverse('My name is Adil Nawaz'))

# sir's method
def reverse_1(string):
    arr = []
    for i in range(len(string) - 1, -1, -1):
        arr.append(string[i])
    return "".join(arr)

print(reverse_1('Baba Yaga'))


# Exercise: Merge Sorted Arrays :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

# my method
def merge_sort(lst_1, lst_2):
    return sorted(lst_1 + lst_2)

print(merge_sort([0, 3, 4, 31], [4, 6, 30]))

# sir's method
def merge_sort_1(lst_1, lst_2):
    merged_array = []
    i = 0
    j = 0
    """Here, 3 and 4 will not be added in merged_array because there is
       nothing to compare it with because the while loop stops as i becomes
       equal to len(lst_1).
       To remove this obstacle, we need to add all those numbers which are greater
       but cannot be compared to any number from another list.
       To do that we add lst_1[i:] + lst_2[j:] at the end with merged_array.
       Remember: This will only works if both the arrays are sorted."""
    while i < len(lst_1) and j < len(lst_2):
        # print(lst_1[i], lst_2[j])  # this part is to show how code works
        if lst_1[i] < lst_2[j]:
            merged_array.append(lst_1[i])
            i += 1
        else:
            merged_array.append(lst_2[j])
            j += 1

    return merged_array + lst_1[i:] + lst_2[j:]  # only either one will be used with merged_array

print(merge_sort_1([1, 2], [3, 4]))


---# Hash Collisions :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

def scream():
    return 'Kame Hame Haaaaa'
user = {
    'age': 42,
    'name': 'Goku',
    'magic': False,
    'power': scream()
       }
"""Lookups can be O(n) if there is a hash collision in an address.
   because we have to go for every k-v pair in the address to find the
   one k-v pair we need.
   deleting and searching in a hash table have O(1) of time complexity."""
# lookup - O(1)
print(user['name'])

# insert - O(1) (unlike array we don't need to change index)
user['spell'] = 'abra kadabra'
print(user)


# Exercise: Implement A Hash Table :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

from random import randint
class Hashtable:
    def __init__(self):  # initializing attributes
        self.my_memory = ['Nil'] * 15  # assigning 15 memory shelves
        self.address_list = []  # to get the index in which data is stored

    def __str__(self):  # very important, without this we can't print anything
        return str(self.__dict__)

    def hash(self):  # our own hash function which randomly assign address(index)
        while True:
            index = randint(0, 14)
            if index not in self.address_list:  # to avoid hash collisions
                return index

    def set(self, key, value):  # to add the k-v pair in hash table
        address = self.hash()
        self.my_memory[address] = [key, value]
        self.address_list.append(address)

    def get(self, key):  # to get the value for a specific key
        for i in self.address_list:
            if self.my_memory[i][0] == key:
                return self.my_memory[i][1]

    def keys(self):  # to show all the keys
        key_address = []
        for i in self.address_list:
            key_address.append(self.my_memory[i][0])
        return key_address

    def values(self):  # to show all the values
        value_address = []
        for i in self.address_list:
            value_address.append(self.my_memory[i][1])
        return value_address

fruit = Hashtable()
fruit.set('grapes', 35)
fruit.set('apples', 10)
fruit.set('oranges', 20)
fruit.set('bananas', 12)

print(fruit)
print(fruit.get('grapes'))

print(fruit.keys())
print(fruit.values())


---# Exercise: First Recurring Character :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""Google Interview Question:
Find the first recurring character in the array.
Sample input 1:                             Sample input 2:
[2, 5, 1, 2, 3, 5, 1, 2, 4]                 [2, 1, 1, 2, 3, 5, 1, 2, 4]
Sample Output 1:                            Sample Output 2:
2                                           1
Return 'Undefined' if no recurring characters inside the array."""

# brute force method (bonus question)
def firstRecurringCharacter(array):  # Time O(n^2)
    for i in range(len(array)):  # Space O(1)
        for j in range(i):  # the tricky part(check all the number before i and not ahead)
            if array[i] == array[j]:
                return array[i]
    return 'Undefined'

print(firstRecurringCharacter([2, 1, 1, 2, 3, 5, 1, 2, 4]))

# my method (using arrays)
def first_rec_char(array):  # Time O(n)
    sets = set()  # Space O(n)
    for i in array:
        if i not in sets:
            sets.add(i)
        elif i in sets:
            return i
    return 'Undefined'

print(first_rec_char([2, 1, 1, 2, 3, 5, 1, 2, 4]))

# Sir's method (using hash table)
def firstRecurringCharacter2(array):  # Time O(n)
    hash_map = {}  # Space O(n)
    for i in range(len(array)):
        if array[i] in hash_map.keys():
            return array[i]
        else:
            hash_map[array[i]] = i
    return 'Undefined'

print(firstRecurringCharacter2([2, 4, 1, 6, 3, 4, 1, 2, 9]))


---# What Is A Linked List? :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

basket = ['apples', 'grapes', 'mangoes']

""" Pseudo code(Working of linked lists)
apples
8967 ---> grapes
          6874 ---> mangoes
                    765 ---> null
**The numbers are memory address and ---> shows the pointer. """


# What Is A Pointer? ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

# a pointer is simply a reference to another location in memory.
obj1 = {'name': True}
obj2 = obj1  # both obj2 and obj1 points to same memory location
print(f'fist: {obj1}')
print(f'second: {obj2}')

obj1['name'] = 'Adil'  # changing the data in memory
print(f'fist: {obj1}')
print(f'second: {obj2}')

del obj1
print(f'second: {obj2}')  # I still have obj2 because it points to the memory not to obj1

"""In high level languages(python, JS) the memory is managed automatically(garbage collected)
   so we don't need to worry about the dictionary that obj2 was pointing before and it got deleted from
   memory automatically. Now obj2 is pointing at some other location which has a data type of string.
But in low level languages(C, C++) we need to manually delete the unreferenced item(dictionary here) in memory."""

obj2 = 'Rock bottom'
print(obj2)


---# Our First Linked List :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""python doesn't have a built-in linked list. So we gonna make it :-)
   10 --> 5 --> 16  (basic diagram of myLinkedList)
   'next' act as a pointer which points to the proceeding node[data('value') + pointer('next')] and so on.
   We need to make this dictionary which is basically a linked list using a class.
   The Required Output:
   myLinkedList = {
    'head': {
        'value': 10,
        'next': {
            'value': 5,
            'next': {
                'value': 16,
                'next': None
            }
        }
    }
}  """

class LinkedList:
    def __init__(self, value):
        self.head = {
            'value': value,
            'next': None
        }
        self.tail = self.head
        self.length = 1

    def __str__(self):  # very important, without this we can't print anything
        return str(self.__dict__)

    def append(self, value):  # add value at the end [O(1)]
        new_node = {
            'value': value,
            'next': None
        }
        self.tail['next'] = new_node
        self.tail = new_node
        self.length += 1
        return self.__dict__

    def prepend(self, value):  # add value at the start [O(1)]
        new_node = {
            'value': value,
            'next': self.head
        }
        self.head = new_node
        self.length += 1
        return self.__dict__

    def traverseToIndex(self, index):
        count = 0
        current_node = self.head
        while count != index:
            current_node = current_node['next']
            count += 1
        return current_node

    def insert(self, index, value):  # add value in the middle [O(n)] - TOUGH ONE
        # check params
        if index >= self.length:  # if index is large then do append automatically
            return self.append(value)
        new_node = {
            'value': value,
            'next': self.head
        }
        """-1 because we need the index(1) of that element(10)[leader] after which we have to insert the value(99)."""
        leader = self.traverseToIndex(index - 1)  # 10 --> 5 --> 16
        holding_pointer = leader['next']  # 10 -->   ...[5 --> 16] = holding_pointer
        leader['next'] = new_node  # 10 --> 99
        new_node['next'] = holding_pointer  # 10 --> 99 --> 5 --> 16
        self.length += 1
        return self.__dict__

    def remove(self, index):  # to remove an element [O(n)]
        leader = self.traverseToIndex(index - 1)  # 10 --> 99 --> 5 --> 16
        unwanted_node = leader['next']  # 10 -->  ...[99 --> 5 --> 16] = unwanted_node
        leader['next'] = unwanted_node['next']  # 10 --> 5 --> 16
        self.length -= 1
        return self.__dict__

    def printList(self):  # to get all the values in LinkedList as an array
        array = []
        current_node = self.head  # this is the value for head(key)
        while current_node is not None:
            array.append(current_node['value'])
            current_node = current_node['next']  # at the end this will become None, then loop stops
        return array

myLinkedList = LinkedList(10)
print(myLinkedList)
print("")

myLinkedList.append(5)
myLinkedList.append(16)
print(myLinkedList)
print("")

print(myLinkedList.prepend(1))
print(myLinkedList.printList())
print("")

myLinkedList.insert(2, 99)
print(myLinkedList)
print(myLinkedList.printList())
print("")

myLinkedList.remove(2)
print(myLinkedList)
print(myLinkedList.printList())


# Node class :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""This code is just to show that by using OOPs we can make our code DRY."""

class Node:  # this class is to avoid creating new node in every new method we create(DRY)
    def __init__(self, value):
        self.value = value
        self.next = None

# noinspection PyDictCreation
class LinkedList:
    def __init__(self, value):
        self.head = {
            'value': value,
            'next': None
        }
        self.tail = self.head
        self.length = 1

    def __str__(self):  # very important, without this we can't print anything
        return str(self.__dict__)

    def append(self, value):
        new_node = Node(value)
        self.tail['next'] = new_node.__dict__  # this .__dict__ is needed otherwise only address is shown
        self.tail = new_node
        self.length += 1
        return self.__dict__


myLinkedList = LinkedList(10)
print(myLinkedList)

myLinkedList.append(5)
print(myLinkedList)


# Doubly Linked List :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

class DoublyLinkedList:
    def __init__(self, value):
        self.head = {
            'value': value,
            'next': None,
            'prev': None
        }
        self.tail = self.head
        self.length = 1

    def __str__(self):  # very important, without this we can't print anything
        return str(self.__dict__)

    def append(self, value):  # add value at the end [O(1)]
        new_node = {
            'value': value,
            'next': None,
            'prev': self.tail
        }
        self.tail['next'] = new_node
        self.tail = new_node
        self.length += 1
        return self.__dict__

    def prepend(self, value):  # add value at the start [O(1)]
        new_node = {
            'value': value,
            'next': self.head,
            'prev': None
        }
        self.head['prev'] = new_node
        self.head = new_node
        self.length += 1
        return self.__dict__

    def traverseToIndex(self, index):
        count = 0
        current_node = self.head
        while count != index:
            current_node = current_node['next']
            count += 1
        return current_node

    def insert(self, index, value):  # add value in the middle [O(n)] - TOUGH ONE
        # check params
        if index >= self.length:  # if index is large then do append automatically
            return self.append(value)
        new_node = {
            'value': value,
            'next': self.head,
            'prev': None
        }
        """-1 because we need the index(1) of that element(10)[leader] after which we have to insert the value(99)."""
        leader = self.traverseToIndex(index - 1)  # 10 <--> 5 <--> 16
        follower = leader['next']  # 10 -->   ...[5 <--> 16] = follower
        leader['next'] = new_node  # 10 --> 99
        new_node['prev'] = leader  # 10 <--> 99
        new_node['next'] = follower  # 99 --> 5
        follower['prev'] = new_node  # 99 <--> 5
        self.length += 1  # 10 <--> 99 <--> 5 <--> 16 --> None
        return self.__dict__

    def remove(self, index):  # to remove an element [O(n)]
        leader = self.traverseToIndex(index - 1)  # 10 --> 99 --> 5 --> 16
        unwanted_node = leader['next']  # 10 -->  ...[99 --> 5 --> 16] = unwanted_node
        follower = unwanted_node['next']  # 99 -->  ..[5 --> 16] = follower
        leader['next'] = follower  # 10 --> 5
        follower['prev'] = leader  # 10 <--> 5
        self.length -= 1  # 10 <--> 5 <--> 16
        return self.__dict__

    def printList(self):  # to get all the values in LinkedList as an array
        array = []
        current_node = self.head  # this is the value for head(key)
        while current_node is not None:
            array.append(current_node['value'])
            current_node = current_node['next']  # at the end this will become None, then loop stops
        return array

myLinkedList = DoublyLinkedList(10)
print(myLinkedList)
print("")

myLinkedList.append(5)
myLinkedList.append(16)
print(myLinkedList)
print("")

print(myLinkedList.prepend(1))
print(myLinkedList.printList())
print("")

myLinkedList.insert(2, 99)
print(myLinkedList)
print(myLinkedList.printList())
print("")

myLinkedList.remove(2)
print(myLinkedList)
print(myLinkedList.printList())


# Exercise: Reverse a (Singly)Linked Lists:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""The working of reversing a linked list:
   actual list = [1, 10, 16, 88]
   process: 1 --> 10 --> 16 --> 88 --> None
            10 --> 1 --> 10 --> 16 --> 88 --> None
            16 --> 10 --> 1 --> 10 --> 16 --> 88 --> None
            88 --> 16 --> 10 --> 1 --> 10 --> 16 --> 88 --> None
            88 --> 16 --> 10 --> 1 --> None
   result = [88, 16, 10, 1]         """

# this is actually a method inside of LinkedList class:
def reverse(self):
    if self.length == 1:
        return self.head
    first = self.head  # first = 1 --> 10 --> 16 --> 88
    self.tail = self.head  # to make 1 as tail
    second = first['next']  # second = 10 --> 16 --> 88
    while second is not None:
        temp = second['next']  # temp = 16 --> 88
        second['next'] = first  # second['next'] = 1 --> 10 --> 16 --> 88, ie.. 10 --> 1 --> 10 --> 16 --> 88
        first = second  # first = 10 --> 1 --> 10 --> 16 --> 88
        second = temp   # second = 16 --> 88
    self.head['next'] = None  # here self.head is 1, now 1 is pointing to None
    self.head = first  # changing self.head from 1 to 88
    return self.__dict__


---# Exercise: Stack Implementation (Linked Lists) ::::::::::::::::::::::::::::::::::::::::::::::::

class Stacks:
    def __init__(self, value):
        self.top = {
            'value': value,
            'next': None
        }
        self.bottom = self.top
        self.length = 1

    def __str__(self):  # very important, without this we can't print anything
        return str(self.__dict__)

    def peek(self):
        return self.top

    def push(self, value):
        newNode = {
            'value': value,
            'next': None
        }
        holdingPointer = self.top
        self.top = newNode
        self.top['next'] = holdingPointer
        self.length += 1
        return self.__dict__

    def pop(self):
        if self.length == 1:
            self.bottom = None
        self.top = self.top['next']
        self.length -= 1
        return self.__dict__


myStacks = Stacks("Google")
print(myStacks)

myStacks.push('Udemy')
myStacks.push('Discord')
print(myStacks)

print(myStacks.peek())  # to see the data on top
myStacks.pop()
myStacks.pop()
print(myStacks)


# Exercise: Stack Implementation (Array) ::::::::::::::::::::::::::::::::::::::::::::::::

class Stacks:
    def __init__(self, value):
        self.array = [value]

    def __str__(self):  # very important, without this we can't print anything
        return str(self.__dict__)

    def peek(self):
        return self.array[-1]

    def push(self, value):
        self.array.append(value)
        return self.__dict__

    def pop(self):
        self.array.pop()
        return self.__dict__


myStacks = Stacks('Google')
print(myStacks)

myStacks.push('Udemy')
myStacks.push('Discord')
print(myStacks)

print(myStacks.peek())  # to see the data on top(last added)
myStacks.pop()
myStacks.pop()
print(myStacks)


# Exercise: Queue Implementation ::::::::::::::::::::::::::::::::::::::::::::::::::::

class Queue:
    def __init__(self, value):
        self.first = {
            'value': value,
            'next': None
        }
        self.last = self.first
        self.length = 1

    def __str__(self):  # very important, without this we can't print anything
        return str(self.__dict__)

    def peek(self):
        return self.first

    def enqueue(self, value):
        newNode = {
            'value': value,
            'next': None
        }
        self.last['next'] = newNode
        self.last = newNode
        self.length += 1
        return self.__dict__

    def dequeue(self):
        if self.length == 1:
            self.last = None
        self.first = self.first['next']
        self.length -= 1
        return self.__dict__

myQueue = Queue('Joey')
myQueue.enqueue("Matt")
myQueue.enqueue("Pavel")
myQueue.enqueue("Samir")
print(myQueue)

print(myQueue.peek())

myQueue.dequeue()
myQueue.dequeue()
print(myQueue)


---# Binary Search Trees ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""The binary Search tree model:
              9
            /  \
           4    20
         / \    / \
        1  6   15  23 """

class BinaryTree:
    def __init__(self, value):
        self.root = {
            'value': value,
            'left': None,
            'right': None
        }

    def __str__(self):  # very important, without this we can't print anything
        return str(self.__dict__['root'])

    def insert(self, value):
        new_node = {
            'value': value,
            'left': None,
            'right': None
        }
        current_node = self.root
        while True:
            if value < current_node['value']:
                # left
                if current_node['left'] is None:
                    current_node['left'] = new_node
                    return self.__dict__
                current_node = current_node['left']
            else:
                # right
                if current_node['right'] is None:
                    current_node['right'] = new_node
                    return self.__dict__
                current_node = current_node['right']

    def lookup(self, value):
        current_node = self.root
        while current_node is not None:
            if value < current_node['value']:
                current_node = current_node['left']
            elif value > current_node['value']:
                current_node = current_node['right']
            elif value == current_node['value']:
                return current_node
        return False

    def remove(self, value):   # VERY COMPLEX, Go step by step to understand
        current_node = self.root
        parent_node = None  # this is needed to connect the two node after removing the node in between
        while current_node is not None:
            if value < current_node['value']:
                parent_node = current_node
                current_node = current_node['left']
            elif value > current_node['value']:
                parent_node = current_node
                current_node = current_node['right']
            elif value == current_node['value']:
                # we have a match, get to work!

                # Option1: No child on right:
                if current_node['right'] is None:
                    # current node is root node
                    if parent_node is None:
                        self.root = current_node['left']

                    # parent > current, make current left child a child of parent
                    elif current_node['value'] < parent_node['value']:
                        parent_node['left'] = current_node['left']

                    # parent < current, make current left child a right child of parent
                    elif current_node['value'] > parent_node['value']:
                        parent_node['right'] = current_node['left']

                # Option2: have a Right child which does not have a left child:
                elif current_node['right']['left'] is None:
                    current_node['right']['left'] = current_node['left']
                    if parent_node is None:
                        self.root = current_node['left']

                    # parent > current, make current right child a left child of parent
                    elif current_node['value'] < parent_node['value']:
                        parent_node['left'] = current_node['right']

                    # parent < current, make current right child a right child of parent
                    elif current_node['value'] > parent_node['value']:
                        parent_node['right'] = current_node['right']

                # Option3: have Right child that has a left child:
                else:
                    # find the Right child's left most child
                    left_most = current_node['right']['left']
                    left_most_parent = current_node['right']
                    while left_most['left'] is not None:
                        left_most_parent = left_most
                        left_most = left_most['left']

                    # parent's left subtree is now leftmost's right subtree
                    left_most_parent['left'] = left_most['right']
                    left_most['left'] = current_node['left']
                    left_most['right'] = current_node['right']

                    if parent_node is None:
                        self.root = left_most
                    elif current_node['value'] < parent_node['value']:
                        parent_node['left'] = left_most
                    elif current_node['value'] > parent_node['value']:
                        parent_node['right'] = left_most
                return True
        return False

tree = BinaryTree(9)

# insert
tree.insert(4)
tree.insert(20)
tree.insert(1)
tree.insert(6)
tree.insert(15)
tree.insert(23)
print(tree)

# lookup
print(tree.lookup(43))  # not in the tree
print(tree.lookup(20))

# remove
print(tree)
print(tree.remove(6))
print(tree.remove(560))
print(tree)


---# Graph data ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""" There are three ways to build a Graph.
Let's take this for example:    2 -- 0
                               / \
                             1 -- 3             """

# 1. Edge List(only shows the connection)
Graph_1 = [[0, 2], [2, 3], [2, 1], [1, 3]]

# 2. Adjacent List(index of graph is value of node, and the item is the connection)
Graph_2a = [[2], [2, 3], [0, 1, 3], [1, 2]]
print(Graph_2a[2])  # shows all the connection the index value has in the graph

Graph_2b = {0: [2],
            1: [2, 3],
            2: [0, 1, 3],
            3: [1, 2]
            }
print(Graph_2b[3])  # shows all connection the key value has in the graph

# 3. Adjacent Matrix (0 means not connected, 1 means connected)
Graph_3a = [
    [0, 0, 1, 0],  # 0(index of bigger list) is connected to 2(index of sublist)
    [0, 0, 1, 1],
    [1, 1, 0, 1],
    [0, 1, 1, 0]
           ]
print(Graph_3a[0])

Graph_3b = {
    0: [0, 0, 1, 0],  # 0(key of dict) is connected to 2(index of sublist)
    1: [0, 0, 1, 1],
    2: [1, 1, 0, 1],
    3: [0, 1, 1, 0]
}
print(Graph_3a[1])


# Exercise: Graph Implementation ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""We are making an Undirected, Unweighted Graph:

                3 ----- 4 ----- 5
                |       |       |
               1 ----- 2       6
                \    /
                  0                                  """

# We are implementing it using a Hash table(dict), we can also do it using a linked list.
class Graph:
    def __init__(self):
        self.numberOfNodes = 0
        self.adjacentList = {}

    def __str__(self):  # very important, without this we can't print anything
        return str(self.__dict__)

    def add_Vertex(self, node):
        self.adjacentList[node] = []  # initially the node will not connected to something else.
        self.numberOfNodes += 1

    def add_Edge(self, node1, node2):  # to connect nodes
        # Undirected Graph
        self.adjacentList[node1].append(node2)
        self.adjacentList[node2].append(node1)

    def show_Connections(self):  # just to see how all nodes are connected
        all_Nodes = self.adjacentList.keys()
        for node in all_Nodes:
            node_connection = self.adjacentList[node]
            connections = ""
            for vertex in node_connection:
                connections += vertex + " "
            print(node + "-->" + connections)

myGraph = Graph()
myGraph.add_Vertex('0')
myGraph.add_Vertex('1')
myGraph.add_Vertex('2')
myGraph.add_Vertex('3')
myGraph.add_Vertex('4')
myGraph.add_Vertex('5')
myGraph.add_Vertex('6')

myGraph.add_Edge('3', '1')
myGraph.add_Edge('3', '4')
myGraph.add_Edge('4', '2')
myGraph.add_Edge('4', '5')
myGraph.add_Edge('1', '2')
myGraph.add_Edge('1', '0')
myGraph.add_Edge('0', '2')
myGraph.add_Edge('6', '5')

myGraph.show_Connections()


---# Anatomy of Recursion ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::;::::::::::::::::

"""Rules for Recursion:
   1. Identify the base case
   2. Identify the recursive case
   3. Get closer and closer to the base case and return when needed.
      (Usually have 2 returns, for the base and recursive case.)

   In case 1 when the return 'done' is called at the end which is inside 3 inception function
   but inception function is not returning anything hence returns None.
   inception(inception(inception(inception(inception(return 'done')))))
   inception(inception(inception(inception(None))))
   hence get None at the end. but in case two each inception function is returning the function and hence
   the return 'done' goes on till the first inception is reached and we get 'done'. """

# case 1(with no return in recursive case)
counter_1 = 0
def inception_1():
    global counter_1
    print(counter_1)  # to check why we are not getting 'done' at the end
    # base case
    if counter_1 > 3:
        return 'done'
    # recursive case
    counter_1 += 1
    inception_1()

print(inception_1())

# case 2(with return in recursive case)
counter_2 = 0
def inception_2():
    global counter_2
    print(counter_2)  # to check why we are getting 'done' at the end
    # base case
    if counter_2 > 3:
        return 'done'
    # recursive case
    counter_2 += 1
    return inception_2()

print(inception_2())


# Exercise: Factorial ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

def factorial_iterative(num):
    prod = 1
    for i in range(1, num + 1):
        prod *= i
    return prod

print(factorial_iterative(5))

def factorial_recursive(num):
    if num == 0:
        return 1
    return num * factorial_recursive(num - 1)

print(factorial_iterative(5))


# Exercise: Fibonacci ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

"""Given a number N return the index value of the Fibonacci sequence, where the sequence is:

   0,1,1,2,3,5,8,13,21,34,55,89,144 .....
   the pattern of the sequence is that each value is the sum of the 2 previous values
   that means N=5 >> 2+3 """

def fibonacci_iterative(index):  # Big O(n)
    arr = [0, 1]
    for i in range(2, index + 1):
        arr.append(arr[i-1] + arr[i-2])
        # print(arr)  # just to understand the code
    return arr[index]

print(fibonacci_iterative(8))


def fibonacci_recursive(index):  # Big O(2^n) - Exponential time(very bad)
    if index < 2:
        return index
    return fibonacci_recursive(index - 1) + fibonacci_recursive(index - 2)

print(fibonacci_recursive(8))


# string reverse using recursion :::::::::::::::::::::::::::::::::::::::::::::::::::::::

def rev_string(string):
    if len(string) == 1:
        return string
    return string[-1] + rev_string(string[:-1])

print(rev_string('Adil'))


---# Exercise: Bubble Sort :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

numbers = [99, 44, 6, 2, 1, 5, 63, 87, 283, 4, 0]

def bubble_sort(array):  # Big O: O(n^2)
    # this loop bubble out the highest number,then second highest and so on.
    for i in range(len(array)-1):
        # this loop compares 2 adjacent numbers
        for j in range(len(array)-1):
            if array[j] > array[j+1]:
                # Swap numbers
                temp = array[j]
                array[j] = array[j + 1]
                array[j + 1] = temp
    return array

print(bubble_sort(numbers))


# Exercise: Selection Sort ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

numbers = [99, 44, 6, 2, 1, 5, 63, 87, 283, 4, 0]

def selection_sort(array):
    for i in range(len(array)):
        min_index = i  # assuming the first item as min                            # min_index = 0
        temp = array[i]                                                            # temp = 99
        # we don't need the number before i
        for j in range(i+1, len(array)):
            if array[j] < array[min_index]:                                        # 44 < 99 and so on till 0.
                min_index = j                                                      # min_index = 9(index of 0)
        array[i] = array[min_index]  # swap the smallest to the least index place  # array[0] = array[9]
        array[min_index] = temp      # # swapped 0 and 99                          # array[9] = 99
    return array                                                                   # and so on.

print(selection_sort(numbers))


---# Exercise: Insertion Sort ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

numbers = [99, 44, 6, 9]

# the print statements are there to see how loop works
def insertion_sort(array):
    for i in range(1, len(array)):
        key = array[i]

        """ Move elements of array[0..i-1], that are GREATER THAN KEY, to one position ahead
         of their current position """

        j = i - 1
        while j >= 0 and key < array[j]:
            array[j + 1] = array[j]  # j + 1 is nothing but i
            # print(array)
            j -= 1  # j value will be reduced till it reaches 0
            # print(j)
        array[j + 1] = key
        # print(array)
        # print("loop restarts")
    return array

print(insertion_sort(numbers))


# Exercise: Merge Sort ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

# heads up!!!, it's a tough one (**not asked in an interview)
numbers = [99, 44, 6, 9]

def merge_Sort(array):
    if len(array) == 1:  # this is very important
        return array
    # split Array into right and left
    mid = len(array) // 2
    left = array[:mid]
    right = array[mid:]
    print(f"left split {left}, right split {right}")
    print("recursion")
    return merge(merge_Sort(left), merge_Sort(right))  # this part is also very important

# this function starts working only after splitting every item
def merge(left, right):
    result = []
    left_index = 0
    right_index = 0
    while left_index < len(left) and right_index < len(right):  # this loop is used to merge all item
        if left[left_index] < right[right_index]:
            result.append(left[left_index])
            left_index += 1
        else:
            result.append(right[right_index])
            right_index += 1
    print(left, right)
    return result + left[left_index:] + right[right_index:]

print(merge_Sort(numbers))


# Exercise: Quick Sort :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

# heads up!!!, it's a tough one (**not asked in an interview)

numbers = [99, 44, 6, 9, 10, 7]

# This function takes last element as pivot, places
# the pivot element at its correct position in sorted
# array, and places all smaller (smaller than pivot)
# to left of pivot and all greater elements to right
# of pivot

def partition(array, low, high):
    i = low - 1
    pivot = array[high]
    for j in range(low, high):
        # If current element is smaller than or
        # equal to pivot element
        if array[j] <= pivot:
            # increment index of smaller element
            i += 1
            array[i], array[j] = array[j], array[i]
    array[i + 1], array[high] = array[high], array[i + 1]
    return i + 1

# The main function that implements QuickSort
# arr[] --> Array to be sorted,
# low  --> Starting index,
# high  --> Ending index

# Function to do Quick sort

def quick_Sort(array, low, high):
    if low < high:
        # pi is partition index, array[p] is now
        # at right place
        pi = partition(array, low, high)

        # separately sort element before
        # partition and after partition
        quick_Sort(array, low, pi - 1)
        quick_Sort(array, pi + 1, high)
    return array

print(quick_Sort(numbers, 0, len(numbers) - 1))


---# Exercise: Which Sort to use? ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

# 1 - Sort 10 schools around your house by distance:
# Sol: insertion sort(small input)

# 2 - eBay sorts listings by the current Bid amount:
# Sol: radix or counting (bid is a number)

# 3 - Sport scores on ESPN
# Sol: Quick sort

# 4 - Massive database (can't fit all into memory) needs to sort through past year's user data
# Sol: Heap sort(less memory)

# 5 - Almost sorted Udemy review data needs to update and add 2 new reviews
# Sol: insertion sort (almost sorted)

# 6 - Temperature Records for the past 50 years in Canada
# Sol:  radix or counting sort[if temp in integer]
#       quick or heap sort(50 years has lot of memory)[if temp in decimal]

# 7 - Large user name database needs to be sorted. Data is very random.
# Sol: Merge, Quick or heap sort

# 8 - You want to teach sorting for the first time
# Sol: Bubble, selection sort


---# BFS vs DFS :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

# 1.If you know a solution is not far from the root of the tree:
# Sol: BFS

# 2.If the tree is very deep and solutions are rare:
# Sol: BFS (tree is very deep so DFS will take a long time)

# 3.If the tree is very wide:
# Sol: DFS (BFS tracks node in a level, hence it will take lot of memory)

# 4.If solutions are frequent but located deep in the tree:
# Sol: DFS (we need to go deep to find the solution)

# 5.Determining whether a path exists between two nodes:
# Sol: DFS

# 6.Finding the shortest path:
# Sol: BFS


# breadthFirstSearch() ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

# This is our tree from BST lecture, just added bfs and bfs_R methods.

"""The binary Search tree model:
              9
            /  \
           4    20
         / \    / \
        1  6   15  23 """

class BinaryTree:
    def __init__(self, value):
        self.root = {
            'value': value,
            'left': None,
            'right': None
        }

    def __str__(self):  # very important, without this we can't print anything
        return str(self.__dict__['root'])

    def insert(self, value):
        new_node = {
            'value': value,
            'left': None,
            'right': None
        }
        current_node = self.root
        while True:
            if value < current_node['value']:
                # left
                if current_node['left'] is None:
                    current_node['left'] = new_node
                    return self.__dict__
                current_node = current_node['left']
            else:
                # right
                if current_node['right'] is None:
                    current_node['right'] = new_node
                    return self.__dict__
                current_node = current_node['right']

    def lookup(self, value):
        current_node = self.root
        while current_node is not None:
            if value < current_node['value']:
                current_node = current_node['left']
            elif value > current_node['value']:
                current_node = current_node['right']
            elif value == current_node['value']:
                return current_node
        return False

    def remove(self, value):   # VERY COMPLEX, Go step by step to understand
        current_node = self.root
        parent_node = None  # this is needed to connect the two node after removing the node in between
        while current_node is not None:
            if value < current_node['value']:
                parent_node = current_node
                current_node = current_node['left']
            elif value > current_node['value']:
                parent_node = current_node
                current_node = current_node['right']
            elif value == current_node['value']:
                # we have a match, get to work!

                # Option1: No child on right:
                if current_node['right'] is None:
                    # current node is root node
                    if parent_node is None:
                        self.root = current_node['left']

                    # parent > current, make current left child a child of parent
                    elif current_node['value'] < parent_node['value']:
                        parent_node['left'] = current_node['left']

                    # parent < current, make current left child a right child of parent
                    elif current_node['value'] > parent_node['value']:
                        parent_node['right'] = current_node['left']

                # Option2: have a Right child which does not have a left child:
                elif current_node['right']['left'] is None:
                    current_node['right']['left'] = current_node['left']
                    if parent_node is None:
                        self.root = current_node['left']

                    # parent > current, make current right child a left child of parent
                    elif current_node['value'] < parent_node['value']:
                        parent_node['left'] = current_node['right']

                    # parent < current, make current right child a right child of parent
                    elif current_node['value'] > parent_node['value']:
                        parent_node['right'] = current_node['right']

                # Option3: have Right child that has a left child:
                else:
                    # find the Right child's left most child
                    left_most = current_node['right']['left']
                    left_most_parent = current_node['right']
                    while left_most['left'] is not None:
                        left_most_parent = left_most
                        left_most = left_most['left']

                    # parent's left subtree is now leftmost's right subtree
                    left_most_parent['left'] = left_most['right']
                    left_most['left'] = current_node['left']
                    left_most['right'] = current_node['right']

                    if parent_node is None:
                        self.root = left_most
                    elif current_node['value'] < parent_node['value']:
                        parent_node['left'] = left_most
                    elif current_node['value'] > parent_node['value']:
                        parent_node['right'] = left_most
                return True
        return False
    # main code of this lecture starts from here.

    def bfs(self):
        current_node = self.root
        array = []  # to return all node in BFS pattern
        queue = [current_node]  # to keep track
        while len(queue) > 0:
            current_node = queue[0]
            # print(current_node['value'])  # to see how code works
            queue.remove(current_node)  # first in first out, hence named it queue
            array.append(current_node['value'])
            if current_node['left'] is not None:
                queue.append(current_node['left'])
            if current_node['right'] is not None:
                queue.append(current_node['right'])
        return array

    def bfs_R(self, queue, array):  # R for recursion
        # base case
        if len(queue) == 0:
            return array
        # same code as bfs
        current_node = queue[0]
        queue.remove(current_node)
        array.append(current_node['value'])
        if current_node['left'] is not None:
            queue.append(current_node['left'])
        if current_node['right'] is not None:
            queue.append(current_node['right'])
        # applying recursion
        return self.bfs_R(queue, array)


tree = BinaryTree(9)

# insert
tree.insert(4)
tree.insert(20)
tree.insert(1)
tree.insert(6)
tree.insert(15)
tree.insert(23)
print(tree)

# breadth first search
print(tree.bfs())

# breadth first search Recursive
print(tree.bfs_R([tree.root], []))  # the argument is a gotcha! in this method

# lookup
print(tree.lookup(43))  # not in the tree
print(tree.lookup(20))

# remove
print(tree)
print(tree.remove(6))
print(tree.remove(560))
print(tree)


# depthFirstSearch() :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

# This is our tree from previous section, just added dfs_InO, dfs_PreO and dfs_postO methods.

"""The binary Search tree model:
              9
            /  \
           4    20
         / \    / \
        1  6   15  23

The number of recursion will be equal to the height of the tree in DFS."""

class BinaryTree:
    def __init__(self, value):
        self.root = {
            'value': value,
            'left': None,
            'right': None
        }

    def __str__(self):  # very important, without this we can't print anything
        return str(self.__dict__['root'])

    def insert(self, value):
        new_node = {
            'value': value,
            'left': None,
            'right': None
        }
        current_node = self.root
        while True:
            if value < current_node['value']:
                # left
                if current_node['left'] is None:
                    current_node['left'] = new_node
                    return self.__dict__
                current_node = current_node['left']
            else:
                # right
                if current_node['right'] is None:
                    current_node['right'] = new_node
                    return self.__dict__
                current_node = current_node['right']

    def lookup(self, value):
        current_node = self.root
        while current_node is not None:
            if value < current_node['value']:
                current_node = current_node['left']
            elif value > current_node['value']:
                current_node = current_node['right']
            elif value == current_node['value']:
                return current_node
        return False

    def remove(self, value):   # VERY COMPLEX, Go step by step to understand
        current_node = self.root
        parent_node = None  # this is needed to connect the two node after removing the node in between
        while current_node is not None:
            if value < current_node['value']:
                parent_node = current_node
                current_node = current_node['left']
            elif value > current_node['value']:
                parent_node = current_node
                current_node = current_node['right']
            elif value == current_node['value']:
                # we have a match, get to work!

                # Option1: No child on right:
                if current_node['right'] is None:
                    # current node is root node
                    if parent_node is None:
                        self.root = current_node['left']

                    # parent > current, make current left child a child of parent
                    elif current_node['value'] < parent_node['value']:
                        parent_node['left'] = current_node['left']

                    # parent < current, make current left child a right child of parent
                    elif current_node['value'] > parent_node['value']:
                        parent_node['right'] = current_node['left']

                # Option2: have a Right child which does not have a left child:
                elif current_node['right']['left'] is None:
                    current_node['right']['left'] = current_node['left']
                    if parent_node is None:
                        self.root = current_node['left']

                    # parent > current, make current right child a left child of parent
                    elif current_node['value'] < parent_node['value']:
                        parent_node['left'] = current_node['right']

                    # parent < current, make current right child a right child of parent
                    elif current_node['value'] > parent_node['value']:
                        parent_node['right'] = current_node['right']

                # Option3: have Right child that has a left child:
                else:
                    # find the Right child's left most child
                    left_most = current_node['right']['left']
                    left_most_parent = current_node['right']
                    while left_most['left'] is not None:
                        left_most_parent = left_most
                        left_most = left_most['left']

                    # parent's left subtree is now leftmost's right subtree
                    left_most_parent['left'] = left_most['right']
                    left_most['left'] = current_node['left']
                    left_most['right'] = current_node['right']

                    if parent_node is None:
                        self.root = left_most
                    elif current_node['value'] < parent_node['value']:
                        parent_node['left'] = left_most
                    elif current_node['value'] > parent_node['value']:
                        parent_node['right'] = left_most
                return True
        return False
    # main code of this lecture starts from here.
    # dfs_Inorder

    def dfs_InO(self):
        return self.traverse_InO(self.root, [])

    def traverse_InO(self, node, array):
        # print(node['value'])  # to see how code works
        if node['left']:  # or u can write node['left'] is not None(same thing)
            self.traverse_InO(node['left'], array)
        array.append(node['value'])  # recursion till the last left child then only add in the array
        if node['right']:
            self.traverse_InO(node['right'], array)  # recursion till the last right child
        return array

    # dfs_Preorder
    def dfs_PreO(self):
        return self.traverse_PreO(self.root, [])

    def traverse_PreO(self, node, array):
        # print(node['value'])  # to see how code works
        array.append(node['value'])  # using recursion and adding the parent node before child
        if node['left']:  # or u can write node['left'] is not None(same thing)
            self.traverse_PreO(node['left'], array)
        if node['right']:
            self.traverse_PreO(node['right'], array)  # recursion till the last right child
        return array

        # dfs_Preorder

    def dfs_PostO(self):
        return self.traverse_PostO(self.root, [])

    def traverse_PostO(self, node, array):
        # print(node['value'])  # to see how code works
        if node['left']:  # or u can write node['left'] is not None(same thing)
            self.traverse_PostO(node['left'], array)
        if node['right']:
            self.traverse_PostO(node['right'], array)  # recursion till the last right child
        array.append(node['value'])  # using recursion and adding the parent node before child
        return array


tree = BinaryTree(9)

# insert
tree.insert(4)
tree.insert(20)
tree.insert(1)
tree.insert(6)
tree.insert(15)
tree.insert(23)
print(tree)

# depth first search Inorder
print(tree.dfs_InO())

# depth first search Preorder
print(tree.dfs_PreO())

# depth first search Postorder
print(tree.dfs_PostO())

# # lookup
# print(tree.lookup(43))  # not in the tree
# print(tree.lookup(20))
#
# # remove
# print(tree)
# print(tree.remove(6))
# print(tree.remove(560))
# print(tree)


# Memoization(caching) ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

def addTo80(num):
    print("long time")  # assuming a function taking long time
    return num + 80


# running the function again and again for same input
print(addTo80(5))
print(addTo80(5))


def memoization_80():
    # we are using nested function to have this cache as local variable
    cache = {}

    def inner_memoization_80(num):
        if num in cache:
            return cache[num]
        else:
            print("long time")
            cache[num] = num + 80
            return cache[num]

    return inner_memoization_80


# we store the value and return it from cache if it is there in it
memo = memoization_80()  # we need to make a variable out of outer function to call inner function
print(memo(10))
print(memo(10))


# Fibonacci and Dynamic Programming ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

""" 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233 .....
    f - fibonacci
                          f(5)
                      /        \
                   f(4)         f(3)X
                   /  \         /  \
               f(3)  f(2)X  f(2)X  f(1)X
              /  \
           f(2)  f(1)

X means we already (calculated and)stored the value in cache so no need to do the operation."""

# fibonacci by recursion
cal_rec = 0
def recursion_fibonacci(num):
    global cal_rec
    cal_rec += 1
    if num < 2:
        return num
    return recursion_fibonacci(num - 1) + recursion_fibonacci(num - 2)

print(recursion_fibonacci(8))
print(f"calculations required = {cal_rec}")  # the time complexity is bad(O(2^n))

print("#####################################################")

# fibonacci by DP(top down approach, mostly used)
cal_dp = 0
def dynamic_fibonacci():
    cache = {}  # space complexity increases as compare to above function

    def master_fibonacci(num):
        global cal_dp
        cal_dp += 1
        if num in cache:
            return cache[num]
        else:
            if num < 2:
                return num
            else:
                cache[num] = master_fibonacci(num - 1) + master_fibonacci(num - 2)
                return cache[num]
    return master_fibonacci

dp_fib = dynamic_fibonacci()
print(dp_fib(8))
print(f"calculations required = {cal_dp}")  # the time complexity is good(O(n))












