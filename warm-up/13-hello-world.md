<h1>Hello World <img src="https://img.shields.io/badge/-warm--up-teal" alt="warm-up"/> </h1>

> [Problem link](https://github.com/type-challenges/type-challenges/tree/main/questions/00013-warm-hello-world)

<h2> Problem </h2>
Hello, World!

In Type Challenges, we use the type system itself to do the assertion.

For this challenge, you will need to change the following code to make the tests pass (no type check errors).

```ts
// expected to be string
type HelloWorld = any;
```

```ts
// you should make this work
type test = Expect<Equal<HelloWorld, string>>;
```

<h2> My Solution </h2>

```ts
type HelloWorld = string;
```
