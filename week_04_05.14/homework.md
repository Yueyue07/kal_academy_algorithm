# Week 4 May 14th Homework

## string

#### 4. Implement a method to perform a basic string compression using the counts of repeated characters. For example, the string aabccccaaa would become a2b1c4a3. If the compressed string would not become smaller than the original string, your method should return the original string.

```
Input: 'aabccccaaa'
Output: 'a2b1c4a3'

'aabccccaaa'.comparison();
'a2b1c4a3'
```

#### Solution
* for loop traverse through each character of string
* count for occurrence times:
  * if characters are equal, count = count + 1;
  * if characters are not equal, save character and count to new string; reset count = 0.
     * compare new string length with original string length. if < , continue loop
     * break loop; return original string

```javascript
String.prototype.comparison = function() {
  // edge case
  if (!this) return null;

  // define variables
  var str = '';
  var count = 1, character = this[0]; // initial values of variables

  // for loop traverse through each character
  for (var i = 1; i < this.length; i++) {
    // check loop through element equal to set character

    if (character === this[i]) { // equal
      count = count + 1;
    } else { // not equal
      // save character and count to string
      str += character + count.toString();
      // str length compare with this length

      if (str.length < this.length) { // less
        // reset
        count = 1;
        character = this[i];      
      } else { // equal or large
        
        // return original string
        return this.valueOf();
      }
    }
  }

  str += character + count.toString();

  return str.length < this.length ? str : this.valueOf();
};

'aabccccaaa'.comparison();


```      
