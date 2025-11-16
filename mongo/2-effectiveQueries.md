# Effective Queries

## Comparison operators

- $eq
- $gt
- $gte
- $lt
- $lte


operators start with $ to distinguish these from fields

<field>: { <operator>: <value> }

document containing an array of sub-documents

sales has items

sub document's field are accessed using dot notation.

{ "items.price": { $gt: 50 } }

## Logical Operators

- $and
- $or

```javascript
db.collection.find( {
    $and: [
        { "items.price": {$gt: 100} },
        { "items.name": "envelopes" },
    ],
} )
```

implicit syntax:
separate different and clauses by comma

```javascript
db.collection.find( {
    { "items.price": {$gt: 100} },
    { "items.name": "envelopes" },
} )
```

implicit syntax will not work with two or clauses because in json we cant have same key twice in one object.

```json
{
    "$or": { "a": 10 },
    "$or": {"b": 10},
}
```

second expression will overwrite the first. One must use explicit and syntax here.

## Array elements

scalar elements and array elements

```javascript
db.accounts.find( {
    products: {
        $elemMatch: {$eq: "investment"}
    }
} )
```

This will only return documents with products array field has an element with value investment. It will not return documents where products is a scalar field.

use **$elemMatch** operator to find all documents that contain the specified subdocument.
