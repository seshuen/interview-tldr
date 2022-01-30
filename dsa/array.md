# Array

Summarizes common things to remember related to an array.

## Table of Contents

- [Create an array](#create-an-array)
- [Traverse through an array](#traverse-through-an-array)
- [Insert a item in an array](#insert-a-item-in-an-array)
- [Delete a item in an array](#delete-a-item-in-an-array)
- [Search a item in an array](#search-a-item-in-an-array)
- [Reverse an array](#reverse-an-array)
- [Two pointers in an array](#two-pointers-in-an-array)
- [Slice an array](#slice-an-array)

## Create an array:

```
let arr = [1,2,3,4];
let arr = new Array();
```

## Traverse through an array:

```
for(let i = 0; i< arr.length; i ++) {
    console.log(arr[i]);
}
```

```
// Foreach method
const array = [“apple”, “mangoes”, “oranges”];
array.forEach( (index, item) => console.log(index, item) );
```

```
// 'of' array method
const array = [ 1, 2, 3, 4, 5];
for( const item of array) {
    console.log(item);
}
```

## Insert item in an array:

```
let array = [1,3,4,2,7];

// Insert at the end of the array
array.push(5);

// Insert at the start of array: remember this is a O(n) operation given you need to shift all values from the start of array one step right
array.unshift(9);

// Insert in specific index: remember splice will return a same array
array.splice(index, 0, <new-item>);
```

## Delete item in an array:

```
let array = [1, 2, 3, 6, 8];

// Delete from end of the array
array.pop();

// Delete from start of the array
array.shift();

// Delete array[index] will replace item with undefined
array.splice(index, count); //Delete in specific index
```

## Search an item in an array:

```
// Method 1:
let itemToSearch = 7;
const array = [ 1, 2, 6, 7];

for(let index = 0; index < array.length; index++) {
    if(array[index] === itemToSearch) {
        console.log(“ Found at: “ + index);
    }
}
```

```
// Using includes
if( array.includes(itemToSearch)) {
    console.log(“Present!”);
}
```

```
// Using find will return the value itself
console.log(array.find(value => value === itemToSearch));
```

```
// Using findIndex will return the index
console.log(array.findIndex(value => value === itemToSearch));
```

```
// Use indexOf to return first index of given value: returns -1 if not found
console.log(array.indexOf( itemToSearch));
```

## Reverse an array:

```
// Method 1
const array = [ 1, 2, 6, 7];
let startPointer = 0;
let endPointer = array.length - 1;

while(endPointer >= startPointer) {
    let tempHolder = array[startPointer];
    array[startPointer] = array[endPointer];
    array[endPointer] = tempHolder;
    startPointer += 1;
    endPointer -= 1;
}
```

```
array.reverse(); //using reverse()
```

## Two pointers in an array:

See above [Method 1](#reverse-an-array) for reverse as an example

## Slice an array:

```
// Remember end index should be one greater than you want to slice at
const array = [ 1, 2, 6, 7];
array.slice(startIndex, endIndex)
```
