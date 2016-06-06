# Week 5 May 21st Homework

## Strings

### 5. 1.	Write an algorithm such that if an element in an MxN matrix is 0, its entire row and column are set to 0.
```
0, 1, 2,      0, 0, 0,
3, 0, 5,  =>  0, 0, 0,
6, 7, 8       0, 0, 8
```

Solutions:

```javascript
var zeroMatrix = function(matrix) {
 // Define Variable
 var rowZero, colZero;

 // zeroRow Function
 function zeroRow(row, matrix) {
   for (var i = 0; i < matrix[0].length; i++) {
     matrix[row][i] = 0;
   }
 }


 // zeroColumn Function
 function zeroColumn(col, matrix) {
   for (var j = 0; j < matrix.length; j++) {
     matrix[j][col] = 0;
   }
 }

 // Loop through the first row and column to check whether has zero elements
 for (var i = 0; i < matrix.length; i++) {
   if (matrix[i][0] === 0) {
     colZero = true;
     break;
   }
 }

 for (var j = 0; j < matrix[0].length; j++) {
   if (matrix[0][j] === 0) {
     rowZero = true;
     break;
   }
 }

 // Traverse the entire matrix to save indexed of zero value to its first row and first column
for (var i = 1; i < matrix.length; i++) {
  for (var j = 1; j < matrix[0].length; j++) {
    if (matrix[i][j] === 0 ) {
      matrix[0][j] = 0;
      matrix[i][0] = 0;
    }
  }
}

 for (var i = 1; i < matrix.length; i++) {
   if (matrix[i][0] === 0) {
     zeroRow(i, matrix);
   }
 }

 for (var j = 1; j < matrix[0].length; j++) {
   if (matrix[0][j] === 0 ) {
     zeroColumn(j, matrix);
   }
 }

 if (rowZero) {
   zeroRow(0, matrix);
 }

 if (colZero) {
   zeroColumn(0, matrix);
 }

 return matrix;

};

```

### 6. Given two sequences, print longest common subsequence LCS for input Sequences “ABCDGH” and “AEDFHR” is “ADH” of length 3. LCS for input Sequences “AGGTAB” and “GXTXAYB” is “GTAB” of length 4.

```
Input: 'ABCDGH', 'AEDFHR'
Output: 'ADH'

Input: 'AGGTAB', 'GXTXAYB'
Output: 'GTAB'

'ABCDGH'.longestCommonSub('AEDFHR'); // 'ADH'
'AGGTAB'.longestCommonSub('AXGTAB'); // 'GTAB'
```

Solutions:

1.

```javascript
String.prototype.longestCommonSub = function(str) {
  // edge case

  // define variables
  var m = this.length // row
    , n = str.length; // column
  var matrix = [];

 // set up matrix built with these two strings
  for (var i = 0; i <= m; i++) { // row m + 1
    for (var j = 0; j <= n; j++) { // column n + 1
      // set first row and first column as 0
      if (i === 0 || j === 0) {
        matrix[i,j] = 0;
      }

      // compare characters of these two strings and set values of matrix
      if (this[i - 1] === str[j - 1]) {
        matrix[i,j] = matrix[i-1,j-1] + 1;
      } else {
        matrix[i,j] = Math.max(matrix[i-1,j], matrix[i,j-1]);
      }

    }
  }

  // print out the longest common sub string
  var i = m, j = n; var lcarr = [], lcstr = '';
  while(i > 0 && j > 0) {
    if(this[i - 1] === str[j - 1]) {
      lcarr.push(this[i-1]);
      i--;
      j--;
    } else {
      if (matrix[i - 1,j] > matrix[i,j - 1]) {
        i--;
      } else {
        j--;
      }
    }
  }

  while(lcarr.length) {
    lcstr += lcarr.pop();
  }

  return lcstr;
};

```


2.
**hints**
* create two dictionary with values of their location index
* traverse the first dictionary
* use a pointer to track current location for the secondary dictionary

```javascript
String.prototype.longestCommonSub = function(str) {
  // Define Variable
  var dictionary = new Object(),
    str1 = this,
    current = 0,
    pointer = 0,
    maxLength = 0,
    commonSubStr = new String(),
    longestCommonSubStr = new String(),
    dictionary4Result = new Object();



  // traverse through first string and check whether our dictionary include this element

  while ((this.length - pointer) >= maxLength) {

    // create dictionary for second string
    for (var i = 0; i < str.length; i++) {
      if (!dictionary[str.charAt(i)]) {
        dictionary[str.charAt(i)] = [];
      }
      dictionary[str.charAt(i)].push(i);
    }

    for (var i = pointer; i < str1.length; i++) {
      if (dictionary[str1.charAt(i)]) {
        var element = dictionary[str1.charAt(i)].shift();
        if ( element >= current ) {
          current = element;
          commonSubStr += str1.charAt(i);
        }      
      }
    }
    if (commonSubStr.length >= maxLength) {
      maxLength = commonSubStr.length;
      if (!dictionary4Result[`'${maxLength}'`]) {
        dictionary4Result[`'${maxLength}'`] = [];
      }
      dictionary4Result[`'${maxLength}'`].pop() !== commonSubStr ?
        dictionary4Result[`'${maxLength}'`].push(commonSubStr) : dictionary4Result[`'${maxLength}'`].push(commonSubStr);
    }
    // reset to default value
    commonSubStr = '';
    current = 0;
    dictionary = new Object();   
    pointer += 1;
  }
  return  dictionary4Result[`'${maxLength}'`];

};

'ABCDGH'.longestCommonSub('AEDFHR'); // 'ADH'
'AGGTAB'.longestCommonSub('GXTXAYB'); // 'GTAB'

```

###8 1.	Remove spaces from a given string in O(n) running time and only one traversal of a string.

```
Input: “I     love     ice   cream”
Output: “Iloveicecream”
```

Solution 1:
```javascript
String.prototype.removeSpace = function() {
  // edge case
  if (!this) return null;

  // define variables
  var count = 0;

  // core code
  for (var i = 0; i < this.length; i++) {
    // ! below code doesn't work because string is immutable
    if (this[i] !== ' ' ) {
      this[count] = this [i]; // JavaScript String is Immutable; This code doesn't work
      count++;
    }
  }
  return this;
};
```

Solution 2:
```javascript
String.prototype.removeSpace = function() {
  // edge case
  if (!this) return null;

  // define variables
  var count = 0, str = ''; // JavaScript String is Immutable; Has to create a new string

  // core code
  for (var i = 0; i < this.length; i++) {
    if (this.charAt(i) !== ' ') {
      str += this.charAt(i);
    }
  }

  return str;
};
```
Solution 3:

```javascript
'i love icecream'.replace(,'');

```



###9 Find all distinct palindromic sub-strings of a given string

```
Input: str = "abaaa"
Output:  Below are 5 palindrome sub-strings
a
aa
aaa
aba
b
```

`Check A String is Palindrome`

```
Input: 'abba'
Output: true

Input: 'abcdcba'
Output: true

Input: 'abcca'
Output: false
```

time complexity: O(n) memory complexity: O(1)
```javascript
function isPalindromic(str) {
  // edge case
  if (!str) return null;

  // define variables
  var i = 0, j = str.length - 1;

  // core code
  while ( i < j) {
    if (str[i] !== str[j]) {
      return false;
    }
    i++;
    j--;
  }

  return true;

}

```
