<h1>Tuple to Union <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23infer-999" alt="#infer"/> <img src="https://img.shields.io/badge/-%23tuple-999" alt="#tuple"/> <img src="https://img.shields.io/badge/-%23union-999" alt="#union"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/00010-medium-tuple-to-union)

<h2> Problem </h2>

Implement a generic `TupleToUnion<T>` which covers the values of a tuple to its values union.

For example

```ts
type Arr = ['1', '2', '3']

type Test = TupleToUnion<Arr> // expected to be '1' | '2' | '3'
```

<h2> My Solution </h2>

```ts
type TupleToUnion<T extends any[]> = T[number];
```

<h2> Notes </h2>

`T[number]` is an indexed access type. By using the number index, it retrieves the union of all possible element types in the array `T`. This means that if `T` is a tuple type with elements of different types, `T[number]` will be a union type containing all those element types.

<h3> Ref </h3>

- https://www.typescriptlang.org/docs/handbook/2/keyof-types.html
- https://www.typescriptlang.org/docs/handbook/2/indexed-access-types.html
- https://stackoverflow.com/questions/59187941/whats-the-tnumber-mean-in-typescript-code
- https://basarat.gitbook.io/typescript/type-system/index-signatures


