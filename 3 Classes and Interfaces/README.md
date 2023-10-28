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