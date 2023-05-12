<h1>Concat <img src="https://img.shields.io/badge/-easy-7aad0c" alt="easy"/> <img src="https://img.shields.io/badge/-%23array-999" alt="#array"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/tree/main/questions/00533-easy-concat)

<h2> Problem </h2>

Implement the JavaScript `Array.concat` function in the type system. A type takes the two arguments. The output should be a new array that includes inputs in ltr order

For example:

```ts
type Result = Concat<[1], [2]>; // expected to be [1, 2]
```

<h2> My Solution </h2>

```ts
type Concat<T extends any[], U extends any[]> = [...T, ...U];
```

<h2> Notes </h2>

There is no difference between `Type[]` and `Array<Type>` at all.
`Type[]` is the shorthand syntax for an array of Type.
`Array<Type>` is the generic syntax.
They are completely equivalent.

<h3> Ref </h3>

- https://stackoverflow.com/questions/36842158/arraytype-vs-type-in-typescript
