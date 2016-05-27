Sort An Array
---------------

#### Method 1 Merge Sort Algorithms


**Example**
```
// divid array into half and half
[1,2,9,3,2,5,14,0]

[1,2,9,3] [2,5,14,0]

[1,2] [9,3] [2,5] [14,0]

-------
// sort each small part
[1,2] [3,9] [2,5] [0,14]

-------

//merge sorted arrays

[1,2,3,9]  [0,2,5,14]

[0,1,2,2,3,5,9,14]
-------

```

**JavaScript Code**

1. [Code From Website](https://jsfiddle.net/GRIFFnDOOR/pxu9x/)

```javascript

function mergeSort (arr) {    
    if (arr.length < 2) return arr;

    var mid = Math.floor(arr.length /2);
    var subLeft = mergeSort(arr.slice(0,mid));
    var subRight = mergeSort(arr.slice(mid));
    // value return by line 46 merge function
    // and return from line 53

    return merge(subLeft, subRight);

}

function merge (a,b) {
    var result = [];
    while (a.length >0 && b.length >0)
        result.push(a[0] < b[0]? a.shift() : b.shift());
    return result.concat(a.length? a : b);
}


mergeSort([1,2,9,3,2,5,14,0]);
// [0,1,2,2,3,5,9,14]

```

2. Code Written By Myself

```javascript
Array.prototype.sortArr = function() {

  function mergeSort(arr) {
    if(arr.length < 2) return arr;

    var mid = Math.floor(arr.length / 2);
    var leftArr = mergeSort(arr.slice(0, mid));
    var rightArr = mergeSort(arr.slice(mid));

    return merge(leftArr, rightArr);
  }

  function merge(a, b) {
    var result = [];
    while(a.length > 0 && b.length > 0)
      result.push(a[0] < b[0] ? a.shift() : b.shift());

    return a.length ? result.concat(a) : result.concat(b);
  }

  return mergeSort(this); // return to recursion function
};

[1,2,9,3,2,5,14,0].mergeSortArr();
```
#### Method 2 Quick Sort Algorithm

Most Language's sorting method is built by quick sort

```javascript

Array.prototype.quickSortArray = function() {
  // edge case
  if (this.length < 1) return this;    

  // define variable
  var array = this;

  // recursion
  var quickSort = function(array, start, end) {
    // base condition to exit execution
    if(start < end){
      var pIndex = partition(array, start, end);
      if (start < pIndex - 1) quickSort(array, start, pIndex - 1);
      if (pIndex - 1 < end) quickSort(array, pIndex + 1, end);
    }
  };

  var partition = function(array, start, end) {
    var pivot = array[end], // choose last element as pivot
    pIndex = start;

    for (var i = start; i < end; i++) {
      if (array[i] <= pivot) {
        if (pIndex !== i) swap(array, pIndex, i);
        pIndex = pIndex + 1;
      }    
    }
    swap(array, pIndex, end);
    return pIndex;
  };

  var swap = function(array, j, k) {
    var temp = array[j];
    array[j] = array[k];
    array[k] = temp;

  };

  quickSort(array, 0, array.length - 1);
  return array;
};
[1,2,9,3,2,5,14,0].quickSortArray();
```

##### (Solution from Wiki)[https://en.wikibooks.org/wiki/Algorithm_Implementation/Sorting/Quicksort#JavaScript]

```javascript
function qsort(a) {
    if (a.length <= 1) return a;
    console.log(a);

    var left = [], right = [], pivot = a[0];

    for (var i = 1; i < a.length; i++) {
        a[i] < pivot ? left.push(a[i]) : right.push(a[i]);
    }

    return qsort(left).concat(pivot, qsort(right));
}
```
