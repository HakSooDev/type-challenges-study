<h1>Shift <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23array-999" alt="#array"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/03062-medium-shift)

<h2> Problem </h2>

Implement the type version of `Array.shift`

For example

```typescript
type Result = Shift<[3, 2, 1]>; // [2, 1]
```

<h2> My Solution </h2>

```ts
type Shift<T extends any[]> = T extends [infer A, ...infer R] ? R : [];
```

<h2> Notes </h2>

`T extends any[]` ensures that `T` is an `array` or `tuple` type. This triggers ts-error when `unknown` type is given. For example `Shift<unknown>` throws ts error.

`T extends [infer A, ...infer R]` checks if `T` extends an `array` or `tuple` type with at least one element. It uses the `infer` keyword to capture the first element's type as `A` and the remaining elements as `R`.

If `T` satisfies the condition above, then `Shift<T>` evaluates to `R`, which represents the remaining elements after removing the first element.
If `T` does not satisfy the condition, meaning it is an empty array or tuple, then `Shift<T>` evaluates to `[]`, indicating an empty array as there are no elements to remove.
