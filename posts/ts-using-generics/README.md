# TypeScript: Using Generics

Generics are a powerful tool for making types configurable. Building your own generic types is a fairly complicated topic, but it's easy to start using existing generics.

```ts
const $li = document.querySelector<HTMLLIElement>("li")
```

When a function uses a generic, put `<>` after its name and put any types that it accepts inside. It's like passing arguments into a function, except for types!
