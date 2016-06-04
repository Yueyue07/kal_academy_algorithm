# Week 1 Apr 23th Class Notes

## Array

*Find Duplicated Element in Array*


**Example**

```
  [3, 1, 3, 4, 2]

  Duplicate Element: 3
```

## Solutions:


### Solution 4:

method:

> Origin array: [3, 1, 3, 4, 2]
> Numbers range: [1, 2, 3, 4]
> The last location of origin array is duplicate location
> Start from last location and switch number to their sorted location
> When switched_number is same to the number at location[switched_number -1]
> Then we find out the duplicated number.

**Assumptions**
* Only 1 Duplicate Number
* number range is from 1~(n-1), where n is the size of origin array


codes:

```javascript

  Array.prototype.duplicateNum = function(){
    var sw;
    var origin = this[this.length-1]; // start from the last element of origin origin = 2
    while(this[origin-1] !== origin) { // break when this[switch-1] = switch 3 !== 1
      sw = this[origin-1]; // switch = 3; element will be switched
      this[origin-1] = origin; //this[0] = 1; put element back to sorted location
      origin = sw; // origin = 3;
    }

    return origin;

  }

  console.log([3, 1, 3, 4, 2].duplicateNum());
  // 3
```
