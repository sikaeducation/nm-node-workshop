# Intro to TypeScript

JavaScript is a dynamically typed language. That means that the data type of a value can be freely changed in the code:

```js
let a = 1     // a is a number
a = "Hello!"  // a changes to a string

const person = {
  firstName: "Ray",
  lastName: "Charles",
}

function printFullName(person){
  console.log(`${person.firstName} ${person.lastName}`) // Assumes person is an object with `firstName` and `lastName` properties
}
```

How do we know that the value passed into `printFullName` will be an object with `firstName` and `lastName` properties? How do we know if it's an object at all? We could add guard clauses:

```js
function printFullName(person){
  if (typeof person !== "object" || !person.firstName || !person.lastName ){
    throw new Error("Got wrong data type")
  }
  console.log(`${person.firstName} ${person.lastName}`)
}
```

This helps, but it still requires actually running the code with real values to see if there's a problem. Static typechecking is a technique where your code is automatically analyzed for situations where it's possible to give something the wrong data type and you're alerted before your code is ever run. TypeScript is a tool that adds static typechecking to JavaScript:

```js
let a = 1     // a is a number
a = "Hello!"  // error, a is a number

type Person = {
  firstName: string;
  lastName: string;
}

function printFullName(person: Person){
  console.log(`${person.firstName} ${person.lastName}`)
}

printFullName({ firstName: "Ray", lastName: "Charles"}) // Works
printFullName({ firstName: "Ray" })                     // Error, missing `lastName` property!
```

This helps catch errors in the code before it's even run, saving time and frustration down the road.

## TypeScript Concepts

### Compile-Time vs. Run-Time Errors

Code errors can happen in two places: When the computer is compiling the code and when the computer is running the code. Compile-time errors are great because they catch mistakes immediately. Run-time errors are bad because at best they got caught by a well-written test and at worst they get caught by your users. The goal of static typing is to convert run-time errors into compile-time errors.

### Typechecking and Type Safety

While the code that you write is TypeScript, your browser still ultimately needs it to be JavaScript. TypeScript code is run through a tool called a typechecker, confirms that all of the types are used correctly, and then takes all of the type-specific code out. The result is plain JavaScript that can be run in any JavaScript environment, but with the added confidence that there aren't type errors in it. This is called _type safety_, and code that has been typechecked is called _typesafe_.

### Type-level Code vs. Value-level code

TypeScript code happens on two levels:

* Type-level code describes the types being used. This code is stripped out when the code is transpiled to JavaScript.
* Value-level code describes the actual logic of the application. This code is left in when the code is transpiled to JavaScript.

```ts
type Person = {       // Type-level code
  firstName: string;
  lastName: string;
}

function printFullName(person: Person){ // function definition and parameter name is value-level, annotation is type-level
  console.log(`${person.firstName} ${person.lastName}`) // Value-level code
}
```

## Basic TypeScript Syntax

TypeScript code is typically written in files that end in `.ts` and transpiled to `.js` files by the typechecker. TypeScript is a superset of JavaScript, meaning that all valid JavaScript code is also valid TypeScript code.

TypeScript uses a syntax called _postfix_ (think: opposite of "prefix") types. That means any value can be typed by adding (or _annotating_) the type to it:

```ts
let a: number = 1;  // OK
a = 1;              // Type error
```

You can remember the postfix syntax by thinking "You see this value? Here's its type!"

One of the best parts about TypeScript is that the typechecker can usually figure out what a type is from usage without needing any annotations:

```ts
let a = 1;  // OK
a = 1;      // Type error
```

This is called _type inference_. Generally speaking, it's better to let TypeScript infer types on its own than to explicitly annotate them everywhere. One of the few places where TypeScript can't infer types are function parameters:

```js
function printMessage(message: string){
  console.log(`Ahoy! ${message}`)
}
printMessage("I'm walkin' over here!")  // OK
printMessage(true)                      // Error
```

Note that type annotations always go with definitions (variable declarations, function parameters, classes), not uses (variable assignment, function arguments, object creation).

## Additional Resources

| Resource | Description |
| --- | --- |
| [TypeScript for the New Programmer](https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html) | TypeScript's official introductory overview |
| [TypeScript for JavaScript Programmers](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html) | TypeScript's official overview for JavaScript developers |
| [The TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html) | TypeScript's official handbook |
| [TypeScript Examples](https://www.typescriptlang.org/play) | TypeScript's interactive playground. Check the "Examples" section for working samples of different TypeScript features. |
