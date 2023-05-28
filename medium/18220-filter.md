<h1>Filter <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23array-999" alt="#array"/> <img src="https://img.shields.io/badge/-%23filter-999" alt="#filter"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/18220-medium-filter)

<h2> Problem </h2>

Implement the type `Filter<T, Predicate>` takes an Array `T`, primitive type or union primitive type `Predicate` and returns an Array include the elements of `Predicate`.

<h2> My Solution </h2>

```ts
type Filter<T extends any[], P, A extends any[] = []> = T extends [
  infer F,
  ...infer R
]
  ? F extends P
    ? Filter<R, P, [...A, F]>
    : Filter<R, P, A>
  : A;
```

<h2> Notes </h2>

`Filter` is defined with three type parameters:

`T` represents the input tuple.
`P` represents the type you want to filter on.
`A` represents the accumulator, which is initially an empty array.

`T extends [infer F, ...infer R]` checks if the input tuple `T` is an array with at least one element. If it is, it uses tuple spreading to `infer` the first element as `F` and the rest of the tuple as `R`.
Inside the conditional type, it checks if the type of the first element `F` matches the type `P`.

If it does, it recursively calls `Filter` with the remaining elements `R`, the type `P`, and a new accumulator array `[...A, F]`. This means the current element `F` satisfies the filter condition, so it is appended to the accumulator.

If the type of the first element `F` does not match `P`, it recursively calls `Filter` with the remaining elements `R`, the type `P`, and the existing accumulator array `A`. This means the current element `F` does not satisfy the filter condition, so it is not appended to the accumulator.

Finally, when the input tuple `T` is empty (i.e., there are no more elements to process), the type `A` (the accumulator) is returned as the result of the filtering operation.

In the solutions, I found out simpler answer.

```ts
type Filter<T extends unknown[], P> = T extends [infer F, ...infer R]
  ? F extends P
    ? [F, ...Filter<R, P>]
    : Filter<R, P>
  : [];
```

The updated implementation avoids introducing an additional accumulator parameter `A`. Instead, it directly spreads the result of the recursive `Filter<R, P>` call inside the returning array.

<h3> Ref </h3>

- https://github.com/type-challenges/type-challenges/issues/20070
