# Site

Contains information on the sites that are part of the Harvard Art Museums.

## Get sites

`GET /site` will get all of the museums sites.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE (see [Elasticsearch Query String syntax](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/query-dsl-query-string-query.html) for more options) |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |

#### Examples

> https://api.harvardartmuseums.org/site  
> Returns all sites records for the Harvard Art Museums.

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 3,
        "pages": 1,
        "page": 1,
        "responsetime": "5 ms"
    },
    "records": [
        {
            "id": 37536066,
            "lastupdate": "2015-12-22T04:13:22-0500",
            "geo": {
                "longitude": -71.114137,
                "latitude": 42.376841
            },
            "address": "29 Kirkland Street, Cambridge, MA 02138",
            "name": "Adolphus Busch Hall",
            "siteid": 37536066
        },
        {
            "id": 37536057,
            "lastupdate": "2015-12-22T04:13:22-0500",
            "geo": {
                "longitude": -71.114101,
                "latitude": 42.374029
            },
            "address": "32 Quincy Street, Cambridge, MA 02138",
            "name": "Harvard Art Museums",
            "siteid": 37536057
        },
        {
            "id": 37536075,
            "lastupdate": "2015-12-22T04:13:22-0500",
            "geo": {
                "longitude": -71.084585,
                "latitude": 42.378
            },
            "address": "200 Inner Belt Road, Somerville, MA 02143",
            "name": "Somerville Research Facility",
            "siteid": 37536075
        }
    ]
}
```

## Get site

`GET /site/SITE_ID` will get detailed info about a specific site.

#### Examples

> https://api.harvardartmuseums.org/site/37536057  
> Returns the full record for the site “Harvard Art Museums”.

#### Response

```json
{
    "id": 37536057,
    "lastupdate": "2015-12-22T04:13:22-0500",
    "name": "Harvard Art Museums",
    "siteid": 37536057,
    "address": "32 Quincy Street, Cambridge, MA 02138",
    "geo": {
        "latitude": 42.374029,
        "longitude": -71.114101
    }
}
```
