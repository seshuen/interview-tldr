# Stacks and Queue

**Common operations of stack:**
_`push()`, `pop()`, `isEmpty()`, `peek()`_

**Common operations of queue:**
_`add()`, `remove()`, `isEmpty()`, `peek()`_

## Table of Contents

- [Implementation of Stack using an array](#implementation-of-stack-using-an-array)
- [Implementation of Stack using Linkedlist](#implementation-of-stack-using-linkedlist)
- [Implementation of Queue using Linkedlist](#implementation-of-queue-using-linkedlist)
- [Implementation of Queue using map](#implementation-of-queue-using-map)
- [Traverse through Stack](#traverse-through-stack)
- [Traverse through Queue](#traverse-through-queue)
- [Search in a Stack/Queue](#search-in-a-stack/queue)
- [Reverse a Stack](#reverse-a-stack)
- [Reverse a Stack](#reverse-a-queue)
- [Create Queue using two Stacks](#create-queue-using-two-stacks)

## Implementation of stack using an array

> Implementation of the stack is simple with array push and pop methods. Both have O(1) time complexity

## Implementation of stack using Linkedlist

```
class Stack{
    constructor(){
        this.stack = new LinkedList();
    }

    push(value){
        this.stack.prepend(value);
    }

    pop(){
        return this.stack.removeHead();
    }

    peek(){
        return this.stack.getHead();
    }

    printStack(){
        this.stack.printLinkedList();
    }
}

let s = new Stack();
s.push(1);
s.push(3);
s.push(4);
s.push(2);
s.pop();
```

## Implementation of Queue using Linkedlist

```
/* First create linked list node */
class Node {
	constructor(value, next = null){
  	this.value = value;
    this.next = next;
  }
}

/* Now create linked list */
class LinkedList {
	constructor(){
        this.head = null;
    }

  add(value){
  	let newNode = new Node(value);
    if(this.head === null) {
    	this.head = newNode;
    } else {
    	let currentNode = this.head;
    	while(currentNode.next !== null){
      	currentNode = currentNode.next;
      }
      currentNode.next = newNode;
    }
  }

  prepend(value){
  	let newNode = new Node(value);
    if(this.head === null) {
    	this.head = newNode;
    } else {
    	newNode.next = this.head;
      this.head = newNode;
    }
  }

  removeHead(){
  	if(this.head == null){
    	return false;
    }
    this.head = this.head.next;
    return true;
  }

  remove(value) {
  	if(this.head == null) {
    	return false;
    }

    if(this.head.value === value){
    	this.head = this.head.next;
      return true
    }

    let currentNode = this.head;
    while(currentNode.next !== null){
    	if(currentNode.next.value === value){
            currentNode.next = currentNode.next.next;
            return true;
        }
    	currentNode = currentNode.next;
    }
    return false;
  }

  getHead() {
  	return this.head;
  }

  printLinkedList(){
  	let currentNode = this.head;
    while(currentNode !== null){
        console.log(currentNode.value);
        currentNode = currentNode.next;
    }
  }
}
```

_Implement queue using Linkedlist_

```
class Queue{
    constructor(){
        this.queue = new LinkedList();
    }

    enqueue(item) {
        this.queue.add(item);
    }

    dequeue() {
        let deleteNode = this.queue.getHead();
        this.queue.removeHead();
        return deleteNode.value;
    }

    peek(){
        return this.queue.getHead().value;
    }

    printQueue(){
        this.queue.printLinkedList();
    }
}


let q = new Queue();
q.enqueue("mango");
q.enqueue("apple");
q.enqueue("orange");
q.enqueue("strawberry");
q.dequeue();
q.printQueue();
```

## Implementation of queue using map

```
class Queue{
    constructor() {
        this.queue = new Map();
        this.head = 0;
        this.tail = 0;
    }

    enqueue(item){
        this.queue.set(this.tail++, item);
    }

    dequeue() {
        if(this.head == this.tail){ return undefined; }
        return this.queue.delete(this.head++);
    }

    printQueue() {
        let tempArr = [];
        for(const [key, value] of this.queue){
            tempArr.push(key + " : " + value);
        }
        console.log(tempArr.join(" -- "));
    }
}

let q = new Queue();
q.enqueue("mango");
q.enqueue("apple");
q.enqueue("orange");
q.enqueue("strawberry");
q.dequeue();
q.printQueue();
```

## Traverse through Stack

```
let stackNode = s.peek();
while(stackNode !== null){
    console.log(stackNode.value);
    stackNode = stackNode.next;
}
```

## Traverse through Queue

```
let queueNode = q.peek();
while(queueNode !== null){
    console.log(queueNode.value);
    queueNode = queueNode.next;
}
```

## Search in a Stack/Queue

**For stack using an array**

> Use normal array search

**For queue using map**

> See search method in map

**For linkedlist**

```
function searchNode(value, stack){
    let stackNode = stack.peek();
    while(stackNode !== null){
        if(stackNode.value === value){
            return true;
        }
        stackNode = stackNode.next;
    }
    return false;
}
```

## Reverse a Stack

```
// Can do this using two stacks. Push into new one while popping the old one.
let s2 = new Stack();
while( s.peek() != null){ s2.push(s.pop()) }


// When using linkedlist you will have to use the logic used to reverse a linkedlist.
let current = this.head();
let previous = this.head();
let progressStamp = this.head();

// Push current up front.
current = current.next;

// Make first node point to null.
previous.next = null;
while(current != null){
    progressStamp = current.next;
    current.next = previous;
    previous = current;
    current = progressStamp;
}
this.head = previous;
```

## Reverse a Queue

> if you are using a LinkedList then use the above logic to reverse the LinkedList

## Create Queue using two Stacks

```
class newQueue{
    constructor(){
        this.old = new Stack();
        this.new = new Stack();
    }

    enqueue(value){
        this.new.push(value);
    }

    dequeue(){
        if(this.old.size > 0){
            return this.old.pop();
        } else {
            while(!this.new.isEmpty()){
            this.old.push(this.new.pop());
            }
            return this.old.pop();
        }
    }

    size() {
        return this.old.size + this.new.size;
    }
}

let testQueue = new newQueue();
testQueue.enqueue(1);
testQueue.enqueue(2);
testQueue.enqueue(3);
testQueue.enqueue(4);
testQueue.enqueue(5);

console.log(testQueue.dequeue());
testQueue.enqueue(6);
testQueue.enqueue(7);
console.log(testQueue.dequeue());
```
