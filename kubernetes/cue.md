# Cue is json superset

## advantages
- c type comments which are not allowed in json
- field names dont need to be quoted

## details
- definition is a field that starts with # or _#. schemas are normally written as definitions
- ... keeps a struct open, else its a closed struct
- order is irrelevant. you can specify a field many times
- unification
- constraints
- shorthand

```cue
// Specify fields concisely ...
fruit: apple: weight: 5
fruit: grape: weight: 2
// ... or don't. Mix and match forms as needed.
fruit: {
	melon: weight: 9
}

// Pattern constraints match multiple fields.
fruit: [string]: weight: int & <10

// Pattern constraints can specify multiple fields.
fruit: [string]: {
	isFruit:     true
	isVegetable: !isFruit
}
```

- a configuration for a package is concatanation of all its files
- cue has built-in packages and user-defined packages which can imported
- hidden field starts with "_" underscore

