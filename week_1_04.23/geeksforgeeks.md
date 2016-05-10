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
