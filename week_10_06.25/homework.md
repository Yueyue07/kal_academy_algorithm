# week 10 June 25th Homework
## Bit Manipulation

### 1. Given an array that contains numbers from 1 to n-1 and exactly 1 duplicate, find that duplicate using bit operations.

`Example`

```
input: [6, 4, 3, 4, 2, 1, 5]
1 ~ n: [1, 2, 3, 4, 5, 6]
result: 4
```

```javascript

function duplNum (array) {
  // edge case
  if (!array.length) return null;

  // define variable
  var result = 0;

  // core code
  for (var i = 0; i < array.length; i++) {
    result = result ^ array[i];
    if (i > 0) {
      result = result ^ i;
    }
  }

  return result;
}

```
