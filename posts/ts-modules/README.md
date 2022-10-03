# TS Modules

## Using Modules

* When importing modules, use `npm i -D @types/package-name` to use prebuilt type definitions
    * If it doesn't exist, put the following in a file to declare it as `any`:

```ts
// package-name.d.ts
declare module "package-name";
```

ES2015 modules can be statically analyzed- CommonJS modules cannot.

You can dynamically import a module with `import()`, which returns a promise. This is only allowed in TS with the `"module": "esnext" }` mode. You can pass any expression in, but you'll lose type-safety if it's not a string. To get around this, you can manually annotate the import:

```ts
import { locale } from "./locales/locale-us" // Type

async function something(){
  const locale: typeof locale = await import(somePath)
}
```

You can allow default exports from CommonJS modules with `{ "compilerOptions": { "esModuleInterop": true }}`

TS decides whether to parse a `.ts` file in module mode or script mode based on whether or not there are any `import` or `export` statements.
