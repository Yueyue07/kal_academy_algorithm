Linked List
--------
Node has two properties: one is value;  another is pointer to next node

```
[10] -> [20] -> [30] -> null
```
```javascript
var LinkedList = function () {
  this.head = null;
}

LinkedList.prototype.isEmpty = function() {
  return this.head === null;
};

// [10] -> [20] -> [30] -> null
LinkedList.prototype.size = function() {
  var current = this.head;
  var count = 0;

  while (current) {
    count++;
    current = current.next;
  }
  return count;
};

LinkedList.prototype.append = function(value) {
  var node = {
    value: value,
    next: null
  };

  if (this.isEmpty()) {
    this.head = node;
    return;
  }

  var current = this.head;

  while (current.next) {
    current = current.next;
  }  
  current.next = node;
};

LinkedList.prototype.prepend = function(value) {
  var node = {
    value: value,
    next: this.head
  };
  this.head = node;
};

LinkedList.prototype.contains = function(value) {
  var current = this.head;

  while (current !==  null) {
    if (current.value === value) {
      return true;
    }
    current = current.next;
  }
  return false;
}

LinkedList.prototype.remove = function(value) {
  if (!this.contains(val)) {
    return;
  }

  if (this.head.value === val) {
    this.head = this.head.next;
    return;
  }

  var previous = null;
  var current = this.head;

  while (current.value !== value ) {
    previous = current;
    current = current.next;
  }
  previous.next = current.next;
};



var ll = new LinkedList();

ll.prepend(1);


```
