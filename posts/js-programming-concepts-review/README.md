# Programming Concepts with JavaScript

These are general programming concepts as implemented in JavaScript.

## Data Types

A data type determines what kinds of values data can have and what kinds of operations can be done on them. The core data types in JavaScript are:

* `boolean`
* `number`
* `string`
* `null`
* `undefined`
* `object`

Note that `object` includes functions, arrays, DOM elements, and most other kinds of complex data.

Additionally, there are two newer types that less commonly used:

* `symbol`
* `bigint`

## Values

A value is what the unique part of the data is. These are all examples of values:

* `true`
* `false`
* `""`
* `"red"`
* `"camelCase is weird"`
* `0`
* `7`
* `NaN`
* `undefined`
* `null`
* `{}`
* `{ city: "Denver" }`
* `{ name: "Andy", age: 27 }`
* `[]`
* `[1, 2, 3, 4]`
* `["1", "2", "3", "4"]`
* `number => number > 1`

Note that objects, arrays, and functions can all be values while also containing other values, expressions, and statements.

## Operators

Operators act on values, often evaluating to a new value. These are the most common operators in JavaScript:

* Math: `+` `-` `/` `*`, `%`, `**`
  * With assignment: `+=`, `-=`, `*=`, `/=`, `**=`, `++` / `--`
  * Negation: `-someNumber`
  * Coercion: `+someNonNumber`
* Comparison: `>`, `<`, `>=`, `<=`, `!==`, `===`
* Boolean: `&&`, `||`, `!`
* Ternary: `? : `
* Spread: `...`
* Concatenation: `+`
* Assignment: `=`
* Keyword: `delete`, `typeof`, `instanceof`, `in`, `of`

## Expressions

An expression is something that evaluates to a value. All values are expressions (because they evaluate to themselves). These are examples of things that aren't values, but are expressions:

* `4**10`
* `4 / 5`
* `5 !== 6`
* `3 < 7`
* `3 > 7`
* `a + b`
* `[10 % 2]`
* `"1" + "10"`
* `` `My name is ${name}` ``
* `"Sweater".length`
* `!someValue`
* `"Brice" + " " + "Cherry"`
* `someObject.name`
* `someObject.age`
* `someObject["age"]`
* `someObject[location]`
* `[2, 4, 6].includes(2)`
* `[1, 2, 3].find(number => number > 1)`
* `[a, b, c].map(letter => letter === "a")`
* `[a, b, c].map(letter => letter === "a").filter(truthyValue => !truthyValue)`
* `"Brice" && ""`
* `someArray === 4`
* `someArray !== 4`
* `someArray[0]`
* `[...someArray, someValue, ...someOtherArray]`
* `...someArray`
* `{ ...someObject, someProperty: "Some Value", ...someOtherObject }`
* `getName({ name: "Kyle"})`
* `name`

Anything that uses an operator is an expression, as is any function invocation that returns a value.

## Statements

A statement is an instruction to the computer to do something. All variable assignments (including reassignments) and function returns are statements.

* `let a = "Thing"`
* `let x = 4 / 5`
* `let someObject = { name: "Jan" }`
* `const green = "blue"`
* `const anything = someObject.name`
* `const anything = someObject["location"]`
* `const someObject = {}`
* `const name = getName({ name: "Kyle"})`
* `someObject.name = "Jan"`
* `someArray[2] = "March"`
* `return "Hey"`
* `return anything`
* `return someObject.name`

Additionally, any function call that produces a side-effect (like output) is a statement.

* `console.log("anything")`
* `printTheNameToTheScreen({ name: "Kyle"})`
* `[1, 2, 3].map(double).forEach(number => console.log(number))`

## Control Structures

These are neither expressions nor statements, but rather control the sequence of the program:

* `if` / `else` / `else if`
* `switch`
* `for`, `for..in`, `for..of`
* `while`, `do while`
* `try` / `catch`

## Declaration

A declaration creates something new, but doesn't actually do anything with it (including assignment). All of these are examples of declarations:

* `let a` (No assignment)
* `function someFunction() { /*function body here */ }`
* `function* someGeneratorFunction() { /* function body here */ }`
* `async function someAsyncFunction() { /* function body here */ }`
* `class SomeClass { /* class details here */ }`
