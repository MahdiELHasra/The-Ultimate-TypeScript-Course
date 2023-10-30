# Modules

- We use modules to organize our code across multiple ﬁles.

- Objects deﬁned in a module are private and invisible to other modules unless exported.

## Exporting and importing:

```ts
// shapes.ts
export class Circle {}
export class Square {}
// app.ts
import { Circle, Square as MySquare } from "./shapes";
```

## Default exports:

```ts
// shapes.ts
export default class Circle {}
// app.ts
import Circle from "./shapes";
```

## Wildcard imports:

```ts
// app.ts
import * as Shapes from "./shapes";
let circle = new Shapes.Circle();
```

## Re-exporting:

```ts
// /shapes/index.ts
export { Circle } from "./circle";
export { Square } from "./square";
// app.ts
import { Circle, Square } from "./shapes";
```
