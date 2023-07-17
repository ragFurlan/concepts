# Array

## Examples of Working with Arrays in JavaScript

This repository contains examples of working with arrays in JavaScript.

### Create an Array

```javascript
let fruits = ['apple', 'banana', 'orange'];
```

### Access Array Elements

```javascript
console.log(fruits[0]); // Output: 'apple'
console.log(fruits[2]); // Output: 'orange'
```

### Add Elements to the End of an Array

```javascript
fruits.push('grape');
console.log(fruits); // Output: ['apple', 'banana', 'orange', 'grape']
```

### Remove the Last Element of an Array

```javascript
fruits.pop();
console.log(fruits); // Output: ['apple', 'banana', 'orange']
```

### Iterate over an Array using a for Loop

```javascript
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
// Output:
// 'apple'
// 'banana'
// 'orange'
```


### Iterate over an Array using the forEach() Method

```javascript
fruits.forEach(function(fruit) {
  console.log(fruit);
});
// Output:
// 'apple'
// 'banana'
// 'orange'
```

### Filter Elements of an Array based on a Condition

```javascript
let longFruits = fruits.filter(function(fruit) {
  return fruit.length > 5;
});
console.log(longFruits); // Output: ['banana', 'orange']
```

### Map Array Elements to Create a New Array

```javascript
let capitalizedFruits = fruits.map(function(fruit) {
  return fruit.toUpperCase();
});
console.log(capitalizedFruits); // Output: ['APPLE', 'BANANA', 'ORANGE']
```


### splice(): Modifying Array Content

```javascript
let fruits = ['apple', 'banana', 'orange'];

// Remove elements starting from index 1 and remove 1 element
fruits.splice(1, 1);
console.log(fruits); // Output: ['apple', 'orange']

// Add elements starting from index 1 and remove 0 elements
fruits.splice(1, 0, 'grape', 'kiwi');
console.log(fruits); // Output: ['apple', 'grape', 'kiwi', 'orange']

// Replace elements starting from index 2 and remove 1 element
fruits.splice(2, 1, 'cherry');
console.log(fruits); // Output: ['apple', 'grape', 'cherry', 'orange']

// Extract elements from index 1 (inclusive) to index 3 (exclusive)
let slicedFruits = fruits.slice(1, 3);
console.log(slicedFruits); // Output: ['banana', 'orange']
```


### concat(): Combining Arrays

```javascript
let fruits = ['apple', 'banana'];
let moreFruits = ['orange', 'grape'];

let allFruits = fruits.concat(moreFruits);
console.log(allFruits); // Output: ['apple', 'banana', 'orange', 'grape']
```


### indexOf(): Finding the Index of an Element

```javascript
let fruits = ['apple', 'banana', 'orange'];

let indexOfBanana = fruits.indexOf('banana');
console.log(indexOfBanana); // Output: 1

let indexOfGrape = fruits.indexOf('grape');
console.log(indexOfGrape); // Output: -1 (not found)
```

[**RETURN**](./README.md)
