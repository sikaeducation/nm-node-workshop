# TypeScript Configuration

## Installing TypeScript

To add TypeScript to a project, first make sure you've initialized a Node project with `npm init`. Then, run `npm install -D typescript` to add the TypeScript compiler to the project.

Once TypeScript is installed, you can generate a new `tsconfig.json` file with `npx tsc --init`. This is the primary configuration file for the TypeScript compiler.

## Configuring `tsconfig.json`

Every TypeScript project needs a `tsconfig.json` that says where the source files are, where the build files should go, what browsers should be targeted, and more:

```json
{
  "compilerOptions": {
    // Compatibility
    "lib": ["DOM", "ESNext"],     // What built-in stuff exists in the environment?
    "target": "es2015",           // Which JS version should your code compile to?

    // Smart default options
    "strict": true,               // Require all of your code to have types
    "module": "commonjs",         // What module system are you using?
    "sourceMap": true,            // Improves debugging messages

    // Output
    "outDir": "dist"              // Where should the compiled .js code go?
  },
  "include": [                    // Where are your .ts files?
    "src"                         // Path is relative to this file
  ]
}
```

## Setting Up ESLint

Install ESLint and the necessary TypeScript plugins:

```bash
npm install -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

Create an `.eslintrc` file in the project root with these defaults:

```json
{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "@typescript-eslint"
  ],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended"
  ]
}
```

## Installing Types For Libraries

Whenever you add a new library like `lodash` or `react`, you may also need to install its types. If official types exist for the library, it is probably under the `@types` package on npm from the organization DefinitelyTyped. You can install it like this:

```bash
npm install lodash
npm install -D @types/lodash
```

## Running TypeScript

To compile all of your TypeScript code once, run `npx tsc`. To continuously compile all of your TypeScript code, run `npx tsc --watch` to continuously recompile your code as you write it.

## Additional Resources

| Resource | Description |
| --- | --- |
| [TSConfig Reference](https://www.typescriptlang.org/tsconfig) | The official reference for TypeScript configuration |
| [ESLint for TypeScript](https://khalilstemmler.com/blogs/typescript/eslint-for-typescript/) | Really well-written blog post on using ESLint with TypeScript |
