# Document Model

- documents, collections, databases, nodes, cluster

- document contain field value pairs

- field names must be unique within a document

- data accessed together should be stored together

- field values can be simple types, arrays, embedded documents

- mongodb documents are similar to JSON documents

JSON is great for representing data but mongoDB stores data/documents as BSON - binary JSON

BSON is extension of JSON. its not human readable. its for storage and transmitting data over the wire.

JSON does not have following but BSON does
dates, objectId and timestamps

flexible data model - documents within same collection dont need to have same fields
there is no need to rebuild entire collection when adding a new field to a document.

maximum document size is 16 MB

maximum 100 levels of nesting

## Datatypes

- Boolean
- Null
- Strings
- Numbers
    + int32
    + int64
    + Double
    + Decimal128

- Objects - curly braces - embedded documents
- Arrays - square brackets, each element can be of different types
- Dates - stored as timestamps - efficient for querying and sorting, unix epopch, milliseconds since Jan 1, 1970
    - Date formats can be challenging for developers. timestamp format is compact, easy to convert to and from other formats. efficient for storage, fast comparison and computation.

- ObjectId - 24 character hexadecimal. guaranteed uniqueness.