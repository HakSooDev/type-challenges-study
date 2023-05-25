<h1>StartsWith <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23template--literal-999" alt="#template-literal"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/02688-medium-startswith)

<h2> Problem </h2>

Implement `StartsWith<T, U>` which takes two exact string types and returns whether `T` starts with `U`

For example

```typescript
type a = StartsWith<"abc", "ac">; // expected to be false
type b = StartsWith<"abc", "ab">; // expected to be true
type c = StartsWith<"abc", "abcd">; // expected to be false
```

<h2> My Solution </h2>

```ts
type StartsWith<T extends string, U extends string> = T extends `${U}${string}`
  ? true
  : false;
```

<h2> Notes </h2>

The conditional type `T extends "${U}${string}"` checks if `T` matches the pattern `${U}${string}`.

`${U}` represents the string `U`. `${string}` represents any remaining characters in the `string`. We use the string type, which represents any valid string value.

So, the pattern `${U}${string}` matches any string that starts with `U` followed by any other characters.

If `T extends "${U}${string}"` is true, it indicates that `T` starts with `U`. So we return true.
Otherwise, we return false.

<h3> Ref </h3>

- https://www.typescriptlang.org/docs/handbook/2/template-literal-types.html
