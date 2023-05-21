<h1>Trim Right <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23template--literal-999" alt="#template-literal"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/04803-medium-trim-right)

<h2> Problem </h2>

Implement `TrimRight<T>` which takes an exact string type and returns a new string with the whitespace ending removed.

For example:

```ts
type Trimed = TrimRight<"   Hello World    ">; // expected to be '   Hello World'
```

<h2> My Solution </h2>

```ts
type TrimRight<S extends string> = S extends `${infer A}${WhiteSpace}`
  ? TrimRight<A>
  : S;
```

<h2> Notes </h2>

Exactly same concept with [106.Trim Left](/medium/106-trim-left.md) but tailing whitespace instead of leading whitespace.
