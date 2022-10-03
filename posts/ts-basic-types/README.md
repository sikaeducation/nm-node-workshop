# TypeScript: Basic Types

There are many different types built into TypeScript, as well as the ability to build your own types. The most simple types mirror the primitive types in JavaScript.

## Primitives

The basic primitive types in TypeScript are the same as JavaScript:

* `string`
* `number`
* `boolean`

```ts
let name: string = "Kyle"
let age: number = 12
let testResult: boolean = true
```

To indicate that something is an array, add `[]` to the type of item in the array:

```ts
let names: string[] = ["Kyle", "Elyse", "Duncan", "Miles"]
let ages: number[] = [12, 13, 9, 6]
let testResults: boolean[] = [true, true, false, true]
```

## Type Inference

In practice, TypeScript can generally infer the types of most variables based on their contents. Even without explicit typing, all of these are typed the same as before:

```ts
let name = "Kyle"       // string
let age = 12            // number
let testResult = true   // boolean

let names = ["Kyle", "Elyse", "Duncan", "Miles"]  // string[]
let ages = [12, 13, 9, 6]                         // number[]
let testResults = [true, true, false, true]       // boolean[]
```

Whenever possible, let TypeScript infer the types instead of explicitly typing things.

## Nullable Types

A type that can also be `null` is called a _nullable type_. To make a type nullable, add `| null` to the end of the type:

```ts
let name: string | null = "Kyle"
name = null // no error
```

Note that instead of `null`, you can often use the empty value for the type instead:

```ts
let name: string = "Kyle"
name = ""

let bookCount: number = 4
bookCount = 0

let isPassed: boolean = true
isPassed = false
```

## Type Literals

Some of the simplest but most powerful types that are narrowed down to specific values:

```ts
type slogan = "Hello, world!"
let headingText: slogan = "Hello, world!"
headingText = "Goodbye, city." // Type error
```

This is done automatically when a primitive value is declared with `const`:

```ts
const headingText = "Hello, world!"
if (headingText === "Goodbye, city."){ // Type error
  //
}
```

## Watch Out!

* Do _not_ use the classes `String`, `Boolean`, and `Number` as types. Use their lowercase equivalents `string`, `boolean`, and `number` instead.
* By default, `null` and `undefined` are assignable to any other type. This is disabled by using `strict: true` in your `.tsconfig.json`.
* `+` coercion doesn't work if the number is possibly null, you need to use the `Number` constructor instead:

```ts
function getRecord(id?: number){
  const normalizedId = +id        // Error
  const normalizedId = Number(id) // Works
}
```

* If you use `let` when you assign a variable, the type of the variable will be whatever the base type of the value is:

```ts
let message = "Hello, world!" // Type is string
```

If you use `const`, it narrows the type to that specific value:

```ts
const message = "Hello, world!" // Type is specifically the string "Hello, world!"
if (message === "Goodbye, room."){
  // Unreachable code
}
```

This is a really nice feature that really helps with text editor hinting.

## Additional Resources

| Resource | Description |
| --- | --- |
| [TypeScript: Everyday Types](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html) | The official guide to basic types. |
