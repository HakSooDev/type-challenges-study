<h1>Exclude <img src="https://img.shields.io/badge/-easy-7aad0c" alt="easy"/> <img src="https://img.shields.io/badge/-%23built--in-999" alt="#built-in"/> <img src="https://img.shields.io/badge/-%23union-999" alt="#union"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/tree/main/questions/00043-easy-exclude)

<h2> Problem </h2>
Implement the built-in Exclude<T, U>

> Exclude from T those types that are assignable to U

For example:

```ts
type Result = MyExclude<"a" | "b" | "c", "a">; // 'b' | 'c'
```

<h2> My Solution </h2>

```ts
type MyExclude<T, U> = T extends U ? never : T;
```

<h2> Notes </h2>

<h3> Ref </h3>

-
