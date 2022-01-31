# Maps and Set

## Table of Contents

- [Create a hashmap](#create-a-hashmap)
- [Find a value by key](#find-a-value-by-key)
- [Traverse through hashmap](#traverse-through-hashmap)
- [Modify a value in hashmap](#modify-a-value-in)
- [Create a set](#create-a-set)
- [Operations in a set](#operations-in-a-set)
- [Good to know](#good-to-know)

## Create a hashmap

```
//Remember using Map instead of Object is a better choice.
const hashTable = new Map();

// Set to insert value.
hashTable.set('apple', 2);
hashTable.set('mango', 5);
hashTable.set('strawberry', 10);

// Can also use object[key] or object.key to set a value for object
// Remember this can't be iterated. so avoid this way.
hashTable['blueberry'] = 15; //hashTable.blueberry = 15;
console.log(hashTable['blueberry']); //returns 15


// Size will give map's size.
console.log(hashTable.size);

// Remember if a value is not present it will return false
console.log(hashTable.delete('oranges')); //returns false

//has to check if key is present
console.log(hashTable.has('mango')); //returns true
```

## Find a value by key

```
// Get to search for value, if not found will return undefined.
console.log(hashTable.get('orange')); //returns undefined
```

## Traverse through hashmap

```
// Iterate through hashmap.
for (const [key, value] of hashTable) {
  console.log(key + ' = ' + value);
}
```

```
//  Iterate through keys of hashmap.
for( const key of hashTable.keys()){
	console.log(key);
}
```

```
// Iterate through values of hashmap.
for( const value of hashTable.values()){
	console.log(value);
}
```

## Modify a value in hashmap

```
if(hashTable.has(‘mango’)){
  hashTable.set(‘mango’, hashTable.get(‘mango’) + 1);
}
```

## Create a set

```
const mySet1 = new Set();
```

## Operations in a set

```
mySet1.add(1)           // Set [ 1 ]
mySet1.add(5)           // Set [ 1, 5 ]
mySet1.add(5)           // Set [ 1, 5 ]
mySet1.add('some text') // Set [ 1, 5, 'some text' ]
const o = {a: 1, b: 2}
mySet1.add(o)

mySet1.add({a: 1, b: 2})   // o is referencing a different object, so this is okay

mySet1.has(1)              // true
mySet1.has(3)              // false, since 3 has not been added to the set
mySet1.has(5)              // true
mySet1.has(Math.sqrt(25))  // true
mySet1.has('Some Text'.toLowerCase()) // true
mySet1.has(o)       // true

mySet1.size         // 5

mySet1.delete(5)    // removes 5 from the set
mySet1.has(5)       // false, 5 has been removed

mySet1.size         // 4, since we just removed one value

console.log(mySet1)
// logs Set(4) [ 1, "some text", {…}, {…} ] in Firefox
// logs Set(4) { 1, "some text", {…}, {…} } in Chrome
```

## Good to know

- Use Set instead of Array when you need to deal with unique values plus it has O(1) lookup time compared to array.
