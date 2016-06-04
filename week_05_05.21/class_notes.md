# Week 5 May 21st Class Notes

## Sort Algorithms

**_Not Efficient Methods_**
1. Selection Sort
2. Insertion Sort
3. Bubble Sort
`O(n^2)`

**_Efficient Methods_**
4. **Merge Sort**
5. **Quick Sort**
6. Heap Sort
`O(nlogn)`


**Merge Sort**
* Runtime: O(nlogn)
* Take additional Memory to save merge array
* divide-conquer ideas

**Quick Sort**
* Average Sort Time: O(nlogn);
   * Worst Case: O(n^2): maximum number and minimum number
   * Best Case: O(n)
* All the language built by quick sort
* Won't take additional memory
* Apply Swap Idea and Track Indexes


**_ Iterative VS Recursion _**

**Iterative**
Dynamic Programming

Running Time: O(n)

`Example`

```javascript
function fib (number) {
  var value_1 = 0;
  var value_2 =1;
  for (var i = 2; i < number; i++) {
    value = value_2 + value_1;
    value_1 = value_2;
    value_2 = value;
  }
  return value;
};

fib(4) // 3
```

**Recursion**

Running Time: O(6n)
`Example`

```javascript
function fib (number) {
  if(number === 0 || number === 1) {
    return number;
  }

  return fib(number - 1) + fib(number - 2);
}

fib(4) // 3
```
