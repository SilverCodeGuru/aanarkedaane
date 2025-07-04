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
    1. wheel distribution (wheel)

- you also uninstall and upgrade a package

``` bash
python -m pip --upgrade pip

python -m pip uninstall pip
```

- extras are specified in square brackets in pip install command. this allows one to get complete development environment without having to install each dependency manually.

```bash
pip install "fastapi[standard]"
```

## requirement specifiers

- you can get latest versions for a library using following command -

``` bash
python -m pip freeze | grep -E 'pytest|pytest-cov|coverage'
```

- it is better to specify minimum version using >= for libraries and have fixed versions using == for applications for reproducibility.

``` plaintext
pytest==8.4.1
pytest>=8.0.0
```
