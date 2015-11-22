# Culture

Contains information on the cultures used to describe items in the Harvard Art Museums.

## Get Cultures

`GET /culture` will get all cultures.

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

> http://api.harvardartmuseums.org/culture  
> Returns all of the cultures. 

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 3,
        "totalrecords": 255,
        "pages": 85,
        "page": 1
    },
    "records": [
        {
            "id": 37527705,
            "objectcount": 24,
            "lastupdate": "2015-11-22T03:17:48-0500",
            "name": "Indonesian"
        },
        {
            "id": 37528335,
            "objectcount": 4,
            "lastupdate": "2015-11-22T03:17:48-0500",
            "name": "Philisto-Arabian"
        },
        {
            "id": 37528974,
            "objectcount": 1,
            "lastupdate": "2015-11-22T03:17:48-0500",
            "name": "Yemeni"
        }
    ]
}
```

## Get Culture

`GET /culture/CULTURE_ID` will get the full record of the specified culture.

#### Examples

> http://api.harvardartmuseums.org/culture/37527705   
> Returns the full record for the culture Indonesian.

#### Response

```json
{
    "id": 37527705,
    "name": "Indonesian",
    "objectcount": 24,
    "lastupdate": "2015-11-22T03:17:48-0500"
}
```