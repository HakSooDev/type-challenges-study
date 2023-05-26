<h1>PickByType <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23object-999" alt="#object"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/02595-medium-pickbytype)

<h2> Problem </h2>

From `T`, pick a set of properties whose type are assignable to `U`.

For Example

```typescript
type OnlyBoolean = PickByType<
  {
    name: string;
    count: number;
    isReadonly: boolean;
    isEnable: boolean;
  },
  boolean
>; // { isReadonly: boolean; isEnable: boolean; }
```

<h2> My Solution </h2>

```ts
type PickByType<T, U> = { [K in keyof T as T[K] extends U ? K : never]: T[K] };
```

<h2> Notes </h2>

This problem is very similar to [Omit By Type](./2852-omit-by-type.md).

However, when `T[K] extends U` is true, we pick `K` by returning `K` as key instead of ommiting by returning `never`
