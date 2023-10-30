# Decorators
 - A decorator is a type of declaration that can be attached to elements such, as class declarations, methods, accessors, properties or parameters. Its purpose is to add information or metadata to the code without altering its core structure.

- Decorators are commonly employed in frameworks like Angular and Vue to modify and enhance the behavior of classes.

- Essentially a decorator is a function that is called by the JavaScript runtime. Within this function we have the opportunity to make changes to a class and its members.

- We have the ability to apply decorators on classes themselves as properties, methods, parameters and accessors (getters and setters).

- To utilize decorators, in TypeScript `tsconfig` we need to enable the **`experimentalDecorators`** setting.

- It's possible to apply decorators on a class or its members. However keep in mind that when multiple decorators are used together they are applied in order.
