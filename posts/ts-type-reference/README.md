# TypeScript Type Reference

## Built-In Types

* **`any`**: Set of all values, which you can do anything with. Use a last resort. Top type.
* **`unknown`**: Set of all values, but can only do comparison. If you check the type with `if (typeof thing === 'number')`, you can do type-specific operations. Better than `any`.
* **`boolean`**: Two values, you can compare them or negate them. You can annotate it as being a specific boolean (type literal), otherwise can always be inferred.
* **`number`**: All numbers, `NaN`, and `Infinity`. All numeric operations. Also can always be inferred.
* **`bigint`**: New, very large numbers.
* **`string`**: Set of all strings, can concat, slice, etc. Also can always be inferred.
* **`symbol`**: Can be annoted as unique. Rare. Just like a type literal.
* **`object`**: Must specify the shape of the object. Can be inferred. Inferring doesn't do literal values since values are reassignable. Avoid emtpy objects, TS won't infer them correctly.
* **Arrays- `T[]` or `Array<T>`, eg `string[]`**: Explicitly type. Typescript won't narrow your types if you create an array with an empty literal, it will just add each type to its inference. Keep arrays homogenous, or you have to type check them every time you want to do something with one of them.
* **Tuples- `[T...]`, eg. `[string, boolean]`**: Mixed types. Have to declare up front or TS will assume its an array.
* **`null`**: One value. Absence of value, eg. an error prevented something from being calculated. It's the subtype of all types except `never`, which means that every type is nullable, which means you always have to check if something exists first. `strictNullChecks` prevents this.
* **`undefined`**: One value. Never assigned.
* **`void`**: No explicit return value (eg. `console.log`)
* **`never`**: No values. A function that never stops running, an exception throwing. The "bottom type," a proposition that's always false.

## Operators and Utilities Reference

### Type Operators

| Type operator      | Syntax                  | Use on                                   |
| ------------------ | ----------------------- | ---------------------------------------- |
| Type query         | `typeof`, `instanceof`  | Any type                                 |
| Keys               | `keyof`                 | Objects                                  |
| Property lookup    | `O[K]`                  | Objects                                  |
| Mapped type        | `[K in O]`              | Objects                                  |
| Add/Sub Modifier   | `+`/`-`                 | Objects                                  |
| Read-only Modifier | `readonly`              | Objects, Arrays, Tuples                  |
| Optional Modifier  | `?`                     | Objects, Arrays, Tuples, Function Params |
| Nonnull Assertion  | `!`                     | Nullable types                           |
| Generic Default    | `=`                     | Generic types                            |
| Type assertion     | `as`, `<>`              | Any type                                 |
| Type guard         | `is`                    | Function return types                    |

### Type Utilities

| Type utilities             | Used on                 | Description                                            |
| -------------------------- | ----------------------- | ------------------------------------------------------ |
| `ConstructorParameters<>`  | Class constructors      | Tuple of parameter types                               |
| `Exclude<>`                | Union types             | Exclude a type from another type                       |
| `Extract<>`                | Union types             | Select a subtype that's assignable to another type     |
| `InstanceType<>`           | Class constructors      | The type you get from newing a constructor             |
| `NonNullable<>`            | Nullable types          | Exclude null and undefined from a type                 |
| `Parameters<>`             | Function types          | Tuple of a function's parameter types                  |
| `Partial<>`                | Object types            | Make all properties in an object optional              |
| `Pick<>`                   | Object types            | A subtype of an object type, with a subset of its keys |
| `Readonly<>`               | Arrays, objects, tuples | Make all properties or keys readonly                   |
| `ReadonlyArray<>`          | Any type                | Make an immutable array of the type                    |
| `Record<>`                 | Object types            | Map from a key type to a value type                    |
| `Required<>`               | Object types            | Make all properties in an object required              |
| `ReturnType<>`             | Function types          | A function's return type                               |
