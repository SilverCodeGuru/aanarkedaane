# **make** to automate

- need make utility
- need a Makefile file under the root folder of the project
- Makefile defines targets and commands to run when target is invoked
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
