<h1>Replace <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23template--literal-999" alt="#template-literal"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/00116-medium-replace)

<h2> Problem </h2>

Implement `Replace<S, From, To>` which replace the string `From` with `To` once in the given string `S`

For example

```ts
type replaced = Replace<"types are fun!", "fun", "awesome">; // expected to be 'types are awesome!'
```

<h2> My Solution </h2>

```ts
type Replace<
  S extends string,
  From extends string,
  To extends string
> = From extends ""
  ? S
  : S extends `${infer A}${From}${infer B}`
  ? `${A}${To}${B}`
  : S;
```

<h2> Notes </h2>

First of all, `From extends ""` checks if the `From` substring is an empty string. If it is, it means there is nothing to replace, so the original string `S` is returned as-is.
If `From` is not empty, it checks if the input string `S` matches the pattern `${infer A}${From}${infer B}`. `${infer A}` and `${infer B}` are placeholders that capture the substring before and after the occurrence of `From` within `S`, respectively.

If `S` matches the pattern, it replaces the first occurrence of `From` with `To` and returns the modified string `${A}${To}${B}`.
If `S` does not match the pattern, it returns the original string `S` without any modifications.
