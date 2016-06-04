# Week3 May 7th Homework

## string

#### 1. Implement an algorithm to determine if a string has all unique characters. What if you cannot use additional data structures?


Example

```javascript

 'abcdef'.unique()
 //true
 'abbb'.unique()
 //false
```

Solutions:

**hints**
  * ASII code 0-255 each number represents a string
  * create an array with size of 256

O(n)

```javascript
String.prototype.unique = function() {
  var arrASII = new Array(256);
  for (var i = 0; i < this.length; i++) {
    if (!arrASII[this.charCodeAt(i)]) {

      arrASII[this.charCodeAt(i)] = true;

    } else {

      return false;
    }
  }

  return true;
};

'abcdef'.unique()
//true
'abbb'.unique()

```

#### 2.

Given two strings, write a method to decide if one is a permutation of the other?

```javascript
'abcdef'.permute('fedcab');
//true
```

**hints**
  * sorted string


```javascript
String.prototype.permute = function(string) {
  if (string.length !== this.length) return false;

  var mergeSort = function(arr) {
    if(arr.length < 2) return arr;
    var mid = Math.floor(arr.length / 2);
    var left = mergeSort(arr.slice(0, mid));
    var right = mergeSort(arr.slice(mid));

    return merge(left, right);
  };
  var merge = function(a, b) {
    var result = [];
    while (a.length > 0 && b.length > 0) {
      if (a[0] < b[0]) {
        result.push(a.shift());
      } else {
        result.push(b.shift());
      }
    }

    return result.concat(a.length ? a : b);
  };

  var arr1 = string.split('');
  var arr2 = this.split('');
  var str1 = mergeSort(arr1).join('');
  var str2 = mergeSort(arr2).join('');
  return str1 === str2 ? true : false;
};

'abcdef'.permute('fedcab');
```  

#### 3.

Write a method to replace all spaces in a string with ‘%20’.

Example

```javascript
'a b'.replace()
//'a%20b'
```

Solutions

**hints**
  * split the string into array
  * loop through array
  * find the blank space and replace it with %20 

O(n)

```javascript

String.prototype.replace = function() {
   var strArr = this.split('');
    for (var i = 0; i < strArr.length; i++) {
      if (strArr[i] === ' ') {
        strArr[i] = null;
        strArr[i] = '%20';
      }
    }
    return strArr.join('');
};

'a b'.replace();
// 'a%20b'

```
