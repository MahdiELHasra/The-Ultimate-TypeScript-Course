# Fundamentals :

Given that TypeScript's an extension of JavaScript it encompasses all the types found in JavaScript such as `number` `string` `boolean` `object` and more. Additionally TypeScript introduces types, like `any` `unknown` `never` `enum` and `tuple`.

## Annotation

In TypeScript the term "annotation" usually pertains to the act of providing type information or metadata to variables, functions or other elements, in your code. These annotations assist the TypeScript compiler, in comprehending and enforcing type correctness during the development process. It's important to note that annotations are not executed during runtime; rather they serve solely for analysis purposes.

### Primitive types:

```ts
let sales: number = 123_456_789;
let course: string = "TypeScript";
let is_Published: boolean = true;
let level: any;
```

> **Note;** The `any` type is capable of representing any type of value. However it is recommended to minimize its usage as possible since doing so undermines the main objective of utilizing TypeScript. When a variable is assigned the type `any` it can accept values of any type, which may result in issues related to typing within your code.

### Arrays:

```ts
let arrayOfNumbers: number[] = [1, 2, 3];

let arrayOfString: string[] = ["m", "a", "h", "d", "i"];

let arrayOfNumbersAndString: (number | string)[] = [
  "M",
  "a",
  "h",
  "d",
  "i",
  2,
  1,
];

let multiDimensionalArray: (number[] | string[])[] = [
  ["m", "a", "h", "d", "i"],
  [1, 2],
];
```

### Tuples:

Tuples are _`ﬁxed-length`_ arrays where each element has a speciﬁc type. We often use them for representing two or three related values.

```ts
let tuple: [number, string] = [1, "Mahdi"];
```

### Enums:

Enums provide a way to define a _`set of named constants`_. They allow you to create a collection of related values with descriptive names, making your code more readable and self-explanatory.

```ts
enum Color {
  Red = "RED",
  Green = "GREEN",
  Blue = "BLUE",
}

const selectedColor: Color = Color.Green;
console.log(selectedColor); // Outputs: "GREEN"
```

### Functions:

In TypeScript, functions play a fundamental role just like in JavaScript, but TypeScript adds a _`layer of static typing`_ to make your code more robust and maintainable.

#### Function Declaration and Type:

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

#### Function Expressions:

```ts
const multiply = function (x: number, y: number): number {
  return x * y;
};
```

#### Arrow Functions:

```ts
const divide = (a: number, b: number): number => a / b;
```

#### Optional and Default Parameters:

```ts
function greet(name: string, greeting = "Hello") {
  console.log(`${greeting}, ${name}!`);
}
```

#### Rest Parameters and Spread Operator:

```ts
function sum(...numbers: number[]): number {
  return numbers.reduce((acc, num) => acc + num, 0);
}

const numbers = [1, 2, 3];
const total = sum(...numbers);
```

### Objects:

TypeScript provides _`strong static typing for objects`_, allowing you to define and work with object structures with clarity and confidence.

```ts
let employee: {
  readonly id: number;
  name: string;
  phone?: number;
  retire: (date: Date) => void;
} = {
  id: 1,
  name: "Mahdi",
  retire: (date: Date) => {
    console.log(date);
  },
};
```

## Compiler Options:

Compiler options in TypeScript, for configuring the behavior of the TypeScript compiler can be utilized to customize the compilation process according to your project requirements. These options can be configured in your `tsconfig.json` file.

| Option               | Description                                                                                                                                                                     |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `noImplicitAny `     | When enabled, the compiler will warn you about variablesthat are inferred with the any type. You’ll then have toexplicitly annotate them with any if you have a reason todo so. |
| `noImplicitReturns`  | When enabled, the compiler will check all code paths in a function to ensure they return a value.                                                                               |
| `noUnusedLocals`     | When enabled, the compiler will report unused local variables.                                                                                                                  |
| `noUnusedParameters` | When enabled, the compiler will report unused parameters.                                                                                                                       |
