# user guide tutorial

- **OpenAPI** defines an API schema for API. And this schema includes definitions (schemas) of data sent or received by API using **JSON schema**, the standard for JSON data schemas.

## Path
- **Path** is also commonly called **endpoint** or a **route**. it is last part of url starting with first "/"
  - path is the main way to separate **concerns** and **resources**

## Operation

- refers to one of the HTTP methods
- in OpenAPI each HTTP method is called an operation
- path operation decorator
- path operation function
- order of paths matter - one coming first will be used.

``` python
# users/me should appear before users/user_id, else me will be passed to user_id and users/me will never be called
@app.get("/users/me")
async def read_user_me():
    return {"user_id": "the current user"}


@app.get("/users/{user_id}")
async def read_user(user_id: str):
    return {"user_id": user_id}
```
