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

## Getters and setters:

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
