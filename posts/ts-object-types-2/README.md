# TypeScript Object Types: Records and Narrowing

## Record Types

These allow you to type keys and all values for things like dictionary lookups:

```ts
type ProductID = string
type AvailabilityTypes = 'sold_out' | 'in_stock' | 'pre_order'
type Availability = {
  availability: AvailabilityTypes
  amount: number
}

const store: Record<ProductID, Availability> = {
  '0d3d8fhd': { availability: 'in_stock', amount: 23 },
  '0ea43bed': { availability: 'sold_out', amount: 0 },
  '6ea7fa3c': { availability: 'sold_out', amount: 0 },
}
```

## Type Literals

If you don't explicitly type an object, TypeScript infers the type very widely:

```ts
const someObject = {
  someKey: "Some Value",
  anotherKey: 42,
}

/*
Inferred type is:

{
  someKey: string;
  anotherKey: number;
}
*/
```

This can be a problem if it's important that the object have specific values, such as dictionary lookups. To narrow an object to the actual values you used, use `as const`:

```ts
const someObject = {
  someKey: "Some Value",
  anotherKey: 42,
} as const

/*
Inferred type is:

{
  someKey: "Some Value";
  anotherKey: 42;
}
*/
```

* Ordinarily, types need to be exported and imported just like values do to use them in different modules. However, since types and values use different namespaces, you can export and import both of them at the same time. These are called "companion objects."
