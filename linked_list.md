Linked List
--------
* Node has two properties: one is value;  another is pointer to next node

* We can only access other nodes of LinkedList through its head

**Methods of LinkedList**:

* isHeadEmpty
* size O(n)
* `append O(n)`
* `prepend O(1)`
* contains O(n)
* `remove O(n)`
* `reverse O(n)`



```
[10] -> [20] -> [30] -> null
```
```javascript
var LinkedList = function () {
  this.head = null;
};


// method: isEmpty, size, append, prepend, contains remove
LinkedList.prototype.isHeadEmpty = function() {
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

  if (this.isHeadEmpty()) {
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
    next: this.head // save old head to next
  };
  this.head = node; // point head to newly inserted head
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

/* Remove Node In LinkedList */
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
  previous.next = current.next; // connect
};

// head->1 -> 2 -> 3 ->
// 1 <- 2 <- 3 <- head

LinkedList.prototype.reverse = function() {
  // edge case
  if (!this.head) return null;
  if (!this.head.next) return this.head;

  // Define Variable
  var temp = null, current, head = this.head;

  while (head) {
    current = head;
    head = head.next;
    current.next = temp;
    temp = current;
  }

  this.head = current;
  return this.head;
};



var ll = new LinkedList();

ll.append(1);
ll.append(2);
ll.append(3);

ll.reverse();


```
