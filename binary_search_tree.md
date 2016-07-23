Binary Search Tree
----------------

Insert Node Without Considering Adjusting

```javascript

var BST = function(){
  this.root = null;
}

BST.prototype.createNode = function (value) {
 var node = {};
 node.Value = value;
 node.Right = null;
 node.Left = null;

 return node;
};

BST.prototype.insertNode = function(value) {

  if(!this.root)
    return this.root = this.createNode(value);

  var current = this.root, temp, parent;


  while (current)
  {
     if (current.Value < value) {
       parent = current;
       current = parent.Right;
     } else {
       parent = current;
       current = parent.Left;
     }
  }

  if (parent.Value < value) {
    parent.Right = this.createNode(value);
  } else {
    parent.Left = this.createNode(value);
  }

  return this.createNode(value);

};
```

-------
Traverse Binary Search Tree Depth-First: **PreOrder**

```javascript


```

Traverse Tree
--------------

## In Order - Depth First

```javascript
var InOrderProcess = function(root) {
  var stack = [];
  stack.push(root);

  while (stack.length > 0) {
    var node = stack.pop();

    if (!node.right || !node.left) {
      node.value ? console.log(node.value) : console.log(node);
    } else {
      if (node.right) {
        stack.push(node.right);
      }

      if (node.value) {
        stack.push(node.value);
      }

      if (node.left) {
        stack.push(node.left);
      }
    }
  }

}


```
