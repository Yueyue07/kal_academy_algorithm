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
// merge sort array
function mergeSort (arr) {    
    if (arr.length < 2) return arr;

    var mid = Math.floor(arr.length /2);
    var subLeft = mergeSort(arr.slice(0,mid));
    console.log(subLeft);
    var subRight = mergeSort(arr.slice(mid));

    merge(subLeft, subRight);
}

function merge (a,b) {
    var result = [];
    while (a.length >0 && b.length >0)
        result.push(a[0] < b[0]? a.shift() : b.shift());
    return result.concat(a.length? a : b);
}

var test = [1,2,9,3,2,5,14,0];
console.log(mergeSort(test)); // -> [0, 1, 2, 2, 3, 5, 9, 14]


```
