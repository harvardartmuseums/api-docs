# Medium

Contains information on the mediums used to describe items in the Harvard Art Museums collections. 

## Get Mediums

`GET /medium` will get all mediums.

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
| level | [0-9+] |
| parent | [0-9+] |

#### Examples

> http://api.harvardartmuseums.org/medium  
> Returns all of the mediums. 

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 3,
        "totalrecords": 271,
        "pages": 91,
        "page": 1
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

> http://api.harvardartmuseums.org/medium/2028206   
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