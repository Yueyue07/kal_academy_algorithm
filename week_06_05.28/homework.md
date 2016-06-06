# Week 6 June 1st Homework

## LinkedList

### 10. Write an algorithm to determine if a linkedlist is a palindrome

`Example`

```
1 -> 2 -> 3 -> 4 -> 3 -> 2 -> 1
s    s    s    s
f         f          f        f
4 -> 6 -> 5 -> 5 -> 6 -> 4
s    s    s    s
f         f         f         f
```

**Solution 1 (using stack)**
* use slow(1 node) and fast(2 nodes) pointers
* save slow pointing node into stack until fast point to the end
* pop stack element to compare with slow pointing node value

```javascript

function isLLPalindrome (ll) {
  // edge case
  if (!ll.head) return null;

  // define variables
  var slow = ll.head;
  var fast = ll.head;
  var stack = [];

  // core code
  while(fast.next) {
    stack.push(slow);
    slow = slow.next;
    fast = fast.next.next;
  }

  console.log(slow);
  console.log(fast);

  // when no. of node is odd value, slow will move over mid node  
  if (fast) {
    slow = slow.next;
  }
  console.log(slow);

  while (slow) {
    if (slow.value !== stack.pop().value) {
      return false;
    }
    slow = slow.next;
  }

  return true;

}
```

**Solution 2(reverse linked list)**

### 11. Write an algorithm to determine if a linked list is circular. FOLLOW UP: Determine where the circle meets.

```
input: 1 -> 2 -> 3 ->4 -> 5 -> 6
                     |         |
                     9 <- 8 <- 7
```

**hints**
* slow pointer
* fast pointer

```javascript
function isCircularLinkedList(head) {
  // edge case
  if(!head || !head.next) return null;

  // define variables
  var slow = head.next, fast = head.next.next;

  // core code
  while(fast) {
    if (slow === head) return true;
    slow = slow.next;
    fast = fast.next.next;
  }
  return false;
}

function isCircularLinkedList(head) {
  // edge case
  if(!head || !head.next) return null;

  // define variables
  var slow = head.next, fast = head.next.next;

  // core code
  while(fast) {
    if (slow === head) return true;
    slow = slow.next;
    fast = fast.next.next;
  }
  return false;
}

```


### 12. Clone a linked list with a random pointer.

``


### 13. Write code to remove duplicates from an unsorted linked list. Follow up: How would you solve it if temporary buffer is not allowed?


### 14. 1.	Implement an algorithm to find the kth to the last element of a singly linked list

**Solution 1 Dynamic Programming**
* slow starts with head
* fast starts with kth node
* loop through fast and slow nodes
* each moves to next node

O(n) O(1)

```javascript
function lastKthNode(ll, k) {
  // edge case
  if (!ll.head) return null;

  // define variables
  var slow = ll.head;

  function kthFast(k, slow) {
    var count = 1, fast = slow.next;

    while(count < (k - 1)){
      fast = fast.next;
      count = count + 1;
    }
    return fast;
  }

  var fast = kthFast(k, slow);
  // core code'
  while(fast.next) {
    slow = slow.next;
    fast = fast.next
  }

  return slow;
}
```
