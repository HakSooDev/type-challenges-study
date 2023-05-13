<h1>Parameters <img src="https://img.shields.io/badge/-easy-7aad0c" alt="easy"/> <img src="https://img.shields.io/badge/-%23infer-999" alt="#infer"/> <img src="https://img.shields.io/badge/-%23tuple-999" alt="#tuple"/> <img src="https://img.shields.io/badge/-%23built--in-999" alt="#built-in"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/tree/main/questions/03312-easy-parameters)

<h2> Problem </h2>

Implement the built-in Parameters<T> generic without using it.

For example:

```ts
const foo = (arg1: string, arg2: number): void => {};

type FunctionParamsType = MyParameters<typeof foo>; // [arg1: string, arg2: number]
```

<h2> My Solution </h2>

```ts
type MyParameters<T extends (...args: any[]) => any> =  
T extends (...any: infer R) => any ? [...R] : never
```

<h2> Notes </h2>

There are two `T extends (...args: any[]) => any` in the above code.

The left-hand side `T extends (...args: any[]) => any` is for describing the constraint for `MyParameters`. This checks if given type is a function type.

The right-hand side `T extends (...any: infer R) => any` is a part that we redefine the function type in order to get the arguments placeholder `infer R`. 

Simply saying, we need to access the parameter `args`. The way we can access is redefining the function and introducing a placeholder `infer R`. This allows us to use `R`. 



<h3> Ref </h3>

- https://driip.me/b812974b-3974-46e3-829e-1476b9b30c94
- https://www.typescriptlang.org/docs/handbook/2/generics.html
