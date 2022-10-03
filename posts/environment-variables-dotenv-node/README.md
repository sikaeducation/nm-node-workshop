# `dotenv`

npm's `dotenv` package is a tool for integrating environment variables in Node applications. To install `dotenv` on a project, run `npm install`:

```js
npm install dotenv
```

Then as early as possible in the application, invoke its `config()` method:

```js
require("dotenv").config()
```

This only needs to be done once. Afterward, all of the environment variables from the `.env` file will be available on the `process.env` object:

```ts
database.type = process.env.DATABASE_TYPE
app.use(morgan(process.env.LOGGING_LEVEL))
const apiUrl = process.env.API_URL
const currentEnvironment = process.env.NODE_ENV
```

## Additional Resources

| Resource | Description |
| --- | --- |
| [Npm: `dotenv`](https://www.npmjs.com/package/dotenv) | Documentation for `dotenv` |
