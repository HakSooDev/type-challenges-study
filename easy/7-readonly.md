<h1>Readonly <img src="https://img.shields.io/badge/-easy-7aad0c" alt="easy"/> <img src="https://img.shields.io/badge/-%23built--in-999" alt="#built-in"/> <img src="https://img.shields.io/badge/-%23readonly-999" alt="#readonly"/> <img src="https://img.shields.io/badge/-%23object--keys-999" alt="#object-keys"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/tree/main/questions/00007-easy-readonly)

<h2> Problem </h2>
Implement the built-in `Readonly<T>` generic without using it.

Constructs a type with all properties of T set to readonly, meaning the properties of the constructed type cannot be reassigned.

For example:

```ts
interface Todo {
  title: string;
  description: string;
}

const todo: MyReadonly<Todo> = {
  title: "Hey",
  description: "foobar",
};

todo.title = "Hello"; // Error: cannot reassign a readonly property
todo.description = "barFoo"; // Error: cannot reassign a readonly property
```

<h2> My Solution </h2>

```ts
type MyReadonly<T> = { readonly [K in keyof T]: T[K] };
```

<h2> Notes </h2>

`readonly` makes a property as read-only. Read-only property can be accessed outside the class, but value cannot be changed. They must be initialized at declaration or initialized inside the class constructor.

<h3> Ref </h3>

- https://www.tutorialsteacher.com/typescript/typescript-readonly
