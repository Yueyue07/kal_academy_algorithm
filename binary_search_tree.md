Binary Search Tree
----------

```javascript

var TreeNode = function(value) {
  this.value = value;
  this.left = null;
  this.right = null;
};

var BST = function() {
  this.root = null;
};

// insert node
BST.prototype.insert = function(value) {
  var newNode = new TreeNode(value);
  if(!this.root) {
    this.root = newNode;
    return this.root;
  }
  var currentNode = this.root;

  while(currentNode) {
    if (value < currentNode.value) {
      if (!currentNode.left) {
        currentNode.left = newNode;
        break;
      } else {
        currentNode = currentNode.left;
      }
    }
    if (value > currentNode.value) {
      if (!currentNode.right) {
        currentNode.right = newNode;
        break;
      } else {
        currentNode = currentNode.right;
      }
    }
  }

  return this.root;

};

```
