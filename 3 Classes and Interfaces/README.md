# Classes and Interfaces

## What is Object-oriented Programming:

Object Oriented Programming (OOP) is a `programming style` that promotes the structuring of code, into objects which're essentially instances of classes. OOP revolves around the idea of `"objects"` that can contain both data (known as `attributes`) and functionality (known as `methods`). TypeScript, being a `typed` extension of JavaScript offers a basis, for incorporating OOP concepts.

## Classes, Constructors and Objects:

- A class serves as a `blueprint`, for creating objects. People often use the terms `"class"` and `"object"` interchangeably.

- A `constructor` is a method (function), within a class that gets invoked when `instances` of that class are created. Constructors help to set up the properties of an object.

- An object is an `entity` that holds data through its properties and performs actions through its methods.

```ts
// Creating Classes
class Account {
  // Properties
  id: number;
  owner: string;
  balance: number;
  // Constructor
  constructor(id: number, owner: string, balance: number) {
    this.id = id;
    this.owner = owner;
    this.balance = balance;
  }
  // Method
  deposit(amount: number): void {
    if (amount <= 0) throw new Error("Invalid Amount");
    this.balance += amount;
  }
}

// Creating Object
let account = new Account(1, "Mahdi", 0);

// Accessing properties and methods
console.log(account);
account.id = 1;
account.deposit(100);

// Type and Instance Checking
console.log(typeof account);
console.log(account instanceof Account);
```

#### Read-only and optional properties:

```ts
class Account {
  readonly id: number;
  nickname?: string;
}
```

## Access modifiers:

Access modifiers are words used to manage the `visibility` and `accessibility` of class members (such, as properties and methods) from, outside the class. They allow you to enforce `encapsulation` and `control access`, which improves the `security` and `maintainability` of your code.

We use access modiﬁers (`public`, `private`, `protected`) to control access to properties and
methods of a class.

```ts
class Account {
  private _balance: number;
  // Protected members are inherited.
  // Private members are not.
  protected _taxRate: number;
}
```

## Parameter properties:

Parameter properties are a feature that lets you `combine` constructor `parameters` with `property` declarations, in a concise and convenient manner. They allow you to declare and `initialize` class properties within the parameter list of the constructor, which reduces the need, for property declarations and assignments. Parameter properties come in handy when you want to create class properties based on the values passed to the constructor.

```ts
class Account {
  // With parameter properties we can
  // create and initialize properties in one place.
  constructor(public readonly id: number, private _balance: number) {}
}
```

## Getters and Setters:

As, in JavaScript you have the ability to utilize getters and setters for managing access, to the properties of a class. Getters are employed to `retrieve` the value of a property whereas setters are used for `assigning` a value to a property.

```ts
class Account {
  private _balance = 0;

  get balance(): number {
    return this._balance;
  }

  set balance(value: number) {
    if (value < 0) {
      throw new Error("Balance cannot be negative.");
    }
    this._balance = value;
  }
}
```

## Index signatures:

Index signatures enable you to create objects, with keys of a type and related values of another type. They prove to be quite handy when you wish to construct objects with property names like how one would utilize a dictionary or map, in other programming languages.

```ts
class SeatAssignment {
  // With index signature properties we can add
  // properties to an object dynamically
  // without losing type safety.
  [seatNumber: string]: string;
}

let seats = new SeatAssignment();
seats.A1 = "Mosh";
seats.A2 = "John";
```

## Static members:

Static members refer to the properties or methods associated with a class itself than specific instances of the class. Unlike instance members static members cannot be accessed through class instances. Can only be accessed using the class name. They are commonly used to define properties or methods that are shared among all instances of a class or to perform utility operations related to the class itself.

To access members we simply use the name of the class. They come in handy when we only need one instance of a class member (property or method) in memory.

```ts
class Ride {
  static activeRides = 0;
}
Ride.activeRides++;
```

## Inheritance:

Inheritance allows a class to inherit and reuse members of another class. The providing
class is called the parent, super or base class while the other class is called the child, sub or
derived class.

```ts
class Cat extends Animal {
  constructor(name: string) {
    super(name);
  }

  meow(): void {
    this.makeSound("meow");
  }
}
```

## Method overriding:

In TypeScript method overriding refers to the capability of a derived class (subclass) to offer its implementation for a method that already exists in its base class (superclass). This functionality allows the subclass to modify or expand upon the behavior of the inherited method while preserving its name and structure. Method overriding is a concept, in object oriented programming as it facilitates the creation of specialized classes, within a class hierarchy.

```ts
class Student extends Person {
  override speak() {
    console.log("Student speaking");
  }
}
```

## Abstract classes and methods:

In TypeScript abstract classes and methods offer a means of outlining class blueprints that share features and specifications. The purpose of classes is to be extended by classes allowing them to include abstract methods that must be implemented in subclasses.

```ts
abstract class Shape {
  // Abstract methods don't have a body
  abstract render();
}
class Circle extends Shape {
  override render() {
    console.log("Rendering a circle");
  }
}
```

