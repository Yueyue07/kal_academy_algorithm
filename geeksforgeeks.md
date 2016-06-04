Array Exercise from geeks for geeks
-----------

###1. Given an array A[] of n numbers and another number x, determine whether or not there exist two elements in A whose sum is exactly x.

**Example**

```javascript
// given number 14
// given array A [3,4,2,6,8,9]

[3,4,2,6,8,9].twoValuExist(14) // true
```

**hints**
* sorted array
* initialized left index: l; right index: r;
* Loop while l < r
  * array[l] + array[r] === num
  * array[l] + array[r] < numb
  * array[l] + array[r] > numb

 **solution**

```javascript

Array.prototype.twoValuExist = function(num) {
  // merge sort array

  function mergeSort (arr) {    
    if (arr.length < 2) return arr;

    var mid = Math.floor(arr.length /2);
    var subLeft = mergeSort(arr.slice(0,mid));
    var subRight = mergeSort(arr.slice(mid));

    return merge(subLeft, subRight);
  }

  function merge (a,b) {
    var result = [];
    while (a.length >0 && b.length >0)
    result.push(a[0] < b[0]? a.shift() : b.shift());
    return result.concat(a.length? a : b);
  }

  var sortArr = mergeSort(this);
  console.log(sortArr);

  function valuesExist(sortArr, num) {
    var li = 0;
    var ri = sortArr.length - 1;
    while (li < ri) {
      if (sortArr[li] + sortArr[ri] === num) {
        return {'true': [ sortArr[ li ], sortArr[ ri ] ]};
      }
      if (sortArr[li] + sortArr[ri] < num) {
        li = li + 1;
      }
      if (sortArr[li] + sortArr[ri] > num) {
        ri = ri - 1;
      }
    }

    return 'There are not these two values exist';
  }

  return valuesExist(sortArr, num);
};



[3,4,2,6,8,9].twoValuExist(14)
```

###2. Majority Element: A majority element in an array A[] of size n is an element that appears more than n/2 times (and hence there is at most one such element).

**Example**
```javascript
[3, 4, 3, 2, 4, 4, 2, 4, 4].majorEle();
//majority element 4
```

*hint*

Moore’s Voting Algorithm

* if find element is same, count++
* if find element is differ, count--
* when count ==== 0 , then point move to this location

**Solution**

```javascript
Array.prototype.majorEle = function() {
  var pointer = 0,
    count = 1;
  for (var i = 1; i < this.length; i++) {
    if (this[i] === this[pointer]) {
      count++;
    } else {
      count--;
    }

    if(count === 0) {
      pointer = i;
      count = 1;
    }
  }

  return this[pointer];  
};

[3, 3, 4, 2, 4, 4, 2, 4, 4].majorEle();
```

####3. Given an array of positive integers. All numbers occur even number of times except one number which occurs odd number of times. Find the number in O(n) time & constant space.

**Example**
```javascript
[1, 2, 3, 2, 3, 1, 3].findOddEle();
// 3
```

*hints*

* hash table element from arr[] as index of result[], which is key
* counts of occurrence of element is value
* find the value with odd numbers occurrence in result array
* Best Solution: XOR


XOR of all the elements. XOR of all elements gives us odd occurring element. Please note that XOR of two elements is 0 if both elements are same and XOR of a number x with 0 is x.

**Solution**

My Solution O(2n)

```javascript

Array.prototype.findOddEle = function() {
  var result = [];
  var index;
  var ele;
  for(var i = 0; i < this.length; i++) {
    index = this[i];
    if (!result[index]) {
      result[index] = 1;
    } else {
      result[index] = result[index] + 1;    
    }

    if (result[index] % 2 === 0) {
       result[index] = 0;
    }
  }
  for (var j = 0; j < result.length; j++) {
    if (result[j]) {
      return j;
    }  
  }    
};

[1,1,2,4,4].findOddEle();
// 2
```

Solution From [GeeksForGeeks](http://www.geeksforgeeks.org/find-the-number-occurring-odd-number-of-times/)

```javascript
Array.prototype.findOddEle = function() {
  var result = 0;
  for(var i = 0; i < this.length; i++) {
    result = result^this[i];
  }
  return result;
};

[1,1,2,4,4].findOddEle();
// 2
```
