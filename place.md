# Place

Contains information on the places used to describe items in the Harvard Art Museums collections. 

## Get Places

`GET /place` will get all places.

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

> http://api.harvardartmuseums.org/place?q=parentplaceid:2028439  
> Returns all records for places that are in New York state.  

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 91,
        "pages": 10,
        "page": 1
    },
    "records": [
        {
            "objectcount": 3,
            "id": 2036944,
            "lastupdate": "2015-01-09T04:12:18-0500",
            "haschildren": 0,
            "level": 4,
            "placeid": 2036944,
            "pathforward": "North America\\United States\\New York\\",
            "parentplaceid": 2028439,
            "name": "Auburn"
        },
        {
            "objectcount": 14,
            "id": 2036956,
            "lastupdate": "2015-01-09T04: 12: 18-0500",
            "haschildren": 0,
            "level": 4,
            "placeid": 2036956,
            "pathforward": "NorthAmerica\\UnitedStates\\NewYork\\",
            "parentplaceid": 2028439,
            "name": "Oswego"
        },
        {
            "objectcount": 77,
            "id": 2036963,
            "lastupdate": "2015-01-09T04:12:18-0500",
            "haschildren": 0,
            "level": 4,
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

#### Examples

> http://api.harvardartmuseums.org/place/2028422  
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
    "id": 2028422,
    "lastupdate": "2015-01-09T04:12:17-0500"
}
```