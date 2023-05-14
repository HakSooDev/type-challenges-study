<h1>OmitByType <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23object-999" alt="#object"/></h1>


> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/02852-medium-omitbytype)

<h2> Problem </h2>

From `T`, pick a set of properties whose type are not assignable to `U`.

For Example

```typescript
type OmitBoolean = OmitByType<{
  name: string
  count: number
  isReadonly: boolean
  isEnable: boolean
}, boolean> // { name: string; count: number }
```

<h2> My Solution </h2>

```ts
type OmitByType<T, U> = {[K in keyof T as T[K] extends U ? never : K ]: T[K]  }
```


<h2> Notes </h2>

First, we create a mapped type using `K in keyof T` to loop through all the properties in `T`. 
While looping through, we have to check whether the type of property `K` in `T` extends `U` type. 
We already have a property `K`. But we do not know type of `K` in `T` which can be written as  `T[K]`.
This is when `as` keyword comes in. `as` asserts the type. We let the typescript knows that we need a type of property(`K`) in the given type (`T`). Finally this can be written as `[K in keyof T as T[K]`. 

Then last thing, we check if this extends given `U`. 
If it extends, we include this property as we return mapped type key `K`, otherwise omitted as we return `never` in mapped type key. ([Link](https://www.zhenghao.io/posts/ts-never#filter-out-keys-in-mapped-types))

`as` keyword seems like it is doing typecasting. However it only tells the compiler to consider this type to another type. It has nothing to do with actual data type. 

Also, what we did in the above is called `Key Remapping` ([Link](https://www.typescriptlang.org/docs/handbook/2/mapped-types.html#key-remapping-via-as))

<h3> Ref </h3>

- https://www.typescriptlang.org/docs/handbook/2/mapped-types.html
- https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#type-assertions
- https://www.zhenghao.io/posts/ts-never#filter-out-keys-in-mapped-types
- https://www.zhenghao.io/posts/ts-never#filter-out-keys-in-mapped-types