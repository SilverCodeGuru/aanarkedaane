# Pytest

## Commands and options

- durations command list slowest test. Examples show 5 slowest tests
```
pytest run . --durations=5
```

pytest is plugin based ecosystem?

fixture - explicit dependecy injection - to provide test data, test doubles and state setup

### conftest.py
conftest.py to define fixtures for whole projects without a need to import.

it can also be used to guard access to resources e.g. api call? it will be great with an example.

in conftest.py

```python
import pytest
import requests

@pytest.fixture(autouse=True)
def disable_network_calls(monkeypatch):
    def stunted_get():
        raise RuntimeError("Network access not allowed during testing!")
    monkeypatch.setattr(requests, "get", lambda *args, **kwargs: stunted_get())

```
### monkeypatch


### pytest.ini

register marks in pytest.ini file to get handle on marks




