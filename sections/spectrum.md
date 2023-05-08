# Spectrum

Contains a list of the colors used in the color spectrum that is part of the branding of the Harvard Art Museums. Read more about the spectrum at https://harvardartmuseums.org/article/the-index-color-spectrum.  

## Get spectrum

`GET /spectrum` will get the museums’ color spectrum.

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

#### Examples

> https://api.harvardartmuseums.org/spectrum?q=month:1&sort=daynumber  
> Returns the colors assigned to the month of January.

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 31,
        "pages": 4,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/spectrum?q=month%3A1&sort=daynumber&size=10&page=2",
        "responsetime": "5 ms"
    },
    "records": [
        {
            "id": 1,
            "color": "#009bdf",
            "month": 1,
            "day": 1,
            "daynumber": 1
        },
        {
            "id": 2,
            "color": "#009ade",
            "month": 1,
            "day": 2,
            "daynumber": 2
        }
    ]
}
```

## Get spectrum color by day

`GET /spectrum/DAY_NUMBER` will get the color associated with a particular day.

#### Examples

> https://api.harvardartmuseums.org/spectrum/50  
> Returns the hex value of the color associated with day 50.

#### Response

```json
{
    "month": 2,
    "day": 19,
    "color": "#0089ae",
    "id": 50,
    "daynumber": 50
}
```
