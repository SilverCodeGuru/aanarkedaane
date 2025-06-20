# pip

- Don't directly call pip, call using python -m to ensure consistency and avoid ambiguity

```bash
python -m pip install pip
```

- packages can be installed from

1. pypi
1. version control (git)
1. local project?
1. ditribution files
    1. source distribution (sdist)
    2. wheel distribution (wheel)

- you also uninstall and upgrade a package

```bash
python -m pip --upgrade pip

python -m pip uninstall pip
```

## requirement specifiers
