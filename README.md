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

**Homework Array**:


1. Find the element that appears once in a **sorted array** where all other elements appear twice one after another. Find that element in O(logn) complexity.

2. A magic index in an array A[0…n-1] is defined to be an index such that A[i] = i. Given a **sorted array** of distinct integers, write a method to find a magic index if one exists, in an array A. FOLLOW UP: What if the values are not distinct?

3. Given a **sorted array** of n integers that has been rotated an unknown number of times, write code to find an element in the array. You may assume that the array was originally sorted in increasing order.

4. Given an array that contains numbers from 1 to n-1 and exactly 1 duplicate, find that duplicate.

5. Search an element in an array where difference between adjacent elements is 1.
   For example: arr[] = [8, 7, 6, 7, 6, 5, 4, 3, 2, 3, 4, 3]
   Search for 3 and Output: Found at index 7

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

**Homework Stack**:

1. Find missing parenthesis in a given expression – 2 * ( 3 + 5(sasdfasdfasd)

2. Evaluate an expression given only single digits and only 2 operators * and +.

3. Reverse a stack and put the reversed value back in the same stack. You can use only one other stack and a temp variable.

---

## Week 3 05.07


### Class Content



**Key Notes**:

1. `Array Redimension`: array hits capacity, create new array with double size, copy old array to new array and destroy old array

2. 1 bit : 1 / 0 (lowest memory); 1 byte: 8 bits

3. int: 32 bits / 4 bytes; long: 64 bits / 8 bytes

4. int[5]: array of size 160 (160 bits)

5. location_index = value % array.length; % remainder: make sure location_index < array.length

6. Handle Negative Case First

7. Dictionary O(1): 1st hasCode(key) where key is string; 2nd abs(step1); 3rd step2 % size of buckets array -> obtain the  location in buckets array to save pointer

------

**Class Example**:

Queue: enqueue; dequeue

------

**Homework String**:

1. **Implement an algorithm to determine if a string has all unique characters. What if you **cannot use additional data structures**?

2. Given two strings, write a method to decide if one is a permutation of the other?

3. **Write a method to replace all spaces in a string with ‘%20’.**



## Week 4 05.14

### Class Content
**Key Notes**
* Dictionary

------
**Homework String**:
4. Implement a method to perform a basic string compression using the counts of repeated characters. For example, the string aabccccaaa would become a2b1c4a3. If the compressed string would not become smaller than the original string, your method should return the original string.

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
**Homework String**:
5.	Write an algorithm such that if an element in an MxN matrix is 0, its entire row and column are set to 0.

6.  **Given two sequences, print longest common subsequence LCS for input Sequences “ABCDGH” and “AEDFHR” is “ADH” of length 3. LCS for input Sequences “AGGTAB” and “GXTXAYB” is “GTAB” of length 4.**

7. **Given two string str1 and str2, find the shortest string that has both str1 and str2 as subsequences.
Examples:
Input: str1 = “geek”, str2=”eke”
Output: “geeke”**

8. **Remove spaces from a given string in O(n) running time and only one traversal of a string.
Input: “I     love     ice   cream”
Output: “Iloveicecream”**

9. **Find all distinct palindromic sub-strings of a given string**

## Week 6 05.28

### Class Content

**Key Notes**:
* Linked List
* String
* Binary Tree and Binary Search Tree

------
**Homework LinkedList**:
10. Write an algorithm to determine if a linkedlist is a palindrome

11. **Write an algorithm to determine if a linkedlist is circular. FOLLOW UP: Determine where the circle meets.**

12. **Clone a linked list with a random pointer.**

13. **Write code to remove duplicates from an unsorted linked list. Follow up: How would you solve it if temporary buffer is not allowed?**

14. **Write code to remove duplicates from an unsorted linked list. Follow up: How would you solve it if temporary buffer is not allowed?**

## Week 8 06.11

**Key Notes**
* String
* String is Immutable
* String Flyweight

---
**Class Example**
1. reverse a string
2. swap two variable: with temp variable;  without temp variable
