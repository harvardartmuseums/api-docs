# Group

Contains information on the groups used to describe items in the Harvard Art Museums collections.

## Get Groups

`GET /group` will get all groups.

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

> https://api.harvardartmuseums.org/group   
> Returns all of the group records    
>     
> https://api.harvardartmuseums.org/group/?q=filters.values.name:Typography   
> Returns all groups that contain "Typography" as a topic   

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 2,
        "totalrecords": 27,
        "pages": 14,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/group?size=2&page=2"
    },
    "records": [
        {
            "name": "Analog Culture",
            "id": 2042184,
            "lastupdate": "2018-04-17T15:29:00-0500"
        },
        {
            "name": "Roman Domestic Art: Glass",
            "id": 37690650,
            "lastupdate": "2017-02-28T00:00:00-0500"
        }
    ]
}
```

## Get Group

`GET /group/GROUP_ID` will get the full record of the specified group.

#### Examples

> https://api.harvardartmuseums.org/group/37690641    
> Returns the full record for group "Roman Domestic Art: Terra sigillata"   

#### Response

```json
{
    "id": 37690641,
    "name": "Roman Domestic Art: Terra sigillata",
    "lastupdate": "2017-02-28T00:00:00-0500",
    "filters": [
        {
            "name": "Medium",
            "valuesurl": "",
            "searchparameter": "medium",
            "multiple_levels": false,
            "values": [
                {
                    "id": 2028311,
                    "name": "Ceramic"
                },
                {
                    "id": 2028328,
                    "name": "Terracotta"
                }
            ]
        },
        {
            "name": "Technique",
            "valuesurl": "",
            "searchparameter": "technique",
            "multiple_levels": false,
            "values": [
                {
                    "id": 1033,
                    "name": "Mold-made"
                },
                {
                    "id": 2704,
                    "name": "Redware"
                },
                {
                    "id": 1484,
                    "name": "Stamped"
                },
                {
                    "id": 635,
                    "name": "Wheel-made"
                }
            ]
        },
        {
        "name": "Culture",
        "valuesurl": "",
        "searchparameter": "culture",
        "multiple_levels": false,
        "values": [
            {
                "id": 37527534,
                "name": "Greek"
            },
            {
                "id": 37528416,
                "name": "Roman"
            }
        ]
        },
        {
            "name": "Classification",
            "valuesurl": "",
            "searchparameter": "classification",
            "multiple_levels": false,
            "values": [
                {
                    "id": 94,
                    "name": "Fragments"
                },
                {
                    "id": 32,
                    "name": "Tools and Equipment"
                },
                {
                    "id": 57,
                    "name": "Vessels"
                }
            ]
        },
            {
            "name": "Work Type",
            "valuesurl": "",
            "searchparameter": "worktype",
            "multiple_levels": false,
            "values": [
                {
                    "id": 146,
                    "name": "fragment"
                },
                {
                    "id": 220,
                    "name": "mold"
                },
                {
                    "id": 314,
                    "name": "sherd"
                },
                {
                    "id": 383,
                    "name": "vessel"
                }
            ]
        }
    ]
}
```
