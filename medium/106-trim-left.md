<h1>Trim Left <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23template--literal-999" alt="#template-literal"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/00106-medium-trimleft)

<h2> Problem </h2>

Implement `TrimLeft<T>` which takes an exact string type and returns a new string with the whitespace beginning removed.

For example

```ts
type trimed = TrimLeft<"  Hello World  ">; // expected to be 'Hello World  '
```

<h2> My Solution </h2>

```ts
type WhiteSpace = " " | "\n" | "\t";
type TrimLeft<S extends string> = S extends `${WhiteSpace}${infer A}`
  ? TrimLeft<A>
  : S;
```

<h2> Notes </h2>

First, We define union type called `WhiteSpace` to specify the possible whitespace characters: space, newline, and tab.
The conditional type `S extends {WhiteSpace}${infer A}` checks if the input string `S` has leading whitespace.
If the input string `S` matches the pattern `${WhiteSpace}${infer A}`, indicating that it has leading whitespace, the conditional type evaluates to the true branch, `TrimLeft<A>`.
By recursively calling `TrimLeft` with the result of the string `A` (after removing one leading whitespace character), we continue removing the leading whitespace characters from the string.
The recursion continues until there are no more leading whitespace characters.

When the condition `S extends ${WhiteSpace}${infer A}` becomes false, indicating that there are no leading whitespace characters, we return the input string `S` as it is.
