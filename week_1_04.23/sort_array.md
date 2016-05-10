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

  return mergeSort(this);
};

[1,2,9,3,2,5,14,0].sortArr();
```
