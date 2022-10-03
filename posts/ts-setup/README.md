# TypeScript Setup

## Installation

To add TypeScript to a Node project:

```bash
npm install typescript
```

If the project is not already a Node project, additionally run `npm init -y` to start a `package.json` file.

## Configuration

To generate a `tsconfig.json`:

```bash
npx tsc --init
```

The top-level options for  `tsconfig.json` are as follows:

```json
{
  "compilerOptions": {},
  "include": [],
  "exclude": [],
}
```

The compiler options are ways to customize TypeScript. `include` and `exclude` are arrays of paths to either include or exclude from TypeScript compilation. Here are some basic configurations:

**Node**:

```json
{
  "compilerOptions": {
    "target": "ES2016",
    "outDir": "./dist",
    "lib": ["ESNext"],
    "module": "CommonJS",
    "strict": true,
    "allowJs": false
  },
  "include": [
    "./src/**/*.ts"
  ]
}
```

**Browser**:

```json
{
  "compilerOptions": {
    "target": "ES2016",
    "outFile": "./dist/index.js",
    "lib": ["dom", "ESNext"],
    "strict": true,
    "allowJs": false
  },
  "include": [
    "./src/**/*.ts"
  ]
}
```

* `"target"`: Which version of JavaScript the compiled files should be in.
* `"outFile"`: Which single JavaScript file the TypeScript should be compiled to. Used for browsers to be included in `<script>` tags. Can't be used in addition to a module system.
* `"outDir"`: Which directory to put the compiled JavaScript files, used in Node projects in combination with a module system.
* `"strict"`: Require the strictest type checking.
* `"allowJs"`: Include uncompiled JavaScript files in the project
* `"lib"`: Which built-in types should be included. Include `dom` in browser apps to include typechecking for the `document`, `window`, `navigator`, etc. Include `ESNext` to support all modern JavaScript features.
* `"module"`: Which module system should be used. Use "CommonJS" for Node, leave it of for browsers.

## Compiling

To compile all the TypeScript files in a project, run `npx tsc`. To continuously compile TypeScript files, run `npx tsc --watch`.

## Running In-Place

Most projects don't need to be explicitly compiled. Instead, run a `.ts` file directly with `ts-node`:

```bash
npm install ts-node
npx ts-node index.ts
```

This functions as a drop-in replacement for `node`. Additionally, ESM module compilation will work without any additional configuration. Note that `nodemon` will also work with `.ts` files once `ts-node` is installed:

```bash
npm install ts-node
npx nodemon index.ts
```

## Additional Resources

| Resource | Description |
| --- | --- |
| [What is a tsconfig.json?](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) | Official overview of TypeScript configuration |
| [Intro to the TSConfig Reference](https://www.typescriptlang.org/tsconfig) | Official reference for TypeScript configuration |
