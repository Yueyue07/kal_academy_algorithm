# Week 8 June 11th Class Notes

## String

**Key Points**
* Immutable
* Flyweight: reuse memory
* StringBuilder

String

```                             ['H', 'e', 'l', 'l', 'o']
                                    ^
                                    |
x = 'Hello' ----->    Key: 123 | value: memory address
y = 'Hello'

y = 'hello' ----->   Key: 345  | value: new memory address
                                    |
                               ['h','e','l','l','o']
```      

**Reverse A String**

```javascript
String.prototype.reverse = function() {
  // convert string into an array
  var arrayChar = this.split('');

 // swap array elements, pass array as an argument
  function swap (array, x , y) {
    var temp = array[x];
    array[x] = array[y];
    array[y] = temp;
  }

  for (var i = 0; i < arrayChar.length/2; i++) {
    swap(arrayChar, i, arrayChar.length - 1 - i);
  }

  return arrayChar.join('');
};

'abcdef'.reverse();
```                         

## Swamp variable

```javascript
function swap(x,y) {
  x = x^y;
  y = x^y;
  x = x^y;
}

function (x,y) {
  var temp = x;
  x = y;
  y = temp
}

```
