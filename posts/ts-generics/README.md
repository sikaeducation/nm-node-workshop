# TypeScript Generics

Generics are placeholders for type. You can indicate that multiple things need to be the same type, without specifying what they are ahead of time.

```ts
type Filter = {
  <T>(array: T[], fn: (item: T) => boolean): T[]
}
type Map = {
  <T, U>(array: T[], fn: (item: T) => U): U[]
}

type Whatever = <T = string>(T): boolean // default value
```

* Generics are like placeholder types
* `<T, U, V>` are the TS conventions, but they can be anything, including descriptive words
* Concrete types are bound at compile time, and are compiled differently for each instance
* Generic types generally inferred well, but may need to be explicitly bound as well (eg. Promises resolution values)

Generics can be scoped two different ways:

```ts
// Per signature
type Filter = {
  <T>(array: T[], fn: (item: T) => boolean): T[]
}
// or
type Filter = <T>(array: T[], fn: (item: T) => boolean): T[]
let filter: Filter = //

// For all signatures
type Filter<T> = {
  (array: T[], fn: (item: T) => boolean): T[]
}
// or
type Filter<T> = (array: T[], fn: (item: T) => boolean): T[]
let filter: Filter<number> = //
```

You can also use generics in type aliases, and pass those like parameters:

```ts
type SomeType<T> = {
  someKey: T
  someOtherKey: string
}

type SomeOtherType<T> = {
  someKey: SomeType<T>
  someOtherKey: boolean
}

type SomeConcreteType = SomeOtherType<string>
```

You can "bound" generics to at least be some concrete type (including joins and intersections), which preserves the original type while still bounding it.

```ts
type NodeMapper = <T extends TreeNode>(item: T[]): T
type NodeMapper = <T extends TreeNode & OtherNode>(item: T[]): T
```

