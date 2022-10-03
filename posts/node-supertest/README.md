# Supertest

Supertest is an Node module that simulates sending HTTP requests to Node servers and allows you to make assertions about the response. It's not a test runner like Jest, but can be used with any test runner.

## Setup

Import the default export of the `supertest` module as `request`. Pass your app into it to make a request and the response will be resolved from it.

```ts
import request from "supertest"
import app from "./app"
import { test } from "jest"

test("App responds to GET requests to /users", async () => {
  const response = await request(app)
    .get("/users")

  expect(response.headers["Content-Type"]).toMatch(/json/)
  expect(response.status).toEqual(200)
  expect(Array.isArray(response.body.users)).toBe(true)
})
```

## Basic API

To make a request, use the name the of the HTTP method:

```ts
request(app).get(somePath)
request(app).post(somePath)
request(app).put(somePath)
request(app).delete(somePath)
request(app).options(somePath)
```

Note that you can set headers with `.set(headerKey, headerValue)` and send a body with `.send(httpBody)`:

```ts
request(app)
  .post("/messages")
  .set("application/Content-Type", "application/json")
  .send(JSON.stringify({ content: "Hello, world!" }))
```

## Role In Testing

Use Supertest to assert the contract of the API, not the logic of your application. Supertest is useful for asserting behavior like "When I make an HTTP GET request to the `/pokemon` API, I get a 200 response with the following headers and the following keys in the response." Details about whether that information is valid should be done by testing the route middleware directly.

## Watch Out!

Supertest expects an application _function_, not the actual running application. For an Express app, that means the two need to be separated:

```ts
// app.ts
import "express" from "express"

const app = express()

app.get("/", (request, response) => {
  response.json({ message: "Hello, world!" })
})

export default app
```

Use a separate application runner to serve the API:

```ts
// index.ts
import "app" from "./app"

app.listen(3000)
```

Now the app can be tested in isolation with Supertest:

```ts
import request from "supertest"
import app from "./app"
import { test } from "jest"

test("Root route works", async () => {
  const response = await request(app).get("/")

  expect(response.status).toBe(200)
})
```

## Additional Resources

| Resource | Description |
| --- | --- |
| [npm: Supertest](https://www.npmjs.com/package/supertest) | Official npm module |
| [GitHub: Supertest](https://github.com/visionmedia/supertest#readme) | Official documentation |
