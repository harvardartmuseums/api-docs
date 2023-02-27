# Technique

Contains information on the techniques (the process by which an object is created) used in the production of items in the Harvard Art Museums. Technique labels are created and assigned by Harvard Art Museums curators.

## Get Techniques

`GET /technique` will get list of techniques used to make items in the collection.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE (see [Elasticsearch Query String syntax](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/query-dsl-query-string-query.html) for more options) |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| usedby | FIELD NAME:ID |

#### Examples

> https://api.harvardartmuseums.org/technique    
> Returns all of the techniques.  

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 3,
        "totalrecords": 306,
        "pages": 102,
        "page": 1
    },
    "records": [
        {
            "objectcount": 171,
            "id": 585,
            "lastupdate": "2015-11-22T03:17:52-0500",
            "name": "Softground etching",
            "techniqueid": 585
        },
        {
            "objectcount": 6,
            "id": 2568,
            "lastupdate": "2015-11-22T03:17:52-0500",
            "name": "Woven, twill",
            "techniqueid": 2568
        },
        {
            "objectcount": 7,
            "id": 2809,
            "lastupdate": "2015-11-22T03:17:52-0500",
            "name": "Assemblage",
            "techniqueid": 2809
        }
    ]
}
```

## Get Technique

`GET /technique/TECHNIQUE_ID` will get detailed info about a technique.

#### Examples

> https://api.harvardartmuseums.org/technique/7317  
> Returns the full record for the technique “Red-figure”.

#### Response

```json
{
    "techniqueid": 7317,
    "name": "Red-figure",
    "objectcount": 34,
    "id": 7317,
    "lastupdate": "2015-01-09T04:12:32-0500",
    "contains": {
        "groups": [
            {
                "name": "Collection Highlights",
                "groupid": 2039923
            },
            {
                "name": "Artstor Digital Library",
                "groupid": 2040173
            },
            {
                "name": "Google Art Project",
                "groupid": 2040174
            }
        ]
    }
}
```
