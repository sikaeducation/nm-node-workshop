# ts-type-declarations
### Type Declarations

* A file that ends with `.d.ts`
* Can only have types, no values
* Only for code that's visible to consumers (otherwise you could just use the TS code directly). You can compile your code and include type declarations, and now other TS projects don't need to also compile your code. They also provide hinting for editors.
* Can be generated with `tsc -d some-file.ts`
* Can declare that types exist somewhere (eg. globals, imported modules)
* Can be use to generate "ambient types" that don't need to be imported every time
  * Useful for models
* Use `types.ts` for ambient types in a TS project, `filename.d.ts` for JS files

```ts
declare let process: {
  env: {
    NODE_ENV: 'development' | 'production'
  }
}

declare module 'some-module' {
  export type MyType = number
  let myDefaultExport = MyType
  export default myDefaultExport
}
declare module 'unsafe-module'
declare module 'something-with-wildcards*'

//

import someModule from "some-module" // Typed!
import unsafeModule from "unsafe-module" // All types are `any`
import something from "something-wild-wildcards-like-this"
```

Type Lookup Steps for JS files:

1. Look for a sibling `.d.ts` file with the same name as the JS file
2. Otherwise try to infer the types and use JSDoc annotations
3. Otherwise, treat the whole module as `any`

```ts
/**
  * @param word { string } An input string to convert
  * @returns { string } The converted string
  */
export function someFunction(word){
  return word.toLowerCase()
}
```
