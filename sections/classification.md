# Classification

Contains information on the classifications used to categorize items in the Harvard Art Museums collections. Classification labels are created and assigned by Harvard Art Museums curators.

## Get Classifications

`GET /classification` will get all classifications.

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

> https://api.harvardartmuseums.org/classification  
> Returns all of the classifications.  

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 3,
        "totalrecords": 62,
        "pages": 21,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/classification?size=3&page=2",
        "responsetime": "6 ms"
    },
    "records": [
        {
            "objectcount": 24,
            "id": 162,
            "lastupdate": "2015-11-22T03:17:45-0500",
            "name": "Portfolios",
            "classificationid": 162
        },
        {
            "objectcount": 69081,
            "id": 23,
            "lastupdate": "2015-11-22T03:17:45-0500",
            "name": "Prints",
            "classificationid": 23
        },
        {
            "objectcount": 5623,
            "id": 30,
            "lastupdate": "2015-11-22T03:17:45-0500",
            "name": "Sculpture",
            "classificationid": 30
        }
    ]
}
```

## Get Classification

`GET /classification/CLASSIFICATION_ID` will get the full record of the specified classification.

#### Examples

> https://api.harvardartmuseums.org/classification/23   
> Returns the full record for the classification Prints.  

#### Response

```json
{
    "classificationid": 23,
    "name": "Prints",
    "objectcount": 69081,
    "id": 23,
    "lastupdate": "2015-11-22T03:17:45-0500"
}
```
