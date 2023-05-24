<h1>Drop Char <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23template--literal-999" alt="#template-literal"/> <img src="https://img.shields.io/badge/-%23infer-999" alt="#infer"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/02070-medium-drop-char)

<h2> Problem </h2>

Drop a specified char from a string.

For example:

```ts
type Butterfly = DropChar<" b u t t e r f l y ! ", " ">; // 'butterfly!'
```

<h2> My Solution </h2>

```ts
type DropChar<S, C> = S extends `${infer A}${infer B}`
  ? `${A extends C ? "" : A}${DropChar<B, C>}`
  : "";
```

<h2> Notes </h2>

The conditional type `S extends ${infer A}${infer B}` checks if `S` can be split into two parts, denoted by `${infer A}` and `${infer B}`.
If `S` can be split, we check if `A` extends to `C`, which means `A` is one of characters that we should drop.
If `A` matches `C`, we return an empty string `""`, dropping `A` from the result. Otherwise we return `A` as is, preserving it in result.

We continue the process by making a recusrive call to `DropCahr<B,C>`, passing the remaing part of the string `B` and the target character `C`.

This recursive process continues until the base case is reached, which occurs when `S` cannot be split into two parts.
The base case is triggered when either the original given string is empty or when we reach the end of the string during a recursive call.

From other solutions, I found a more optimized approach for this problem.

```ts
type DropChar<S, C extends string> = S extends `${infer L}${C}${infer R}`
  ? DropChar<`${L}${R}`, C>
  : S;
```

In this solution, we check if `S` can be split into three parts: `${infer L}, ${C}, and ${infer R}`.
If `S` can be split into three parts, it indicates that `C` is present in `S`. In this case, we call `DropChar<${L}${R}, C>`, which recursively removes occurrences of `C` from the combined string `${L}${R}`.
The recursive call continues until all occurrences of `C` are dropped.

If `S` cannot be split into three parts, it means that `C` is not present in `S`, or we have processed all occurrences of `C`. In this case, the original string `S` is returned as is.

This solution offers a more efficient solution by avoiding unnecessary recursion when there are no occurrences of the target character `C` in the string `S`. It ensures that the type terminates when no more characters need to be dropped, reducing unnecessary computation.

<h3> Ref </h3>

- https://github.com/type-challenges/type-challenges/issues/2074
