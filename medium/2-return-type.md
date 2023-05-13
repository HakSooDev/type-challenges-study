<h1>Get Return Type <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23infer-999" alt="#infer"/> <img src="https://img.shields.io/badge/-%23built--in-999" alt="#built-in"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/00002-medium-return-type)

<h2> Problem </h2>

Implement the built-in `ReturnType<T>` generic without using it.

For example

```ts
const fn = (v: boolean) => {
  if (v)
    return 1
  else
    return 2
}

type a = MyReturnType<typeof fn> // should be "1 | 2"
```

<h2> My Solution </h2>

```ts
type MyReturnType<T extends (...args: any) => any> = T extends (...args: any) => infer R ? R : never
```


<h2> Notes </h2>

The important point in the above code is that we re-write `extends` clause of a conditional type to introduce a type to be inferred with `infer` keyword.
Since now we have `infer R`, we can return this. 

<h3> Ref </h3>

- https://github.com/Microsoft/TypeScript/pull/21496
- https://jkchao.github.io/typescript-book-chinese/tips/infer.html#%E4%BB%8B%E7%BB%8D
- https://dev.to/aexol/typescript-tutorial-infer-keyword-2cn