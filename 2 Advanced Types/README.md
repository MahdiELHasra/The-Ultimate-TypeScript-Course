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
