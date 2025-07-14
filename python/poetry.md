# Poetry hacks

## How to test with locally modified private dependencies?

1. edit pyproject.toml file for dependency in question to include the path

```text
abc-common = {version = "^0", source = "abc-pypi"}
abc-common = {path="../abc-common"}
```

1. call following commands

```bash
poetry lock
poetry install
```
