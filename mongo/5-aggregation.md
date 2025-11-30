# aggregation

pipeline with multiple stages

common stages

- $match
- $unwind
- $group
- $project
- $sort
- $limit
- $out - write output to a collection. if it exists all data is dropped first. if collection doesnt exist, it is created.



```js
db.sales.aggregate([
  {
    $match:
      /**
       * query: The query in MQL.
       */
      {
        title: "Bill of Rights"
      }
  },
  {
    $unwind:
      /**
       * path: Path to the array field.
       * includeArrayIndex: Optional name for index.
       * preserveNullAndEmptyArrays: Optional
       *   toggle to unwind null and empty values.
       */
      {
        path: "$comments"
      }
  },
  {
    $group:
      /**
       * _id: The id of the group.
       * fieldN: The first field name.
       */
      {
        _id: "$comments.author",
        numberOfComments: {
          $count: {}
        }
      }
  },
  {
    $project:
      /**
       * specifications: The fields to
       *   include or exclude.
       */
      {
        _id: 0,
        commentAuthor: "$_id",
        numberOfComments: 1
      }
  },
  {
    $sort:
      /**
       * Provide any number of field/order pairs.
       */
      {
        numberOfComments: -1
      }
  }
])
```

- $lookup - get data from other collections as array. $unwind stage after this is useful.
- $set - adds new fields. is alias for $addFields


```js
db.sales.aggregate([
    {
        $lookup: {
            from: "customers",
            localField: "customer",
            foreignField: "_id",
            as: "customer_details"
        }
    },
    {
        $unwind: {
            path: "$customer_details"
        }
    },
    {
        $set: {
            childrensBooks: {
                $filter: {
                    input: "$books",
                    as: "book",
                    cond: {
                        $eq: ["$$book.genre", "Children's literature"]
                    }
                }
            }
        }
    },
    {
        $match: {
            childrensBooks: {
                $ne: []
            }
        }
    },
    {
        $project: {
            _id: 0,
            customerName: {
                $concat: [
                    "$customer_details.name.first",
                    " ",
                    "$customer_details.name.last"
                ]
            },
            email: "$customer_details.email",
            childrensBooks: "$childrensBooks.title"
        }
    }
]);
```

- $filter

```js
db.sales.aggregate([
    {
        $lookup: {
            from: "customers",
            localField: "customer",
            foreignField: "_id",
            as: "customer_details"
        }
    },
    {
        $unwind: {
            path: "$customer_details"
        }
    },
    {
        $set: {
            childrensBooks: {
                $filter: {
                    input: "$books",
                    as: "book",
                    cond: {
                        $eq: ["$$book.genre", "Children's literature"]
                    }
                }
            }
        }
    },
    {
        $match: {
            childrensBooks: {
                $ne: []
            }
        }
    },
    {
        $project: {
            _id: 0,
            customerName: {
                $concat: [
                    "$customer_details.name.first",
                    " ",
                    "$customer_details.name.last"
                ]
            },
            email: "$customer_details.email",
            childrensBooks: "$childrensBooks.title"
        }
    },
    { $out: "book_recommendations" }
]);
```