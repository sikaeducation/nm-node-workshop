# TypeScript Functions

Since JavaScript functions can be stored in values, functions have types like any other value. While many types in TypeScript can be inferred, function parameters must be explicitly typed.

## Format

The general format for typing a function is:

```ts
function someFunction(firstParameter: FirstParameterType, secondParameter: SecondParameterType): ReturnType {
  // Body
}
```

This also directly translates to the other syntaxes for writing functions:

```ts
const functionExpression = function(firstParameter: FirstParameterType, secondParameter: SecondParameterType): ReturnType {
  // Body
}
const arrowFunction = (firstParameter: FirstParameterType, secondParameter: SecondParameterType): ReturnType => {
  // Body
}
const someObject = {
  someMethod: (firstParameter: FirstParameterType, secondParameter: SecondParameterType): ReturnType => {
    // Body
  },
}
```

TypeScript generally can't infer the types of parameters, but can usually infer the return type. As such, you should generally let TypeScript try to infer the return type:

```js
function add(firstNumber: number, secondNumber: number) { // Return type is inferred as `number`
  return number + number
}
```

## Destructuring Parameters

The syntax for destructuring an object parameter is a little counter-intuitive:

```ts
function someFunction({ someKey }: { someKey: string}){
  // Function body
}
```

TypeScript treats an object and destructuring statements with objects the same, so the type goes in the same place the object would. It is usually easier to read to create a type alias when destructuring:

```ts
type Parameters = {
  someKey: string;
}

function someFunction({ someKey }: Parameters){
  // Function body
}
```

Type aliases can be used in place of their types.

## `void`

There's a built-in type called `void` that represents the value of a function that doesn't return anything:

```ts
function printMessage(message: string): void {
  console.log(message)
}
```

This helps TypeScript know that the function doesn't evaluate to anything so it shouldn't be saved in variables etc.

## `unknown`

`unknown` is a built-in type that represents values with types that aren't known ahead of time. They often get used in functions when the function is just passing the value through to something else:

```ts
function someFunction(someValue: unknown){
  return someOtherFunction(someValue)
}
```

## Watch Out!

* You can make a parameter optional by putting `?` after its name, but optional parameters must go last.
* Parameters can be given default values with `=`, which will also mean they don't need to be explicitly typed.

## Additional Resources

| Resource | Description |
| --- | --- |
| [TypeScript: Functions](https://www.typescriptlang.org/docs/handbook/2/functions.html) | TypeScript's official handbook on functions |
