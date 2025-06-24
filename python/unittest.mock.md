# unittest.mock

- assert_called_with()
  - positional arguments
  - keyword arguments


- you can substitute an object with Mock instance by passing it as an argument to a function or by **redefining another object**

``` python
from unitest.mock import Mock

mock = Mock()
```

- you can even use mock to mock whole library
- mock creates attributes lazily - only when these are called/accessed
- mocked method requires no argument. it will accept any arguments you pass.
- return value of mock is also a Mock


- use ANY from unittest.mock for ease on asserting on arguments of a function

``` python
from unittest.mock import ANY, Mock


def test_mock_json_many_rgs():
    json = Mock()

    json.loads('{"key": "value"}', 10)

    json.loads.assert_called_once_with(ANY, 10)
```