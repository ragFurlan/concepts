# SOLID

### Single Responsibility Principle (SRP): A class should have only one reason to change.

```javascript	
// Bad Example (Violates SRP)
class User {
  constructor(name) {
    this.name = name;
  }

  save() {
    // Code for saving the user to the database
  }

  sendEmail() {
    // Code for sending an email to the user
  }
}

// Good Example (Follows SRP)
class User {
  constructor(name) {
    this.name = name;
  }
}

class UserRepository {
  save(user) {
    // Code for saving the user to the database
  }
}

class EmailService {
  sendEmail(user) {
    // Code for sending an email to the user
  }
}
```

### Open-Closed Principle (OCP): Software entities (classes, modules, functions) should be open for extension but closed for modification.

```javascript
// Bad Example (Violates OCP)
class Shape {
  constructor() {
    this.type = '';
  }

  calculateArea() {
    // Code for calculating area
  }
}

class Circle extends Shape {
  constructor(radius) {
    super();
    this.type = 'circle';
    this.radius = radius;
  }

  calculateArea() {
    return Math.PI * this.radius * this.radius;
  }
}

// Good Example (Follows OCP)
class Shape {
  constructor() {
    this.type = '';
  }

  calculateArea() {
    // Code for calculating area
  }
}

class Circle extends Shape {
  constructor(radius) {
    super();
    this.type = 'circle';
    this.radius = radius;
  }

  calculateArea() {
    return Math.PI * this.radius * this.radius;
  }
}

class Square extends Shape {
  constructor(side) {
    super();
    this.type = 'square';
    this.side = side;
  }

  calculateArea() {
    return this.side * this.side;
  }
}

```

### Liskov Substitution Principle (LSP): Subtypes must be substitutable for their base types.

```javascript
// Bad Example (Violates LSP)
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  setWidth(width) {
    this.width = width;
  }

  setHeight(height) {
    this.height = height;
  }

  calculateArea() {
    return this.width * this.height;
  }
}

class Square extends Rectangle {
  constructor(side) {
    super(side, side);
  }

  setWidth(width) {
    this.width = width;
    this.height = width;
  }

  setHeight(height) {
    this.width = height;
    this.height = height;
  }
}

// Good Example (Follows LSP)
class Shape {
  calculateArea() {
    throw new Error('Method not implemented');
  }
}

class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
  }

  calculateArea() {
    return this.width * this.height;
  }
}

class Square extends Shape {
  constructor(side) {
    super();
    this.side = side;
  }

  calculateArea() {
    return this.side * this.side;
  }
}
```

### Interface Segregation Principle (ISP): Clients should not be forced to depend on interfaces they do not use.

```javascript
// Bad Example (Violates ISP)
class Printer {
  print(document) {
    // Code for printing
  }

  fax(document) {
    // Code for faxing
  }

  scan(document) {
    // Code for scanning
  }
}

// Good Example (Follows ISP)
class Printer {
  print(document) {
    // Code for printing
  }
}

class Fax {
  fax(document) {
    // Code for faxing
  }
}

class Scanner {
  scan(document) {
    // Code for scanning
  }
}
```

### Dependency Inversion Principle (DIP): High-level modules should not depend on low-level modules. Both should depend on abstractions.

```javascript
// Bad Example (Violates DIP)
class Database {
  save(data) {
    // Code for saving data to a specific database
  }
}

class UserService {
  constructor() {
    this.database = new Database(); // Direct dependency on the Database class
  }

  saveUser(user) {
    this.database.save(user);
  }
}

// Good Example (Follows DIP)
class Database {
  save(data) {
    // Code for saving data to a specific database
  }
}

class UserService {
  constructor(database) {
    this.database = database; // Dependency on an abstraction (interface)
  }

  saveUser(user) {
    this.database.save(user);
  }
}
```

[**RETURN**](./README.md)