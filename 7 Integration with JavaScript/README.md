# Integration with JavaScript

- To include JavaScript code in a TypeScript project, we need to enable the **_`allowJs`_** setting
  in `tsconﬁg`.

- JavaScript code included in TypeScript projects is **not type-checked** by default.

- We can enable type checking by enabling the **_`checkJs`_** setting in `tsconﬁg`.

- We can optionally turn off compiler errors on a ﬁle-by-ﬁle basis by applying `// @ts-nocheck` once on top of JavaScript ﬁles.

- When migrating a large JavaScript project to TypeScript, we might face numerous
  errors. In such cases, it’s easier to disable **_`checkJs`_** and apply `// @ts-check` (the opposite of `@ts-nocheck`) on individual ﬁles to migrate them one by one.
- We have two ways to describe type information for JavaScript code: using **_`JSDoc`_** and declaration (type deﬁnition ﬁles).

- Type deﬁnition ﬁles are similar to header ﬁles in `C`. They describe the features of a
  module.

- We don’t need to create type deﬁnition ﬁles for third-party JavaScript libraries. We can
  use type deﬁnition ﬁles from the Deﬁnitely Typed GitHub repository (**_`@types/<package>`_**).

- Newer JavaScript libraries come with type deﬁnition ﬁles. So there’s no need to install
  type deﬁnition ﬁles separately.
