# Century

Contains information on the centuries used to describe items in the Harvard Art Museums collections.

## Get Centuries

`GET /century` will get all centuries.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY ***required*** |
| q | FIELD:VALUE (see [Elasticsearch Query String syntax](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/query-dsl-query-string-query.html) for more options) |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |
| aggregation |  see [Elasticsearch aggregations](http://www.elastic.co/guide/en/elasticsearch/reference/7.17/search-aggregations.html#_structuring_aggregations) |
| id | pipe separated list of record IDs |
| usedby | FIELD NAME:ID |

#### Examples

> https://api.harvardartmuseums.org/century  
> Returns all of the centuries.  

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 3,
        "totalrecords": 47,
        "pages": 16,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/century?size=3&page=2",
        "responsetime": "6 ms"
    },
    "records": [
        {
            "id": 37525374,
            "objectcount": 28,
            "lastupdate": "2015-11-22T03:17:52-0500",
            "temporalorder": 3,
            "name": "6th millennium BCE"
        },
        {
            "id": 37525437,
            "objectcount": 378,
            "lastupdate": "2015-11-22T03:17:52-0500",
            "temporalorder": 9,
            "name": "18th century BCE"
        },
        {
            "id": 37525482,
            "objectcount": 581,
            "lastupdate": "2015-11-22T03:17:52-0500",
            "temporalorder": 13,
            "name": "14th century BCE"
        }
    ]
}
```

## Get Century

`GET /century/CENTURY_ID` will get the full record of the specified century.

#### Examples

> https://api.harvardartmuseums.org/century/37525482   
> Returns the full record for the century 14th century BCE.  

#### Response

```json
{
    "id": 37525482,
    "name": "14th century BCE",
    "objectcount": 581,
    "temporalorder": 13,
    "lastupdate": "2015-11-22T03:17:52-0500"
}
```