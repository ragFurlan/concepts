# Design Patterns the most used

- Module Pattern: This pattern is widely used to encapsulate private data and expose a public API. It helps with code organization, reduces naming conflicts, and promotes data privacy.

Ex:
```javascript
const counterModule = (function() {
  let count = 0;

  function increment() {
    count++;
  }

  function decrement() {
    count--;
  }

  function getCount() {
    return count;
  }

  return {
    increment,
    decrement,
    getCount
  };
})();

counterModule.increment();
console.log(counterModule.getCount()); // Output: 1

```

- Singleton Pattern: The Singleton pattern is commonly used for managing shared resources or configurations. It ensures that a class has only one instance and provides a global point of access to it.

Ex:
```javascript
const singleton = (function() {
  let instance;

  function createInstance() {
    const object = new Object('Singleton instance');
    return object;
  }

  return {
    getInstance: function() {
      if (!instance) {
        instance = createInstance();
      }
      return instance;
    }
  };
})();

const instance1 = singleton.getInstance();
const instance2 = singleton.getInstance();

console.log(instance1 === instance2); // Output: true
```
- Observer Pattern: The Observer pattern is heavily used in event-driven systems. It establishes a one-to-many relationship between objects, where changes in one object are automatically propagated to its dependent objects (observers).

Ex:
```javascript
class Subject {
  constructor() {
    this.observers = [];
  }

  addObserver(observer) {
    this.observers.push(observer);
  }

  removeObserver(observer) {
    this.observers = this.observers.filter(obs => obs !== observer);
  }

  notifyObservers(data) {
    this.observers.forEach(observer => observer.update(data));
  }
}

class Observer {
  update(data) {
    console.log('Received data:', data);
  }
}

const subject = new Subject();
const observer1 = new Observer();
const observer2 = new Observer();

subject.addObserver(observer1);
subject.addObserver(observer2);

subject.notifyObservers('Hello observers!'); // Output: Received data: Hello observers!
```

- Factory Pattern: The Factory pattern is frequently used for object creation without tightly coupling the client code to specific classes. It provides a flexible way to create objects by using a common interface.

Ex:
```javascript
class Car {
  constructor(make, model) {
    this.make = make;
    this.model = model;
  }

  getInfo() {
    return `Car: ${this.make} ${this.model}`;
  }
}

class CarFactory {
  createCar(make, model) {
    return new Car(make, model);
  }
}

const factory = new CarFactory();
const car1 = factory.createCar('Toyota', 'Camry');
const car2 = factory.createCar('Honda', 'Accord');

console.log(car1.getInfo()); // Output: Car: Toyota Camry
console.log(car2.getInfo()); // Output: Car: Honda Accord
```

- MVC (Model-View-Controller): Although not a specific design pattern, the MVC architecture is widely adopted in JavaScript applications. It separates the application into three components: the model (data), the view (user interface), and the controller (handles user input and updates the model and view).

Ex:
```javascript
// Model
class User {
  constructor(name) {
    this.name = name;
  }
}

// View
class UserView {
  displayUser(user) {
    console.log(`User: ${user.name}`);
  }
}

// Controller
class UserController {
  constructor(model, view) {
    this.model = model;
    this.view = view;
  }

  updateUser(name) {
    this.model.name = name;
    this.view.displayUser(this.model);
  }
}

// Usage
const user = new User('John Doe');
const view = new UserView();
const controller = new UserController(user, view);

controller.updateUser('Jane Smith'); // Output: User: Jane Smith
```

- Promises and Async/Await: While not traditional design patterns, Promises and Async/Await are language features that help manage asynchronous operations in a more structured and readable manner. They are widely used in modern JavaScript development to handle asynchronous code.

Ex:
```javascript
// Using Promises
function getData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = 'Some data';
      resolve(data);
    }, 2000);
  });
}

getData()
  .then(data => {
    console.log('Received data:', data);
  })
  .catch(error => {
    console.error('Error:', error);
  });

// Using Async/Await
async function getDataAsync() {
  try {
    const data = await getData();
    console.log('Received data:', data);
  } catch (error) {
    console.error('Error:', error);
  }
}

getDataAsync();
```

[**RETURN**](./README.md)