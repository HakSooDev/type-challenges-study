<h1>Construct Tuple <img src="https://img.shields.io/badge/-medium-d9901a" alt="medium"/> <img src="https://img.shields.io/badge/-%23tuple-999" alt="#tuple"/></h1>

> [Problem link](https://github.com/type-challenges/type-challenges/blob/main/questions/07544-medium-construct-tuple)

<h2> Problem </h2>

Construct a tuple with a given length.

For example

```ts
type result = ConstructTuple<2>; // expect to be [unknown, unkonwn]
```

<h2> My Solution </h2>

```ts
type ConstructTuple<
  L extends number,
  R extends unknown[] = []
> = L extends R["length"] ? R : ConstructTuple<L, [unknown, ...R]>;
```

<h2> Notes </h2>

The generic parameter `L` is constrained to be a subtype of `number`, ensuring that the value passed as `L` is a number or a type that can be assigned to a `number`. This constraint guarantees that `L` represents the desired length of the `tuple` and enables type safety.

The generic parameter `R` represents the current state of the tuple being constructed. If no value is explicitly provided for `R`, it is initialized as an empty array (`[]`). This initialization sets the initial state for the construction of the `tuple`.

The conditional type `L extends R["length"]` acts as the base case for the recursive call. It checks if the length of `R` matches the desired length `L`. When the lengths match, indicating that the `tuple` is fully constructed, the type alias returns `R`, representing the completed tuple.

If `L extends R["length"]` is `false`, it means that `R` is not yet filled up to the desired length `L`. In this case, the type alias recursively calls `ConstructTuple` with the same `L` value and an updated `tuple`. The updated `tuple` is created by adding an `unknown` element to the beginning of `R`. This recursion continues until the base case is reached, and the desired length is achieved.
