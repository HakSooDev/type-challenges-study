<h1>Reverse <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23tuple-999" alt="#tuple"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/03192-medium-reverse)

<h2> Problem </h2>

Implement the type version of `Array.reverse`

For example:

```typescript
type a = Reverse<["a", "b"]>; // ['b', 'a']
type b = Reverse<["a", "b", "c"]>; // ['c', 'b', 'a']
```

<h2> My Solution </h2>

```ts
type Reverse<T extends unknown[]> = T extends [infer F, ...infer R]
  ? [...Reverse<R>, F]
  : T;
```

<h2> Notes </h2>

The condition `T extends [infer F, ...infer R]` checks if `T` is an array with at least one element. At the same time, it infers the type of the first element as `F` and captures the remaining elements in the `R` tuple using `infer` keyword.

If `T` has at least one element, `Reverse<R>` is recursively called to reverse the remaining elements in `R` and obtain the reversed array result.

Also, the first element `F` is then added at the end of the reversed array result using `[...Reverse<R>, F]`.

This recursive process continues until `T` becomes an empty array, indicating that there are no more elements left to reverse. In this case, the base case is triggered, and the empty array `T` is returned as is.
