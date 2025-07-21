# bash/shell scripting

## bash scripts - if else

- [ 1 eq 1 ] is equivalent to test 1 eq 1

## Logical And (&&) and Or (||)

- use parenthesis to group complex commands
- command after && is executed only after the first command is successful
- command after || is executed only when the first command fails
- each command returns code on completion. default value zero indicates success and non-zero value indicates failure
- one can see the return value of last command using $?

```bash
([ -f "file.txt" ] && echo "Found") || echo "Not found"
echo $?
```

## if else

- conditions must be enclosed in brackets and spaces [ space around condition ]

```bash
if [ -z abc.def ]; then
    echo "yes";
elif [ another_condition ]; then
    echo "no";
else
    echo "oops";
fi
```
