# models

- models have pydantic validation.

  - if you want a field which can have None value, you cant use `str | None` as type notation. This will result in good openapi but will fail while generating go code.
  - correct approach is not have these nullable fields in dictionary while generating the class instance. And have these field with default value of None. Without this either openapi generation or pydantic data validation at runtime will keep happening

  ``` python
  class Person(BaseModel):
    name: str
    brothers_name: str = Field(default=None)

    @classmethod
    def from_data(cls, name: str, brothers_name: str | None):
        person_data = {
            "name": name,
            **({"brothers_name": brothers_name} if brothers_name else {})
        }
        return Person(person_data)
  ```
