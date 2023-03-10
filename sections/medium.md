# Medium

Contains information on the mediums (the materials that are applied in the making of an object) used to describe items in the Harvard Art Museums collections. This information is oftentimes provided by the Harvard Art Museums' conservators as a result of their expertise, technical examination, and/or analysis.

## Get Mediums

`GET /medium` will get all mediums.

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
| level | [0-9+] |
| parent | [0-9+] |

#### Examples

> https://api.harvardartmuseums.org/medium  
> Returns all of the mediums.

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 3,
        "totalrecords": 271,
        "pages": 91,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/medium?size=3&page=2",
        "responsetime": "6 ms"
    },
    "records": [
        {
            "objectcount": null,
            "id": 2039518,
            "lastupdate": "2015-11-22T03:18:09-0500",
            "haschildren": 0,
            "level": 1,
            "pathforward": "",
            "name": "Resin",
            "parentmediumid": null,
            "mediumid": 2039518
        },
        {
            "objectcount": null,
            "id": 2036627,
            "lastupdate": "2015-11-22T03:18:09-0500",
            "haschildren": 0,
            "level": 1,
            "pathforward": "",
            "name": "Varnish",
            "parentmediumid": null,
            "mediumid": 2036627
        },
        {
            "objectcount": 14,
            "id": 2035845,
            "lastupdate": "2015-11-22T03:18:09-0500",
            "haschildren": 0,
            "level": 1,
            "pathforward": "",
            "name": "Hair",
            "parentmediumid": null,
            "mediumid": 2035845
        }
    ]
}
```

## Get Medium

`GET /medium/MEDIUM_ID` will get the full record of the specified medium.

#### Examples

> https://api.harvardartmuseums.org/medium/2028206   
> Returns the full record for the medium Watercolor.  

#### Response

```json
{
    "mediumid": 2028206,
    "name": "Watercolor",
    "pathforward": "",
    "parentmediumid": null,
    "haschildren": 0,
    "level": 1,
    "objectcount": 2509,
    "id": 2028206,
    "lastupdate": "2015-11-22T03:18:09-0500"
}
```
