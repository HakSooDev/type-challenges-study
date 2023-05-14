<h1>First of Array <img src="https://img.shields.io/badge/-easy-7aad0c" alt="easy"/> <img src="https://img.shields.io/badge/-%23array-999" alt="#array"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/00014-easy-first)

<h2> Problem </h2>

Implement a generic `First<T>` that takes an Array `T` and returns its first element's type.

For example:

```ts
type arr1 = ['a', 'b', 'c']
type arr2 = [3, 2, 1]

type head1 = First<arr1> // expected to be 'a'
type head2 = First<arr2> // expected to be 3
```

<h2> My Solution </h2>

```ts
type First<T extends any[]> = T extends [infer A, ...infer B] ? A : never 
```

<h2> Notes </h2>

This is similar with [3312.parameters](3312-parameters.md) problem.

We re-write `extends` clause of a conditional type on the right-hand side to `infer` the first element in array. 
If empty array is given, `T extends [infer A, ...infer B]` will become false which will return `never` finally. 

```ts
// answer1
type First<T extends any[]> = T extends [] ? never : T[0]

// answer2
type First<T extends any[]> = T['length'] extends 0 ? never : T[0]
```

Also, I found out two different answers. 
These two answers have similar approach. It checks if given array is empty first. If it is, return the first element in `T`, otherwise return never. 
These two answers might be better answer since it does not introduce unnecessary declaration and clearer.   

`never` can be used to denote theoretically unreachable conditional branches. ([Link](https://www.zhenghao.io/posts/ts-never#denote-theoretically-unreachable-conditional-branches))

`infer` can be used to create a local type variable. ([Link](https://www.zhenghao.io/posts/ts-never#denote-theoretically-unreachable-conditional-branches))

<h3> Ref </h3>

- https://github.com/type-challenges/type-challenges/issues/16315
- https://www.zhenghao.io/posts/ts-never
- https://www.zhenghao.io/posts/type-programming#local-variable-declaration
