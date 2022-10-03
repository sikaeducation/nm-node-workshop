# ts-arrays
### Improving Type Inference for Tuples

Ordinary tuples infer pretty wide:

```ts
let a = [1, true] // (number | boolean)[]
```

Make function that spreads the arguments, and they'll get typed by position:

```ts
function tuple<T extends unknown[]>(...types: T): T {
  return types
}

let a = tuple([1, true]) // [number, boolean]
```

