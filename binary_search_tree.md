Binary Search Tree
----------------

## Insert Node Without Considering Adjusting

```javascript

var BST = function(){
  this.root = null;
}

BST.prototype.createNode = function (value) {
 var node = {};
 node.Value = value;
 node.Right= null;
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
## Traverse Binary Search Tree With Iteration

```
 2
1 3
```

### Pre Order -  Depth First

Output
```
2 1 3
```
```javascript
var PreOrderTraverse = function(root){
  var stack = [];
  stack.push(root);

  while (stack.length > 0) {
    var node = stack.pop();
    if (!node.Right || !node.Left) {
      node.Value ? console.log(node.Value) : console.log(node);
    } else {
      if (node.Right) {
        stack.push(node.Right);
      }
      if (node.Left) {
        stack.push(node.Left);
      }
      stack.push(node.Value);   
    }
  }
};
```




### In Order - Depth First

Output
```
1 2 3
```

```javascript
var InOrderTraverse = function(root) {
  var stack = [];
  stack.push(root);

  while (stack.length > 0) {
    var node = stack.pop();

    if (!node.Right || !node.Left) {
      node.Value ? console.log(node.Value) : console.log(node);
    } else {
      if (node.Right) {
        stack.push(node.Right);
      }

      if (node.Value) {
        stack.push(node.Value);
      }

      if (node.Left) {
        stack.push(node.Left);
      }
    }
  }

};
```

## Post Order - Depth First

Output
```
1 3 2
```

```javascript
var PostOrderTraverse = function(root) {
  // edge case
  if (!root) return null;

  // define variables
  var stack = [];
  stack.push(root);

  // core code
  while (stack.length > 0) {

    var node = stack.pop();
    debugger;
    if ( !node.Left || !node.Right ) {
      node.Value ? console.log(node.Value) : console.log(node);
    } else {
      stack.push(node.Value);
      if ( node.Right ) {
        stack.push(node.Right);
      }
      if ( node.Left ) {
        stack.push(node.Left);
      }
    }

  }

};
```
