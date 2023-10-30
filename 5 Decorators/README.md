# Decorators
 - A decorator is a type of declaration that can be attached to elements such, as class declarations, methods, accessors, properties or parameters. Its purpose is to add information or metadata to the code without altering its core structure.

- Decorators are commonly employed in frameworks like Angular and Vue to modify and enhance the behavior of classes.

- Essentially a decorator is a function that is called by the JavaScript runtime. Within this function we have the opportunity to make changes to a class and its members.

- We have the ability to apply decorators on classes themselves as properties, methods, parameters and accessors (getters and setters).

- To utilize decorators, in TypeScript `tsconfig` we need to enable the **`experimentalDecorators`** setting.

- It's possible to apply decorators on a class or its members. However keep in mind that when multiple decorators are used together they are applied in order.

## Class decorators:

```ts
function Component(constructor: Function) {
  // Here we have a chance to modify members of
  // the target class.
  constructor.prototype.uniqueId = Date.now();
}
@Component
class ProfileComponent {}
```

## Parameterized decorators:

```ts
function Component(value: number) {
  return (constructor: Function) => {
    // Here we have a chance to modify members of
    // the target class.
    constructor.prototype.uniqueId = Date.now();
  };
}
@Component(1)
class ProfileComponent {}
```

## Decorator composition:

```ts
// Multiple decorators are applied in reverse order.
// Pipe followed by Component.
@Component
@Pipe
class ProfileComponent {}
```

## Method decorators:

```ts
function Log(target: any, methodName: string, descriptor: PropertyDescriptor) {
  // We get a reference to the original method
  const original = descriptor.value as Function;
  // Then, we redefine the method
  descriptor.value = function (...args: any) {
    // We have a chance to do something first
    console.log("Before");
    // Then, we call the original method
    original.call(this, ...args);
    // And we have a chance to do something after
    console.log("After");
  };
}
class Person {
  @Log
  say(message: string) {}
}
```

## Accessor decorators:

```ts
function Capitalize(
  target: any,
  methodName: string,
  descriptor: PropertyDescriptor
) {
  const original = descriptor.get;
  descriptor.get = function () {
    const result = original.call(this);
    return "newResult";
  };
}
class Person {
  @Capitalize
  get fullName() {}
}
```

## Property decorators:

```ts
function MinLength(length: number) {
  return (target: any, propertyName: string) => {
    // We use this variable to hold the value behind the
    // target property.
    let value: string;
    // We create a descriptor for the target property.
    const descriptor: PropertyDescriptor = {
      // We're defining the setter for the target property.
      set(newValue: string) {
        if (newValue.length < length) throw new Error();
        value = newValue;
      },
    };
    // And finally, we redefine the property.
    Object.defineProperty(target, propertyName, descriptor);
  };
}
class User {
  @MinLength(4)
  password: string;
}
```
