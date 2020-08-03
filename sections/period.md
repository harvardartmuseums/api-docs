# Period

Contains information on the periods (art movements within a specific period of time) used to describe items in the Harvard Art Museums collections. With some exceptions, the periods typically follow the Getty Research Institute's Art & Architecture Thesaurus.

## Get Periods

`GET /period` will get all periods.

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

> https://api.harvardartmuseums.org/period  
> Returns all of the periods.

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 3,
        "totalrecords": 298,
        "pages": 100,
        "page": 1
    },
    "records": [
        {
            "objectcount": 2,
            "id": 7056,
            "lastupdate": "2015-11-22T03:17:48-0500",
            "name": "Helladic period, Late Helladic I",
            "periodid": 7056
        },
        {
            "objectcount": 171,
            "id": 345,
            "lastupdate": "2015-11-22T03:17:48-0500",
            "name": "Hellenistic period, Late",
            "periodid": 345
        },
        {
            "objectcount": 1,
            "id": 3237,
            "lastupdate": "2015-11-22T03:17:48-0500",
            "name": "Jômon period, Middle, c. 2500-c. 1500 BCE",
            "periodid": 3237
        }
    ]
}
```

## Get Period

`GET /period/PERIOD_ID` will get the full record of the specified period.

#### Examples

> https://api.harvardartmuseums.org/period/345  
> Returns the full record for the period Hellenistic period, Late.  

#### Response

```json
{
    "periodid": 345,
    "name": "Hellenistic period, Late",
    "objectcount": 171,
    "id": 345,
    "lastupdate": "2015-11-22T03:17:48-0500"
}
```
