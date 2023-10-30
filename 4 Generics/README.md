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

## The keyof operator:

The **_keyof_** operator produces a union of the keys of the given object.

```ts
interface Product {
  name: string;
  price: number;
}
let property: keyof Product;
// Same as
let property: "name" | "price";
property = "name";
property = "price";
property = "otherValue"; // Invalid
```

## Type mapping:

Using type mapping we can create new types based off of existing types. For example,
we can create a new type with all the properties of another type where these properties
are readonly, optional, etc.

```ts
type ReadOnly<T> = {
  readonly [K in keyof T]: T[K];
};
type Optional<T> = {
  [K in keyof T]?: T[K];
};
type Nullable<T> = {
  [K in keyof T]: T[K] | null;
};
```

## Utility types:

TypeScript comes with several utility types that perform type mapping for us.
Examples are: `Partial<T>`, `Required<T>`, `Readonly <T>`, etc.

```ts
interface Product {
  id: number;
  name: string;
  price: number;
}

// A Product where all properties are optional
let product: Partial<Product>;

// A Product where all properties are required
let product: Required<Product>;

// A Product where all properties are read-only
let product: Readonly<Product>;

// A Product with two properties only (id and price)
let product: Pick<Product, "id" | "price">;

// A Product without a name
let product: Omit<Product, "name">;
```
> See the complete list of utility types:
https://www.typescriptlang.org/docs/handbook/utility-types.html