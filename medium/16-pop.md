<h1>Pop <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23array-999" alt="#array"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/00016-medium-pop)

<h2> Problem </h2>

Implement a generic `Pop<T>` that takes an Array `T` and returns an Array without it's last element.

For example

```ts
type arr1 = ['a', 'b', 'c', 'd']
type arr2 = [3, 2, 1]

type re1 = Pop<arr1> // expected to be ['a', 'b', 'c']
type re2 = Pop<arr2> // expected to be [3, 2]
```

<h2> My Solution </h2>

```ts
type Pop<T extends any[]> = T extends [...infer A, infer B] ? A : T
```

<h2> Notes </h2>

The important point in this question is that we can `infer` the given type as we want. 
`T extends [...infer A, infer B]` is a conditional type to check if `T` is assignable to `[...infer A, infer B]`. 
`...infer A` holds the rest of first elements excluding the last element. `infer B` holds the last element in the array. 
For example, `infer A` will be `['a', 'b']` and `infer B` will be `c` in `['a', 'b', 'c']` example.

Since we do not need the last element, we can just return `A`.

Please note that there is a tiny edge case.
When given array is empty, `T extends [...infer A, infer B]` is false, so we have to just return `T` which is empty array. 




