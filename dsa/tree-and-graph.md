# Tree and Graph

> A binary search tree is a binary tree with left descendants less than root and right descendants greater than root.

## Table of Contents

- [Implementing a Binary Tree](#implementing-a-binary-tree)
- [Insert in a Binary Tree](#insert-in-a-binary-tree)
- [Remove a node in a Binary Tree](#remove-a-node-in-a-binary-tree)
- [Traversal of Tree](#traversal-of-tree)
- [DFS & BFS in Tree](#dfs--bfs-in-tree)
- [Depth/Height of a Tree](#depthheight-of-a-tree)
- [Implementing Graph in JS](#implementing-graph-in-js)
- [DFS & BFS in Graph](#dfs--bfs-in-graph)

## Implementing a Binary Tree

```
class Node{
    constructor(value){
        this.value = value;
        this.left = null;
        this.right = null;
    }
}

class BinaryTree{
    constructor(){
        this.root = null;
    }
}
```

## Insert in a Binary Tree

```
 insert(value){
    let newNode = new Node(value);
    if(this.root === null){
        this.root = newNode;
    } else {
        let currentNode = this.root;
        let parentNode = this.root;
        while(currentNode !== null){
            parentNode = currentNode;
            if(value > currentNode.value){
                currentNode = currentNode.right;
            } else{
                currentNode = currentNode.left;
            }
        }

        if(value > parentNode.value){
            parentNode.right = newNode;
        } else{
            parentNode.left = newNode;
        }
    }
}
```

## Remove a node in a Binary Tree

```
remove(value){
    this.root = this.removeNode(this.root, value);
}

removeNode(node, value){
    if(node === null){
      return null;
    } else if(node.value < value){
        node.right = this.removeNode(node.right, value);
        return node;
    } else if(node.value > value){
        node.left = this.removeNode(node.left, value);
        return node;
    } else{
        if(node.left === null && node.right === null){
            node = null;
            return node;
        }

        if(node.left === null){
            node = node.right;
            return node;
        } else if(node.right === null){
            node = node.left;
            return node;
        }
        let minNode =  this.findMinNode(node.right);
        node.value = minNode.value;
        node.right = this.removeNode(node.right, minNode.value);
        return node;
    }
}
```

_Helper Function_

```
findMinNode(node){
  	let currentNode = node;
    let parentNode = node;
    while(currentNode !== null){
    	parentNode =  currentNode;
      currentNode = currentNode.left;
    }
    return parentNode;
}
```

```
findParentNode(value){
    let currentNode = this.root;
    let parentNode = this.root;
    if(this.root === null || value === parentNode.value){
      return null;
    }
    while(currentNode !== null){
    	parentNode = currentNode;
      if(parentNode.left.value === value || parentNode.right.value === value){
      	return parentNode;
      }
      if(value > currentNode.value){
      	currentNode = currentNode.right;
      } else{
      	currentNode = currentNode.left;
      }
    }
    return null;
}
```

```
findParentNodeRec(value){
    return this.findAboveNode(this.root, value);
  }

findAboveNode(node, value){
    if(node === null){
        return null;
    }
    if(node.left.value === value || node.right.value === value){
        return node;
    }
    if(value > node.value){
        return this.findAboveNode(node.right, value);
    } else if(value < node.value){
        return this.findAboveNode(node.left, value);
    } else{
        return false;
    }
}

```

```
 findNode(value){
  	if(this.root.value === value){
    	return this.root;
    } else{
      let parentNode = this.findParentNode(value);
      if(parentNode === null ){
        return false;
      } else {
        if(parentNode.left.value === value){
          return parentNode.left;
        } else {
          return parentNode.right;
        }
      }
    }
}
```

```
let t = new BinaryTree();
t.insert(8);
t.insert(3);
t.insert(10);
t.insert(1);
t.insert(6);
t.insert(13);
t.insert(4);
t.insert(7);
let testNode = new Node(8);
console.log(t.findParentNode(7)); // 6
```

## Traversal of Tree

**Inorder Traversal**

```
let result = [];
function inoderTraversal(root){
  if(root !== null){
    inoderTraversal(root.left);
    result.push(root.value);
    inoderTraversal(root.right);
  }
}

inoderTraversal(t.root);
console.log(result);
```

**Preorder Traversal**

```
let result = [];
function preorderTraversal(root){
  if(root !== null){
    result.push(root.value);
    preorderTraversal(root.left);
    preorderTraversal(root.right);
  }
}
preorderTraversal(t.root);
console.log(result);
```

**Postorder Traversal**

```
let result = [];
function postorderTraversal(root){
  if(root !== null){
  	postorderTraversal(root.left);
    postorderTraversal(root.right);
    result.push(root.value);
  }
}
postorderTraversal(t.root);
console.log(result);
```

## DFS & BFS in Tree

> Use a queue to implement BFS & stack to implement DFS

**Depth First Search**

```
function DFS(root){
	if(root === null){
    return root;
  }

  let stack = [];
  let result = [];
  stack.push(root);
  while(stack.length > 0){
  	let currentNode = stack.pop();
    if(currentNode.right !== null){
      stack.push(currentNode.right);
    }
    if(currentNode.left !== null){
      stack.push(currentNode.left);
    }

    result.push(currentNode.value);
  }
  console.log(result);
}

DFS(t.root);
```

**Breadth First Search**

```
function BFS(root){
	if(root === null){
  	return null;
  }
  let queue = [];
  let result = [];
  queue.push(root);

  while(queue.length > 0){
  	let currentNode = queue.shift();

    if(currentNode.left !== null){
    	queue.push(currentNode.left);
    }
    if(currentNode.right !== null){
    	queue.push(currentNode.right);
    }
    result.push(currentNode.value);
  }
	console.log(result);
}

BFS(t.root);
```

## Depth/Height of a Tree

```
function findDepth(node){
   if(node === null){
  	return 0;
  } else{
   return Math.max(findDepth(node.left), findDepth(node.right)) + 1;
  }
}
```

## Implementing Graph in JS

```
class Graph{
	constructor(noOfVertices){
  	this.noOfVertices = noOfVertices;
    this.adjList = new Map();
  }

  addVertex(vertex){
  	this.adjList.set(vertex, []);
  }

  addEdge(vertex1, vertex2){
  	this.adjList.get(vertex1).push(vertex2);

    this.adjList.get(vertex2).push(vertex1);
  }
}
```

## DFS & BFS in Graph

**Depth First Search**

```
dfs(vertex){
  	let visited = new Map();
    if(this.adjList.has(vertex)){
    	let stack = [];
      stack.push(vertex);

      while(stack.length > 0){
      	let currentVertex = stack.pop();
        let edges = this.adjList.get(currentVertex);
        for(const edge of edges){
        	if(!visited.has(edge)){
          	stack.push(edge);
          }
        }
        visited.set(currentVertex, 1);
      }
    }
    for(const [key, value] of visited.keys()){
    	console.log(key);
    }
}
```

**Breadth First Search**

```
bfs(vertex){
  	let visited = new Map();
    if(this.adjList.has(vertex)){
    	let queue = [];
      queue.push(vertex);

      while(queue.length > 0){
      	let currentVertex = queue.shift();
        let edges = this.adjList.get(currentVertex);
        for(const edge of edges){
        	if(!visited.has(edge)){
          	queue.push(edge);
          }
        }
        visited.set(currentVertex, 1);
      }
    }
    for(const [key, value] of visited.keys()){
    	console.log(key);
    }
}
```
