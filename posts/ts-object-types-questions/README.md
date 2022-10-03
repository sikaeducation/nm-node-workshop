> Write a reasonably narrow type for this object:

```ts
const someObject = {
  optionalProperty: 10,
  thisWillAlwaysBeHello: "Hello",
  someMethod(someString, someOptionalNumber){
    return `${someString}${someOptionalNumber ?? "default"}`
  },
  thisWontChange: "Not changing, but I could have been something else!"
}
```

> Write a type for a table object that has a `legCount`, a color, a length and a width:

> Write a type for a guinea pig object that has a `furColors` property that's an array of strings, an age, a weight, and a method called `wheek` with no parameters and no return value:

> What's the difference between `readonly` and `as const`?

> When should you use the `object` type?

> What is the advantage of narrowing a type as much as possible?

