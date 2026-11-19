# Info

Describes the API itself: which endpoints exist, how big each one is, when it was last refreshed, and which parameters, facets, sorts, and views each one accepts.

This is the one endpoint that does **not** require an API key, which makes it a convenient way to check that the service is up before you have a key in hand.

## Get info

`GET /info` will get the manifest for every endpoint. It takes no parameters.

Each entry in the `endpoints` array describes one endpoint.

| Field | Description |
| :--------- | :----- |
| path | the endpoint path, i.e. `/object` |
| name | the name of the underlying index |
| totalrecords | the number of records in the index, including ones you may not be able to see |
| publicrecords | the number of records available to a standard API key |
| privaterecords | the number of records restricted to privileged keys |
| lastupdated | when any record in the index was last modified and republished |
| filters | the filter parameters the endpoint accepts |
| facets | the facet names the endpoint supports, if any |
| sorts | the named sorts the endpoint supports, if any |
| views | the named views the endpoint supports, if any |
| relationships | other endpoints this one links to, naming the field that carries the link and the parameter to filter the other endpoint with |
| similar | the similarity endpoint and its signals, if the endpoint has one; otherwise an empty array |

The manifest is maintained by hand, so treat it as a guide rather than a contract. If you find it disagreeing with the rest of this documentation, [tell us](https://github.com/harvardartmuseums/api-docs/issues).

#### Examples

> https://api.harvardartmuseums.org/info  
> Returns the manifest for every endpoint. No API key required.  

#### Response

```json
{
    "endpoints": [
        {
            "path": "/century",
            "name": "centuries",
            "totalrecords": 47,
            "publicrecords": 47,
            "privaterecords": 0,
            "lastupdated": "2026-11-18T09:01:58.000Z",
            "filters": [
                "usedby"
            ],
            "facets": [],
            "sorts": [],
            "views": [],
            "relationships": [
                {
                    "endpoint": "/object",
                    "field": "id",
                    "filter": "century",
                    "cardinality": "one-to-many"
                }
            ],
            "similar": []
        },
        {
            "path": "/object",
            "name": "objects",
            "totalrecords": 293867,
            "publicrecords": 248503,
            "privaterecords": 45364,
            "lastupdated": "2026-11-18T12:33:41.000Z",
            "filters": [
                "keyword",
                "q",
                "semantic",
                "match",
                "hasimage",
                "objectnumber",
                "title",
                "exact_title",
                "classification",
                "worktype",
                "culture",
                "century",
                "technique",
                "medium",
                "support",
                "period",
                "place",
                "topic",
                "color",
                "group",
                "person",
                "image",
                "exhibition",
                "publication",
                "yearmade",
                "relatedto",
                "gallery",
                "video",
                "audio",
                "division",
                "verificationlevel",
                "accessionmethod",
                "department",
                "style",
                "state",
                "role",
                "before",
                "after"
            ],
            "facets": [
                "classification",
                "worktype",
                "culture",
                "century",
                "technique",
                "medium",
                "support",
                "period",
                "place",
                "gallery",
                "color",
                "grouping",
                "division",
                "verificationlevel",
                "topic",
                "accessionmethod",
                "department",
                "style",
                "state"
            ],
            "sorts": [
                "dated",
                "pageviews",
                "lastupdate",
                "accession",
                "rank"
            ],
            "views": [
                "core",
                "stats",
                "images",
                "provenance",
                "minimal"
            ],
            "relationships": [
                {
                    "endpoint": "/person",
                    "field": "people.personid",
                    "cardinality": "one-to-one"
                },
                {
                    "endpoint": "/activity",
                    "field": "objectid",
                    "filter": "object",
                    "cardinality": "one-to-many"
                }
            ],
            "similar": {
                "path": "/object/:id/similar",
                "signals": [
                    "visual",
                    "concrete",
                    "interpretive",
                    "mixed"
                ],
                "parameters": [
                    "size",
                    "fields",
                    "debug"
                ]
            }
        }
    ]
}
```

The response above is abridged. A real response contains an entry for every endpoint, and the `relationships` arrays are longer.
