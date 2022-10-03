## Guide to TypeScript Escape Hatches

Use rarely.

## Non-Null Assertions

You can tell the typechecker that you're confident that something isn't null or undefined with `!`:

```ts
type Something = {
  id?: number;
}

let something: Something = { id: 2 }

find(something.id!)
```

This is usually a sign that you need some refactoring to multiple types.

### Definite Assignment Assertions

Tell the typechecker that something will definitely have a value before it's used:

```ts
let userId!: string

assignId()

userId.toUpperCase()
```

## Type Assertions

You can widen a type using `as`.

```ts
// Example
```

Note that if TypeScript doesn't think the types are similar enough, you will need to widen it all the way to `unknown` first:

```ts
(string as unknown as number)
```

Tell Typescript to assign a related type:

```ts
let someVariable: string | number = "hi"
someFunction(someVariable as string)
someFunction(someVariable as any) // Super unsafe
```

## `any`

Turns off type checking for a particular value. Note that this tends to infect other types.

## `// @ts-nocheck`

Turn off type checking for an entire file.
