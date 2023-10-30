# Generics:

- Generics offer the advantage of creating classes, interfaces and functions that can be reused with data types while still ensuring type safety. They allow you to parameterize types, functions and classes so that they can be utilized with data types without compromising on type checking. Generics prove to be highly beneficial when you aim to create code that's both flexible and reusable.

- A generic type is characterized by having one or more generic type parameters specified within angle brackets.

- When working with types it is important to provide arguments, for the generic type parameters or allow the compiler to infer them automatically (if possible).

## Generic classes:

```ts
class KeyValuePair<K, V> {
  constructor(public key: K, public value: V) {}
}
let pair = new KeyValuePair<number, string>(1, "a");
// The TypeScript compiler can sometimes infer
// generic type arguments so we don't need to specify them.
let other = new KeyValuePair(1, "a");
```

## Generic functions:

```ts
function wrapInArray<T>(value: T) {
  return [value];
}
let numbers = wrapInArray(1);
```

## Generic interfaces:

```ts
interface Result<T> {
  data: T | null;
}
```

## Generic constraints:

We can constrain generic type arguments by using the **_extends_** keyword after generic
type parameters.

```ts
function echo<T extends number | string>(value: T) {}
// Restrict using a shape object
function echo<T extends { name: string }>(value: T) {}
// Restrict using an interface or a class
function echo<T extends Person>(value: T) {}
```

## Extending generic classes:

When we extend classes we have three choices. We can pass on the generic type parameters to ensure that the derived classes also have the generic type parameters. Another option is to limit or fix them.

```ts
// Passing on generic type parameters
class CompressibleStore<T> extends Store<T> {}
// Constraining generic type parameters
class SearchableStore<T extends { name: string }> extends Store<T> {}
// Fixing generic type parameters
class ProductStore extends Store<Product> {}
```
