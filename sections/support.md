# Support

Contains information on the suports (the surface upon which media have been applied during the making of an object) used to describe items in the Harvard Art Museums collections. This information is oftentimes provided by the Harvard Art Museums' conservators as a result of their expertise, technical examination, and/or analysis.

## Get Supports

`GET /support` will get all supports.

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
| level | [0-9+] |
| parent | [0-9+] |

#### Examples

> https://api.harvardartmuseums.org/support  
> Returns all of the supports.

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 3,
        "totalrecords": 362,
        "pages": 121,
        "page": 1,
        "responsetime": "6 ms"
    },
    "records": [
        {
            "pathforward": "wood\\",
            "parentsupportid": 2028322,
            "level": 2,
            "objectcount": null,
            "name": "ebony",
            "id": 2038687,
            "supportid": 2038687,
            "lastupdate": "2023-03-01T09:17:22-0500",
            "haschildren": 0
        },
        {
            "pathforward": "wood\\",
            "parentsupportid": 2028322,
            "level": 2,
            "objectcount": null,
            "name": "walnut",
            "id": 2038689,
            "supportid": 2038689,
            "lastupdate": "2023-03-01T09:17:22-0500",
            "haschildren": 0
        },
        {
            "pathforward": "wood\\",
            "parentsupportid": 2028322,
            "level": 2,
            "objectcount": 5,
            "name": "spruce",
            "id": 2035315,
            "supportid": 2035315,
            "lastupdate": "2023-03-01T09:17:22-0500",
            "haschildren": 0
        }
    ]
}
```

## Get Support

`GET /support/SUPPORT_ID` will get the full record of the specified support.

#### Examples

> https://api.harvardartmuseums.org/support/2035314   
> Returns the full record for the support slate.  

#### Response

```json
{
    "id": 2035314,
    "supportid": 2035314,
    "name": "slate",
    "pathforward": "stone\\",
    "parentsupportid": 2028653,
    "haschildren": 0,
    "level": 2,
    "objectcount": 2,
    "lastupdate": "2023-03-01T09:17:22-0500"
}
```
