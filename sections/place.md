# Place

Contains information on the places (states, countries, continents, or historical regions) used to describe items in the Harvard Art Museums collections.

## Get Places

`GET /place` will get all places.

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

> https://api.harvardartmuseums.org/place?parent=2028439  
> Returns all records for places that are in New York state.  

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 91,
        "pages": 10,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/place?parent=2028439&size=10&page=2",
        "responsetime": "6 ms"
    },
    "records": [
        {
            "objectcount": 3,
            "id": 2036944,
            "lastupdate": "2017-02-02T04:18:45-0500",
            "tgn_id": 7013343,
            "haschildren": 0,
            "level": 4,
            "geo": {
                "lon": -76.55,
                "lat": 42.916
            },
            "placeid": 2036944,
            "pathforward": "North America\\United States\\New York\\",
            "parentplaceid": 2028439,
            "name": "Auburn"
        },
        {
            "objectcount": 14,
            "id": 2036956,
            "lastupdate": "2017-02-02T04:18:45-0500",
            "tgn_id": 7014317,
            "haschildren": 0,
            "level": 4,
            "geo": {
                "lon": -76.5,
                "lat": 43.45
            },
            "placeid": 2036956,
            "pathforward": "North America\\United States\\New York\\",
            "parentplaceid": 2028439,
            "name": "Oswego"
        },
        {
            "objectcount": 78,
            "id": 2036963,
            "lastupdate": "2017-02-02T04:18:45-0500",
            "tgn_id": 7015822,
            "haschildren": 0,
            "level": 4,
            "geo": {
                "lon": -73.966,
                "lat": 40.683
            },
            "placeid": 2036963,
            "pathforward": "North America\\United States\\New York\\",
            "parentplaceid": 2028439,
            "name": "Brooklyn"
        }
    ]
}
```

## Get Place

`GET /place/PLACE_ID` will get the full record of the specified place.

**tgn_id** contains the ID of the equivalent record in the [Getty Thesaurus of Geographic Names](http://www.getty.edu/research/tools/vocabularies/tgn/)

#### Examples

> https://api.harvardartmuseums.org/place/2028422  
> Returns the full record for the country Norway.  

#### Response

```json
{
    "placeid": 2028422,
    "name": "Norway",
    "pathforward": "Europe\\",
    "parentplaceid": 2028188,
    "haschildren": 1,
    "level": 2,
    "objectcount": 12,
    "tgn_id": 1000088,
    "id": 2028422,
    "geo": {
        "lat": 62,
        "lon": 10
    },
    "lastupdate": "2017-02-02T04:18:42-0500"
}
```
