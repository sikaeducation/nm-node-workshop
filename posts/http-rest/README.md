# REST

Representational State Transfer, or REST, is a philosophy for web API design. It has several principles, but these are the most commonly embraced:

* APIs are based on the concept of _resources_, which represent the underlying data. Examples of resources are users, dogs, students, subscriptions, and posts.
* Resources are represented by paths called endpoints. Any particular resource is addressed with an ID. An endpoint for all "users" resources would be `/users`, while a the user with the ID of 42 would be at `/users/42`.
* HTTP methods map to actions that you can take on those resources:
  * `GET`: Read resources
  * `POST`: Create a new resource
  * `PUT`: Replace an existing resource with another
  * `PATCH`: Update part of a resource
  * `DELETE`: Remove a resource

These conveniently map directly to the Create/Read/Update/Delete/List, or CRUD-L actions you can take on data:

| RESTful Route | CRUD-L Action | Successful Response Code | Description |
| --- | --- | --- | --- |
| `GET /dogs` | `List()` | 200 OK | Read all dogs |
| `GET /dogs/42` | `findById()` | 200 OK | Read one dogs |
| `POST /dogs` | `create()` | 201 Created | Create a dog |
| `PUT /dogs/42` or `PATCH /dogs/42` | `update()` | 200 OK | Update a dog |
| `DELETE /dogs/42` | `delete()` | 204 No Content | Delete a dog |

Following this pattern when designing your APIs makes them more intuitive and uniform.

Resource paths can also nest:

```
GET /users/42/dogs
POST /users/42/dogs
```

The `GET` route would list all of the dogs owned by user 42, while the `POST` route would add a dog to user 42.

## Trivia

REST was the result of the doctoral research work of Roy Fielding, who was one of the creators of the HTTP specification.

## Watch Out!

* Resource names in paths are always plural. The path should be `/users`, not `/user`.

## Additional Resources

| Resource | Description |
| --- | --- |
| [Wikipedia: Representational State Transfer](https://en.wikipedia.org/wiki/Representational_state_transfer) | Wikipedia's article on REST |
| [Codecademy: What Is REST?](https://www.codecademy.com/article/what-is-rest) | Blog post on RESTful principles |
| [Architectural Styles and the design of Network-based Software Architectures](https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm) | Roy Fielding's original thesis outlining RESTful principles |
