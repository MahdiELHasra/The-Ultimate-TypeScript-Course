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
