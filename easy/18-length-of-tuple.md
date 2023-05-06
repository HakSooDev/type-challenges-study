<h1>Length of Tuple <img src="https://img.shields.io/badge/-easy-7aad0c" alt="easy"/> <img src="https://img.shields.io/badge/-%23tuple-999" alt="#tuple"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/tree/main/questions/00018-easy-tuple-length)

<h2> Problem </h2>
For given a tuple, you need create a generic `Length`, pick the length of the tuple

For example:

```ts
type tesla = ["tesla", "model 3", "model X", "model Y"];
type spaceX = [
  "FALCON 9",
  "FALCON HEAVY",
  "DRAGON",
  "STARSHIP",
  "HUMAN SPACEFLIGHT"
];

type teslaLength = Length<tesla>; // expected 4
type spaceXLength = Length<spaceX>; // expected 5
```

<h2> My Solution </h2>

```ts
type Length<T extends readonly any[]> = T["length"];
```

<h2> Notes </h2>

`as const` is a type assertion in TypeScript that restricts the inference range of a literal type and prevents its value from being reassigned.

In the given problem, the value is asserted as const using the syntax 'const tesla = ['tesla', 'model 3', 'model X', 'model Y'] as const'. When the asserted value is received using `typeof`, it comes with the `readonly` attribute.

Therefore, `T extends readonly any[]` is used to receive the value `T` in the form of an array that has the `readonly` attribute. Then, since `T` is an array, it has a `length` property, which can be retrieved using `T["length"]`.

<h3> Ref </h3>

- https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-4.html#const-assertions
- https://bobbyhadz.com/blog/typescript-as-const
- https://github.com/junghyeonsu/type-challenges-study/blob/main/easy/18-length-of-tuple.md
