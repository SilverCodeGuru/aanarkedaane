# Enums

- have name and value
- dont compare enum values. use **is**

``` python
class Status(Enum):
    SUCCESS = 1
    FAILURE = 2

result = Status.SUCCESS

if result is Status.SUCCESS:
    print("it was a success")
```
