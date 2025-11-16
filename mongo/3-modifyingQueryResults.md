# modifying results of query

find returns a cursor which a pointer to resultset

```javascript
db.collection.find(<query>).sort(<sort>)
```

following methods operate on cursor

## sort

1 means ASC  ascending order
-1 means DESC descending order

## limit

maximum number of results the cursor will return

## projection

```javascript
db.collection.find(<query>, <projection>)

db.collection.find( <query>, { <field> : 1 })

db.collection.find( <query>, { <field> : 0 })
```

find method takes a find document and a projection document

return only fields I am interested in

```javascript
db.companies.find( 
    { category_code: "music" }, 
    { name: 1, number_of_employees: 1 } )
    .sort( { number_of_employees: -1 } )
    .limit( 10 )
```

_id is included by default

to turn it off, exclude _id by setting it to zero.

_id is exception. 

you can exclude fields by setting it to zero

```
db.inspections.find( { sector: "Restaurant - 818" }, { business_name: 1, _id: 0 } )
db.inspections.find( { sector: "Restaurant - 818" }, { business_name: 0, _id: 0 } )
```

dot notation needs quotation marks
used for field of sub-document
