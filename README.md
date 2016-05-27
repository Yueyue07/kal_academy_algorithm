# Kal Academy - Data Structures and Algorithms


## Week 1 04.23


### Class Content



**Key Notes**:

1. Big O : efficiency running time

2. O(1), O(logn), O(n), O(nlogn), O(n^2), ... , O(n^n), where n is size of data

3.  Always consider worst case in terms of Big O

------

**Class Example**:

Find the duplicate elements in the array

------

**Homework**:

1. Find the element that appears once in a **sorted array** where all other elements appear twice one after another. Find that element in O(logn) complexity.

2. A magic index in an array A[0…n-1] is defined to be an index such that A[i] = i. Given a sorted array of distinct integers, write a method to find a magic index if one exists, in an array A. FOLLOW UP: What if the values are not distinct?

3. Given a sorted array of n integers that has been rotated an unknown number of times, write code to find an element in the array. You may assume that the array was originally sorted in increasing order.

4. Given an array that contains numbers from 1 to n-1 and exactly 1 duplicate, find that duplicate.

5. Search an element in an array where difference between adjacent elements is 1.

6. Given an array of numbers, split the array into two where one array contains the sum of n-1 numbers and the other array with all the n-1 elements.

---

## Week 2 04.30


### Class Content



**Key Notes**:

1. Binary Search: `only work for sorted array`

2. Efficient and Manageable Code (trade-off) `find more than one magic index, considering linear search`

3. Always stick to one pattern of structure and algorithm

4. Queue (FIFO)

5. Stack (LIFO)

------

**Class Example**:

Work on Last Week's homework

------

**Homework**:

1. Find missing parenthesis in a given expression – 2 * ( 3 + 5(sasdfasdfasd)

2. Evaluate an expression given only single digits and only 2 operators * and +.

3. Reverse a stack and put the reversed value back in the same stack. You can use only one other stack and a temp variable.

---

## Week 3 05.07


### Class Content



**Key Notes**:

1. `Array Redimension`: array hits capacity, create new array with double size, copy old array to new array and destroy old array

2. 1 bit : 1 / 0 (lowest memory); 1 byte: 8 bits

3. int: 32 bits / 8 bytes; long: 64 bits / 8 bytes

4. int[5]: array of size 160 (160 bits)

5. location_index = value % array.length; % remainder: make sure location_index < array.length

6. Handle Negative Case First

7. Dictionary O(1): 1st hasCode(key) where key is string; 2nd abs(step1); 3rd step2 % size of buckets array -> obtain the  location in buckets array to save pointer

------

**Class Example**:

Queue: enqueue; dequeue

------

## Week 5 05.21


### Class Content

**Key Notes**:

1. Array Sort Algorithms
   * Inefficient Sort Methods O(n^2): selection sort, insertion sort, bubble sort

   * Efficient Sort: O(nlogn)
      * Merge Sort

      * Quick Sort

      * Heap Sort

2. Merge Sort VS Quick Sort
    * Merge Sort: Running time always O(nlogn); Require extra space
    * Quick Sort: Average Running time: O(nlogn); Worst Running time: O(n^2) (max and min value as pivot); Don't need extra space

3. Dynamic Programming VS Recursion


----
**Class Example**:

Merge Sort; Quick Sort; fib(n) Dynamic programming; fib(n) Recursion

------
