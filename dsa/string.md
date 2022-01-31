# String

## Table of Contents

- [Common Methods](#common-methods)
- [Further Reads](#further-reads)

## Common Methods

**<string>.at(index)**

> Returns the character (exactly one UTF-16 code unit) at the specified index. Accepts negative integers, which count back from the last string character.

**<string>.charCodeAt(index)**

> Returns a number that is the UTF-16 code unit value at the given index.

**<string>.concat()**

> The concat() method concatenates the string arguments to the calling string and returns a new string.

```
const str1 = 'Hello';
const str2 = 'World';

console.log(str1.concat(' ', str2)); // expected output: "Hello World"
```

**<string>.includes(searchString [, position])**

> Determines whether the calling string contains searchString.

**<string>.indexOf(searchValue [, fromIndex])**

> Returns the index within the calling String object of the first occurrence of searchValue, or -1 if not found.

**<string>.toLowerCase()**

> Returns the calling string value converted to lowercase.

**<string>.toString()**

> Returns a string representing the specified object. Overrides the Object.prototype.toString() method.

**<string>.toUpperCase()**

> Returns the calling string value converted to uppercase.

**<string>.trim()**

> Trims whitespace from the beginning and end of the string. Part of the ECMAScript 5 standard.

## Further Reads

- [MDN String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
