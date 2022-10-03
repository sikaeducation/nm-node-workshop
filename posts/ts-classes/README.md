# TypeScript Classes

TypeScript adds several new features to JavaScript classes.

## Types

A class functions as a type in TypeScript:

```ts
class Person {
  constructor(firstName: string, lastName: string){
    this.firstName = firstName
    this.lastName = lastName
  }
}
const kyle = new Person("Kyle", "Coberly")
kyle.firstName  // "Kyle"
kyle.age        // Type error
```

This is the one place where type-level code and value-level code overlap. Note that TypeScript also checks the type of the constructor:

```ts
class Person {
  constructor(firstName: string, lastName: string){
    this.firstName = firstName
    this.lastName = lastName
  }
}
const kyle = new Person("Kyle") // Error, missing lastName
```

## Interfaces

Interfaces can be used to ensure that a class has particular properties and methods:

```ts
interface Person {
  firstName: string;
  lastName: string;
}

class Student implements Person {
  constructor(firstName){
    this.firstName = firstName
  }
}
// Type error, `Student` class is missing property "lastName"
```

These function the same as type aliases in functional code:

```ts
type Person = {
  firstName: string;
  lastName: string;
  shout: (message: string) => void;
}

// Same thing
interface Person {
  firstName: string;
  lastName: string;
  shout: (message: string) => void;
}
```

This is a key part of abstraction. When writing code that interfaces with classes, rely on their interfaces not their implementations.

## Access Modifiers

Access modifiers control where properties and methods are visible:

* `public` means anything can access it
* `private` means only other properties and methods on this object can access it
* `protected` is like `private`, except subclasses of the class can also access it

```ts
class SomeSuperClass {
  public somePublicProperty = "some public property"
  protected someProtectedProperty = "some protected property"
  private somePrivateProperty = "some private property"
  someMethod(){
    console.log(this.someProtectedProperty) // OK
    console.log(this.somePrivateProperty) // OK
  }
}
class SomeSubClass extends SomeSuperClass {
  someMethod(){
    console.log(this.someProtectedProperty) // OK
    console.log(this.somePrivateProperty) // Error
  }
}

const someObject = new SomeSubClass()
someObject.somePublicProperty // "some public property"
someObject.someProtectedProperty // Error
someObject.somePrivateProperty // Error
```

Much like how `const` protects against accidental reassignment in functional code, `private` is a good default for properties and methods. Ony make something `public` if it actually needs to be accessed outside the class.

## `readonly`

All properties and methods in JavaScript classes are mutable by default. You add `readonly` to keep them from being reassigned:

```ts
class SomeClass {
  readonly someProperty = "This can't change"
  someOtherProperty = "This can change"
}
```

You can combine this with other keywords such as access modifiers and static.

## Others

* Classes can use generics just like functions: `const someProduct = new Product<Service>`
* TypeScript offers abstract classes. They work a lot like interfaces, except a class can only use one and they can also include default implementations.
* If you redeclare an interface, the interfaces will merge together
* It's possible to specify `this` as the return type of a class method

## Watch Out!

Note that TypeScript doesn't differentiate between a class that has a particular name and something that has the same properties and methods.

```ts
class Person {
  constructor(name){
    this.name = name
  }
}
class Student {
  constructor(name){
    this.name = name
  }
}

const steve: Student = new Person("Steve") // OK
```

## Additional Resources

| Resource | Description |
| --- | --- |
| [TypeScript: Classes](https://www.typescriptlang.org/docs/handbook/2/classes.html) | TypeScript's official guide to classes |
