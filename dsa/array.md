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
- [Good to know about an array](#good-to-know-about-an-array)
- [Interesting Problems](#interesting-problems)

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
array.splice(index, count);

//Delete in specific index
delete array[i]
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

## Good to know about an array

- JS uses dynamic arrays by default.
- Use `new Array(<length>)` to declare an empty array of given length.
- **Array.push() & Array.unshift()**
  > Both methods take one or more elements as parameters and add those elements to the array method is being called on; the `push()` method adds elements to the end of an array, and `unshift()` adds elements to the beginning.
- **Array.pop() & Array.shift()**
  > The above two methods take a single element as a parameter. While `pop()` helps to remove an element from the end of an array and display, `shift()` helps to remove the front element and display it.
- **Array.splice()**
  > Remove consecutive elements from the array. First parameter is the index, and the second is the number of elements.
  > **Note:** Splice will change the current array. Use slice if you need to get the result in a different array.
- **Array.map()**
  > Map is a pure function which helps to map a callback function on each element of an array. The `map()` method creates a new array populated with the results of calling a provided function on every element in the calling array.
- **Array.filter()**
  > Filter helps to filter array values using the callback function we pass to it. The `filter()` method creates a new array with all elements that pass the test implemented by the provided function.
- **Array.concat()**
  > The `concat()` method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.
- **Array.reduce()**
  > The reduce method allows for more general forms of array processing, and it's possible to show that both filter and map can be derived as special applications of reduce. The reduce method iterates over each item in an array and returns a single value (i.e. string, number, object, array).
- **Array.sort()**
  > The sort method sorts the elements of an array according to the callback function. If `compareFunction(a,b)` returns a value less than 0 for two elements a and b, then a will come before b. If `compareFunction(a,b)` returns a value greater than 0 for two elements a and b, then b will come before a. If `compareFunction(a,b)` returns a value equal to 0 for two elements a and b, then a and b will remain unchanged.
- The join method is used to join the elements of an array together to create a string
- Use Array.includes() to check if the value is inside the array.
- If you have to use Indexof of a value or find any other value that exists in an array try map.

## Interesting Problems

1. [Remove Element](https://leetcode.com/problems/remove-element/)
2. [Valid Mountain Array](https://leetcode.com/problems/valid-mountain-array/)
3. [Remove Duplicates from sorted array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)
4. [Move Zeroes](https://leetcode.com/problems/move-zeroes/)
