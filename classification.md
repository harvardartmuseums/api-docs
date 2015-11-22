# Classification

Contains information on the classifications used to categorize items in the Harvard Art Museums collections.

## Get Classifications

`GET /classification` will get all classifications.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| usedby | FIELD NAME:ID |

#### Examples

> http://api.harvardartmuseums.org/classification  
> Returns all of the classifications.  

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 3,
        "totalrecords": 62,
        "pages": 21,
        "page": 1
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

> http://api.harvardartmuseums.org/classification/30   
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