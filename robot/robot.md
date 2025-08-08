# Robot framework

- built using python
- more than two spaces to separate
- no indentation means its the same of test case or setting
- indentation under test case name means these are keywords used in a test case

## Syntax
- inside an expression (Should Be True, Run Keyword If, Evaluate)
  - ${RC} gives you string representation of value of RC
  - $RC directly gives you the values. this is called special variable syntax.
    - special variable syntax is a bit slower
  - strings must be quoted
    - and if they contain newline, they must be triple quoted
```Robot
Run Keyword If    '${status}' == 'PASS'        Log    Passed
```

## Limitations
- it does not suppose if-else, nexted loops



## Good place to refer
- https://docs.robotframework.org/docs/getting_started/how_to_write_rf
- https://docs.robotframework.org/docs/examples/restfulbooker
- https://robotframework.org/robotframework/latest/libraries/BuiltIn.html


## Variables

- variable names are case insensitive
- space and underscores are ignores
- variable identifiers are $ @ & and %
- if variable is used alone, it is replaced by its value
- if variable is used with other variables/text, its value is first converted to string
- variable values are used as is when being passed to arguments to keywords

```text
    Log To Console    ${GREET}
    Log To Console    ${GREET}, ${NAME}!!
    Log To Console
    ...    \${VAR NAME} is same as \${VAR_NAME} which is same as \${VARNAME}. Space and underscores are ignored in variable names.
    Log To Console    case is also ignored i.e. \${VAR NAME} is same as \{var name}
```