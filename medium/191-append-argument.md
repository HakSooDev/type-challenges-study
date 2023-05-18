<h1>Append Argument <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23arguments-999" alt="#arguments"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/00191-medium-append-argument)

<h2> Problem </h2>

For given function type `Fn`, and any type `A` (any in this context means we don't restrict the type, and I don't have in mind any type 😉) create a generic type which will take `Fn` as the first argument, `A` as the second, and will produce function type `G` which will be the same as `Fn` but with appended argument `A` as a last one.

For example,

```typescript
type Fn = (a: number, b: string) => number;

type Result = AppendArgument<Fn, boolean>;
// expected be (a: number, b: string, x: boolean) => number
```

<h2> My Solution </h2>

```ts
type AppendArgument<Fn extends Function, A> = Fn extends (
  ...args: infer R
) => infer C
  ? (...args: [...R, A]) => C
  : never;
```

<h2> Notes </h2>

The `Fn extends Function` constraint ensures that `Fn` must be a subtype of the `Function` type, triggering a TypeScript error if the given type is not a function type. For example `AppendArgument<unknown, undefined>` throws ts error.

The conditional clause `Fn extends (...args: infer R) => infer C` allows capturing the parameter types and the return type of the function type `Fn` and assigns them to the type variables `R` and `C` using `infer` keyword.

As we re-write the conditional clause `Fn extends (...args: infer R) => infer C`, we are able to capture parameters and return type, assign them to type variable `R` and `C`.

The resulting function type appends the type `A` after the original arguments type `R` and keeps the return type unchanged as `C`, representing the original function's return type.

The usage of `never` in the else branch denotes an impossible scenario because the constraint `Fn extends Function` guarantees that `Fn` will be a `function` type.

<h3> Ref </h3>

- https://www.zhenghao.io/posts/ts-never#denote-theoretically-unreachable-conditional-branches
