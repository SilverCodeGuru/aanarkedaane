# **make** to automate

## basics

- has targets and recipes
- each line runs in its own shell. values cant the shared across
- has built-in variables e.g. CURDIR
- has built-in functions e.g. abspath
- can define your own variables which can be accessed using $(var-name) syntax

    ```shell
    PWD := $(abspath $(CURDIR))
    PYPROJECT_PATH := $(PWD)/my-project/pyproject.toml

    .PHONY: test
    test:
        poetry -C my-project run pytest --config-file=$(PYPROJECT_PATH) $(PWD)
    ```

- uses default shell by default
    - default shell on ubuntu is dash and not bash. dash is faster and lacks some features that bash offers.

## usage
- need make utility
- need a Makefile file under the root folder of the project
- Makefile defines targets and recipes (containing commands) to run when target is invoked
- you can club commands together
- from bash, you can run group of commands by calling

    ```bash
    make all
    ```

- **.PHONY** declares phony targets. make is looking for files be default. if there was a file named format, make would have tried to check that file instead of running your commands

    ```bash
    .PHONY: format
    format:
        poetry run isort .
        poetry run black .
    ```

- makefiles like tabs and not spaces. vscode replaces tabs with spaces by default. edit it user level settings for makefile

    ``` json
    "[makefile]": {
            "editor.insertSpaces": false,
            "editor.detectIndentation": false
        }
    ```

- prepend a command with @ to ensure that is not echoed/printed before execution

- for makefile, each line is a command. If scripts spans many lines, each line must be separated by **line continuation character \\**

    ```bash
    build:
        if [ -z abc.def ]; then \
            echo "yes"; \
        elif [ another_condition ]; then \
            echo "no"; \
        else \
            echo "oops"; \
        fi
    ```
