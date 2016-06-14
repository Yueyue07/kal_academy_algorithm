# Week 7 June 4th Class Notes

## Linked List Homework Questions

* Find the Duplicate Element in Linked List

```
  Input: head -> 4 -> 1 -> 5 -> 7 -> 1 -> 8 -> null

  Output: 1
```

Solution 1
> Use two loop to find out duplicate element time complexity: O(n^2); space complexity: null

```javascript
function duplicateElementLinkedList(head) {
  var pointer = head;
  while (pointer.next) {
    var current = pointer.next;
    while(current.next) {
      if (pointer.value === current.value) {
        return current;
      }
      current = current.next;
    }
    pointer = pointer.next;
  }

  return false;
}

// test
var LinkedList = function () {
  this.head = null;
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

// method: isEmpty, size, append, prepend, contains remove
LinkedList.prototype.isHeadEmpty = function() {
  return this.head === null;
};

var ll = new LinkedList();
ll.append(4);
ll.append(1);
ll.append(5);
ll.append(7);
ll.append(1);
ll.append(8);

duplicateElementLinkedList(ll.head);

```

Solution 2
> use dictionary to save flag of visited node.  Time complexity O(n); Space complexity O(n)

```javascript
function duplicateElementLinkedList(head) {
  var dictionary = [];
  var pointer = head;
  while(pointer) {
    var index = pointer.value;
    if (!dictionary[index]) {
      dictionary[index] = true;
    } else {
      return pointer;
    }
    pointer = pointer.next;
  }
  return false;
}
var ll = new LinkedList();
ll.append(4);
ll.append(1);
ll.append(5);
ll.append(7);
ll.append(1);
ll.append(8);

duplicateElementLinkedList(ll.head);
```

* Copy Random Pointer of Linked List

* Arithmetic Progression
