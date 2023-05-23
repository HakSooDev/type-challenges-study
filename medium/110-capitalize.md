<h1>Capitalize <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23template--literal-999" alt="#template-literal"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/00110-medium-capitalize)

<h2> Problem </h2>

Implement `Capitalize<T>` which converts the first letter of a string to uppercase and leave the rest as-is.

For example

```ts
type capitalized = Capitalize<"hello world">; // expected to be 'Hello world'
```

<h2> My Solution </h2>

```ts
type MyCapitalize<S extends string> = S extends `${infer F}${infer R}`
  ? `${Uppercase<F>}${R}`
  : S;
```

<h2> Notes </h2>

The conditional type checks if the string `S` can be split into two parts: the first character `A` and the rest of the string `B`. If the string can be split, it transforms the first character to uppercase using the `Uppercase` utility type and then combines it with the rest of the string `${Uppercase<A>}${B}`.

If the string cannot be split, which means the string `S` is empty string, we return the original string `S` unchanged.

From other answers, I found out the solution that do not use built-in utility type `Uppercase`.

```ts
interface ToUpperCase {
  a: "A";
  b: "B";
  // ... (remaining letters)
  y: "Y";
  z: "Z";
}

type LowerCase = keyof ToUpperCase;
type MyCapitalize<S extends string> =
  S extends `${infer First extends LowerCase}${infer Rest}`
    ? `${ToUpperCase[First]}${Rest}`
    : S;
```

The `ToUpperCase` interface defines a mapping between lowercase letters (a to z) and their corresponding uppercase letters (A to Z).
Then type `LowerCase` is created using the `keyof` keyword applied to the ToUpperCase interface. It represents the union of all lowercase letters (a to z) as string literal types.

In conditional type `First extends LowerCase`, we check if the first character of the string `S` is a lowercase letter using `LowerCase`.

If it is, the true branch is executed, returning a new string formed by capitalizing the first character (`ToUpperCase[First]`) and appending the remaining part of the string (`Rest`).
Otherwise, we will return original string `S`

<h3> Ref </h3>

- https://www.typescriptlang.org/docs/handbook/2/template-literal-types.html#uppercasestringtype
- https://github.com/type-challenges/type-challenges/issues/11344
