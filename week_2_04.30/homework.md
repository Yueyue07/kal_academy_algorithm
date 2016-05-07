# Week 2 Apr30th Homework

## Queue and Stack

#### 7.

Find missing parenthesis in a given expression – 2 * ( 3 + 5(sasdfasdfasd)

**hints**
* split string into an array
* use stack to pop out elements
* save "(" and ")" into two arrays: left and right;
* compare the length of these two arrays to decide the missing parenthesis


Solutions:

##### Solution 1:

O(n)

```javascript

String.prototype.missParenth = function() {
  var left = [];
  var right = [];
  for(var i = 0; i < this.length; i++) {
    if(this.charAt(i) === '(') {
      left.push(this.charAt(i));
    }  

    if(this.charAt(i) === ')') {
      right.push(this.charAt(i));
    }
  }  

  if (left.length === right.length) {
    return 'no missing parenthesis';
  }

  if (left.length > right.length) {
    return 'missing right parenthesis )';
  }

  if (left.length < right.length) {
    return 'missing left parenthesis ( '
  }
}

'-2*(3+5(sasdfasdfasd)'.missParenth();


```

#### 8.

Evaluate an expression given only single digits and only 2 operators * and +.

```
2*3+1

2+3*1
```

**hints**

* [Express Evaluation](http://www.geeksforgeeks.org/expression-evaluation/)

* [Shunting-yard algorithm](https://en.wikipedia.org/wiki/Shunting-yard_algorithm): parsing mathematical expressions specified in infix notation

* Infix Notation: 3 + 4

* Prefix Notation: + 3 4

* Postfix Notation: 3 +



Solution:

```javascript
String.prototype.expressEvalu = function() {
  var arr = this.split('');
  var operands = [];
  var operators = [];
  var value;
  for(var i = 0; i < arr.length; i++) {
    if ( 0 <= parseInt(arr[i]) <= 9 && !isNaN(parseInt(arr[i])) ) {
      operands.push(parseInt(arr[i]));
    } else {
      operators.push(arr[i]);
    }    
  }

  if(operators[0] === '*') {
    value = operands.shift() * operands.shift() + operands.shift(); //queue
  } else {
    value = operands.pop() * operands.pop() + operands.pop(); // stack
  }

  return value;
};

'2*3+4'.expressEvalu();
```




#### 9.

Reverse a stack and put the reversed value back in the same stack. You can use only one other stack and a temp variable.


**hints**
* target array is stack: [1, 2, 3] LIFO
* temporary array is stack as well
* return back to target array from temporary array: [3, 2 ,1]


Solutions (when temporary array is stack):

O(n^2)

```javascript

Array.prototype.reverseStack = function() {
  var temp = this.pop();
  var tempArr = [];
  var eleLength = 0;
  var tempArrPush = function() {
    while(this.length > eleLength) {
      tempArr.push(this.pop());
    }
    this.push(temp);
    temp = null;
    eleLength = this.length;
  }

  var tempArrPop = function() {
    while(tempArr.length > 1) {
      this.push(tempArr.pop());
    }
    temp = tempArr.pop();
  }

 tempArrPush.apply(this);

  while(tempArr.length) {
    tempArrPop.apply(this);    
    tempArrPush.apply(this);
  }
  return this;
};

[1,2,3].reverseStack();

```





Solutions (when temporary array is queue):

O(2n)

```javascript

Array.prototype.reverse = function() {
  var tempArr = [];
  var temp;

  while(this.length) {
    temp = this.pop();
    tempArr.push(temp);
  }

  while(tempArr.length) {
    temp = tempArr.shift();
    this.push(temp);
  }

  return this;

};

[1, 2, 3].reverse();
//[3, 2, 1]
```
