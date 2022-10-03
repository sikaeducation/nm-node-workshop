# TypeScript: Objects

Object types look similar to objects:

```ts
type Person = {
  readOnly firstName: string;
  age?: number;
  victoryYell: (message: string) => void;
}

const kyle: Person = {
  firstName: "Kyle",
  age: 12,
  victoryYell: (message) => {
    console.log(`${message}, I'm Kyle!`)
  }
}
```

However, there are a few differences between regular objects and object types:

* Object types are declared using the `type` keyword rather than `const` or `let`. This is called a _type alias_.
* The key/value pairs are separated by semicolons instead of commas
* Objects are conventionally camelCased, custom types are conventionally PascalCased

## Methods

Methods use function signature syntax:

```ts
type Dog = {
  name: string;
  bark: (message: string) => void;
}
```

These look just like one-line arrow functions except they use types in place of the values. Note that parameters still need to be labeled and typed.

## Object Mutability

There are a couple of modifiers that can be used to indicate whether values of objects can change:

```ts
type Person = {
  readonly firstName: string;   // Type must be set when declared and never changed
  lastName?: string;            // Optional, meaning type is string | null
  readonly species: "Human";    // Type is "Human"
}
```

You add additional type-safety to entire objects by adding `as const` to the end of the declaration:

```ts
const person = {
  firstName: "Peter",   // Type is widened to string
  lastName: "Pan",      // Type is widened to string
}

const person = {
  firstName: "Peter",   // Type is narrowed to "Peter"
  lastName: "Pan",      // Type is narrowed to "Pan"
} as const
```

You generally want to make your types as narrow as possible. When typing an object, ask:

* Do you know what values a property will have ahead of time?
* Are any properties going to be a specific values that never change?
* Are any values ever going to not be set?

If the values of an object won't change, use `as const`.

## Watch Out!

* There is an `object` type, but it should not be used. Objects should be typed with the particular properties and methods they contain.
* TypeScript will catch if you add a property to an object that wasn't on the type. This is called _Excess Property Checking_
* You can't declare a type alias twice in the same scope, but types shadow in nested scopes the same way variables do.
* `readonly` is used when defining types, `as const` is used when defining values

## Additional Resources

| Resource | Description |
| --- | --- |
| [TypeScript: Object Types](https://www.typescriptlang.org/docs/handbook/2/objects.html) | TypeScript's official handbook on object types |
