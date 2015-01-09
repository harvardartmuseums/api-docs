# Technique

Contains a list of the colors used in the color spectrum that is part of the branding of the Harvard Art Museums

## Get Techniques

'GET /technique' will get list of techniques used to make items in the collection..

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

>   
>  

#### Response

```json
{
}
```

## Get Technique

`GET /technique/TECHNIQUE_ID` will get detailed info about a technique.

#### Examples

> http://api.harvardartmuseums.org/technique/7317  
> Returns the full record for the technique “Red-figure”.

#### Response

```json
{
    "techniqueid": 7317,
    "name": "Red-figure",
    "objectcount": 34,
    "id": 7317,
    "lastupdate": "2015-01-09T04:12:32-0500",
    "contains": {
        "groups": [
            {
                "name": "Collection Highlights",
                "groupid": 2039923
            },
            {
                "name": "Artstor Digital Library",
                "groupid": 2040173
            },
            {
                "name": "Google Art Project",
                "groupid": 2040174
            }
        ]
    }
}
```