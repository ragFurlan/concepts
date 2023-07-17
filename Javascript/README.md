# Javascript


## Design Patterns

For more details, see [here](./PATTERNS_README.md).

## SOLID

For more details, see [here](./SOLID_README.md).


## Array

For more details, see [here](./ARRAY_README.md).

## Promise


promises are used to handle asynchronous operations, such as fetching data from an API, reading files, or making database queries


Example of a resolved Promise:

```javascript	
const resolvedPromise = new Promise((resolve, reject) => {
  // Simulating a successful asynchronous operation after 1 second
  setTimeout(() => {
    resolve('Operation successful!');
  }, 1000);
});

resolvedPromise.then((result) => {
  console.log(result); // Output: 'Operation successful!'
}).catch((error) => {
  console.error(error);
});
```

Example of a rejected Promise:
```javascript
const rejectedPromise = new Promise((resolve, reject) => {
  // Simulating an asynchronous operation that fails after 1 second
  setTimeout(() => {
    reject(new Error('Operation error!'));
  }, 1000);
});

rejectedPromise.then((result) => {
  console.log(result);
}).catch((error) => {
  console.error(error); // Output: Error: Operation error!
});
```

Chaining Promises:
```javascript
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('First part completed!');
  }, 1000);
});

const promise2 = (data) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`${data} Second part completed!`);
    }, 1000);
  });
};

const promise3 = (data) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`${data} Third part completed!`);
    }, 1000);
  });
};

promise1
  .then((result) => promise2(result))
  .then((result) => promise3(result))
  .then((result) => {
    console.log(result); // Output: 'First part completed! Second part completed! Third part completed!'
  })
  .catch((error) => {
    console.error(error);
  });
```

Waiting result

```javascript
function performAsynchronousTask() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve('Async task completed!');
    }, 2000);
  });
}

async function runAsyncTask() {
  console.log('Start');

  try {
    const result = await performAsynchronousTask();
    console.log(result);
    console.log('End');
  } catch (error) {
    console.error(error);
  }
}

runAsyncTask();

```

## Synchronous/asynchronous

In synchronous operations, the code is executed in a sequential, step-by-step manner. Each instruction must be completed before the next one is executed.

During the execution of a synchronous operation, the program typically becomes blocked, waiting for the current task to finish before moving on to the next.

In an asynchronous operation, the code does not block or wait for the completion of the current task before proceeding. Instead, it continues executing other instructions while the asynchronous operation is in progress

## Callbacks

Callback is a function that is passed as an argument to another function and is executed later, typically when an event or an asynchronous operation completes.

The function that receives the callback is responsible for calling that callback at an appropriate time

The main advantage of callbacks is to allow asynchronous code to be executed in a controlled manner without blocking the execution flow of the program.

EX:

```javascript
function doSomething(callback) {
  console.log('Doing something...');
  // Simulating a 2-second delay before calling the callback
  setTimeout(() => {
    const result = 'Operation completed!';
    callback(result);
  }, 2000);
}

function callbackFunction(result) {
  console.log('Callback:', result);
}

// Calling the doSomething() function and passing the callbackFunction as an argument
doSomething(callbackFunction);

```


## Classes

In JavaScript, classes are a way to define objects that share similar characteristics and behaviors. They provide a high-level syntax for creating objects using the object-oriented programming (OOP) paradigm.

A class is a structure that describes the state and behavior of an objec

EX:
```javascript
class Animal {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  eat(food) {
    console.log(`${this.name} is eating ${food}.`);
  }

  sleep() {
    console.log(`${this.name} is sleeping.`);
  }
}

// Creating an instance of the Animal class
const cat = new Animal('Whiskers', 3);

// Calling methods on the instance
cat.eat('fish'); // Output: Whiskers is eating fish.
cat.sleep(); // Output: Whiskers is sleeping.
```

## Inheritance

Inheritance is a fundamental concept in object-oriented programming (OOP) that allows objects to inherit properties and behaviors from other objects. In JavaScript, inheritance can be achieved using prototype-based inheritance.

EX:

```javascript	
// Parent class
function Animal(name) {
  this.name = name;
}

Animal.prototype.eat = function () {
  console.log(this.name + ' is eating.');
};

// Child class inheriting from Animal
function Cat(name, breed) {
  Animal.call(this, name); // Call the parent constructor
  this.breed = breed;
}

// Set up the prototype chain
Cat.prototype = Object.create(Animal.prototype);
Cat.prototype.constructor = Cat;

Cat.prototype.meow = function () {
  console.log(this.name + ' says meow.');
};

// Creating instances of the classes
var animal = new Animal('Animal');
var cat = new Cat('Whiskers', 'Persian');

// Using inherited methods
animal.eat(); // Output: Animal is eating.
cat.eat(); // Output: Whiskers is eating.

// Using child-specific method
cat.meow(); // Output: Whiskers says meow.


```

## Unit Test 

Unit testing is a crucial practice in software development that involves testing individual units, such as functions or classes, in isolation to ensure they work as expected. In JavaScript, there are several frameworks and libraries available to facilitate unit testing. One popular testing framework is Jest.

### Installation

1. Install Jest using npm or yarn:
```
npm install --save-dev jest
```

### Example

1. Create a test file, e.g., `math.test.js`, to write your tests.

2. Write test cases in the test file using the `test()` function provided by Jest.

```javascript
// math.js - module with utility functions
function sum(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

// math.test.js - test file
const { sum, subtract } = require('./math');

test('sum function adds two numbers correctly', () => {
  expect(sum(2, 3)).toBe(5);
});

test('subtract function subtracts two numbers correctly', () => {
  expect(subtract(5, 3)).toBe(2);
});
```

### Running the tests

```
 npx jest
```


## Frameworks Javascript

- React
- Angular
- Vue.js
- Express.js
- Next.js
- VuePress
- Nest.js



