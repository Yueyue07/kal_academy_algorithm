# Week 6 June 1st Class Notes

## Linked List

**Key Points**
* node: consists of value and pointer
* pointer: address of next pointer and point to next node;
* head: Linked List starts with head
* add node: O(n) - to the end; O(1) - to the head; (Array: O(1)/O(n))
* find node: O(n);  (Array: O(1))
* remove node: O(n);  (Array: O(n))


**Core Logic Code**

```javascript
var current = head;
while (current !== NULL) {
  current = current.next;
}
```

**More About Linked List**
* Singly Linked List
* Doubly Linked List
* Circular Linked List


**Reverse Linked List**
* Dynamic Reverse
* Recursion Reverse


**Typical Questions about Linked List**
* Find the last Kth Element from a Linked List O(n) (`hint`: slow and fast pointers; distance between slow and fast node is (k-1) if last point ends with last node)
* Check a linked list whether it is circular O(1.5n) (`hint`: slow and fast pointers: slow speed 1node/step; fast pointer speed 2nodes/step)
* Find circular linkedlist insection point O(1.5n + k/2)


**Questions**
* merge two array
* merge two linked list

------
## String

**Key Points**
* Immutable
* hash table: key is hash code of string and value is address pointing to the array to save string
* Array used to save string
* Every time modify the string, it will create new hash code and the value is its location address

                   hash code  |  address value
                   -----------|---------------
x:'helloo' ------>    hash    |   address      ---------> ['h', 'e', 'l', 'l', 'o', 'o']
y:'helloo'


-----
## Tree

**Key**

* Linked List: head
* Tree: root
* Binary Tree: Every node has most two children

**Binary Search Tree**
* Binary Search Tree: elements in left side less than elements in right side
* Search Element: O(logn); array O(n) linked list O(n)
* Add Element: O(logn); array O(1)/O(n)  linked list O(1)/O(n)
* Remove Element: O(logn); array O(n) linked list O(n)


Traverse Binary Tree
-------
* Breadth First Search
* Depth First Search
  * preorder: root -> left -> right
  * in order: left -> root -> right (descending, ascending)
  * post order: left -> right -> root


`preorder`

```javascript
function preOrder (root) {
  if (root !== NULL) return;

  console.log(root.data);
  preorder
}
```  
