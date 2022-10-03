# TypeScript: Narrowing, Widening, and Casting

## Narrowing

Narrow when something is polymorphic.

### Casting

* Casting only happens when something is being called, not defined

```ts
function getSubmissionComponent(
  performance: postedPerformance,
  post: hydratedPost
) {
  const components = {
    submission: (
      <LearnerSubmission
        performance={performance as evaluatedSubmissionPerformance}
        post={post}
      />
    ),
  } as const;
  return components[performance.type];
}
```

You can also cast in place with:

```ts
(someVariable as Whatever).somethingOnlyOnWhatever()
```

### Type Predicates

Note the `is` keyword.

```ts
function isPostedViewPerformance(
  performance: postedPerformance
): performance is postedViewPerformance {
  return (performance as postedViewPerformance).type === "view";
}

function getSubmissionComponent(
  performance: postedPerformance,
  post: hydratedPost
) {
  const components = {
    view: (
      <LearnerViewing
        performance={
          isPostedViewPerformance(performance)
            ? performance
            : (undefined as never)
        }
        post={post}
      />
    ),
  } as const;
  return components[performance.type];
}
```

Can be used to give types to `unknown`.

### Type Guard Functions

Actually return the type, otherwise are similar to type guards.

```ts
function assertPostedViewPerformance(performance: postedPerformance): postedViewPerformance {
  if (!("evaluation" in performance)) {
    throw new Error("Not a postedViewPerformance");
  }
  return performance;
}

function getSubmissionComponent(
  performance: postedPerformance,
  post: hydratedPost
) {
  const components = {
    view: (
      <LearnerViewing
        performance={assertPostedViewPerformance(performance)}
        post={post}
      />
    ),
  } as const;
  return components[performance.type];
}
```

### Type Widening

If you use `const`, the type is the literal value. If you use `let`, it's the base type for the value. You can explitly annotate to narrow it. Reassigning a type from `const` to `let` widens it. `null` and `undefined` are widened to `any`, but given definite types when they leave the scope (like by invoking a function). You can opt out of type widening (recursively!) with `as const`.

```ts
let a = 1 // number
const b = 1 // 1
let c: 1 | 2 = 1 // 1 | 2
let d = { a: { b: "c" }} as const // { readonly a: { readonly b: "c" }}
```

## Using `unknown`

You can widen and then narrow with casting:

```ts
const a: (oldThing as unknown as newThing) = 1
```

This is pretty unsafe and usually means you did something wrong.

### User-Defined Type Guards

Type refinement only works within the scope you're in. So this won't work:

```ts
function isString(a: unknown): boolean {
  return typeof a === "string"
}

function someFunction(a: string | number){
  if (isString(a)){
    a.toUpperCase() // Error, can't call that on numbers
  }
}
```

To fix that, you can use the `is` keyword. This means that the return value is boolean, and the parameter you passed in should be refined. You can only use this with one parameter.

```ts
function isString(a: unknown): a is string {
  return typeof a === "string"
}
```

Type Assertions: Make a type (like `any`) more specific.

```ts
let aString: any = "hey";
let aStringLength = (aString as string)
```

or

```ts
let aString: any = "hey";
let aStringLength = (<string>aString).length;
```

### Refinement

TS does "flow-based type inference", which means it follows the logic of your app and narrows things like union types to their specific types.

#### Discriminated Unions

Flow-based type inference will pick out specific types, but has limits to its logic:

```ts
type a = {a: number, b: string}
type b = {a: array, b: boolean}
type aOrB = a | b

function (someparameter: aOrB){
  if (typeof someParameter.a === "number"){
    someParameter.a // number
    someParameter.b // string | boolean, uh oh
  }
}
```

To fix this, add an extra artificial property that discriminates between them:

```ts
type a = {type: "a", a: number, b: string}
type b = {type: "b", a: array, b: boolean}
type aOrB = a | b

function (someparameter: aOrB){
  if (someParameter.type == "a"){
    someParameter.a // number
    someParameter.b // string
  }
}
```

### Discriminated Unions

Can't be done in a different scope.

```ts
function getSubmissionComponent(
  performance: postedPerformance,
  post: hydratedPost
) {
  const components = {
    view: (
      <LearnerViewing
        performance={
          postedPerformance.type === "posted-performance"
            ? performance
            : (undefined as never)
        }
        post={post}
      />
    ),
  } as const;
  return components[performance.type];
}
```
