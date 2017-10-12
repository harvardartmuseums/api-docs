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
| floor | FLOOR NUMBER or pipe separated list of FLOOR NUMBERS; acceptable floor numbers are 0 through 5 |

#### Examples

> https://api.harvardartmuseums.org/gallery?floor=2  
> Returns all records for galleries that are on floor (Level) 2 in the Harvard Art Museums building. 

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

> https://api.harvardartmuseums.org/gallery/1220  
> Returns the full record for the gallery “European Art, 19th–20th century”.

#### Response

```json
{
    "galleryid": 1220,
    "gallerynumber": "1220",
    "name": "European Art, 19th–20th century",
    "floor": 1,
    "theme": "Collection of Maurice Wertheim, Class of 1906",
    "objectcount": 31,
    "labeltext": "Maurice Wertheim (1886–1950), Harvard Class of 1906, was an investment banker from New York. He began amassing his renowned collection in the 1930s, acquiring masterpieces by famed artists like Edgar Degas, Claude Monet, and Pierre-Auguste Renoir, as well as contemporary figures such as Aristide Maillol, Henri Matisse, and Pablo Picasso. His interest in modern art was informed by recommendations from advisors, who included Alfred M. Frankfurter, editor of the highly read periodical Art News, and Paul J. Sachs, associate director of the Fogg Art Museum from 1923–45.\r\nWertheim’s decision to focus on nineteenth- and twentieth-century art also derived from practical considerations. Like other American collectors purchasing art after World War I, Wertheim perceived that art from this era was both critically acclaimed and financially accessible. An added benefit, for him, was the fact that its scale and varied styles were well suited to his modern penthouse apartment on the Upper East Side of New York City, where the works were first installed.\r\nWertheim bequeathed his collection to Harvard, to be studied and enjoyed by students and scholars, with the stipulation that it be shown together in a single gallery.",
    "id": 1220,
    "lastupdate": "2015-11-22T03:11:38-0500",
    "contains": {
        "groups": [
            {
                "name": "Collection Highlights",
                "groupid": 2039923
            },
            {
                "name": "Art and Science",
                "groupid": 2040113
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