# Week 5 May 21st Homework

## Strings

### 6. Given two sequences, print longest common subsequence LCS for input Sequences “ABCDGH” and “AEDFHR” is “ADH” of length 3. LCS for input Sequences “AGGTAB” and “GXTXAYB” is “GTAB” of length 4.

```javascript
'ABCDGH'.longestCommonSub('AEDFHR'); // 'ADH'
'AGGTAB'.longestCommonSub('AXGTAB'); // 'GTAB'
```

Solutions:

#### My Solution O(2n)

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

  // create second dictionary for second string
  for (var i = 0; i < str.length; i++) {
    if (!dictionary[str.charAt(i)]) {
      dictionary[str.charAt(i)] = [];
    }
    dictionary[str.charAt(i)].push(i);
  }

  // traverse through first string and check whether our dictionary include this element

  while ((this.length - pointer) >= maxLength) {
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
