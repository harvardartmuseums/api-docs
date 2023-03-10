# Worktype

Contains information on the types of works in the Harvard Art Museums collections. Worktype labels are more specific classifications of the object, and they are created and assigned by Harvard Art Museums curators.

## Get Worktypes

`GET /worktype` will get all work types.

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

> https://api.harvardartmuseums.org/worktype  
> Returns all of the work types.

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 3,
        "totalrecords": 394,
        "pages": 132,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/worktype?size=3&page=2",
        "responsetime": "5 ms"
    },
    "records": [
        {
            "objectcount": 0,
            "id": "4",
            "lastupdate": "2015-11-22T03:17:53-0500",
            "name": "adze",
            "worktypeid": "4"
        },
        {
            "objectcount": 0,
            "id": "11",
            "lastupdate": "2015-11-22T03:17:53-0500",
            "name": "ammunition",
            "worktypeid": "11"
        },
        {
            "objectcount": 0,
            "id": "16",
            "lastupdate": "2015-11-22T03:17:53-0500",
            "name": "architectural fragment",
            "worktypeid": "16"
        }
    ]
}
```

## Get Worktype

`GET /worktype/WORKTYPE_ID` will get the full record of the specified work type.

#### Examples

> https://api.harvardartmuseums.org/worktype/25   
> Returns the full record for the work type astrolabe.  

#### Response

```json
{
    "worktypeid": "25",
    "name": "astrolabe",
    "objectcount": 0,
    "id": "25",
    "lastupdate": "2015-11-22T03:17:53-0500"
}
```
