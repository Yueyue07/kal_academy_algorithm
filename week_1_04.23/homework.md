# Week 1 Apr 23th Homework


## Array


#### 1.


Find the element that appears once in a **sorted array** where all other elements appear twice one after another. Find that element in O(logn) complexity.


```
Input: arr[] = {1, 1, 3, 3, 4, 5, 5, 7, 7, 8, 8}

Output: 4
```

Solutions:

##### Solution 1: Cut Array and Create New Array

O(logn)

**hints**
* cut the array into half: binary search;
* based on the comparison of the two values at cutting point and decide which half as target array containing element appearing once


```javascript
 // The element only appears once is always in odd position
 // In computer science the position starts from 0 instead of 1
Array.prototype.appearOne = function() {
  var target = this;

  var index1, index2, half1, half2;

  // target is the array that may contain element only appears once
  // find the cut target array with odd number of elements
  while (target.length > 1) {
    // stop computation when target only has 3 elements
    half = Math.floor(target.length / 2);
    index1 = half - 1;
    index2 = half;
    half1 =  target.slice(0, half);
    half2 = target.slice(half);
    if (half % 2 === 0){ // even index
      if (target[index1] === target[index2]){
        target = half1;
      } else {
        target = half2;
      }
    } else { // odd index
      if (target[index1] === target[index2]){
        target = half2;
      } else {
        target = half1;
      }
    }
  }
  return target;
};

[1, 1, 2, 2, 3, 4, 4].appearOne();

```

#### Solution 2: Same Array and Different Indexes
> even(first occurrence) odd(second occurrence) Target odd(first occurrence) even (second occurrence)



```javascript
Array.prototype.appearOne = function() {

  // recursion
   function search (arr, low, high) {
    // Exit Execution Condition
    if (low === high) {
      return arr[low];
    }

    // initialize variables
    var mid = (high + low) / 2;

    if (mid % 2 === 0) {
      if (arr[mid] ===  arr[mid + 1]) {
        return search(arr, mid + 2, high);
      } else {
        return search(arr, low, mid);
      }
    } else {
      if (arr[mid] === arr[mid - 1]) {
        return search(arr, mid + 1, high);
      } else {
        return search(arr, low, mid - 1);
      }
    }
  };

  // call
  return search(this, 0, this.length - 1);

};

[1, 1, 2, 2, 3, 4, 4].appearOne();

```


##### Solution 3:

O(n)

*hints*

the difference between the sum of even numbers and odd numbers

```javascript
Array.prototype.appearOne = function() {
  var oneElement = 0;
  for(var i = 0; i < this.length; i++) {
    if ((i+1) % 2 === 0) {
      oneElement += this[i];
    } else {
      oneElement -= this[i];
    }
  }
  return Math.abs(oneElement);
};

[1, 1, 2, 2, 3, 4, 4].appearOne();
// 3

```


#### 2.
A magic index in an array A[0…n-1] is defined to be an index such that A[i] = i. Given a sorted array of distinct integers, write a method to find a magic index if one exists, in an array A. FOLLOW UP: What if the values are not distinct?


Example:

distinct integers

```
  [-1, 0, 2, 3, 4]; // more than one magic indexes 2, 3, 4

  [-1, 0, 2, 4, 5]; // one magic index 2
```

**Solutions For Distinct Integers:**

*hints*
* sorted array
* distinct integers

For the algorithm will be used, it is best practice to keep same algorithm. Instead of mixing binary search with linear search. Also another import thing to remember. How to manage the trade off between efficiency and manageability of your code. Like for these questions, we you array are not distinct, we cannot stick to binary search anymore. In this case, we could use linear search instead of binary search.


##### Solution1 O(n)

```javascript

Array.prototype.magicIndex = function() {
  var magicindex = [];
  for (var i = 0; i < this.length; i++ ) {
    if(i === this[i]) {
      magicindex.push(i);
    }
  }

  return magicindex;
};

[-1,0,2,4,5].magicIndex();
// 2

```

##### Solution2 O(log n)

Example:

      [-1, 0, 2, 4, 5]
index:  0, 1, 2, 3, 4


*hints*
* left side of magic position: value < index
* right side of magic position: value > index
* magic position: value = index

`Search the first magic index`

```javascript

// Binary Search Ideas
// cannot use slice method in array since we need to play with the indexes of array.
Array.prototype.magicIndex = function() {
  var divIndex;
  var index1 = 0;
  var index2 = this.length;
  var len = index2 - index1 + 1;

  while(len > 1) {
    divIndex = Math.floor(len/ 2);
    // half1 = target.slice(0,divIndex); //cannot slice
    // half2 = target.slice(divIndex);
    if(this[divIndex-1] === (divIndex - 1)){
      return divIndex - 1;
    }
    if(this[divIndex-1] < (divIndex - 1)) {
      index1 = divIndex;
      index2 = this.length;
      len = index2 - index1 + 1;
    }
    if(this[divIndex-1] > (divIndex - 1)) {
      index1 = 0;
      index2 = divIndex - 1;
      len = index2 - index1 + 1;
    }

  }
  if (this[idex2] = index2) {
    return index2;
  }
  if (this[index1] = index1) {
    return index1;
  }

}

[-1, 0, 2, 4, 5].magicIndex();
// 2
```

**Solutions For Distinct Integers:**

linear search instead of binary search




#### 3.
Given a sorted array of n integers that has been rotated an unknown number of times, write code to find an element in the array. You may assume that the array was originally sorted in increasing order.

*hints*
* unsorted array
* cannot use binary search

##### solution O(n)

```javascript

Array.prototype.search = function(ele) {
  for(var i = 0; i < this.length; i++) {
    if (ele === this[i]) {
      return {index: i, value: this[i]};
    }
  }
}

[1, 2, 3, 4].search(2);

```

#### 4.
Given an array that contains numbers from 1 to n-1 and exactly 1 duplicate, find that duplicate.

*hints*
* 1 duplicate
* n elements and number from 1 to n-1

#### solution O(n)

```javascript

Array.prototype.duplicate = function() {
  var sum = 0;
  for(var i = 0; i < this.length; i++) {
    sum += this[i] - i;
  }
  return sum;
};

[2,1,5,4,2,3].duplicate();

```

#### 5.
Search an element in an array where difference between adjacent elements is 1.

For example: arr[] = {8, 7, 6, 7, 6, 5, 4, 3, 2, 3, 4, 3}

Search for 3 and Output: Found at index 7

##### solution O(n)

```javascript

Array.prototype.adjacOne = function(ele) {
  for(var i = 0; i < this.length; i++) {
    if(this[i] === ele && Math.abs(this[i-1] - ele) === 1) {
      if((i + 1) === this.length) {
        return i;
      }
      if(Math.abs(this[i+1] - ele) === 1) {
        return i;        
      }
    }
  }
};

[0,1,2,1,2,3].adjacOne(3);
// 5
```
##### 6.
Given an array of numbers, split the array into two where one array contains the sum of n-1 numbers and the other array with all the n-1 elements.

*hints*
* split two
* sum of n-1 numbers
* the other array with all of n-1 elements


#### solutions O(2n)

```javascript
Array.prototype.sumElement = function() {
  var sum = 0;
  for(var i = 0; i < this.length; i++) {
    sum += this[i];
  }
  var element = sum / 2;

  for(var i = 0; i < this.length; i++) {
    if(this[i] === element) {
      return element;
    }
  }
};
[6,3,4,13].sumElement();
// 13
```
