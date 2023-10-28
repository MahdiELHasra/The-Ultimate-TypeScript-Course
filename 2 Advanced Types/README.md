# Advanced Types

## Type alias:

```ts
type Employee = {
  readonly id: number;
  name: string;
  phone?: number;
  retire: (date: Date) => void;
};

let employee_1: Employee = {
  id: 1,
  name: "Mahdi",
  retire: (date: Date) => {
    console.log(date);
  },
};
```

## Union types:

With union types, we can allow a variable to take `one of many types` (eg `number` | `string`)

```ts
function kgToLbs(weight: number | string): number {
  // Narrowing
  if (typeof weight === "number") return weight * 2.2;
  else return parseInt(weight) * 2.2;
}
kgToLbs(20);
kgToLbs("20");
```

## Intersection types:

With intersection types, we can `combine multiple types into one` (eg Draggable & Resizable).

```ts
let width: string & number;

type Draggable = {
  drag: () => void;
};
type Resizable = {
  resize: () => void;
};

type UIWidget = Draggable & Resizable;

let textBox: UIWidget = {
  drag: () => {},
  resize: () => {},
};
```

## Literal types:

Literal types in TypeScript allow you to specify that a variable or parameter must have a `specific, exact` value.

```ts
let qte: 50 | 100 = 50;
```

```ts
type Quantity = 50 | 100;
let quantity: Quantity = 100;
```

```ts
type Metric = "cm" | "inch";
```

## Nullable types:

Nullable types are a way to indicate that a variable can have a value of a type or be empty represented by either `null` or `undefined`. We use the union type operator `|` to combine the type with the possibility of being null or undefined.

```ts
let greet = (name: string | null | undefined) => {
  if (name) console.log(`Hello ${name}`);
  else console.log("Hallo");
};

greet(null); // Output: "Hallo"
greet(undefined); // Output: "Hallo"
greet("Mahdi"); // Output: "Hello Mahdi"
```

## Optional Chaining (?.):

Using optional chaining `(?.)` we can simplify our code and remove the need for null checks.

```ts
type Customer = {
  birthday?: Date;
};
function getCostumer(id: number): Customer | null | undefined {
  return id === 0 ? null : { birthday: new Date() };
}
let customer = getCostumer(1);
// Optional property access operator
console.log(customer?.birthday?.getFullYear());
// Optional element access operator
customer?.[1];
//Optional Call
let log: any = null;
log?.("a");
```
