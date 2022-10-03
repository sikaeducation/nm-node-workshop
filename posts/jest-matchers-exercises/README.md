# Jest Matchers Exercises

Revise the following assertions to use more appropriate matchers

```ts
expect(undefined).toEqual(undefined)
```

```ts
expect(!someString).toEqual(false)
```

```ts
expect(!!someNumber).toEqual(true)
```

```ts
const someString = "Hello, world!"
const containsHello = someString.includes("Hello")
expect(containsHello).toEqual(true)
```

```ts
const someString = "Hello, world!"
const startsWithHello = (/^hello/i).test(someString)
expect(startsWithHello).toEqual(true)
```

```ts
const five = await Promise.resolve(5)
expect(five).toEqual(5)
```

```ts
const array = [1, 2, 3]
expect(array.length).toEqual(3)
```

```ts
const numbers = [1, 2, 3]
const includesThree = numbers.includes(3)
expect(includesThree).toEqual(true)
```

```ts
const array = [{ id: 1 }, { id: 2 }, { id: 3 }]
const includesThree = array.filter(item => item.id === 3).length > 0
expect(includesThree).toEqual(true)
```

```ts
const person = { id: 1, name: "Kyle" }
const hasName = person.hasOwnProperty("name")
expect(hasName).toEqual(true)
```

```ts
const person = { id: 1, name: "Kyle" }
const isKyle = person.name === "Kyle"
expect(isKyle).toEqual(true)
```

```ts
const numbers = [1, 2, 3]
const includesThree = numbers.includes(3)
expect(!includesThree).toEqual(true)
```
