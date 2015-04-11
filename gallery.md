# Gallery

Contains information on physical spaces within the museums’ building at [32 Quincy Street, Cambridge, MA](https://www.google.com/maps/place/Harvard+Art+Museums/@42.3742591,-71.1136073,19z/data=!4m2!3m1!1s0x0:0x3ea24d53829c6322).

## Get galleries

`GET /gallery` will get all galleries in the museum building.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY required |
| q | FIELD:VALUE |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |
| aggregation |  see [Elasticsearch aggregations](http://www.elastic.co/guide/en/elasticsearch/reference/1.4/search-aggregations.html#_structuring_aggregations) |
| usedby | FIELD NAME:ID |
| floor | 0-5 |

#### Examples

> http://api.harvardartmuseums.org/gallery?floor=2  
> Returns all records for galleries that are on Level 2 in the Harvard Art Museums building. 

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 24,
        "pages": 3,
        "page": 1
    },
    "records": [
        {
            "gallerynumber": "2300",
            "objectcount": 27,
            "id": 2300,
            "lastupdate": "2015-01-09T04:07:36-0500",
            "floor": 2,
            "name": "European Art, 17th–19th century",
            "theme": "Seventeenth–Century Dutch and Flemish Art",
            "galleryid": 2300
        },
        {
            "gallerynumber": "2540",
            "objectcount": 35,
            "id": 2540,
            "lastupdate": "2015-01-09T04:07:36-0500",
            "floor": 2,
            "name": "European Art, 13th–16th century",
            "theme": "The Renaissance",
            "galleryid": 2540
        }
    ]
}
```

## Get gallery

`GET /gallery/GALLERY_ID` will get detailed info about a specific gallery.

#### Examples

> http://api.harvardartmuseums.org/gallery/1740  
> Returns the full record for the gallery “Early Chinese Art”.

#### Response

```json
{
    "galleryid": 1740,
    "gallerynumber": "1740",
    "name": "Early Chinese Art",
    "floor": 1,
    "theme": "Arts of Ancient China from the Neolithic to the Bronze Age",
    "objectcount": 166,
    "id": 1740,
    "lastupdate": "2015-01-09T04:07:36-0500",
    "contains": {
        "groups": [
            {
                "name": "Collection Highlights",
                "groupid": 2039923
            },
            {
                "name": "Hotspots",
                "groupid": 2040117
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