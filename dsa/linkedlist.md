# Linkedlist

## Table of Contents

- [Implementing a Linkedlist in JavaScript](#implementing-a-linkedlist-in-javascript)
- [Add a item in a Linkedlist](#add-a-item-in-a-linkedlist)
- [Delete in a Linkedlist](#delete-in-a-linkedlist)
- [Search in a Linkedlist](#search-in-a-linkedlist)
- [Reverse a Linkedlist](#reverse-a-linkedlist)
- [Two pointers in Linkedlist](#two-pointers-in-linkedlist)

## Implementing a Linked List in JavaScript

```
class Node{
    constructor(value, next = null){
        this.value = value;
        this.next = next;
    }
}
```

```
class LinkedList{
    constructor(){
        this.head = null;
    }
}
```

## Add a item in a Linkedlist

```
add(value){
    let newNode = new Node(value);

    if(this.head === null){
        this.head =  newNode;
    } else {
        let currentNode =  this.head;
        while(currentNode.next != null){
        currentNode = currentNode.next;
        }
        currentNode.next = newNode;
    }
}
```

```
addToHead(value){
    let newNode = new Node(value);
    if(this.head === null){
        this.head = newNode;
    } else {
        newNode.next =  this.head;
        this.head = newNode;
    }
}
```

## Delete in a Linkedlist

```
 remove(value){
    if(this.head === null){
        return false;
    }

    if( this.head.value === value){
        let deleteNode = this.head;
        this.head = this.head.next;
        return deleteNode;
    }

    let currentNode = this.head;
    while(currentNode !== null){
        if(currentNode.next.value === value){
        let deleteNode = currentNode.next;
        currentNode.next =  currentNode.next.next;
        return deleteNode;
        }
        currentNode = currentNode.next;
    }
    return false;
}
```

```
removeFromTail(){
    if(this.head === null){
        return false;
    }

    if(this.head.next === null){
        let deleteNode =  this.head;
        this.head =  null;
        return deleteNode;
    } else {
        let currentNode =  this.head;
        while(currentNode !== null){
        if(currentNode.next.next === null){
            let deleteNode = currentNode.next;
            currentNode.next = null;
            return deleteNode;
        }
        currentNode =  currentNode.next;
        }
    }
}
```

```
removeFromHead(){
    let deleteNode = this.head;
    this.head = this.head.next;
    return deleteNode;
}
```

## Search in a Linkedlist

```
search(value){
    if(this.head === null){
        return false;
    }
    let currentNode = this.head;
    while(currentNode !== null){
        if(currentNode.value === value){
        return true;
        }
        currentNode = currentNode.next;
    }
    return false;
}
```

## Reverse a Linkedlist

```
reverse(){
    let current = this.head;
    let previous = this.head;
    current = current.next;
    previous.next = null;
    while(current !=null ){
        let progress = current.next;
        current.next = previous;
        previous = current;
        current = progress;
    }
    this.head = previous;
    }
}
```

## Two pointers in Linkedlist

```
let l = new LinkedList();
l.add(2);
l.addHead(1);
l.add(3);
l.add(4);
l.add(5);

let slow = l.head;
let fast = l.head.next.next;

while(fast.next !== null){
	slow = slow.next;
    fast = fast.next.next;
}

console.log(slow.value); // 2
console.log(fast.value); // 5
```
