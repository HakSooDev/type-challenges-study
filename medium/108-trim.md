<h1>Trim <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23template--literal-999" alt="#template-literal"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/00108-medium-trim)

<h2> Problem </h2>

Implement `Trim<T>` which takes an exact string type and returns a new string with the whitespace from both ends removed.

For example

```ts
type trimmed = Trim<"  Hello World  ">; // expected to be 'Hello World'
```

<h2> My Solution </h2>

```ts
type WhiteSpace = " " | "\n" | "\t";
type Trim<S extends string> = S extends `${infer A}${WhiteSpace}`
  ? Trim<A>
  : S extends `${WhiteSpace}${infer A}`
  ? Trim<A>
  : S;
```

<h2> Notes </h2>

I originally thought that I can just recursively call [TrimLeft](/medium/106-trim-left.md) and [TrimRight](/medium/4803-trim-right.md), and ended up just combining two conditional types.

However, I found out that we could check two conditions at once using union type.

The below code, we check both `${WhiteSpace}${infer T}` and `${infer T}${WhiteSpace}` conditions at once. If any of two conditions is `true`, we recursively call `Trim` with the one whitespace removed string `T`, otherwise return `S` as it is.

```ts
type Trim<S> = S extends `${WhiteSpace}${infer T}` | `${infer T}${WhiteSpace}`
  ? Trim<T>
  : S;
```

<h3> Ref </h3>

- https://github.com/type-challenges/type-challenges/issues/13354
