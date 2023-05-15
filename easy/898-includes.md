<h1>Includes <img src="https://img.shields.io/badge/-easy-7aad0c" alt="easy"/> <img src="https://img.shields.io/badge/-%23array-999" alt="#array"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/00898-easy-includes)

<h2> Problem </h2>

Implement the JavaScript `Array.includes` function in the type system. A type takes the two arguments. The output should be a boolean `true` or `false`.

For example:

```ts
type isPillarMen = Includes<['Kars', 'Esidisi', 'Wamuu', 'Santana'], 'Dio'> // expected to be `false`
```

<h2> My Solution </h2>

```ts
type Includes<T extends readonly any[], U> = T extends [infer First, ...infer Rest]
  ? Equal<First, U> extends true
    ? true
    : Includes<Rest, U>
  : false;
```

<h2> Notes </h2>

In this problem, we call `Includes<T extends readonly any[], U>` recursively. 
We first check if `T extends [infer First, ...infer Rest]` is true. If there is at least one element in the array, it will be `true`. 
If it is `true`, we take out the first element as `infer First`. Then check if it is `U` type. If it is `true`, it means `T` includes `U` type. The final value will be true. 
However, if `Equal<First, U>` is `false`, we have to call `Includes` recursively with rest of array elements to find the possible `U` type element.
If it cannot find any Equal type until `Rest` becomes empty, `T extends [infer First, ...infer Rest]` will be false. Then the final value will be false. 
