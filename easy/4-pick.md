<h1>Pick <img src="https://img.shields.io/badge/-easy-7aad0c" alt="easy"/> <img src="https://img.shields.io/badge/-%23union-999" alt="#union"/> <img src="https://img.shields.io/badge/-%23built--in-999" alt="#built-in"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/00004-easy-pick/README.md)

<h2> Problem </h2>

Implement the built-in `Pick<T, K>` generic without using it.

Constructs a type by picking the set of properties `K` from `T`

For example:

```ts
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

type TodoPreview = MyPick<Todo, "title" | "completed">;

const todo: TodoPreview = {
  title: "Clean room",
  completed: false,
};
```

<h2> My Solution </h2>

```ts
type MyPick<T, K extends keyof T> = { [P in K]: T[P] };
```

<h2> Notes </h2>

`keyof` takes an object type and produces a string or numeric literal union of its keys

`in` takes the value of the union type, mainly used for the construction of arrays and objects

<h3> Ref </h3>

- https://github.com/type-challenges/type-challenges/issues/13427
- https://www.typescriptlang.org/docs/handbook/2/keyof-types.html
- https://yceffort.kr/2022/03/typescript-omit-exclude-pick#pick
