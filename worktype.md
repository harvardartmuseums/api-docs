# Worktype

Contains information on the types of works in the Harvard Art Museums collections.

## Get Worktypes

`GET /worktype` will get all work types.

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

> http://api.harvardartmuseums.org/worktype  
> Returns all of the work types. 

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 3,
        "totalrecords": 394,
        "pages": 132,
        "page": 1
    },
    "records": [
        {
            "objectcount": 0,
            "id": "4",
            "lastupdate": "2015-11-22T03:17:53-0500",
            "name": "adze",
            "worktypeid": "4"
        },
        {
            "objectcount": 0,
            "id": "11",
            "lastupdate": "2015-11-22T03:17:53-0500",
            "name": "ammunition",
            "worktypeid": "11"
        },
        {
            "objectcount": 0,
            "id": "16",
            "lastupdate": "2015-11-22T03:17:53-0500",
            "name": "architectural fragment",
            "worktypeid": "16"
        }
    ]
}
```

## Get Worktype

`GET /worktype/WORKTYPE_ID` will get the full record of the specified work type.

#### Examples

> http://api.harvardartmuseums.org/worktype/25   
> Returns the full record for the work type astrolabe.  

#### Response

```json
{
    "worktypeid": "25",
    "name": "astrolabe",
    "objectcount": 0,
    "id": "25",
    "lastupdate": "2015-11-22T03:17:53-0500"
}
```