<h1>Unshift <img src="https://img.shields.io/badge/-easy-7aad0c" alt="easy"/> <img src="https://img.shields.io/badge/-%23array-999" alt="#array"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/03060-easy-unshift)

<h2> Problem </h2>

Implement the type version of `Array.unshift`

For example

```typescript
type Result = Unshift<[1, 2], 0>; // [0, 1, 2,]
```

<h2> My Solution </h2>

```ts
type Unshift<T extends unknown[], U> = [U, ...T];
```

<h2> Notes </h2>

Similar with [Push](3057-push.md) problem
