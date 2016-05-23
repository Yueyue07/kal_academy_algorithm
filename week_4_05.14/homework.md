# Week 4 May 14th Homework

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

1. One Solution is to create an array of boolean values, where the flag at index i indicates whether
character i in the alphabet is contained in the string.

**hints**
  * ASII code 0-255 each number represents a string
  * create an array with size of 256

time complexity: O(n)
space complexity: O(1)

```javascript
String.prototype.unique = function() {
  // negative case
  if (this.length > 256) return false;

  var arrASII = new Array(256);
  for (var i = 0; i < this.length; i++) {
    if (!arrASII[this.charCodeAt(i)]) { // flag indicate whether the element is in the string

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

2. dictionary and using JavaScript Object

```javascript
String.prototype.unique = function() {
  // define a dictionary as object with size of string length
  var dictionary = new Object();
  //loop through each character in the string
  for (var i = 0; i < this.length; i++) {
    if (!dictionary[this.charAt(i)]) {
      dictionary[this.charAt(i)] = true;
    } else {
      return false;
    }
  }
  return true;
};

'abcdef'.unique()
//true
'abbb'.unique()
//false
```

#### 2. Given two strings, write a method to decide if one is a permutation of the other?

```javascript
'abcdef'.permute('fedcab');
//true
```

Solutions:

1. Sort these two strings and then compare the each character of these two strings

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

2. using dictionary and JavaScript Object

O(3n)

```javascript
String.prototype.permute = function (string) {
  if (this.length !== string.length)  return false;

  var dictionary = new Object();
  for (var i = 0; i < this.length; i++) {
    if (!dictionary[this.charAt(i)]) { // initializing value as 1
      dictionary[this.charAt(i)] = 1;
    } else {
      dictionary[this.charAt(i)] += 1;    
    }
  }

  for (var j = 0; j < string.length; j++) {
    if (!dictionary[string.charAt(j)]) {
      return false;
    }
      dictionary[string.charAt(j)] -= 1;      
  }

  for (key in dictionary) {
    if (dictionary[key] !== 0) return false;
  }

  return true;

};
'abcdef'.permute('fedcab');
```

#### 3.Write a method to replace all spaces in a string with ‘%20’.

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


#### Solution 1 A combination of Array and String
O(3n)

```javascript

String.prototype.replace = function() {
   var strArr = this.split(''); // O(n)
    for (var i = 0; i < strArr.length; i++) { // O(n)
      if (strArr[i] === ' ') {
        strArr[i] = null;
        strArr[i] = '%20';
      }
    }
    return strArr.join(''); // O(n)
};

'a b'.replace();
// 'a%20b'

```

#### Solution 2

O(n)

```javascript
String.prototype.replace = function() {
  // initializing
  var replaceStr = new String();

  // Loop Through String and Check space
  for (var i = 0; i < this.length; i++) {
    if (this.charAt(i) === ' ') {
      replaceStr = replaceStr + '%20';
    } else {
      replaceStr = replaceStr + this.charAt(i);
    }
  }

  return replaceStr

};

'a b'.replace();

```

####4. 1.	Implement a method to perform a basic string compression using the counts of repeated characters. For example, the string aabccccaaa would become a2b1c4a3. If the compressed string would not become smaller than the original string, your method should return the original string.


#### Solution 1 Dictionary

O(n1*n2)



```javascript
String.prototype.comparison = function() {
  // Initializing
  var dictionary = new Object();
  var comparisonStr = new String();

  for (var i = 0; i < this.length; i++) {
    if (!dictionary[this.charAt(i)]) {
      dictionary[this.charAt(i)] = 1;
    } else {
      dictionary[this.charAt(i)] += 1;
    }
  }

  for (var key in dictionary) {
    comparisonStr += key + dictionary[key].toString();
  }

  return comparisonStr.length < this.length ? comparisonStr : this;
};

'aabbbbcdddd'.comparison();
// 'a2b4c1d4'
```
