Binary Search Tree
----------

```javascript

function BinarySearchTree () {
  this.root = null;
}

// insert node
BinarySearchTree.prototype.insert = function(value) {
  var newNode = {
    value: value,
    left: null,
    right: null
  };
  console.log(value);
  if(!this.root) {
    this.root = newNode;
    return this.root;
  }
  var currentNode = this.root;

  while(currentNode) {
    if (value < currentNode.value) {
      if (!currentNode.left) {
        currentNode.left = newNode;
        return this.root;
      } else {
        currentNode = currentNode.left;
      }
    }
    if (value > currentNode.value) {
      if (!currentNode.right) {
        currentNode.right = newNode;
        return this.root;
      } else {
        currentNode = currentNode.right;
      }
    }
  }
};


var tree = new BinarySearchTree();
tree.insert(6);

```
